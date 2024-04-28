# Makefile for RISC-V ISA Manuals
#
# This work is licensed under the Creative Commons Attribution-ShareAlike 4.0
# International License. To view a copy of this license, visit
# http://creativecommons.org/licenses/by-sa/4.0/ or send a letter to
# Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
#
# SPDX-License-Identifier: CC-BY-SA-4.0
#
# Description:
# 
# This Makefile is designed to automate the process of building and packaging 
# the documentation for RISC-V ISA Manuals. It supports multiple build targets 
# for generating documentation in various formats (PDF, HTML).

# Build Targets
TARGETS := ime-pdf imd-html

# Declare phony targets
.PHONY: all $(TARGETS) clean

# Default target builds all
all: $(TARGETS)

# Build with preinstalled docker container; first install it with:
#   docker pull riscvintl/riscv-docs-base-container-image:latest
docker:
	cd .. && docker run -it -v `pwd`:/build riscvintl/riscv-docs-base-container-image:latest /bin/sh -c 'cd ./build; make -$(MAKEFLAGS)'

# Asciidoctor options
ASCIIDOCTOR_OPTS := -a compress \
                    --attribute=mathematical-format=svg \
                    --failure-level=ERROR \
                    --require=asciidoctor-bibtex \
                    --require=asciidoctor-diagram \
                    --require=asciidoctor-mathematical \
                    --trace

# Source directory
SRCDIR := ../src

# Temporary files to clean up for LaTeX build
JUNK := *.pdf *.aux *.log *.bbl *.blg *.toc *.out *.fdb_latexmk *.fls *.synctex.gz

# Privileged ISA build
ime-pdf: spacemit-ime-asciidoc.pdf

spacemit-ime-asciidoc.pdf: $(SRCDIR)/header.adoc $(SRCDIR)/*.adoc
	@echo "Building Privileged ISA"
	rm -f $@.tmp
	asciidoctor-pdf $(ASCIIDOCTOR_OPTS) --out-file=$@.tmp $<
	mv $@.tmp $@

# Privileged ISA HTML build
ime-html: spacemit-ime-asciidoc.html

spacemit-ime-asciidoc.html: $(SRCDIR)/header.adoc  
	@echo "Building Privileged ISA HTML"
	asciidoctor $(ASCIIDOCTOR_OPTS) --out-file=$@ $<

clean:
	@if [ -f spacemit-ime-asciidoc.pdf ]; then \
		echo "Removing spacemit-ime-asciidoc.pdf"; \
		rm -f spacemit-ime-asciidoc.pdf; \
	fi
