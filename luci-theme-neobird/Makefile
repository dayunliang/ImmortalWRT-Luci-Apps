# SPDX-License-Identifier: MIT
#
# Makefile for luci-theme-neobird (ImmortalWRT 23.05 兼容)

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-theme-neobird
PKG_VERSION:=2.0
PKG_RELEASE:=1

LUCI_TITLE:=LuCI Theme - Neobird (ImmortalWRT 23.05)
LUCI_PKGARCH:=all
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=dayunliang <youremail@example.com>

include $(INCLUDE_DIR)/package.mk

define Package/luci-theme-neobird
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=Themes
  TITLE:=$(LUCI_TITLE)
  DEPENDS:=+luci-base
endef

define Package/luci-theme-neobird/description
  Neobird 主题，为 ImmortalWRT (OpenWrt 23.05) 定制：
  - 适配最新 LuCI 23.05 API
  - 修复 __entries 全局变量兼容性
  - 去除多余控制器拷贝，精简 Makefile
endef

define Build/Prepare
	# 源码已经在当前目录，无需额外准备
	true
endef

define Build/Compile
	# 主题无需编译，直接跳过
	true
endef

define Package/luci-theme-neobird/install
	# 1. 安装 Lua 视图文件 (*.htm)
	mkdir -p $(1)/usr/lib/lua/luci/view/themes/neobird
	cp -fpR ./luasrc/view/themes/neobird/* $(1)/usr/lib/lua/luci/view/themes/neobird/

	# 2. 安装静态资源 (css、js、images、fonts 等)
	mkdir -p $(1)/www/luci-static/neobird
	cp -fpR ./htdocs/luci-static/neobird/* $(1)/www/luci-static/neobird/

	# 3. 安装 UCI 默认安装脚本
	mkdir -p $(1)/etc/uci-defaults
	install -m 0755 ./root/etc/uci-defaults/30_luci-theme-neobird $(1)/etc/uci-defaults/30_luci-theme-neobird
endef

$(eval $(call BuildPackage,luci-theme-neobird))
