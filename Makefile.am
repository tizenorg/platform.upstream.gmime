## Process this file with automake to produce Makefile.in

ACLOCAL_AMFLAGS = -I m4

SUBDIRS = m4 build util gmime

if ENABLE_MONO
SUBDIRS += mono
endif

SUBDIRS += docs

SUBDIRS += tools .

# build documentation when doing distcheck
DISTCHECK_CONFIGURE_FLAGS = --enable-gtk-doc

DISTCLEANFILES = iconv-detect.h gmime-$(GMIME_API_VERSION).pc config.lt doltcompile doltlibtool

EXTRA_DIST = 				\
	PORTING				\
	gmime.pc.in			\
	gmime.spec.in 			\
	iconv-detect.c			\
	zentimer.h 			\
	gtk-doc.make

BUILD_EXTRA_DIST = 			\
	gmime.spec

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = gmime-$(GMIME_API_VERSION).pc

$(pkgconfig_DATA): config.status

dist-hook: $(BUILD_EXTRA_DIST)
	files='$(BUILD_EXTRA_DIST)'; \
	for f in $$files; do \
	  if test -f $$f; then d=.; else d=$(srcdir); fi; \
	  rm -f $(distdir)/$$f && cp $$d/$$f $(distdir) || exit 1; done

gmime-$(GMIME_API_VERSION).pc: gmime.pc
	-cp gmime.pc gmime-$(GMIME_API_VERSION).pc
