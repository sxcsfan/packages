#
# Copyright (C) 2018 Daniel Engberg <daniel.engberg.lists@pyret.net>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=fio
PKG_VERSION:=3.9
PKG_RELEASE:=1
PKG_MAINTAINER:=Dragan Stancevic <ds@codeminutia.com>
PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE_URL:=http://brick.kernel.dk/snaps
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_HASH:=74737319addca4eb33051a07e481b425757c54a69999b7cd9884bc3b8c54c4b5

include $(INCLUDE_DIR)/package.mk

define Package/fio
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Disc
  DEPENDS:=+libaio +zlib
  TITLE:=I/O testing and benchmarking tool
  URL:=https://github.com/axboe/fio
endef

define Package/fio/description
  Fio is an I/O testing tool that will spawn a number of threads or
  processes doing a particular type of I/O action as specified by
  the user. Fio can be driven by a 'job file' describing the I/O
  load one wants to simulate.
endef

TARGET_CFLAGS := $(filter-out -O%,$(TARGET_CFLAGS))

CONFIGURE_ARGS = \
	--disable-numa \
	--disable-rdma \
	--disable-rados \
	--disable-rbd \
	--disable-gfapi \
	--disable-lex \
	--disable-pmem \
	--disable-native \
	--cc="$(TARGET_CC)" \
	--extra-cflags="$(TARGET_CFLAGS)"

define Package/fio/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/fio $(1)/usr/bin/
endef

$(eval $(call BuildPackage,fio))
