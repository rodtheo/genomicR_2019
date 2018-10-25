#
# Makefile
# gpappas, 2017-11-12 18:20
#

all:
	@echo "Makefile needs your attention"

RMD_FILES = $(wildcard *.Rmd)
CSS_FILES = $(wildcard css/*.css)
HTML_FILES = $(RMD_FILES:%.Rmd=%.html)

all: html

html: $(HTML_FILES) $(CSS_FILES)

%.html: %.Rmd $(CSS_FILES)
	-R --vanilla --slave -e "rmarkdown::render('$<',encoding='UTF-8')"

watch:
	watchman-make -p '*.Rmd*' '**/*.css' -t html
	livereload .
	# watchman watch "$(shell pwd)"
	# watchman -- trigger "$(shell pwd)" slides slides/*.Rmd slides/Makefile -- make -C slides all

unwatch:
	watchman watch-del "$(shell pwd)"

.PHONY: clean
clean:
	-rm -rf *_cache *_files

.PHONY: clean-all
clean-all: clean
	-rm -rf $(HTML_FILES)


# vim:ft=make
#
