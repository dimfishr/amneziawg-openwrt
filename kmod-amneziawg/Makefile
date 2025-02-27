include $(TOPDIR)/rules.mk

PKG_NAME:=kmod-amneziawg
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_URL:=https://github.com/dimfishr/wolf-wireguard-kernel.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2025-02-28
PKG_SOURCE_VERSION:=ab46f8c5c1842304b431861a8bf0d56322a98a04
PKG_MIRROR_HASH:=baf216926e12b634a24819e648e5d008e011163c527e705030030979c5b5d1ea

PKG_BUILD_PARALLEL:=1
PKG_FLAGS:=nonshared

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/amneziawg
	SECTION:=kernel
	CATEGORY:=Kernel modules
	SUBMENU:=Network Support
	URL:=https://amnezia.org/
	MAINTAINER:=Amnezia Admin <admin@amnezia.org>
	TITLE:=AmneziaWG Kernel Module
	FILES:=$(PKG_BUILD_DIR)/amneziawg.ko
	DEPENDS:= \
		+kmod-udptunnel4 \
		+IPV6:kmod-udptunnel6
  AUTOLOAD:=$(call AutoLoad,31,amneziawg,1)
endef

define Build/Compile
	+$(KERNEL_MAKE) $(PKG_JOBS) \
		-C "$(LINUX_DIR)" \
		M="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="$(EXTRA_CFLAGS)" \
		modules
endef

$(eval $(call KernelPackage,amneziawg))
