AC_PREREQ(2.52)

AC_INIT(mate-netspeed, 1.12.0, https://github.com/mate-desktop/mate-netspeed)
AC_CONFIG_SRCDIR(src/netspeed.c)
AM_INIT_AUTOMAKE([foreign no-dist-gzip dist-xz check-news])

m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])
AM_MAINTAINER_MODE
AC_CONFIG_HEADERS(config.h)
AC_CONFIG_MACRO_DIR([m4])
IT_PROG_INTLTOOL([0.50.1])

AM_PROG_LIBTOOL
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_MAKE_SET

# GLib min/max required versions
AC_DEFINE([GLIB_VERSION_MAX_ALLOWED], [GLIB_VERSION_2_36],
	[Warn on use of APIs added after GLib 2.36])
AC_DEFINE([GLIB_VERSION_MIN_REQUIRED], [GLIB_VERSION_2_36],
	[Warn on use of APIs deprecated before GLib 2.36])

AM_GLIB_GNU_GETTEXT
GETTEXT_PACKAGE=mate-netspeed
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE", GETTEXT_PACKAGE)

GTOP_REQUIRED_VERSION=2.14.2
MATE_PANEL_REQUIRED_VERSION=1.7.0
MATE_DESKTOP_REQUIRED_VERSION=1.9.0

PKG_CHECK_MODULES(NETSPEED,
                  libmatepanelapplet-4.0 >= $MATE_PANEL_REQUIRED_VERSION
                  mate-desktop-2.0 >= $MATE_DESKTOP_REQUIRED_VERSION
                  libgtop-2.0 >= $GTOP_REQUIRED_VERSION
                  gio-2.0)

AC_SUBST(NETSPEED_APPLET_CFLAGS)
AC_SUBST(NETSPEED_APPLET_LIBS)

YELP_HELP_INIT

ac_have_iwevgenie=no
AC_MSG_CHECKING([for libiw >= 28pre9])
AC_COMPILE_IFELSE([AC_LANG_PROGRAM([
                #include <iwlib.h>
                #ifndef IWEVGENIE
                #error "not found"
                #endif])],
               [ac_have_iwevgenie=yes],
    AC_MSG_WARN([iwlib.h not found. It's provided by libiw or wireless-tools (depends on the distro)])
)
AC_MSG_RESULT([$ac_have_iwevgenie])
if test "$ac_have_iwevgenie" = yes; then
        AC_DEFINE(HAVE_IW, 1, [Defined if you have libiw/wireless-tools (depends on the distro)])
	IWLIB=-liw
	AC_SUBST(IWLIB)
fi

GLIB_GSETTINGS

AC_OUTPUT([
Makefile
data/Makefile
data/org.mate.panel.applet.netspeed.gschema.xml
icons/Makefile
icons/16x16/Makefile
icons/16x16/apps/Makefile
icons/16x16/devices/Makefile
icons/22x22/Makefile
icons/22x22/apps/Makefile
icons/24x24/Makefile
icons/24x24/apps/Makefile
icons/24x24/status/Makefile
icons/32x32/Makefile
icons/32x32/apps/Makefile
icons/48x48/Makefile
icons/48x48/apps/Makefile
icons/scalable/Makefile
icons/scalable/apps/Makefile
src/Makefile
po/Makefile.in
help/Makefile
])
