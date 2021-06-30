## Sysmon Download and install Sysmon and Winlogbeats  

cd c:\users\rangecontrol\downloads
New-Item -ItemType Directory -Name Security
cd Security

Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/sysmon-config/repository/sysmonconfig-export.xml -OutFile ./sysmon-config.xml  

Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/Sysinternals/repository/Sysmon.exe -OutFile ./sysmon.exe  

Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/winlogbeat-6.8.8/repository/winlogbeat-6.8.8-windows-x86_64.zip -OutFile ./winlogbeats.zip  

Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/winlogbeat-6.8.8/repository/winlogbeat.yml -OutFile ./winlogbeat.yml  

sysmon.exe -accepteula -i sysmonconfig-export.xml

((Get-content .\winlogbeat.yml -raw) -replace "seconion_ip", "91.73.30.75") | set-content .\winlogbeat.yml  

((Get-content .\winlogbeat.yml -raw) -replace "seconion_ip", "91.73.30.75") | set-content .\winlogbeat.yml  

Expand-archive .\winlogbeats.zip -destination .\winlogbeat
move-item .\winlogbeat\winlogbeat-6.8.8-windows.x86_64\* .\winlogbeat
move-item .\winlogbeat "c:\program files\"  

& "c:\Program Files\winlogbeat\install-service-winlogbeat.ps1"  

## Ben ORR Artifacts

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion"

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion\Admin"

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion\Scripts"

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion\Filebeats"

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion\Sysmon"

New-Item -ItemType Directory -path c:\users\$env:USERNAME\Documents -name "Security Onion\Winlogbeats"  

## Create the text documents

New-Item -ItemType File -Path "C:\Users\169user\Documents\Security Onion\Admin\Things to do" -Name "ThingsToDo.txt"  

Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "user: bStar"  
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "password: P@ssword01"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" " "
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Add CentOS Boxes in IT-User space to allow SO-Allow as Analyst"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Add Beats config for the Pfsence and CentOS boxes"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Update WinlogBeats Config on the domain controllers to ship PowerShell Logs"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Update Winlogbeats to ship top events only"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Open Firewall on the Seconion to ingest firewall logs from Pfsence"
Add-Content "C:\Users\169user\Documents\Security Onion\Admin\Things to do\ThingsToDo.txt" "Setup Repo to be able to update Seconion and APT packages"

New-Item -ItemType File -Path "C:\Users\169user\Documents\Security Onion\FileBeats" -Name "ThingsToDo.txt"  -value "Install FileBeats on Pfsence"

Add-Content "C:\Users\169user\Documents\Security Onion\FileBeats\ThingsToDo.txt" "INstall FileBeats on the 2 CentOS Boxes in the IT user group"

Expand-archive .\winlogbeats.zip -destination .\winlogbeat  
move-item .\winlogbeat\winlogbeat-6.8.8-windows.x86_64\* .\winlogbeat
move-item .\winlogbeat "c:\Users\$env:UserName\Documents\Security Onion\Winlogbeats"  

move-item .\sysmon.exe "c:\users\$env:UserName\Documents\Security Onion\Sysmon"  

move-item .\sysmon-config.xml "c:\users\$env:UserName\Documents\Security Onion\Sysmon"

Move-Item .\Install-notes.ps1 "c:\users\$env:UserName\Documents\Security Onion\Scripts" 
