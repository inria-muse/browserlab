#
# Copyright (C) 2007-2010 OpenWrt.org (original iperf)
# Copyright (C) 2014 Anna-Kaisa Pietilainen <anna-kaisa.pietilainen@inria.fr>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=iperfng
PKG_VERSION:=2.0.6
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/apietila/iperf-ng.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

define Package/iperfng/Default
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:= $(CXX_DEPENDS)
  TITLE:=Internet Protocol bandwidth measurement tool
  URL:=https://github.com/apietila/iperf-ng
endef

define Package/iperfng/Default/description
 Iperf is a modern alternative for measuring TCP and UDP bandwidth
 performance, allowing the tuning of various parameters and
 characteristics. Iperf-NG adds NAT traversal and JSON output options.
endef

define Package/iperfng
$(call Package/iperfng/Default)
  TITLE+= (with single thread support)
  VARIANT:=single
endef

define Package/iperfng/description
$(call Package/iperfng/Default/description)
 This package is built with single thread support.
endef

define Package/iperfng-mt
$(call Package/iperfng/Default)
  DEPENDS+= +libpthread
  TITLE+= (with multithread support)
  VARIANT:=mt
endef

define Package/iperfng-mt/description
$(call Package/iperfng/Default/description)
 This package is built with multithread support.
endef

CONFIGURE_ARGS += --disable-multicast
CONFIGURE_VARS += ac_cv_func_malloc_0_nonnull=yes

ifeq ($(BUILD_VARIANT),single)
  CONFIGURE_ARGS += --disable-threads
else
  CONFIGURE_ARGS += --enable-threads=posix
  CONFIGURE_VARS += ac_cv_func_pthread_cancel=no
endif

CONFIGURE_VARS += CXXFLAGS="$$$$CXXFLAGS -fno-rtti"

ifeq ($(BUILD_VARIANT),mt)
  CONFIGURE_VARS += LIBS="-lpthread"
endif

define Package/iperfng/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/iperf $(1)/usr/bin/iperfng
endef
Package/iperfng-mt/install = $(Package/iperfng/install)

$(eval $(call BuildPackage,iperfng))
$(eval $(call BuildPackage,iperfng-mt))
