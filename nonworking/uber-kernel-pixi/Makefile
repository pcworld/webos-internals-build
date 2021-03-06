NAME = $(shell basename $(shell pwd))
TITLE = UberKernel (Pixi/Pixi+)
DEVICE   = pixi
CATEGORY = Experimental
VERSIONS = 1.5.0-124
APPINFO_DESCRIPTION = A collection of all the best kernel improvements for the Palm Pixi/Pixi+, rolled into a single OTA-safe installation package.<br>\
<b>Note that usage of this package is very likely to <a href=http://developer.palm.com/blog/2010/03/a-statement-on-the-overclocking-patches/>void your warranty</a> if things go wrong.</b><br>\
Current additions include:<ul>\
<li>748.8MHz and 768MHz kernel operating points, based on information from the Android community, ported to the Palm Pre/Pre+ by jhojho and rwhitby</li>\
<li>Modification of the lowmemnotify threshold calculation to take into account free swap space, written by rwhitby</li>\
<li>A new <a href=http://lwn.net/Articles/334649/><b>compcache</b> compressed RAM swap kernel module</a> ported to the Palm Pixi/Pixi+ by uNiXpSyChO & rwhitby</li>\
<li>All standard Linux 2.6.24 <a href=http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/index.html>cpufreq governors</a> made available for selection via the Govnah application</li>\
<li>Additions to the USB mass storage driver for XBox 360 compatibility.  Note that your USB drive may be reformatted when you plug it into an XBox 360.</li>\
<li>Support for kernel crypto modules required by TrueCrypt</li>\
</ul><br>\
All additions are disabled by default, and must be enabled by using the Govnah application.<br>\
For more information, visit <a href=${HOMEPAGE}>${HOMEPAGE}</a>
DESCRIPTION = ${APPINFO_DESCRIPTION}<br>${KERNEL_DISCLAIMER}
APPINFO_CHANGELOG = [ \
{ "version" : "${WEBOS_VERSION}-124", "log" : [ "Disable Palm diagnostics reporting when installed" ] }, \
{ "version" : "${WEBOS_VERSION}-122", "log" : [ "Make UberKernel/Pixi overclocking compliant with the 7 principes of kernel design and packaging" ] }, \
{ "version" : "${WEBOS_VERSION}-121", "log" : [ "Added 768MHz Pixi overclocking", "Added crypto module support for TrueCrypt" ] }, \
{ "version" : "${WEBOS_VERSION}-118", "log" : [ "Added 750MHz Pixi overclocking" ] }, \
{ "version" : "${WEBOS_VERSION}-113", "log" : [ "Added USB mass storage patch for XBox360 compatibility" ] }, \
{ "version" : "${WEBOS_VERSION}-74", "log" : [ "Improved verification of target files for no existing modifications" ] }, \
{ "version" : "${WEBOS_VERSION}-58", "log" : [ "Incorporated compile flag performance improvements" ] }, \
{ "version" : "${WEBOS_VERSION}-43", "log" : [ "Updated with latest postinst and prerm OTA safety measures" ] }, \
{ "version" : "${WEBOS_VERSION}-40", "log" : [ "First Pixi custom kernel" ] }, \
]
CHANGELOG = \
${WEBOS_VERSION}-124: Disable Palm diagnostics reporting when installed.<br>\
${WEBOS_VERSION}-122: Make UberKernel/Pixi overclocking compliant with the 7 principles of kernel design and packaging.<br>\
${WEBOS_VERSION}-121: Added 768MHz Pixi overclocking. Added crypto module support for TrueCrypt.<br>\
${WEBOS_VERSION}-118: Added 750MHz Pixi overclocking.<br>\
${WEBOS_VERSION}-113: Added USB mass storage patch for XBox360 compatibility.<br>\
${WEBOS_VERSION}-74: Improved verification of target files for no existing modifications.<br>\
${WEBOS_VERSION}-50: Incorporated compile flag performance improvements.<br>\
${WEBOS_VERSION}-43: Updated with latest postinst and prerm OTA safety measures.<br>\
${WEBOS_VERSION}-40: First Pixi custom kernel

HOMEPAGE = http://www.webos-internals.org/wiki/Application:UberKernel
SRC_GIT = git://git.webos-internals.org/kernels/patches.git
KERNEL_PATCHES = overclocking/pixi-acpuclock.patch \
		 overclocking/pixi-freq-table.patch overclocking/pixi-freq-set.patch \
		 makefiletune/armMakefile.diff \
		 defconfig/defconfig.pixi.cpugov \
		 compcache/compcache.patch compcache/lowmemnotify-total-memory.patch \
		 usb/f_mass_storage.patch crypto/truecrypt-support-pixi.patch
EXTERNAL_MODULES = compcache/compcache-0.5.4
TYPE = Kernel

include ../../support/kernel.mk

# Override the compiler
CROSS_COMPILE_arm = $(shell cd ../.. ; pwd)/toolchain/cs09q1armel/build/arm-2009q1/bin/arm-none-linux-gnueabi-
