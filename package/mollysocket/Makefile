include $(TOPDIR)/rules.mk

PKG_NAME:=mollysocket
PKG_VERSION:=1.7.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/mollyim/mollysocket/tar.gz/$(PKG_VERSION)?
PKG_HASH:=db9d913af9e285422f260397acbf4341d48c1e7d2e0b50b08b209e2101a63fea

PKG_LICENSE:=AGPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/mollysocket
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=MollySocket UnifiedPush bridge
  URL:=https://github.com/mollyim/mollysocket
  DEPENDS:=$(RUST_ARCH_DEPENDS) +ca-bundle +libopenssl +libsqlite3 +libncurses
endef

define Package/mollysocket/description
  MollySocket allows getting Signal notifications via UnifiedPush.
endef

define Package/mollysocket/conffiles
/etc/mollysocket.conf
endef

define Package/mollysocket/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/mollysocket $(1)/usr/bin/mollysocket

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/mollysocket.init $(1)/etc/init.d/mollysocket

	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/mollysocket.conf $(1)/etc/mollysocket.conf
endef

$(eval $(call RustBinPackage,mollysocket))
$(eval $(call BuildPackage,mollysocket))
