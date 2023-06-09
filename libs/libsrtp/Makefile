#
# Copyright (C) 2014 BoluWrt.org
# Copyright (C) 2011 Victor Seva <linuxmaniac@torreviejawireless.org>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=libsrtp
PKG_VERSION:=1.4.4
PKG_RELEASE:=1

PKG_SOURCE:=srtp-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=@SF/srtp
PKG_MD5SUM:=9b449edb011c934ca97009e7e0566d22

PKG_BUILD_DIR:=$(BUILD_DIR)/srtp
PKG_INSTALL:=1

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jiri Slachta <jiri@slachta.eu>

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS += $(FPIC)
CONFIGURE_ARGS += --disable-stdout --enable-syslog

define Package/libsrtp
  SUBMENU:=Telephony
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Secure Real-time Transport Protocol (SRTP) library
  URL:=http://sourceforge.net/projects/srtp
endef

define Package/libsrtp/description
Open-source implementation of the Secure Real-time Transport
Protocol (SRTP) originally authored by Cisco Systems, Inc.
It is available under a BSD-style license.
endef

define Build/Install
	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR=$(PKG_INSTALL_DIR) uninstall
	$(call Build/Install/Default)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/srtp $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsrtp.{a,so*} $(1)/usr/lib/
endef


define Package/libsrtp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsrtp.so.* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsrtp))
