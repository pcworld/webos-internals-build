NAME = $(shell basename $(shell pwd))
PATCH = system/${NAME}.patch
TWEAKS =
TITLE = Sync Fix for Stable Upload
DESCRIPTION = Auto sync will now retry uploading new/updated account data (contacts, calendar etc) in next sync, after previous failure due to reasons like network timeout or something
CATEGORY = System
VERSIONS = 2.1.0-219 2.1.1-22 2.1.2-46 2.2.4-71 3.0.2-99 3.0.4-72 3.0.5-34
ICON = http://www.webos-internals.org/images/f/f9/Icon_WebOSInternals_Patch.png
SCREENSHOTS =
META_SUB_VERSION = 1

include ../common.mk

include ../modifications.mk

MAINTAINER = moo <moo.tinys@gmail.com>
HOMEPAGE = http://www.treo8.com/bbs/thread-272398-1-1.html