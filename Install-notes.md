cd c:\users\rangecontrol\downloads
Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/sysmon-config/repository/sysmonfonfig-export.xml -OutFile ./sysmon-config.xml
Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/Sysinternals/repository/Sysmon.exe -OutFile ./sysmon.exe
Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/winlogbeat-6.8.8/repository/winlogbeat-6.8.8-windows.x86_64.zip -OutFile ./winlogbeats.zip
Invoke-RestMethod -URI http://mirrors.it.com/mirrored/github.com/repositories/169CPT/winlogbeat-6.8.8/repository/winlogbeat.yml -OutFile ./winlogbeat.yml
sysmon.exe -accepteula -i sysmonconfig-export.xml
Expand-archive .\winlogbeats.exe -destination .\winlogbeat
move-item .\winlogbeat\winlogbeat-6.8.8-windows.x86_64\* .\winlogbeat
move-item .\winlogbeat "c:\program files\"
& "c:\Program Files\winlogbeat\install-service-winlogbeat.ps1"
start-service winlogbeat
