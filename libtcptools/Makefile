include $(TOPDIR)/rules.mk

PKG_NAME:=libtcptools
PKG_VERSION:=1.0.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/apietila/libtcptools.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/libtcptools
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Libtcptools library for TCP analysis.
	URL:=http://research.wand.net.nz/software/libtcptools.php
	DEPENDS:=+libtrace
endef

define Package/libtcptools/description
	Libtcptools is a library that leverages libtrace to perform several 
	useful TCP analysis tasks, including RTT estimation, classification 
	of reordering events and bandwidth estimation.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtcptools.{a,so*} $(1)/usr/lib/
endef

define Package/libtcptools/install    
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/libtcptools.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtcptools))

