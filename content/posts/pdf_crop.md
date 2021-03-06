+++
title = "PDF Cropping"
author = ["Jethro Kuan"]
lastmod = 2020-06-07T17:26:03+08:00
draft = false
+++

tags
: [Pdf Tools]({{< relref "pdf_tools" >}})

Cropping PDFs can be done through `pdfcrop`. `pdfcrop` only takes a
single argument, use a bash function to batch crop:

```bash
  pdfconstcrop() {
      pdfcrop --bbox "$(
          pdfcrop --verbose "$@" |
          grep '^%%HiResBoundingBox: ' |
          cut -d' ' -f2- |
          datamash -t' ' min 1 min 2 max 3 max 4
      )" "$@"
  }

  pdfcrop_all() {
      for FILE in *.pdf; do
          pdfconstcrop --margins '20 20 20 20' "${FILE}"
      done
  }
```

This script ensures that the cropped pages are of the same size.
Requires `datamash`.
