# Creating folders for each user (example)
## Bash, Filesystem 
### URL: https://www.jesusninoc.com/2014/11/22/creating-folders-user-example/
```Shell
for line in $(cat names)
do
#Create folder for each user
#For each user create 3 folders more
#Create multiple new folders in user directory
mkdir -p $line/{folder1,folder2,folder}
done

```
# Creating Folders for each user (example)
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2014/11/17/creating-folders-for-each-user-example/
```PowerShell
#Creating folders for each user
Set-Location F:\power\
#User list in a file
ForEach($user in Get-Content .\names.txt)
{
#Create folder for each user
#If the item you are trying to create already exists
#Override the default behavior
New-Item $user -ItemType directory -Force
#For each user create 3 folders more
#Create Multiple New Folders in user directory
$foldersname="folder1","folder2","folder3"
foreach($folder in $foldersname)
{
New-Item $user\$folder -ItemType directory -Force
}
}

```
