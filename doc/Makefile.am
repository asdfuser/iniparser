static_docs = iniparser.main
#noinst_doc_DATA = $(static_docs) doxygen-build.stamp
EXTRA_DIST = $(static_docs) Doxyfile.in doxygen-build.stamp

if HAVE_DOXYGEN
doxygen-build.stamp: Doxyfile $(top_srcdir)/src/iniparser.h
	doxygen
	touch doxygen-build.stamp

directory = $(top_srcdir)/doc/man/man3/

dist_man_MANS = $(directory)/iniparser.h.3
$(dist_man_MANS): doxygen-build.stamp

clean-local:
	rm -rf $(top_srcdir)/doc/man
	rm -rf $(top_srcdir)/doc/html

else
doxygen-build.stamp:
	echo "*** Warning: Doxygen not found; documentation will not be built."
	touch doxygen-build.stamp
endif

CLEANFILES = doxygen-build.stamp

all-local: doxygen-build.stamp

