# Download videos from YouTube (youtube-dl)
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2014/10/18/download-videos-youtube/
```PowerShell
#Open file
(Get-Content C:\exa\url.txt) | %{
$_
#Use youtube-dl
#Youtube-dl is a small command-line program to download videos from YouTube.com and a few more sites. It requires the Python interpreter (2.6, 2.7, or 3.3+), and it is not platform specific. We also provide a Windows executable that includes Python. youtube-dl should work in your Unix box, in Windows or in Mac OS X. It is released to the public domain, which means you can modify it, redistribute it or use it however you like.
C:\exa\youtube-dl.exe $_
}

```
