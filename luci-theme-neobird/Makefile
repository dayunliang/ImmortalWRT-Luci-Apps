#
# Makefile for luci-theme-neobird (ImmortalWRT 23.05 兼容版本，方案 B)
#
# 上游版本信息：
#   Title: Neobird Theme
#   Version: 2.0
#   Release: 202202260758
#
# License: GPL-2.0
# Maintainer: Your Name <your.email@example.com>
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luci-theme-neobird
PKG_VERSION:=2.0
PKG_RELEASE:=202202260758
PKG_MAINTAINER:=Your Name <your.email@example.com>
PKG_LICENSE:=GPL-2.0

# 对 ImmortalWRT 23.05，需要依赖 luci-compat 与 luci-base，以保证 API 向后兼容
DEPENDS:=+luci-compat +luci-base

include $(INCLUDE_DIR)/package.mk

# 主题包在 LuCI 中的元信息
define Package/luci-theme-neobird
  SECTION:=luci
  CATEGORY:=LuCI
  SUBMENU:=Themes
  TITLE:=Neobird Theme (ImmortalWRT 23.05)
  DEPENDS:=$(DEPENDS)
endef

define Package/luci-theme-neobird/description
  Neobird 主题，已针对 ImmortalWRT (OpenWrt 23.05) 做兼容性修改。
  - Lua 模板放在 usr/lib/lua/luci/view/themes/neobird/
  - Lua 控制器脚本（若有）放在 usr/lib/lua/luci/controller/
  - 静态资源放在 www/luci-static/neobird/（源路径为 htdocs/luci-static/neobird/）
  - 依赖 luci-compat, luci-base，确保在 ImmortalR23.05 下正常加载 LuCI 核心 API。
endef

# 该主题无需编译，直接“复制（install）”即可
define Build/Compile
	true
endef

# 安装步骤：分三部分安装 HTM、Lua 控制器、静态资源
define Package/luci-theme-neobird/install
	# 1. 安装 Lua 视图模板 (*.htm) 到目标路径
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view/themes/neobird
	$(CP) ./luasrc/view/* $(1)/usr/lib/lua/luci/view/themes/neobird/

	# 2. 安装 Lua 控制器（如果存在 lua 脚本）
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/controller
	$(CP) ./luasrc/controller/* $(1)/usr/lib/lua/luci/controller/

	# 3. 安装静态资源 (CSS/JS/图片) 到 www/luci-static/neobird
	#    源路径改为 ./htdocs/luci-static/neobird/*
	$(INSTALL_DIR) $(1)/www/luci-static/neobird
	$(CP) -r ./htdocs/luci-static/neobird/* $(1)/www/luci-static/neobird/

	# 4. 安装配置文件（可选）
	$(INSTALL_DIR) $(1)/etc/config
	$(CP) ./etc/config/luci-theme-neobird $(1)/etc/config/luci-theme-neobird
endef

# 调用 BuildPackage 注册本包
$(eval $(call BuildPackage,luci-theme-neobird))

