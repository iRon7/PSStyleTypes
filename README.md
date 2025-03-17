# PSStyleTypes
Supplies a set of PSStyle types for inline coloring

## Description
There are few reasons to [avoid the write-host cmdlet][2] and even for coloring text the use questionable because:

* Hardcoded colors as e.g. `Yellow` should be avoided as they might conflict with the theme of the host
* It can only coloring the full line and not a part of it (multiple [Write-Host][3] commands are requied to do so)

For this each color property in [Get-PSReadLineOption][4] is available as a type (e.g. `[CommandColor]`) which
result in a need PowerShell syntax that also makes sure that the orginal (color) selection is being reset:

### Example 1
To color a specific word in a specific line you might use the following syntax:

"This is an $([EmphasisColor]'emphasis') and this is an $([ErrorColor]'Error')."

### Example 2
There are no backgroud colors defined. Instead the `InverseColor` could be used:


An exitcode $([ErrorColor][InverseColor]13) has been returned."
