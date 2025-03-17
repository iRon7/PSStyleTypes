# PSStyleTypes
Supplies a set of PSStyle types for inline coloring

## Description
There are few reasons to [avoid the write-host cmdlet][2] and even for coloring text the use is questionable because:

* Hardcoded colors as e.g. `Yellow` should be avoided as they might conflict with the theme of the host
* It can only coloring the full line and not a part of it (multiple [Write-Host][3] commands are requied to do so)

For this each color property in [Get-PSReadLineOption][4] is available as a type (e.g. `[CommandColor]`) which
result in a need PowerShell syntax that also makes sure that the orginal (color) selection is being reset:

### Example 1
To color a specific word in a specific line you might use the following syntax:

```PowerShell
"This is a $([CommentColor]'comment') and this is an $([ErrorColor]'error')."
```

![alt text](https://github.com/iRon7/PSStyleTypes/blob/main/CommentError.png?raw=true)

### Example 2
There are **no backgroud colors** defined. Instead the `InverseColor` could be used:

```PowerShell
An exitcode $([ErrorColor][InverseColor]13) has been returned."
```

![alt text](https://github.com/iRon7/PSStyleTypes/blob/main/ExitCode.png?raw=true)

[1]: https://learn.microsoft.com/dotnet/api/system.management.automation.psstyle "PSStyle Class"
[2]: https://learn.microsoft.com/powershell/utility-modules/psscriptanalyzer/rules/avoidusingwritehost "avoid the write-host cmdlet"
[3]: https://learn.microsoft.com/powershell/module/microsoft.powershell.utility/write-host "Write-Host"
[4]: https://learn.microsoft.com/powershell/module/psreadline/get-psreadlineoption "Get-PSReadLineOption"
