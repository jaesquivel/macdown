SASS = node_modules/.bin/sass

target = ../../MacDown/Resources/Styles/GitHub-2020.css

all: $(target)

# The generated stylesheet is committed, so building MacDown does not need
# Node.js. Run `npm ci` here first if you want to regenerate it.
$(target): index.sass package-lock.json
	@if [ -x $(SASS) ]; then \
		$(SASS) --no-source-map --quiet --load-path=node_modules $< | sed s/.markdown-body/body/ > $@; \
	elif [ -f $@ ]; then \
		echo "note: $(SASS) not found (run 'npm ci' in Tools/GitHub-style-generator to regenerate); using committed $(notdir $@)"; \
	else \
		echo "error: $(SASS) not found; run 'npm ci' in Tools/GitHub-style-generator" >&2; \
		exit 1; \
	fi

clean:
	$(RM) $(target)

.PHONY: all clean
