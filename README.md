
# rasterisePDF
Flattening PDF using Ghostscript

If you have a digitally secured PDF and having issue printing it, you might consider rasterise it first. Using command below.

## On Windows
```
gswin64c.exe -sDEVICE=pdfwrite -sOutputFile=output.pdf -dBATCH -dNOPAUSE input.pdf
```

[Ghostscript](https://www.ghostscript.com/) is required. 
