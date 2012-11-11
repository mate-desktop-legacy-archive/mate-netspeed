SUBDIRS = data help icons po src

distuninstallcheck_listfiles = find . -type f -print | grep -v scrollkeeper

EXTRA_DIST = mate-doc-utils.make \
             intltool-update.in \
             intltool-merge.in \
             intltool-extract.in

CLEANFILES = $(server_DATA)
DISTCLEANFILES = \
                 mate-doc-utils.make \
                 intltool-extract \
                 intltool-merge \
                 intltool-update \
                 $(server_in_files)

DISTCHECK_CONFIGURE_FLAGS = --disable-scrollkeeper
