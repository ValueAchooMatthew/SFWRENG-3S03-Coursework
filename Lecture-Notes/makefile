LECTURES := $(shell find . -mindepth 2 -maxdepth 2 -type f -name "lecture-*.tex" | sort -V)
INCLUDES := includes.tex
MASTER := master.tex
OUT := master.pdf

.PHONY: all includes clean

all: $(OUT)

includes: $(INCLUDES)

$(INCLUDES): $(LECTURES)
	@echo "% Automatically generated. Do not edit." > $(INCLUDES)
	@for f in $(LECTURES); do \
		echo "\\input{$$f}" >> $(INCLUDES); \
	done
	@echo "Generated $(INCLUDES) with $$(echo $(LECTURES) | wc -w) lectures."

$(OUT): $(MASTER) $(INCLUDES)
	@echo "=== Building master document ==="
	pdflatex $(MASTER)
	pdflatex $(MASTER)
	rm master.out master.aux master.log
	@echo "=== Build complete: $(OUT) ==="
	firefox $(OUT)
