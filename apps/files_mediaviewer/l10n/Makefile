NODE_BINDIR = ../node_modules/.bin
export PATH := $(NODE_BINDIR):$(PATH)


# Name of the generated .po files for each available locale.
LOCALE_FILES = $(shell find locale -name '*.po')

GETTEXT_JS_SOURCES = $(shell find ../src -name '*.js')
GETTEXT_VUE_SOURCES = $(shell find ../src -name '*.vue')
GETTEXT_PHP_SOURCES = $(shell find ../lib -name '*.php')

# Makefile Targets
.PHONY: clean makemessages translations push pull

clean:
	rm -rf files_mediaviewer.pot locale

makemessages:
	touch files_mediaviewer.pot
	../node_modules/.bin/gettext-extract --attribute v-translate \
		--output=files_mediaviewer.pot $(GETTEXT_VUE_SOURCES)
	xgettext --language=JavaScript --keyword=t:2 --keyword=n:2,3 \
		--from-code=utf-8 --join-existing --no-wrap \
		--package-name=FilesMediaViewer \
		--package-version=0.0.1 \
		--output=files_mediaviewer.pot $(GETTEXT_JS_SOURCES)
