
SUBDIRS = libmediaplayerid

noinst_LTLIBRARIES = librb.la

rbincludedir = $(includedir)/rhythmbox/lib
rbinclude_HEADERS =					\
	rb-builder-helpers.h				\
	rb-debug.h					\
	rb-file-helpers.h				\
	rb-list-model.h					\
	rb-stock-icons.h				\
	rb-string-value-map.h				\
	rb-util.h					\
	rb-task-progress.h				\
	rb-task-progress-simple.h

librb_la_SOURCES =					\
	$(rbinclude_HEADERS)				\
	rb-debug.c					\
	eggdesktopfile.c				\
	eggdesktopfile.h				\
	rb-file-helpers.c				\
	rb-builder-helpers.c				\
	rb-stock-icons.c				\
	rb-cut-and-paste-code.c				\
	rb-cut-and-paste-code.h				\
	rb-util.c					\
	rb-tree-dnd.c					\
	rb-tree-dnd.h					\
	rb-string-value-map.c				\
	rb-async-queue-watch.c				\
	rb-async-queue-watch.h				\
	rb-text-helpers.c				\
	rb-text-helpers.h				\
	rb-gst-media-types.c				\
	rb-gst-media-types.h				\
	rb-missing-plugins.c				\
	rb-missing-plugins.h				\
	rb-async-copy.c					\
	rb-async-copy.h					\
	rb-chunk-loader.c				\
	rb-chunk-loader.h				\
	rb-task-progress.c				\
	rb-task-progress-simple.c			\
	rb-list-model.c

INCLUDES =						\
	-DGNOMELOCALEDIR=\""$(datadir)/locale"\"        \
	-DG_LOG_DOMAIN=\"Rhythmbox\"		 	\
	-DSHARE_DIR=\"$(pkgdatadir)\"			\
	-DDATADIR=\""$(datadir)"\"			\
	-DEGG_SM_CLIENT_BACKEND_XSMP			\
	-I$(top_srcdir) 				\
	-I$(top_srcdir)/widgets				\
	$(RHYTHMBOX_CFLAGS)

librb_la_LIBADD = -lSM -lICE

BUILT_SOURCES=

CLEAN_FILES = $(BUILT_SOURCES)

rb-marshal.c: rb-marshal.list
	@GLIB_GENMARSHAL@ --prefix=rb_marshal $(srcdir)/rb-marshal.list --header --body > rb-marshal.c

rb-marshal.h: rb-marshal.list
	@GLIB_GENMARSHAL@ --prefix=rb_marshal $(srcdir)/rb-marshal.list --header > rb-marshal.h

# inline icons
rhythmbox-set-star-inline.h: $(top_srcdir)/data/icons/hicolor/16x16/status/rhythmbox-set-star.png
	@GDK_PIXBUF_CSOURCE@ --raw --name=rhythmbox_set_star_inline $< > $@

rhythmbox-unset-star-inline.h: $(top_srcdir)/data/icons/hicolor/16x16/status/rhythmbox-unset-star.png
	@GDK_PIXBUF_CSOURCE@ --raw --name=rhythmbox_unset_star_inline $< > $@

rhythmbox-no-star-inline.h: $(top_srcdir)/data/icons/hicolor/16x16/status/rhythmbox-no-star.png
	@GDK_PIXBUF_CSOURCE@ --raw --name=rhythmbox_no_star_inline $< > $@


BUILT_SOURCES += 				\
	rb-marshal.c 				\
	rb-marshal.h 				\
	rhythmbox-set-star-inline.h		\
	rhythmbox-unset-star-inline.h		\
	rhythmbox-no-star-inline.h

librb_la_SOURCES += $(BUILT_SOURCES)

librb_la_LDFLAGS = -export-dynamic

EXTRA_DIST = rb-marshal.list
