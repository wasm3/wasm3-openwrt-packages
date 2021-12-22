include $(TOPDIR)/rules.mk

PKG_NAME:=wasm3
PKG_VERSION:=0.5.0
PKG_RELEASE:=1

PKG_MAINTAINER:=Volodymyr Shymanskyy
PKG_LICENSE:=MIT

#PKG_SOURCE_URL:=file:///path/to/local/wasm3/

PKG_SOURCE_URL:=https://github.com/wasm3/wasm3/archive/main.tar.gz
#PKG_SOURCE_URL:=https://github.com/wasm3/wasm3/archive/v$(PKG_VERSION).tar.gz
#PKG_HASH:=b778dd72ee2251f4fe9e2666ee3fe1c26f06f517c3ffce572416db067546536c
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/wasm3
  SUBMENU:=WebAssembly
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=The fastest WebAssembly interpreter
  URL:=https://github.com/wasm3/wasm3
endef

define Package/wasm3/description
 wasm3 is the fastest WebAssembly interpreter
endef

MAKE_PATH := platforms/openwrt/build

MAKE_FLAGS += LD="$(TARGET_CC)"
MAKE_FLAGS += RELEASE=1
MAKE_FLAGS += OPENWRT_UCLIBC=1

define Package/wasm3/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/$(MAKE_PATH)/wasm3 $(1)/usr/bin/
endef

$(eval $(call BuildPackage,wasm3))
