#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
#
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		memcache
COMPONENT_VERSION=	2.2.5
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tgz
COMPONENT_ARCHIVE_HASH=	\
    sha256:5307dad7952a5ba3b742969061b2235ee87cc51e267e40fc7e496b0e49148666
COMPONENT_ARCHIVE_URL=	http://pecl.php.net/get/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=	http://pecl.php.net/package/memcache/

include ../extensions.mk

CONFIGURE_OPTIONS  += \
	--disable-debug \
	--enable-memcache \
	--with-zlib-dir=/usr

COMPONENT_POST_INSTALL_ACTION = ( \
	$(MKDIR) $(PROTO_DIR)/$(APACHE2_SAMPLES_CONFDIR); \
	$(INSTALL) -m 0644 $(COMPONENT_DIR)/../Solaris/php-memcache-stats.conf \
		$(PROTO_DIR)/$(APACHE2_SAMPLES_CONFDIR); \
	$(MKDIR) $(PROTO_DIR)/usr/php/5.2/samples/memcache; \
	$(INSTALL) -m 0555 $(SOURCE_DIR)/memcache.php \
		$(PROTO_DIR)/usr/php/5.2/samples/memcache/memcache.php; \
	) ; \
	$(FIX_CONFIG_FILES)

PKG_PROTO_DIRS += $(COMPONENT_DIR)/../memcache-zts/build/prototype/$(MACH)
