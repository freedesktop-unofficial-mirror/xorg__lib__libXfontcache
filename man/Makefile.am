#
# Copyright 2005 Sun Microsystems, Inc.  All rights reserved.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
# DEALINGS IN THE SOFTWARE.
# 

libmandir = $(LIB_MAN_DIR)

LIB_MAN_DIR_SUFFIX = $(LIB_MAN_DIR:@mandir@/man%=%)

libman_PRE = Xfontcache.man

EXTRA_DIST = $(libman_PRE)

CLEANFILES = $(libman_DATA) $(BUILT_SOURCES)

libman_DATA = $(libman_PRE:man=@LIB_MAN_SUFFIX@) \
	      $(Xfontcache_shadowmen)

SED = sed

# Strings to replace in man pages
XORGRELSTRING = @PACKAGE_STRING@
  XORGMANNAME = X Version 11

MAN_SUBSTS = \
	-e 's/__vendorversion__/"$(XORGRELSTRING)" "$(XORGMANNAME)"/' \
	-e 's/__xservername__/Xorg/g' \
	-e 's/__xconfigfile__/xorg.conf/g' \
	-e 's/__miscmansuffix__/$(MISC_MAN_SUFFIX)/g' \
	-e 's/__libmansuffix__/$(LIB_MAN_SUFFIX)/g' \
	-e 's/__filemansuffix__/$(FILE_MAN_SUFFIX)/g'

SUFFIXES = .$(LIB_MAN_SUFFIX) .man

.man.$(LIB_MAN_SUFFIX):
	$(AM_V_GEN)$(SED) $(MAN_SUBSTS) < $< > $@

# Generate man page shadow files (Replaces InstallManPageAliases from Imake)

Xfontcache_shadows =                        \
    FontCacheQueryExtension                 \
    FontCacheQueryVersion                   \
    FontCacheGetCacheSettings               \
    FontCacheChangeCacheSettings            \
    FontCacheGetCacheStatistics

Xfontcache_shadowmen = $(Xfontcache_shadows:=.@LIB_MAN_SUFFIX@)

$(Xfontcache_shadowmen):
	$(AM_V_GEN)echo .so man$(LIB_MAN_DIR_SUFFIX)/Xfontcache.$(LIB_MAN_SUFFIX) > $@
