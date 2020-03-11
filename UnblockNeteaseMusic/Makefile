include $(TOPDIR)/rules.mk

PKG_NAME:=UnblockNeteaseMusic
PKG_VERSION:=0.1.9
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/cnsilvan/UnblockNeteaseMusic/tar.gz/$(PKG_VERSION)?
PKG_HASH:=skip
PKG_MAINTAINER:=Silvan <cnsilvan@gmail.com>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/cnsilvan/UnblockNeteaseMusic
GO_PKG_LDFLAGS:=-s -w
# +%Y-%m-%d %H:%M:%S cause compile error 
COMPILE_TIME := $(shell TZ=UTC-8 date '+%Y-%m-%d %H:%M:%S')
GO_PKG_LDFLAGS+= \
	-X '$(GO_PKG)/version.Version=$(PKG_VERSION)' \
	-X '$(GO_PKG)/version.BuildTime=$(COMPILE_TIME)' 
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Revive unavailable songs for Netease Cloud Music (Golang)
	URL:=https://github.com/cnsilvan/UnblockNeteaseMusic
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef
define Package/$(PKG_NAME)/description
	Revive unavailable songs for Netease Cloud Music (Golang)
endef
define Build/Prepare
	# tar -xzf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR)
	# unzip -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE)
	 $(call Build/Prepare/Default)
endef

define Build/Configure
endef

define Build/Compile
	$(eval GO_PKG_BUILD_PKG:=$(GO_PKG))
	$(call GoPackage/Build/Configure)
	$(eval GO_PKG_LDFLAGS+=-X '$(GO_PKG)/version.ExGoVersionInfo=$(GO_ARM) $(GO_MIPS)$(GO_MIPS64)')
	$(call GoPackage/Build/Compile)
	$(STAGING_DIR_HOST)/bin/upx --lzma --best $(GO_PKG_BUILD_BIN_DIR)/UnblockNeteaseMusic
	chmod +wx $(GO_PKG_BUILD_BIN_DIR)/UnblockNeteaseMusic
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/UnblockNeteaseMusic $(1)/usr/bin/UnblockNeteaseMusic
	$(INSTALL_DIR) $(1)/usr/share/UnblockNeteaseMusic
	
endef
$(eval $(call GoBinPackage,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))
