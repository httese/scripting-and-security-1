# Split a PDF into single-page files
## PowerShell 
### URL: https://www.jesusninoc.com/2015/12/29/split-a-pdf-into-single-page-files/
```PowerShell
#Coherent PDF Command Line Tools
#The Coherent PDF Command Line Tools allow you to manipulate existing PDF files in a variety of ways

#Split a file into single-page files page001.pdf, page002.pdf etc
#https://community.coherentpdf.com/

cpdf -split in.pdf -o page%%%.pdf

```
