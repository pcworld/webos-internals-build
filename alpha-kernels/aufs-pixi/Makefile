NAME           = $(shell basename $(shell pwd))
APP_ID         = org.webosinternals.modules.${NAME}
TITLE          = AUFS module
CATEGORY       = Filesystem
VERSIONS       = 1.4.5-97
BLDFLAGS       = -p
DESCRIPTION    = This is the AUFS (Another Union FileSystem) kernel module for the Pixi/Pixi+.  AUFS is useful for mounting rw overlays on ro filesystems.  
CHANGELOG      = 
DEVICE         = pixi
SRC_GIT = git://git.webos-internals.org/kernels/patches.git
KERNEL_UPSTART = aufs/upstart.${DEVICE}
EXTERNAL_MODULES  = aufs
SUFFIX='-${DEVICE}'
TYPE = Kernel Module

include ../../support/kernel.mk
