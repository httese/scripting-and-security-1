# Analizar las líneas capturadas con tshark
## Network 
### URL: https://www.jesusninoc.com/2014/12/31/analizar-las-lineas-capturadas-con-tshark-2/
```PowerShell
cd "C:\Program Files\Wireshark"
.\tshark.exe -r C:\Users\user\capture1.pcapng |%{
Select-String 'Spanning' -InputObject $_
}

```
# Analizar las líneas capturadas con tshark
## Network 
### URL: https://www.jesusninoc.com/2014/12/21/analizar-las-lineas-capturadas-con-tshark/
```PowerShell
.\tshark -i Ethernet > F:\power\capture4.txt
Get-Content F:\power\capture4.txt | Select-String "DNS"

```
```PowerShell
.\tshark -i Ethernet > F:\power\capture4.txt
Get-Content F:\power\capture4.txt | Select-String "HTTP"

```
```PowerShell
.\tshark -i Ethernet > F:\power\capture4.txt
Get-Content F:\power\capture4.txt | Select-String "GET"

```
