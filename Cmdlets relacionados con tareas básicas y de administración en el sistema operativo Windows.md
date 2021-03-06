# Cmdlets relacionados con tareas básicas y de administración en el sistema operativo Windows
## Filesystem, Hardware, Memory, Network, Operating Systems, Permissions, PowerShell, Processes, Schedule tasks, Services, Software, Threads, Updates, Users 
### URL: https://www.jesusninoc.com/2015/04/28/cmdlets-relacionados-con-tareas-basicas-y-de-administracion-en-el-sistema-operativo-windows/
```PowerShell
#Computer System Hardware Classes
#Cooling Device Classes
Get-WmiObject Win32_Fan
Get-WmiObject Win32_HeatPipe
Get-WmiObject Win32_Refrigeration
Get-WmiObject Win32_TemperatureProbe

#Input Device Classes
Get-WmiObject Win32_Keyboard
Get-WmiObject Win32_PointingDevice

#Mass Storage Classes
Get-WmiObject Win32_AutochkSetting
Get-WmiObject Win32_CDROMDrive
Get-WmiObject Win32_DiskDrive
Get-WmiObject Win32_FloppyDrive
Get-WmiObject Win32_PhysicalMedia
Get-WmiObject Win32_TapeDrive

#Motherboard, Controller, and Port Classes
Get-WmiObject Win32_1394Controller
Get-WmiObject Win32_1394ControllerDevice
Get-WmiObject Win32_AllocatedResource
Get-WmiObject Win32_AssociatedProcessorMemory
Get-WmiObject Win32_BaseBoard
Get-WmiObject Win32_BIOS
Get-WmiObject Win32_Bus
Get-WmiObject Win32_CacheMemory
Get-WmiObject Win32_ControllerHasHub
Get-WmiObject Win32_DeviceBus
Get-WmiObject Win32_DeviceMemoryAddress
Get-WmiObject Win32_DeviceSettings
Get-WmiObject Win32_DMAChannel
Get-WmiObject Win32_FloppyController
Get-WmiObject Win32_IDEController
Get-WmiObject Win32_IDEControllerDevice
Get-WmiObject Win32_InfraredDevice
Get-WmiObject Win32_IRQResource
Get-WmiObject Win32_MemoryArray
Get-WmiObject Win32_MemoryArrayLocation
Get-WmiObject Win32_MemoryDevice
Get-WmiObject Win32_MemoryDeviceArray
Get-WmiObject Win32_MemoryDeviceLocation
Get-WmiObject Win32_MotherboardDevice
Get-WmiObject Win32_OnBoardDevice
Get-WmiObject Win32_ParallelPort
Get-WmiObject Win32_PCMCIAController
Get-WmiObject Win32_PhysicalMemory
Get-WmiObject Win32_PhysicalMemoryArray
Get-WmiObject Win32_PhysicalMemoryLocation
Get-WmiObject Win32_PNPAllocatedResource
Get-WmiObject Win32_PNPDevice
Get-WmiObject Win32_PNPEntity
Get-WmiObject Win32_PortConnector
Get-WmiObject Win32_PortResource
Get-WmiObject Win32_Processor
Get-WmiObject Win32_SCSIController
Get-WmiObject Win32_SCSIControllerDevice
Get-WmiObject Win32_SerialPort
Get-WmiObject Win32_SerialPortConfiguration
Get-WmiObject Win32_SerialPortSetting
Get-WmiObject Win32_SMBIOSMemory
Get-WmiObject Win32_SoundDevice
Get-WmiObject Win32_SystemBIOS
Get-WmiObject Win32_SystemDriverPNPEntity
Get-WmiObject Win32_SystemEnclosure
Get-WmiObject Win32_SystemMemoryResource
Get-WmiObject Win32_SystemSlot
Get-WmiObject Win32_USBController
Get-WmiObject Win32_USBControllerDevice
Get-WmiObject Win32_USBHub
 
#Networking Device Classes
Get-WmiObject Win32_NetworkAdapter
Get-WmiObject Win32_NetworkAdapterConfiguration
Get-WmiObject Win32_NetworkAdapterSetting
 
#Power Classes
Get-WmiObject Win32_Battery
Get-WmiObject Win32_CurrentProbe
Get-WmiObject Win32_PortableBattery
Get-WmiObject Win32_PowerManagementEvent
Get-WmiObject Win32_VoltageProbe
 
#Printing Classes
Get-WmiObject Win32_DriverForDevice
Get-WmiObject Win32_Printer
Get-WmiObject Win32_PrinterConfiguration
Get-WmiObject Win32_PrinterController
Get-WmiObject Win32_PrinterDriver
Get-WmiObject Win32_PrinterDriverDll
Get-WmiObject Win32_PrinterSetting
Get-WmiObject Win32_PrintJob
Get-WmiObject Win32_TCPIPPrinterPort
 
#Telephony Classes
Get-WmiObject Win32_POTSModem
Get-WmiObject Win32_POTSModemToSerialPort
 
#Video and Monitor Classes
Get-WmiObject Win32_DesktopMonitor
Get-WmiObject Win32_DisplayControllerConfiguration
Get-WmiObject Win32_VideoController
Get-WmiObject Win32_VideoSettings

Get-WmiObject Win32_Processor
Get-WmiObject -Class Win32_Processor
Get-WmiObject -query "select * from Win32_Processor"

Get-WmiObject Win32_PnPEntity
Get-WmiObject -Class Win32_PnPEntity
Get-WmiObject -query “select * from Win32_PnPEntity”

Get-WmiObject Win32_battery
Get-WmiObject -Class Win32_battery
Get-WmiObject -query “select * from Win32_battery”

```
```PowerShell
Get-WmiObject win32_processor | Select-Object LoadPercentage
Get-WmiObject -query "select NumberOfCores from Win32_Processor"
Get-WmiObject -Class Win32_Processor | Select-Object NumberOfCores
Get-WmiObject -query “select Name,Status from Win32_PnPEntity”
Get-WmiObject -query “select * from Win32_PnPEntity” | Select-Object Name, Status
Get-WmiObject -query "select * from Win32_PnPEntity where caption like '%cam%'"
Get-WmiObject Win32_PnPEntity | where {$_.caption -match 'webcam'}
gwmi Win32_USBControllerDevice |%{[wmi]($_.Dependent)} | Sort Manufacturer,Description,DeviceID | Ft -GroupBy Manufacturer Description,Service,DeviceID
Get-WmiObject -Class win32_battery

```
```PowerShell
#Crear o modificar un archivo
New-Item

#Crear un directorio
New-Item

#Ver el contenido de un archivo
Get-Content

#Acceder al contenido de un directorio
Set-Location

#Listar el contenido de un directorio
Get-ChildItem

#Eliminar un archivo
Remove-Item

#Eliminar un directorio
Remove-Item

#Copiar un archivo o un directorio
Copy-Item

#Mover un archivo o un directorio
Move-Item

#Renombrar un archivo o un directorio
Rename-Item

#Comprimir y descomprimir un archivo o un directorio
Compress-Archive
Expand-Archive

#Imprimir
Out-Printer

#Ver carpetas compartidas
Get-SmbShare
Get-WmiObject -Class Win32_Share

#Compartir carpeta
New-SmbShare

#Ver y asignar permisos
Get-Acl
Set-Acl
New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule

```
```PowerShell
#Comprimir
Compress-Archive -LiteralPath C:\powershell\example.txt –CompressionLevel Optimal -DestinationPath C:\powershell\comprimido.zip

#Actualizar un archivo comprimido
Compress-Archive -LiteralPath C:\powershell\example2.txt -Update -DestinationPath C:\powershell\comprimido.zip

#Descomprimir
Expand-Archive -LiteralPath C:\powershell\comprimido.zip -DestinationPath C:\powershell\descomprimir

#Crear y recurso compartido
New-SmbShare -Name fso -Path F:\power

#Crear y asignar permisos a un recurso compartido
New-SmbShare -Name fso -Path F:\power –FullAccess administrador -ReadAccess Everyone

#Ver permisos
Get-Acl D:\power

#Añadir permisos mediante reglas de acceso
$permisos = Get-Acl -Path D:\power
#Crear regla de acceso
#System.Security.AccessControl.FileSystemAccessRule: Representa una abstracción de una entrada de control de acceso (ACE) que define una regla de acceso para un archivo o directorio
$permisoadd = 'Todos', 'FullControl', 'ContainerInherit, ObjectInherit', 'None', 'Allow'
$regla = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $permisoadd
$permisos.SetAccessRule($regla)
#Añadir permisos a la carpeta
$permisos | Set-Acl -Path $ruta

```
```PowerShell
Get-Package
Get-WmiObject -Class Win32_Product

Install-Package

```
```PowerShell
#Ver el nombre de programas instalados
(Get-Package).name
(Get-WmiObject -Class Win32_Product).name

#Número de programas instalados
(Get-WmiObject -Class Win32_Product).count

#Instalar un programa
Install-Package filezilla

#Ver en el Registro información sobre el software instalado
Get-ChildItem hklm:\software\microsoft\windows\currentversion\uninstall | ForEach-Object {(Get-ItemProperty $_.pspath).DisplayName}

```
```PowerShell
Get-HotFix

```
```PowerShell
#Información sobre actualizaciones instaladas
Get-HotFix | Select-Object HotFixID,InstalledOn

#Agrupar por descripción las actualizaciones instaladas en el equipo
Get-HotFix | Group-Object Description

#Listar por fecha las actualizaciones instaladas en el equipo
Get-HotFix | Sort-Object InstalledOn

```
```PowerShell
Get-Process
gps
ps
Get-WmiObject -Class win32_process

Stop-Process

Get-WmiObject -Class Win32_Thread

Get-Service
Get-WmiObject -Class Win32_Service
Get-WmiObject -query "select * from win32_service"

```
```PowerShell
#Obtener información ampliada sobre procesos
Get-Process | Select-Object *
gps | Select-Object *
ps | Select-Object *

#Obtener información sobre las propiedades de los procesos
Get-Process | Select-Object Name, Id, Company
gps | Select-Object Name, Id, Company
ps | Select-Object Name, Id, Company

#Obtener información ordenada sobre las propiedades de los procesos
Get-Process | Select-Object Name, Id, Company | Sort-Object Name
gps | Select-Object Name, Id, Company | Sort-Object Name
ps | Select-Object Name, Id, Company | Sort-Object Name

#Obtener los 5 primeros procesos ordenados
Get-Process | Select-Object Name, Id, Company | Sort-Object Name | Select-Object -First 5
gps | Select-Object Name, Id, Company | Sort-Object Name | Select-Object -First 5
ps | Select-Object Name, Id, Company | Sort-Object Name | Select-Object -First 5

#Contador de procesos
(Get-WmiObject Win32_OperatingSystem).NumberOfProcesses
(Get-Process).count

#Información sobre procesos
Get-Process | Select-Object Name,Path,Company,CPU,Product,TotalProcessorTime,StartTime

#Seleccionar nombre de procesos y compañía
Get-Process | select Company,Name

#Información sobre procesos
#Name
#CPUSeconds
#WorkingSetMB
#TotalProcessorTime
#Description
Get-Process | ? {$_.TotalProcessorTime -ne $Null} | Select-Object -Property Name, @{Name="CPUSeconds"; Expression = {($_.CPU)}},@{Name="WorkingSetMB"; Expression = {($_.WorkingSet / 1mb)}},TotalProcessorTime, Description

#DLL
Get-Process | select -expand MainModule
Get-Process | select -expand Modules

#Mostrar todos los procesos y sus propiedades
Get-Process | select *
Get-WmiObject win32_process

#Mostrar los procesos que ejecuta un usuario
Get-WmiObject win32_process |% {Write-Host $_.processname $_.getowner().user}

#Mostrar información sobre un proceso indicando el nombre del proceso
Get-Process -Name notepad

#Mostrar información sobre un proceso indicando el ID del proceso
Get-Process -Id 2732

#Ordenar procesos por CPU y por memoria usada
Get-Process | Sort-Object CPU,PM

#Mostrar de forma jerárquica los procesos que se están ejecutando
Get-Process | Select * | Format-Custom

#Mostrar los identificadores de los procesos junto con sus identificadores padre
Get-WmiObject win32_process | Select-Object ParentProcessId,ProcessId

#Mostrar las propiedades especificadas de los procesos
Get-Process | Select-Object Id,CPU,PM

#Mostrar el tiempo transcurrido en la ejecución de un proceso
Get-Process | Select-Object Id,TotalProcessorTime

#Formas de arrancar un proceso
$str = "Get-Process"
Invoke-Expression $str
$scriptblock = {ping host3}
Invoke-Command -scriptblock $scriptblock -computername "host1","host2"
#Información sobre hilos
(Get-Process chrome | Select-Object Threads).Threads
Get-Process | select -expand Threads

#Prioridad de los hilos
(Get-WmiObject -Class Win32_Thread) | Select-Object ProcessHandle,Priority,PriorityBase | Sort-Object ProcessHandle
(Get-Process).Threads | Select-Object Id,CurrentPriority,BasePriority | Sort-Object Id

#Estado de los hilos
(Get-WmiObject -Class Win32_Thread) | Select-Object ProcessHandle,ThreadState | Sort-Object ProcessHandle
(Get-Process).Threads | Select-Object Id,ThreadState | Sort-Object Id

#WS(K): The size of the working set of the process, in kilobytes. The working set consists of the pages of memory that were recently referenced by the process
@(Get-Process).where{$_.WorkingSet -gt 100MB}
@(Get-Process).where{$_.WS -gt 100MB}

#Ruta donde se ejecutan los procesos
Get-Process -FileVersionInfo

#Procesos que no responden
(Get-Process).Where{-not $_.Responding}

#Buscar procesos que se están ejecutando
(Get-Process).Where{$_.Name -like "chrome"}

#Formas de parar un proceso
Get-Process -Name notepad | Stop-Process
Get-WmiObject -Class Win32_Process -Filter “name=’notepad.exe'” | Invoke-WmiMethod -Name Terminate
Get-Process -Name notepad | ForEach-Object -Process {$_.Kill()}

#Listar y parar procesos
Get-Process | Out-GridView -PassThru | Stop-Process

#Información sobre servicios
Get-Service
Get-Service | Select-Object Name,Status
Get-Service | Where-Object Status -EQ 'Running'
Get-Service | Where-Object Status -EQ 'Stopped'

#Listar servicios WQL
Get-WmiObject -query "select * from win32_service"

#Servicios que están Running
Get-WmiObject -query "select * from win32_service where state='Running'"

#Identificar servicios mediante identificadores de procesos
Get-WmiObject -Class Win32_Service | Select-Object Name,ProcessID

#Información en el resgistro sobre estado de los servicios
Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\*' | % {Write-host $_.DisplayName : $_.Start}

```
```PowerShell
New-ScheduledTaskAction
New-ScheduledTaskTrigger
Register-ScheduledTask

```
```PowerShell
$action=New-ScheduledTaskAction -Execute 'Powershell.exe' -Argument '-NoProfile -WindowStyle Hidden -command D:\mysqlmail.ps1'
$trigger=New-ScheduledTaskTrigger -Daily -At 9am
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "TareaProgramada" -Description "Comprobación de valor"

```
```PowerShell
#Windows 10
Add-LocalGroupMember
Disable-LocalUser
Enable-LocalUser
Get-LocalGroup
Get-LocalGroupMember
Get-LocalUser
New-LocalGroup
New-LocalUser
Remove-LocalGroup
Remove-LocalGroupMember
Remove-LocalUser
Rename-LocalGroup
Rename-LocalUser
Set-LocalGroup
Set-LocalUser

#Active Directory
Get-ADUser
New-ADUser
Set-ADAccountPassword
Remove-ADUser
Enable-ADAccount
Disable-ADAccount

Get-ADGroup
New-ADGroup
Add-ADGroupMember
Remove-ADGroup

```
```PowerShell
Flush-Volume
Initialize-Volume
Write-FileSystemCache
Add-InitiatorIdToMaskingSet
Add-PartitionAccessPath
Add-PhysicalDisk
Add-TargetPortToMaskingSet
Add-VirtualDiskToMaskingSet
Clear-Disk
Clear-FileStorageTier
Connect-VirtualDisk
Disable-PhysicalDiskIndication
Disable-StorageEnclosureIdentification
Disconnect-VirtualDisk
Dismount-DiskImage
Enable-PhysicalDiskIndication
Enable-StorageEnclosureIdentification
Format-Volume
Get-Disk
Get-DiskImage
Get-FileIntegrity
Get-FileStorageTier
Get-InitiatorId
Get-InitiatorPort
Get-MaskingSet
Get-OffloadDataTransferSetting
Get-Partition
Get-PartitionSupportedSize
Get-PhysicalDisk
Get-ResiliencySetting
Get-StorageEnclosure
Get-StorageEnclosureVendorData
Get-StorageJob
Get-StorageNode
Get-StoragePool
Get-StorageProvider
Get-StorageReliabilityCounter
Get-StorageSetting
Get-StorageSubSystem
Get-StorageTier
Get-StorageTierSupportedSize
Get-SupportedClusterSizes
Get-SupportedFileSystems
Get-TargetPort
Get-TargetPortal
Get-VirtualDisk
Get-VirtualDiskSupportedSize
Get-Volume
Get-VolumeCorruptionCount
Get-VolumeScrubPolicy
Hide-VirtualDisk
Initialize-Disk
Mount-DiskImage
New-MaskingSet
New-Partition
New-StoragePool
New-StorageSubsystemVirtualDisk
New-StorageTier
New-VirtualDisk
New-VirtualDiskClone
New-VirtualDiskSnapshot
New-Volume
Optimize-Volume
Register-StorageSubsystem
Remove-InitiatorId
Remove-InitiatorIdFromMaskingSet
Remove-MaskingSet
Remove-Partition
Remove-PartitionAccessPath
Remove-PhysicalDisk
Remove-StoragePool
Remove-StorageTier
Remove-TargetPortFromMaskingSet
Remove-VirtualDisk
Remove-VirtualDiskFromMaskingSet
Rename-MaskingSet
Repair-FileIntegrity
Repair-VirtualDisk
Repair-Volume
Reset-PhysicalDisk
Reset-StorageReliabilityCounter
Resize-Partition
Resize-StorageTier
Resize-VirtualDisk
Set-Disk
Set-FileIntegrity
Set-FileStorageTier
Set-InitiatorPort
Set-Partition
Set-PhysicalDisk
Set-ResiliencySetting
Set-StoragePool
Set-StorageProvider
Set-StorageSetting
Set-StorageSubSystem
Set-StorageTier
Set-VirtualDisk
Set-Volume
Set-VolumeScrubPolicy
Show-VirtualDisk
Unregister-StorageSubsystem
Update-Disk
Update-HostStorageCache
Update-StoragePool
Update-StorageProviderCache
Write-VolumeCache

Get-WmiObject -Class win32_DiskDrive
Get-WmiObject win32_volume

Get-WmiObject -Class win32_logicalDisk

```
```PowerShell
#Crear un disco virtual
New-VirtualDisk –Path d:\disc.vhdx –SizeBytes 1GB

#Mostrar información sobre los discos
Get-WmiObject -Class win32_DiskDrive

#Comprobar el espacio de las unidades
Get-WmiObject win32_volume -computername . | select name, @{expression={$_.capacity/1GB}}, @{expression={$_.freespace/1GB}}, @{name=”% Free”;expression={$_.freespace/$_.capacity*100}}

#Mostrar los nombres de las unidades de los discos lógicos
Get-WmiObject -Class win32_logicalDisk | Select-Object DeviceID

```
```PowerShell
Find-NetRoute
Get-DnsClient
Get-DnsClientCache
Get-DnsClientGlobalSetting
Get-DnsClientNrptGlobal
Get-DnsClientNrptPolicy
Get-DnsClientNrptRule
Get-DnsClientServerAddress
Get-NetAdapter
Get-NetAdapterBinding
Get-NetAdapterHardwareInfo
Get-NetAdapterStatistics
Get-NetCompartment
Get-NetFirewallAddressFilter
Get-NetFirewallApplicationFilter
Get-NetFirewallInterfaceFilter
Get-NetFirewallInterfaceTypeFilter
Get-NetFirewallPortFilter
Get-NetFirewallProfile
Get-NetFirewallRule
Get-NetFirewallSecurityFilter
Get-NetFirewallServiceFilter
Get-NetFirewallSetting
Get-NetIPAddress
Get-NetIPConfiguration
Get-NetIPInterface
Get-NetIPv4Protocol
Get-NetIPv6Protocol
Get-NetNat
Get-NetNatExternalAddress
Get-NetNatGlobal
Get-NetNatSession
Get-NetNatStaticMapping
Get-NetNatTransitionConfiguration
Get-NetNatTransitionMonitoring
Get-NetNeighbor
Get-NetOffloadGlobalSetting
Get-NetPrefixPolicy
Get-NetRoute
Get-NetTCPConnection
Get-NetTCPSetting
Get-NetTransportFilter
Get-NetUDPEndpoint
Get-NetUDPSetting
New-NetIPAddress
New-NetNeighbor
New-NetRoute
New-NetTransportFilter
Remove-NetIPAddress
Remove-NetNeighbor
Remove-NetRoute
Remove-NetTransportFilter
Set-NetIPAddress
Set-NetIPInterface
Set-NetIPv4Protocol
Set-NetIPv6Protocol
Set-NetNeighbor
Set-NetOffloadGlobalSetting
Set-NetRoute
Set-NetTCPSetting
Set-NetUDPSetting
Test-NetConnection

Get-WmiObject-ClassWin32_NetworkAdapterConfiguration

```
```PowerShell
#Información sobre conexiones
#https://www.jesusninoc.com/2015/11/13/cmdlets-for-tcpip-model-layers/
Get-NetAdapterHardwareInfo
Get-NetAdapter -Physical
Get-NetNeighbor
Get-NetAdapterStatistics
Get-NetAdapter | Select-Object Name,MacAddress
Get-NetAdapter | Select-Object Name,MacAddress
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
Get-NetAdapter | Select-Object Name,MacAddress
Get-WmiObject -Class Win32_NetworkAdapterConfiguration | Select-Object Description,MACAddress
((Get-NetAdapterBinding).DisplayName) -match 'Protocolo de Internet'
(Get-NetIPInterface) | Select-Object InterfaceAlias,AddressFamily
Get-NetIPv4Protocol
Get-NetIPv6Protocol
Get-NetRoute
Get-NetNat
Get-NetNatExternalAddress
Get-NetNatGlobal
Get-NetNatSession
Get-NetNatStaticMapping
Get-NetNatTransitionConfiguration
Get-NetNatTransitionMonitoring
Get-NetFirewallAddressFilter
Get-NetFirewallApplicationFilter
Get-NetFirewallInterfaceFilter
Get-NetFirewallInterfaceTypeFilter
Get-NetFirewallPortFilter
Get-NetFirewallProfile
Get-NetFirewallRule
Get-NetFirewallSecurityFilter
Get-NetFirewallServiceFilter
Get-NetFirewallSetting
Get-NetTCPSetting
Get-NetTCPConnection
Get-NetTCPConnection | Select-Object LocalPort,Remoteport
Get-NetUDPSetting
Get-NetUDPEndpoint
(Get-NetUDPEndpoint).LocalPort
Get-DnsClient
Get-DnsClientCache
Get-DnsClientGlobalSetting
Get-DnsClientNrptGlobal
Get-DnsClientNrptPolicy
Get-DnsClientNrptRule
Get-DnsClientServerAddress

```
```PowerShell
Add-WBBackupTarget
Add-WBBareMetalRecovery
Add-WBFileSpec
Add-WBSystemState
Add-WBVirtualMachine
Add-WBVolume
Get-WBBackupSet
Get-WBBackupTarget
Get-WBBackupVolumeBrowsePath
Get-WBBareMetalRecovery
Get-WBDisk
Get-WBFileSpec
Get-WBJob
Get-WBPerformanceConfiguration
Get-WBPolicy
Get-WBSchedule
Get-WBSummary
Get-WBSystemState
Get-WBVirtualMachine
Get-WBVolume
Get-WBVssBackupOption
New-WBBackupTarget
New-WBFileSpec
New-WBPolicy
Remove-WBBackupSet
Remove-WBBackupTarget
Remove-WBBareMetalRecovery
Remove-WBCatalog
Remove-WBFileSpec
Remove-WBPolicy
Remove-WBSystemState
Remove-WBVirtualMachine
Remove-WBVolume
Restore-WBCatalog
Resume-WBBackup
Resume-WBVolumeRecovery
Set-WBPerformanceConfiguration
Set-WBPolicy
Set-WBSchedule
Set-WBVssBackupOption
Start-WBApplicationRecovery
Start-WBBackup
Start-WBFileRecovery
Start-WBHyperVRecovery
Start-WBSystemStateRecovery
Start-WBVolumeRecovery
Stop-WBJob

```
```PowerShell
Get-ComputerRestorePoint
Restore-Computer
Get-ComputerRestorePoint

```
```PowerShell
#Restaurar el sistema a un punto de restauración anterior
Restore-Computer -RestorePoint 253

#Restaurar y comprobar estado
Get-ComputerRestorePoint
Restore-Computer -RestorePoint 255
Get-ComputerRestorePoint -LastStatus

```
```PowerShell
Get-Process
gps
ps
Get-WmiObject -Class win32_process

Stop-Process

Get-WmiObject -Class Win32_Thread

Get-Service
Get-WmiObject -Class Win32_Service
Get-WmiObject -query "select * from win32_service"

Get-EventLog

```
```PowerShell
#Eventos System
Get-EventLog system

```
