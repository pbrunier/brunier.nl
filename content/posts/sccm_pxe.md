---
author: ["Patrick Brunier"]
title: "SCCM – Automaticly clear PXE advertisements"
date: "2015-04-18"
description: ""
summary: "If you want to automaticly clear the PXE advertisements of a certain age..."
tags: ["Powershell","PXE","SCCM","Windows"]
categories: ["IT"]
series: [""]
ShowToc: false
TocOpen: false
---
If you want to automaticly clear the PXE advertisements of a certain age, you can use the Powershell script below to clear them.
The script determines what advertisements are OK to clear, using a WQL query. Please note…timing logic works accurate if you keep $minutesBeforeAction < 60. Otherwise you might need to alter the logic a bit. Have fun

```powershell
Import-Module “C:Program Files (x86)Microsoft Configuration ManagerAdminConsolebinConfigurationManager.psd1”

$siteServer = “localhost”

$siteCode = “SITECODE”

$minutesBeforeAction = 15

$query = “select lastPXEAdvertisementTime, NetbiosName from SMS_LastPXEAdvertisement”

$formattedTime = [bigint](Get-Date).ToString(“yyyyMMddhhmmss”)

cd “$($siteCode):”

$PXEAdvertisements = Get-WmiObject -Query $query -Namespace “ROOTSMSsite_$siteCode” -ComputerName “$siteServer”

foreach ($PXEAdvertisement in $PXEAdvertisements){

    $simpleLastPXEAdvertisementTime = [bigint]$PXEAdvertisement.LastPXEAdvertisementTime.Split(“.”)[0]

    if ($formattedTime – $simpleLastPXEAdvertisementTime -gt ($minutesBeforeAction*100)){

        Clear-CMPxeDeployment -DeviceName $PXEAdvertisement.NetbiosName

    }

}
```