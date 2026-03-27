# Windows Command Line Cheat Sheet
### CMD & PowerShell Quick Reference

---

## Table of Contents
- [Navigation](#navigation)
- [File & Directory Management](#file--directory-management)
- [Viewing & Searching Files](#viewing--searching-files)
- [System Information](#system-information)
- [Network Commands](#network-commands)
- [Process Management](#process-management)
- [User & Permissions](#user--permissions)
- [Environment Variables](#environment-variables)
- [Scripting Essentials](#scripting-essentials)
- [Package Management (PowerShell)](#package-management-powershell)
- [Useful Shortcuts & Tips](#useful-shortcuts--tips)

---

## Navigation

| Task | CMD | PowerShell |
|---|---|---|
| Print current directory | `cd` | `pwd` or `Get-Location` |
| Change directory | `cd folder\path` | `cd folder\path` or `Set-Location` |
| Go up one level | `cd ..` | `cd ..` |
| Go to root of drive | `cd \` | `cd \` |
| Change drive | `D:` | `D:` |
| List directory contents | `dir` | `ls` or `Get-ChildItem` |
| List with hidden files | `dir /a` | `ls -Force` |
| List subdirectories only | `dir /ad` | `ls -Directory` |
| Clear screen | `cls` | `cls` or `Clear-Host` |

---

## File & Directory Management

| Task | CMD | PowerShell |
|---|---|---|
| Create a directory | `mkdir foldername` | `mkdir foldername` or `New-Item -ItemType Directory` |
| Remove an empty directory | `rmdir foldername` | `rmdir foldername` |
| Remove directory (recursive) | `rmdir /s /q foldername` | `rm -Recurse -Force foldername` |
| Create a file | `echo. > file.txt` | `New-Item file.txt` |
| Copy a file | `copy source.txt dest.txt` | `Copy-Item source.txt dest.txt` |
| Move a file | `move source.txt dest\` | `Move-Item source.txt dest\` |
| Rename a file | `ren oldname.txt newname.txt` | `Rename-Item oldname.txt newname.txt` |
| Delete a file | `del file.txt` | `rm file.txt` or `Remove-Item file.txt` |
| Delete all files in folder | `del /q /f folder\*` | `rm folder\* -Force` |
| Copy directory (recursive) | `xcopy src\ dest\ /s /e` | `Copy-Item src\ dest\ -Recurse` |

---

## Viewing & Searching Files

| Task | CMD | PowerShell |
|---|---|---|
| Print file contents | `type file.txt` | `cat file.txt` or `Get-Content file.txt` |
| Print first N lines | *(not built-in)* | `Get-Content file.txt -TotalCount 10` |
| Print last N lines | *(not built-in)* | `Get-Content file.txt -Tail 10` |
| Search for text in file | `findstr "text" file.txt` | `Select-String "text" file.txt` |
| Search recursively | `findstr /s /i "text" *.txt` | `Select-String "text" *.txt -Recurse` |
| Find files by name | `where /r . filename.txt` | `Get-ChildItem -Recurse -Filter "filename.txt"` |
| Compare two files | `fc file1.txt file2.txt` | `Compare-Object (gc file1.txt) (gc file2.txt)` |
| Count lines in file | `find /c /v "" file.txt` | `(Get-Content file.txt).Count` |

---

## System Information

| Task | CMD | PowerShell |
|---|---|---|
| OS version | `winver` | `[System.Environment]::OSVersion` |
| System info | `systeminfo` | `Get-ComputerInfo` |
| Hostname | `hostname` | `hostname` or `$env:COMPUTERNAME` |
| Username | `echo %USERNAME%` | `$env:USERNAME` or `whoami` |
| CPU info | `wmic cpu get name` | `Get-WmiObject Win32_Processor` |
| RAM info | `wmic memorychip get capacity` | `Get-WmiObject Win32_PhysicalMemory` |
| Disk info | `wmic diskdrive get size` | `Get-PSDrive` |
| Uptime | `net stats workstation` | `(Get-Date) - (gcim Win32_OperatingSystem).LastBootUpTime` |
| List installed software | `wmic product get name` | `Get-Package` |

---

## Network Commands

| Task | CMD | PowerShell |
|---|---|---|
| Show IP config | `ipconfig` | `Get-NetIPConfiguration` |
| Full IP details | `ipconfig /all` | `Get-NetIPAddress` |
| Flush DNS cache | `ipconfig /flushdns` | `Clear-DnsClientCache` |
| Ping a host | `ping google.com` | `Test-Connection google.com` |
| Trace route | `tracert google.com` | `Test-NetConnection -TraceRoute google.com` |
| DNS lookup | `nslookup google.com` | `Resolve-DnsName google.com` |
| Show open ports/connections | `netstat -an` | `Get-NetTCPConnection` |
| Show routing table | `route print` | `Get-NetRoute` |
| Test port connectivity | *(not built-in)* | `Test-NetConnection -ComputerName host -Port 443` |
| Download a file | *(not built-in)* | `Invoke-WebRequest -Uri "url" -OutFile "file"` |

---

## Process Management

| Task | CMD | PowerShell |
|---|---|---|
| List running processes | `tasklist` | `Get-Process` |
| Find process by name | `tasklist \| findstr "chrome"` | `Get-Process -Name "chrome"` |
| Kill process by name | `taskkill /im chrome.exe /f` | `Stop-Process -Name "chrome" -Force` |
| Kill process by PID | `taskkill /pid 1234 /f` | `Stop-Process -Id 1234 -Force` |
| Start a program | `start notepad.exe` | `Start-Process notepad.exe` |
| Run as administrator | *(right-click)* | `Start-Process cmd -Verb RunAs` |
| Schedule a task | `schtasks /create ...` | `New-ScheduledTask` |
| List scheduled tasks | `schtasks /query` | `Get-ScheduledTask` |

---

## User & Permissions

| Task | CMD | PowerShell |
|---|---|---|
| Current user | `whoami` | `whoami` or `$env:USERNAME` |
| List local users | `net user` | `Get-LocalUser` |
| Add a local user | `net user username pass /add` | `New-LocalUser "username" -Password (Read-Host -AsSecureString)` |
| Delete a user | `net user username /delete` | `Remove-LocalUser "username"` |
| List local groups | `net localgroup` | `Get-LocalGroup` |
| Add user to group | `net localgroup Administrators user /add` | `Add-LocalGroupMember -Group "Administrators" -Member "user"` |
| Check file permissions | `icacls file.txt` | `Get-Acl file.txt` |
| Take ownership of file | `takeown /f file.txt` | `(Get-Acl file.txt).SetOwner(...)` |

---

## Environment Variables

| Task | CMD | PowerShell |
|---|---|---|
| List all env vars | `set` | `Get-ChildItem Env:` or `ls env:` |
| Print a variable | `echo %PATH%` | `$env:PATH` |
| Set a variable (session) | `set MYVAR=value` | `$env:MYVAR = "value"` |
| Set a variable (permanent) | `setx MYVAR "value"` | `[System.Environment]::SetEnvironmentVariable("MYVAR","value","User")` |
| Delete a variable | `set MYVAR=` | `Remove-Item Env:MYVAR` |
| Append to PATH (session) | `set PATH=%PATH%;C:\new\path` | `$env:PATH += ";C:\new\path"` |

---

## Scripting Essentials

### CMD Batch Scripting

```batch
@echo off                          :: Suppress command echo
:: This is a comment
set NAME=World
echo Hello, %NAME%!

:: IF / ELSE
if "%1"=="yes" (echo Yes!) else (echo No!)

:: FOR loop
for %%i in (1 2 3) do echo %%i

:: Read input
set /p INPUT=Enter something:

:: Goto label
goto :myLabel
:myLabel
echo Jumped here!

:: Call another script
call other_script.bat
```

### PowerShell Scripting

```powershell
# This is a comment
$name = "World"
Write-Host "Hello, $name!"

# IF / ELSE
if ($x -gt 10) { "Big" } else { "Small" }

# Comparison operators: -eq -ne -lt -gt -le -ge

# FOR loop
foreach ($i in 1..5) { Write-Host $i }

# FOR each item
Get-Process | ForEach-Object { $_.Name }

# WHERE filter
Get-Process | Where-Object { $_.CPU -gt 10 }

# Functions
function Greet($name) {
    Write-Host "Hello, $name"
}
Greet "Stephen"

# Try / Catch
try {
    Do-Something
} catch {
    Write-Host "Error: $_"
}

# Read input
$input = Read-Host "Enter something"

# Pipeline output to file
Get-Process | Out-File processes.txt
```

---

## Package Management (PowerShell)

| Task | Command |
|---|---|
| Find a package | `Find-Package "name"` |
| Install a package | `Install-Package "name"` |
| List installed packages | `Get-Package` |
| Uninstall a package | `Uninstall-Package "name"` |
| Install from winget | `winget install "appname"` |
| Search winget | `winget search "appname"` |
| Update all winget apps | `winget upgrade --all` |
| Install PS module | `Install-Module -Name "ModuleName"` |
| List PS modules | `Get-Module -ListAvailable` |
| Update PS module | `Update-Module -Name "ModuleName"` |

---

## Useful Shortcuts & Tips

### CMD Shortcuts
| Shortcut | Action |
|---|---|
| `↑` / `↓` | Scroll through command history |
| `F7` | Show command history in a popup |
| `Tab` | Autocomplete file/folder name |
| `Ctrl+C` | Cancel running command |
| `Ctrl+V` | Paste (or right-click) |
| `Doskey /history` | Print full command history |

### PowerShell Shortcuts
| Shortcut | Action |
|---|---|
| `↑` / `↓` | Scroll through command history |
| `Ctrl+R` | Reverse search command history |
| `Tab` | Autocomplete (cycle through options) |
| `Ctrl+Space` | Show all completions |
| `Ctrl+C` | Cancel running command |
| `Get-History` | Show session command history |
| `Invoke-History N` | Re-run command #N from history |

### Handy One-Liners

```powershell
# Restart the computer in 60 seconds
shutdown /r /t 60

# Cancel a pending shutdown
shutdown /a

# Get public IP address
(Invoke-WebRequest ifconfig.me/ip).Content

# Empty the Recycle Bin
Clear-RecycleBin -Force

# Get Wi-Fi password for saved networks
netsh wlan show profile name="SSID" key=clear

# Export running processes to CSV
Get-Process | Export-Csv -Path processes.csv -NoTypeInformation

# Find large files over 100MB
Get-ChildItem C:\ -Recurse -ErrorAction SilentlyContinue |
  Where-Object { $_.Length -gt 100MB } |
  Sort-Object Length -Descending

# Bulk rename files
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace "old","new" }
```

---

> **Tip:** Run `Get-Help <cmdlet>` in PowerShell for detailed documentation on any command.
> Run `<command> /?` in CMD for help on any command.
