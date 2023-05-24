---
layout: default
title: set_network_conf.ps1
parent: powershell
nav_order: 2
---

```
Set-NetIPInterface -InterfaceAlias Ethernet -Dhcp Disabled
Clear-DnsClientCache
Get-NetAdapter -Name Ethernet| New-NetIPAddress -IPAddress [[ip]] -DefaultGateway [[gtw]] -PrefixLength [[/prefix]]
Get-NetAdapter -Name Ethernet |Set-DNSClientServerAddress -ServerAddresses [[ip]]
Set-NetAdapterAdvancedProperty -Name Ethernet -DisplayName "VLAN ID" -DisplayValue [[vlan]]
```

```
Set-NetIPInterface -InterfaceAlias Ethernet -Dhcp Enabled
Set-DnsClientServerAddress -InterfaceAlias Ethernet -ResetServerAddresses
Restart-NetAdapter -InterfaceAlias Ethernet
Set-NetIPInterface -InterfaceAlias Ethernet| Remove-NetRoute -Confirm:$false
Remove-NetRoute -InterfaceAlias "Ethernet" -NextHop [[gtw]] -Confirm:$false
Clear-DnsClientCache
```