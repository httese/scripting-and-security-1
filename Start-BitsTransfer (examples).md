# Start-BitsTransfer (examples)
## Network, PowerShell, Servers 
### URL: https://www.jesusninoc.com/2014/10/08/start-bitstransfer-examples/
```PowerShell
C:\PS>Start-BitsTransfer -Source https://server01/servertestdir/testfile1.txt -Destination c:\clienttestdir\testfile1.txt

```
```PowerShell
C:\PS>Import-CSV filelist.txt | Start-BitsTransfer

```
```PowerShell
C:\PS>Start-BitsTransfer -Source c:\clienttestdir\testfile1.txt -Destination 

```
```PowerShell
C:\PS>Start-BitsTransfer -Source https://server01/servertestdir/testfile1.txt, https://server01/servertestdir/testfile1.txt -Destination c:\clienttestdir\testfile1.txt, c:\clienttestdir\testfile1.txt

```
```PowerShell
C:\PS>$c = Get-Credential
New-FileTransfer -DisplayName MyJob -Credential c$ -Source https://server01/servertestdir/testfile1.txt -Destination c:\clienttestdir\testfile1.txt

```
```PowerShell
C:\PS>Import-CSV filelist.txt | Start-BitsTransfer -Asynchronous -Priority Normal

```
```PowerShell
C:\PS>Start-BitsTransfer -Source https://server01/servertestdir/*.* -Destination c:\clienttestdir\

```
```PowerShell
C:\PS>Import-CSV filelist.txt | Start-BitsTransfer -TransferType Upload

```
