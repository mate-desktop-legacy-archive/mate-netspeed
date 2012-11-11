INCLUDES = -I$(top_srcdir) -I$(includedir) $(NETSPEED_CFLAGS) $(NETSPEED_LIBGTOP_CFLAGS) \
       -DMATELOCALEDIR=\""$(datadir)/locale"\" \
       -DDATADIR=\""$(datadir)/"\" \
       -DPREFIX=\""$(prefix)/"\" \
       -DLIBDIR=\""$(libdir)/"\" \
       -DSYSCONFDIR=\""$(sysconfdir)/"\" \
       -DNETSPEED_MENU_UI_DIR=\""$(datadir)/mate-panel/ui"\"

libexec_PROGRAMS = mate-netspeed-applet

mate_netspeed_applet_SOURCES = backend.h backend.c netspeed.c

mate_netspeed_applet_LDADD = $(NETSPEED_LIBS) $(NETSPEED_LIBGTOP_LIBS) $(IWLIB) $(INTLLIBS)
