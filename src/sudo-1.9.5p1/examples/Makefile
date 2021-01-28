#
# SPDX-License-Identifier: ISC
#
# Copyright (c) 2014, 2017-2020 Todd C. Miller <Todd.Miller@sudo.ws>
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
# examples/Makefile.  Generated from Makefile.in by configure.
#

#### Start of system configuration section. ####

srcdir = .
abs_srcdir = /root/sudo-1.9.5p1/examples
top_srcdir = ..
abs_top_srcdir = /root/sudo-1.9.5p1
top_builddir = ..
abs_top_builddir = /root/sudo-1.9.5p1
exampledir = $(docdir)/examples
docdir = $(datarootdir)/doc/$(PACKAGE_TARNAME)
scriptdir = $(top_srcdir)/scripts

# Our install program supports extra flags...
INSTALL = $(SHELL) $(top_srcdir)/install-sh -c
INSTALL_OWNER = -o $(install_uid) -g $(install_gid)

# Where to install things...
prefix = /usr/local
exec_prefix = $(prefix)
bindir = $(exec_prefix)/bin
sbindir = $(exec_prefix)/sbin
sysconfdir = /etc
libexecdir = $(exec_prefix)/libexec
datarootdir = $(prefix)/share
localstatedir = $(prefix)/var

# User and group ids the installed files should be "owned" by
install_uid = 0
install_gid = 0

#### End of system configuration section. ####

SHELL = /bin/bash

LOGSRVD_CONF = $(srcdir)/sudo_logsrvd.conf

EXAMPLES = $(srcdir)/pam.conf sudo.conf $(LOGSRVD_CONF) \
	   $(srcdir)/sudoers $(srcdir)/syslog.conf
 
VERSION = 1.9.5p1
PACKAGE_TARNAME = sudo

all: $(EXAMPLES)

depend:

Makefile: $(srcdir)/Makefile.in
	cd $(top_builddir) && ./config.status --file examples/Makefile

sudo.conf: $(srcdir)/sudo.conf.in
	cd $(top_builddir) && ./config.status --file examples/sudo.conf

pre-install:

install: install-doc

install-dirs:
	$(SHELL) $(scriptdir)/mkinstalldirs $(DESTDIR)$(exampledir)

install-binaries:

install-includes:

install-doc: install-dirs
	for f in $(EXAMPLES); do $(INSTALL) $(INSTALL_OWNER) -m 0644 $$f $(DESTDIR)$(exampledir); done
	test -r $(DESTDIR)$(sysconfdir)/sudo.conf || \
	    $(INSTALL) $(INSTALL_OWNER) -m 0644 sudo.conf $(DESTDIR)$(sysconfdir)
	if test -n "$(LOGSRVD_CONF)" -a ! -r $(DESTDIR)$(sysconfdir)/sudo_logsrvd.conf; then \
	    $(INSTALL) $(INSTALL_OWNER) -m 0644 $(LOGSRVD_CONF) $(DESTDIR)$(sysconfdir); \
	fi

install-plugin:

uninstall:
	-rm -rf	$(DESTDIR)$(exampledir)

splint:

cppcheck:

pvs-log-files:

pvs-studio:

check:

clean:

mostlyclean: clean

distclean: clean
	-rm -rf Makefile

clobber: distclean

realclean: distclean

cleandir: distclean
