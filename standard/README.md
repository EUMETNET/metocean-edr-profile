# metocean-edr-profile

## Overview

This directory contains the report and provides instructions for managing the document.

### Dependencies

Documentation is managed with [Asciidoctor](https://asciidoctor.org).

Link checking is managed with [asciidoc-link-check](https://www.npmjs.com/package/asciidoc-link-check).

PDF generation is managed with [asciidoctor-pdf](https://www.npmjs.com/package/asciidoctor-pdf).

```bash
apt-get install pandoc
npm install asciidoctor asciidoctor-pdf asciidoc-link-check
```
### Building the document

```bash
# create HTML (single page)
asciidoctor --trace -o metocean-edr-profile.html index.adoc
# create PDF
asciidoctor --trace -r asciidoctor-pdf --trace -b pdf -o metocean-edr-profile.pdf index.adoc
# create Word document
asciidoctor --trace --backend docbook --out-file - index.adoc | pandoc --from docbook --to docx --output metocean-edr-profile.docx
```

# check links
```bash
find . -name "*.adoc" -exec asciidoc-link-check -p -c asciidoc-link-check-config.json {} \;
```

**Note**: `Makefile` provides shortcuts to these commands if you are able to run `make`.
