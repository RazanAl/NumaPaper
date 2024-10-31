# Variables
TEX_FILE = Numa_main  # The name of your LaTeX file without the .tex extension
PDF_FILE = $(TEX_FILE).pdf
LATEX = pdflatex
BIBTEX = bibtex

# Default target
all: $(PDF_FILE)

# Rule to compile the LaTeX file
$(PDF_FILE): $(TEX_FILE).tex
	$(LATEX) $(TEX_FILE).tex
	# Run BibTeX if .aux file is generated (for bibliography support)
	if grep -q "citation" $(TEX_FILE).aux; then $(BIBTEX) $(TEX_FILE); fi
	# Re-run pdflatex to resolve references
	$(LATEX) $(TEX_FILE).tex
	$(LATEX) $(TEX_FILE).tex

# Clean up auxiliary files
clean:
	rm -f $(TEX_FILE).aux $(TEX_FILE).bbl $(TEX_FILE).blg $(TEX_FILE).log $(TEX_FILE).out $(TEX_FILE).toc $(TEX_FILE).lof $(TEX_FILE).lot

# Remove auxiliary files and the PDF
clean-all: clean
	rm -f $(PDF_FILE)

.PHONY: all clean clean-all

