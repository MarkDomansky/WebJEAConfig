# WebJEA: PowerShell driven Web Forms for Secure Self-Service

> [!IMPORTANT]
> **This repository is archived and the WebJEAConfig module is no longer needed.**
>
> The WebJEA `config.json` file now has a published JSON schema. Keep the `$schema` line in your config and editors like VS Code will validate and autocomplete it as you type, with no module required:
>
> ```json
> "$schema": "https://raw.githubusercontent.com/markdomansky/WebJEA/master/schemas/webjea-config-2026-04.schema.json"
> ```
>
> Because the config is no longer tied to a companion PowerShell module, new configuration options can ship as soon as WebJEA supports them. This makes WebJEA much more flexible and much faster to improve. See the [WebJEA repository](https://github.com/markdomansky/WebJEA) for current configuration docs.

WebJEA allows you to dynamically build web forms for any PowerShell script.  WebJEA automatically parses the script at page load for description, parameters and validation, then dynamically builds a form to take input and display formatted output.  You define access groups via AD and the scripts run within the AppPool user context.

**This is the PowerShell Module used to modify the configuration of a [WebJEA](../WebJEA) site.**

## Requirements

* Domain Joined server running Windows 2016 Core/Full with PowerShell 5.1 <br>_(Windows 2012 R2 or PowerShell 4.0 should work, but haven't been tested.)_

## Releases

All releases are published on [PowerShellGallery.com](powershellgallery.com/)

## Installation

WebJEAConfig is installed via PowerShellGallery.com.

```powershell
Install-Package WebJEAConfig
```

## Adding Scripts to WebJEA

```powershell
Import-Module WebJEAConfig
Open-WebJEAConfig "c:\webjea\config.json" 
Set-WebJEAConfig -PermittedGroups @('domain\group3') #these groups will have access to all commands
New-WebJEACommand -DisplayName "New Script" -Script "c:\webjea\newscript.ps1" -PermittedGroups @('domain\group1','domain\group2') #these groups will have access only to this commandh
Save-WebJEAConfig
```

## License

Copyright, 2018, Mark Domansky.  All rights not granted explicitly are reserved.

This code is released under the GPL v3 license.

