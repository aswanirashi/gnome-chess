SUBDIRS = icons pieces

desktopdir = $(datadir)/applications
desktop_in_files = gnome-chess.desktop.in
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)
@INTLTOOL_DESKTOP_RULE@

appdatadir = $(datadir)/appdata
appdata_in_files = gnome-chess.appdata.xml.in
appdata_DATA = $(appdata_in_files:.appdata.xml.in=.appdata.xml)
@INTLTOOL_XML_RULE@

uidir = $(pkgdatadir)
dist_ui_DATA = \
	gnome-chess.ui \
	preferences.ui \
	promotion-type-selector.ui \
	menu.ui

gsettings_SCHEMAS = org.gnome.chess.gschema.xml
@GSETTINGS_RULES@

pkgsysconfdir = $(sysconfdir)/gnome-chess
dist_pkgsysconf_DATA = engines.conf

dist_man_MANS = gnome-chess.6

check-local: $(appdata_DATA) $(desktop_DATA)
	$(APPDATA_VALIDATE) $(appdata_DATA)
	$(DESKTOP_FILE_VALIDATE) $(desktop_DATA)

EXTRA_DIST = \
	$(appdata_in_files) \
	$(desktop_in_files) \
	$(gsettings_SCHEMAS)

CLEANFILES = \
	$(appdata_DATA) \
	$(desktop_DATA)

-include $(top_srcdir)/git.mk
