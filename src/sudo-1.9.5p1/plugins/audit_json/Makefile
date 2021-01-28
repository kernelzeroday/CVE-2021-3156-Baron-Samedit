#
# SPDX-License-Identifier: ISC
#
# Copyright (c) 2020 Todd C. Miller <Todd.Miller@sudo.ws>
#
# Permission to use, copy, modify, and distribute this software for any
# purpose with or without fee is hereby granted, provided that the above
# copyright notice and this permission notice appear in all copies.
#
# THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
# WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
# MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
# ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
# WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
# ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
# OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
#
# plugins/audit_json/Makefile.  Generated from Makefile.in by configure.
#

#### Start of system configuration section. ####

srcdir = .
devdir = $(srcdir)
top_builddir = ../..
top_srcdir = ../..
scriptdir = $(top_srcdir)/scripts
incdir = $(top_srcdir)/include
cross_compiling = no

# Compiler & tools to use
CC = afl-clang
LIBTOOL = $(SHELL) $(top_builddir)/libtool
SED = /usr/bin/sed
AWK = mawk

# Our install program supports extra flags...
INSTALL = $(SHELL) $(top_srcdir)/install-sh -c
INSTALL_OWNER = -o $(install_uid) -g $(install_gid)
INSTALL_BACKUP = 

# Libraries
LT_LIBS = $(top_builddir)/lib/util/libsudo_util.la
LIBS = $(LT_LIBS)

# C preprocessor flags
CPPFLAGS = -I$(incdir) -I$(top_builddir) -DZLIB_CONST -D_FORTIFY_SOURCE=2

# Usually -O and/or -g
CFLAGS = -g -O2 -fvisibility=hidden

# Flags to pass to the link stage
LDFLAGS =  -Wl,--enable-new-dtags -Wl,-z,relro
LT_LDFLAGS =  -Wl,--version-script,$(shlib_map)

# Flags to pass to libtool
LTFLAGS = --tag=disable-static

# Address sanitizer flags
ASAN_CFLAGS = 
ASAN_LDFLAGS = 

# PIE flags
PIE_CFLAGS = -fPIE
PIE_LDFLAGS = -Wc,-fPIE -pie

# Stack smashing protection flags
SSP_CFLAGS = -fstack-protector-strong
SSP_LDFLAGS = -Wc,-fstack-protector-strong

# cppcheck options, usually set in the top-level Makefile
CPPCHECK_OPTS = -q --enable=warning,performance,portability --suppress=constStatement --suppress=compareBoolExpressionWithInt --error-exitcode=1 --inline-suppr -Dva_copy=va_copy -U__cplusplus -UQUAD_MAX -UQUAD_MIN -UUQUAD_MAX -U_POSIX_HOST_NAME_MAX -U_POSIX_PATH_MAX -U__NBBY -DNSIG=64

# splint options, usually set in the top-level Makefile
SPLINT_OPTS = -D__restrict= -checks

# PVS-studio options
PVS_CFG = $(top_srcdir)/PVS-Studio.cfg
PVS_IGNORE = 'V707,V011,V002,V536'
PVS_LOG_OPTS = -a 'GA:1,2' -e -t errorfile -d $(PVS_IGNORE)

# Where to install things...
prefix = /usr/local
exec_prefix = $(prefix)
bindir = $(exec_prefix)/bin
sbindir = $(exec_prefix)/sbin
sysconfdir = /etc
libexecdir = $(exec_prefix)/libexec
datarootdir = $(prefix)/share
localstatedir = $(prefix)/var
plugindir = /usr/local/libexec/sudo

# File mode and map file to use for shared libraries/objects
shlib_enable = yes
shlib_mode = 0644
shlib_exp = $(srcdir)/audit_json.exp
shlib_map = audit_json.map
shlib_opt = audit_json.opt

# User and group ids the installed files should be "owned" by
install_uid = 0
install_gid = 0

#### End of system configuration section. ####

SHELL = /bin/bash

OBJS =	audit_json.lo

IOBJS = $(OBJS:.lo=.i)

POBJS = $(IOBJS:.i=.plog)

LIBOBJDIR = $(top_builddir)/@ac_config_libobj_dir@/

VERSION = 1.9.5p1

all: audit_json.la

depend:
	$(scriptdir)/mkdep.pl --srcdir=$(top_srcdir) \
	    --builddir=`pwd`/$(top_builddir) plugins/audit_json/Makefile.in
	cd $(top_builddir) && ./config.status --file plugins/audit_json/Makefile

Makefile: $(srcdir)/Makefile.in
	cd $(top_builddir) && ./config.status --file plugins/audit_json/Makefile

.SUFFIXES: .c .h .i .lo .plog

.c.lo:
	$(LIBTOOL) $(LTFLAGS) --mode=compile $(CC) -c $(CPPFLAGS) $(CFLAGS) $(ASAN_CFLAGS) $(PIE_CFLAGS) $(SSP_CFLAGS) $<

.c.i:
	$(CC) -E -o $@ $(CPPFLAGS) $<

.i.plog:
	ifile=$<; rm -f $@; pvs-studio --cfg $(PVS_CFG) --sourcetree-root $(top_srcdir) --skip-cl-exe yes --source-file $${ifile%i}c --i-file $< --output-file $@

$(shlib_map): $(shlib_exp)
	@$(AWK) 'BEGIN { print "{\n\tglobal:" } { print "\t\t"$$0";" } END { print "\tlocal:\n\t\t*;\n};" }' $(shlib_exp) > $@

$(shlib_opt): $(shlib_exp)
	@$(SED) 's/^/+e /' $(shlib_exp) > $@

audit_json.la: $(OBJS) $(LT_LIBS) $(shlib_map)
	$(LIBTOOL) $(LTFLAGS) --mode=link $(CC) $(LDFLAGS) $(ASAN_LDFLAGS) $(SSP_LDFLAGS) $(LT_LDFLAGS) -o $@ $(OBJS) $(LIBS) -module -avoid-version -rpath $(plugindir) -shrext .so

pre-install:

install: install-plugin

install-dirs:
	$(SHELL) $(scriptdir)/mkinstalldirs $(DESTDIR)$(plugindir)

install-binaries:

install-includes:

install-doc:

install-plugin: install-dirs audit_json.la
	if [ X"$(shlib_enable)" = X"yes" ]; then \
	    INSTALL_BACKUP='$(INSTALL_BACKUP)' $(LIBTOOL) $(LTFLAGS) --mode=install $(INSTALL) $(INSTALL_OWNER) -m $(shlib_mode) audit_json.la $(DESTDIR)$(plugindir); \
	fi

uninstall:
	-$(LIBTOOL) $(LTFLAGS) --mode=uninstall rm -f $(DESTDIR)$(plugindir)/audit_json.la
	-test -z "$(INSTALL_BACKUP)" || \
	    rm -f $(DESTDIR)$(plugindir)/audit_json.so$(INSTALL_BACKUP)

splint:
	splint $(SPLINT_OPTS) -I$(incdir) -I$(top_builddir) $(srcdir)/*.c

cppcheck:
	cppcheck $(CPPCHECK_OPTS) -I$(incdir) -I$(top_builddir) $(srcdir)/*.c

pvs-log-files: $(POBJS)

pvs-studio: $(POBJS)
	plog-converter $(PVS_LOG_OPTS) $(POBJS)

check:

clean:
	-$(LIBTOOL) $(LTFLAGS) --mode=clean rm -f *.lo *.o *.la *.a *.i *.plog \
	    stamp-* core *.core core.*

mostlyclean: clean

distclean: clean
	-rm -rf Makefile .libs $(shlib_map) $(shlib_opt)

clobber: distclean

realclean: distclean
	rm -f TAGS tags

cleandir: realclean

# Autogenerated dependencies, do not modify
getgrent.lo: $(srcdir)/getgrent.c $(incdir)/compat/stdbool.h \
             $(incdir)/sudo_compat.h $(incdir)/sudo_util.h \
             $(top_builddir)/config.h
	$(LIBTOOL) $(LTFLAGS) --mode=compile $(CC) -c $(CPPFLAGS) $(CFLAGS) $(ASAN_CFLAGS) $(PIE_CFLAGS) $(SSP_CFLAGS) $(srcdir)/getgrent.c
getgrent.i: $(srcdir)/getgrent.c $(incdir)/compat/stdbool.h \
             $(incdir)/sudo_compat.h $(incdir)/sudo_util.h \
             $(top_builddir)/config.h
	$(CC) -E -o $@ $(CPPFLAGS) $<
getgrent.plog: getgrent.i
	rm -f $@; pvs-studio --cfg $(PVS_CFG) --sourcetree-root $(top_srcdir) --skip-cl-exe yes --source-file $(srcdir)/getgrent.c --i-file $< --output-file $@
audit_json.lo: $(srcdir)/audit_json.c $(incdir)/compat/stdbool.h \
               $(incdir)/sudo_compat.h $(incdir)/sudo_plugin.h \
               $(top_builddir)/config.h
	$(LIBTOOL) $(LTFLAGS) --mode=compile $(CC) -c $(CPPFLAGS) $(CFLAGS) $(ASAN_CFLAGS) $(PIE_CFLAGS) $(SSP_CFLAGS) $(srcdir)/audit_json.c
audit_json.i: $(srcdir)/audit_json.c $(incdir)/compat/stdbool.h \
               $(incdir)/sudo_compat.h $(incdir)/sudo_plugin.h \
               $(top_builddir)/config.h
	$(CC) -E -o $@ $(CPPFLAGS) $<
audit_json.plog: audit_json.i
	rm -f $@; pvs-studio --cfg $(PVS_CFG) --sourcetree-root $(top_srcdir) --skip-cl-exe yes --source-file $(srcdir)/audit_json.c --i-file $< --output-file $@
