# Convert a string to a character array
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2014/03/10/convert-string-character-array/
```PowerShell
"PowerShell"|%{for ($c=0;$i -lt $_.Length; ++$c) { $_[$c] }}

```
