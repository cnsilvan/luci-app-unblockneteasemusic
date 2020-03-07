# Copyright (C) 2020 Silvan
include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI support for UnblockNeteaseMusic
LUCI_DEPENDS:= +bash +busybox +coreutils-nohup +curl +dnsmasq-full +ipset +UnblockNeteaseMusic
LUCI_PKGARCH:=all
PKG_NAME:=luci-app-unblockneteasemusic
PKG_VERSION:=1.6
PKG_RELEASE:=1

PKG_MAINTAINER:=https://github.com/cnsilvan/luci-app-unblockneteasemusic

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
