# Pluralsight - Installing and Running PowerShell

## Installing Powershell

*Script is already located in the 'Introduction' folder*

To get the latest package from CLI (on Windows `Install-PowerShell` is enough), run:

```powershell
Get-PSReleaseAsset -Family MacOS -LTS -format pkg | Save-PSReleaseAsset -Path "$PSScriptRoot/../Updates/" | Remove-Item "$PSScriptRoot./Updates/*x64*"
```

## Navigating

To search recursively for a particular item through directory, run:

```powershell
Get-ChildItem -Path '../*.jpg' -Recurse
```

Instead of using *Get-ChildItem* we can use `dir` or `ls`. Other Cmdlets are also aliased.

## Commands

`Get-Command` followed by *name* of the command, will return the command basic information. If we follow up with `-Syntax` (typing `-` followed by hitting Tab key will list all possible parameters for the particular command) will return the correct syntax help for the searched command. For example, `Get-Command -noun *share* -verb *Re*` will find all commands, that contains *Remove* or *Revoke* along with *Share* commands.

> Alias for `Get-Command` is `gcm`.

`Get-Command -CommandType Alias` will list all aliases for the current PowerShell session. To get the **active** aliases in the current PowerShell sessions, run `Get-Aliases`.

We can also use `help Get-Service` to get the manual page for the command.

Hitting `Ctrl + R` will launch search for the recent commands. Start typing and PowerShell will search through command history.