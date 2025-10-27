TEX      := main.tex
OUTDIR   := build
PDF      := $(basename $(TEX)).pdf

all: $(PDF)

$(PDF): $(TEX)
	@mkdir -p $(OUTDIR)
	@echo "🧱 Compiling $(TEX)..."
	@pdflatex -interaction=nonstopmode -halt-on-error -output-directory=$(OUTDIR) $(TEX) >/dev/null
	@bibtex $(OUTDIR)/$(basename $(TEX)) >/dev/null 2>&1 || true
	@pdflatex -interaction=nonstopmode -halt-on-error -output-directory=$(OUTDIR) $(TEX) >/dev/null
	@pdflatex -interaction=nonstopmode -halt-on-error -output-directory=$(OUTDIR) $(TEX) >/dev/null
	@mv $(OUTDIR)/$(PDF) ./$(PDF)
	@echo "✅ Done → $(PDF)"

clean:
	@rm -rf $(OUTDIR) *.pdf
	@echo "🧹 Cleaned."
