#
# Copyright (C) 2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=shairport
PKG_VERSION:=0.05
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/sancome/shairport.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=136bad5e875cb4f92e551c670eb40eb171e61487
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk


define Package/shairport/Default
  SECTION:=sound
  CATEGORY:=Sound
  TITLE:=ShairPort
  URL:=http://mafipulation.org/
endef


define Package/shairport
  $(Package/shairport/Default)
  DEPENDS:= +libopenssl +libao +avahi-daemon-dbus +avahi-utils
endef

define Package/shairport/description
  ShairPort is server software that implements the RAOP protocol for
  playback of music streamed from a compatible remote client.
endef


define Package/shairport/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/{hairtunes,shairport} $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_BIN) ./files/init.d/shairport $(1)/etc/init.d/
	$(INSTALL_DATA) ./files/config/shairport $(1)/etc/config/
endef


$(eval $(call BuildPackage,shairport))
