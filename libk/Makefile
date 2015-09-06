# Added to inteno by Martin Schröder
# used by JUCI lua backend 

include $(TOPDIR)/rules.mk

PKG_NAME:=libk
PKG_VERSION:=devel
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/mkschreder/martink.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:=1
MAKE += BUILD=linux-generic

include $(INCLUDE_DIR)/package.mk

define Package/libk
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Cross-platform Userspace Device Drivers Library
  URL:=https://github.com/mkschreder/martink
  DEPENDS:=
endef

define Package/libk/description
 LibK is a userspace device drivers library that works on a variety of platforms, 
 including bare AVR and STM32 platforms - as well as linux. 
endef

define Build/Configure
	( cd $(PKG_BUILD_DIR); [ ! -f include/autoconf.h ] && $(MAKE) oldconfig)
	$(call Build/Configure/Default)
endef

define Build/InstallDev
	#$(INSTALL_DIR) $(1)/usr/include/
	#$(CP) \
	#	$(PKG_INSTALL_DIR)/usr/include/* \
	#	$(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libk*.a \
		$(1)/usr/lib/

	#$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	#$(CP) \
	#	$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libk.pc \
	#	$(1)/usr/lib/pkgconfig/
endef

define Package/libk/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libk*.a \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libk))

