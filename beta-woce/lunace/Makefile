NAME = $(shell basename $(shell pwd))
TITLE = LunaCE
DEVICE = touchpad
DESCRIPTION = ${APPINFO_DESCRIPTION}<br>${KERNEL_DISCLAIMER}
CATEGORY = User Interface
VERSION = 4.5.2
APPINFO_DESCRIPTION = A collection of all the best LunaSysMgr improvements for the HP TouchPad, rolled into a single convenient installation package.<br><br>\
To upgrade from the alpha versions (<= 4.4.2) of LunaCE to the beta version (4.5.0) of LunaCE you need to first remove the existing LunaCE package manually, as the package id has changed.<br><br>\
Current additions include:<ul>\
<li>App switching bezel gestures.</li>\
<li>Tabbed card support.</li>\
<li>Infinite card cycling.</li>\
<li>Maximizable edge cards.</li>\
<li>Lower minimum brightness for better night-time reading.</li>\
<li>A status bar search button.</li>\
<li>Show the device name instead of HP webOS.</li>\
<li>Additional keyboard layouts.</li>\
<li>Ability to remove the Tap Ripple.</li>\
<li>Additional gesture detection engines.</li>\
<li>New APIs for developers. (See <a href="http://webos-ports.org/wiki/LunaCE_APIs">LunaCE APIs</a> for details.)</li>\
<li>Other various user interface refinements and improvements.</li>\
</ul>\
All additions are controlled by using the Tweaks application.<br>\
You need to remove your PIN code before installing this package, and all your saved passwords will need to be entered again.<br>
APPINFO_CHANGELOG = [ \
{ "version" : "4.5.2", "log" : [ "Fixed Fluid Gestures behaviour in portrait orientations." ] }, \
{ "version" : "4.5.1", "log" : [ "Additional keyboard layouts and fixes, large improvements to Fluid Gestures." ] }, \
{ "version" : "4.5.0", "log" : [ "Fixed missing Mojo encryption functions" ] }, \
{ "version" : "4.4.2", "log" : [ "Added the Tap Ripple tweak", "Added Dynamic Dashboard height API", "New keyboard layouts", "Various bug fixes" ] }, \
{ "version" : "4.3.5", "log" : [ "Fixes various bugs introduced in 4.3.x" ] }, \
{ "version" : "4.3.4", "log" : [ "Fixed compatibility between Tabbed Cards and Fluid Gestures" ] }, \
{ "version" : "4.3.3", "log" : [ "Restored fluid upswipe functionality" ] }, \
{ "version" : "4.3.2", "log" : [ "Disabled fluid gesture upswipe due to conflict" ] }, \
{ "version" : "4.3.1", "log" : [ "New fluid gesture detection system" ] }, \
{ "version" : "4.2.0", "log" : [ "Fixed input focus issue" ] }, \
{ "version" : "4.1.1", "log" : [ "Fixed some features" ] }, \
{ "version" : "4.1.0", "log" : [ "Added some more features" ] }, \
{ "version" : "4.0.0", "log" : [ "Initial public release" ] } \
]

HOMEPAGE = http://www.webos-ports.org
TYPE = OS Application

SRC_GIT = git://github.com/woce/LunaSysMgr-binaries.git

include ../../support/woce.mk

build/.unpacked-${VERSION}: ${DL_DIR}/${NAME}-${VERSION}.tar.gz
	rm -rf build
	mkdir -p build/src
	tar -C build/src -xf ${DL_DIR}/${NAME}-${VERSION}.tar.gz
	touch $@

build/arm.built-${VERSION}: build/.unpacked-${VERSION} ${WEBOS_DOCTOR}
	rm -rf build/arm
	mkdir -p build/arm/usr/palm/applications/${APP_ID}/additional_files
	unzip -p ${WEBOS_DOCTOR} resources/webOS.tar | \
	${TAR} -O -x -f - ./nova-cust-image-${CODENAME}.rootfs.tar.gz | \
	${TAR} -C build/arm/usr/palm/applications/${APP_ID}/additional_files/ -m -z -x -f - ./md5sums.gz
	gunzip -f build/arm/usr/palm/applications/${APP_ID}/additional_files/md5sums.gz
	mkdir -p build/arm/usr/palm/applications/${APP_ID}/additional_files/etc/event.d
	cp upstart/LunaSysMgr build/arm/usr/palm/applications/${APP_ID}/additional_files/etc/event.d/LunaSysMgr
	mkdir -p build/arm/usr/palm/applications/${APP_ID}/additional_files/usr/bin
	cp build/src/bin/LunaSysMgr build/arm/usr/palm/applications/${APP_ID}/additional_files/usr/bin/LunaSysMgr
	mkdir -p build/arm/usr/palm/applications/${APP_ID}/additional_files/etc/palm
	cp build/src/configs/lunaAnimations.conf build/arm/usr/palm/applications/${APP_ID}/additional_files/etc/palm/lunaAnimations.conf
	mkdir -p build/arm/usr/palm/applications/${APP_ID}/additional_files/tweaks
	cp build/src/tweaks/* build/arm/usr/palm/applications/${APP_ID}/additional_files/tweaks
	touch $@
