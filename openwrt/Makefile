#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=eoip
PKG_VERSION:=0.5
PKG_RELEASE:=2

PKG_SOURCE_URL:=https://github.com/Npeca75/eoip
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-02-06
PKG_SOURCE_VERSION:=PLACE HASH HERE !!!!

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/linux-eoip/Default
  TITLE:=Mikrotik-compatible userspace EoIP tunnel
  URL:=http://code.google.com/p/linux-eoip/
endef

define Package/eoip
  $(call Package/eoip/Default)
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+kmod-tun +libpthread +liblzo
  TITLE+= (command line)
endef

define Package/eoip/conffiles
/etc/config/eoip
endef

define Package/eoip/description
  eoip can create ethernet tunnels compatible with Mikrotik EoIP tunnel.
endef

TARGET_CFLAGS += -std=gnu99

CONFIGURE_ARGS += \
        --with-kernel="$(LINUX_DIR)" \
        --with-zlib="$(STAGING_DIR)/usr" \
        --with-lzo-include="$(STAGING_DIR)/usr/include/lzo"

define Package/eoip/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/eoip $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/files/eoip.config $(1)/etc/config/eoip
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/files/eoip.init $(1)/etc/init.d/eoip
endef

$(eval $(call BuildPackage,eoip))
