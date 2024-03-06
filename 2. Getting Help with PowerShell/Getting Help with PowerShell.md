# Pluralsight - Getting help with PowerShell

## working with Help

- `Get-Help` will print out entire help page
- `help` will print the help page, but with with pagination
- `man` is an alias for `Get-Help`

To update the help run `Update-Help`. This will download entire manual pages for commands installed on the machine.

This command will display only *Examples* section, if it is available:

```powershell
Get-Help Connect-PnPOnline -Examples
```

There are also `about_*` (topics) help files, which extends the help provided by the cmdlet or function. They are not always available.

Help can be acquired from online sources just by specifying parameter `-Online`.

>NOTE: some online help can unavailable or old.

## Interpreting Help

### Syntax

```text
Connect-PnPOnline [[-Url] <String>] [-ValidateConnection] -AccessToken
    <String> [-AzureEnvironment {Production | PPE | China | Germany |
    USGovernment | USGovernmentHigh | USGovernmentDoD | Custom}]
    [-ReturnConnection] [-Verbose] [-MicrosoftGraphEndPoint <String>]
    [-AzureADLoginEndPoint <String>] [<CommonParameters>]
```

If there is `-DisplayName <String[]>`, it accepts collection of string, typically separated with comma.

If there is only `-Required` parameter without a type following it, it is *true/false* value (aka 'switch'), nothing else is required. If the same parameter has specified *boolean* type, we need to specify it explicitly like `-Required $true`.

If the parameter is in square brackets like so: `[-DisplayName <String[]>]`, the parameter is optional and does not have to be specified.

There can be a *positional parameters* like `[[-Name] <String>]`. This means, that the *Name* keyword is not required and user can only specify the literal name as string without the `-Name` before it.

`<CommonParameters>` is a placeholder for all common parameters like `-Verbose`, `-ErrorAction` etc.

To lookup more detiled information about the paramaters, users can run:

```powershell
help Connect-PnPOnline -Parameter url,clientid
```

Which will output:

```text
-Url <String>
    The Url of the site collection or subsite to connect to, i.e.
    tenant.sharepoint.com, https://tenant.sharepoint.com,
    tenant.sharepoint.com/sites/hr, etc.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false


-ClientId <String>
    The Client ID of the Azure AD Application

    Required?                    false
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false
```

If the *Position?* is `0`, we don't have type the parameter name, just value. If it is set to `named`, we need to type in the parameter name.

