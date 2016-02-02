include $(TOPDIR)/rules.mk

PKG_NAME:=libtrace-tools-extra
PKG_RELEASE:=0.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/apietila/libtrace-tools-extra.git
PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_VERSION:=HEAD
PKG_SOURCE_SUBDIR:=$(PKG_NAME)

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/libtrace-tools-extra
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libtrace +libtcptools
	TITLE:=libtrace-tools-extra
endef

define Package/libtrace-tools-extra/description
	Libtrace based tools for packet trace analysis.
endef

define Package/libtrace-tools-extra/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tracepktiv $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tracertt $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libtrace-tools-extra))

