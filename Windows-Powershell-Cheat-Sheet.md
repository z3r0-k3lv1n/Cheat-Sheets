# Windows PowerShell Cheat Sheet

Windows PowerShell is a command-line shell and scripting language designed for system administration and automation tasks in the Windows environment.

## Basic Commands

- `Get-Help <cmdlet>`: Display help information for a specific cmdlet.
- `Get-Command`: List all available cmdlets.
- `Get-Alias`: List all defined aliases.
- `Get-Module`: List loaded modules.

## Working with Files and Directories

- `Get-ChildItem`: List files and directories in the current location.
- `Set-Location <path>`: Change the current working directory.
- `Copy-Item <source> <destination>`: Copy files or directories.
- `Move-Item <source> <destination>`: Move files or directories.
- `Remove-Item <path>`: Delete files or directories.

## Working with Processes

- `Get-Process`: List running processes.
- `Start-Process <executable>`: Start a new process.
- `Stop-Process <name>`: Stop a process.

## Working with Services

- `Get-Service`: List services.
- `Start-Service <name>`: Start a service.
- `Stop-Service <name>`: Stop a service.
- `Restart-Service <name>`: Restart a service.

## Working with Variables

- `$variableName = <value>`: Assign a value to a variable.
- `$variableName`: Access the value of a variable.
- `Clear-Variable <variableName>`: Clear the value of a variable.

## Working with Pipelines

- `|`: Pipe operator, passes the output of one cmdlet as input to another.
- `ForEach-Object`: Process each item in the pipeline.

## Filtering and Sorting

- `Where-Object`: Filter items based on a condition.
- `Sort-Object`: Sort items in ascending or descending order.

## Remote Management

- `Enter-PSSession`: Start an interactive session with a remote computer.
- `Invoke-Command`: Run commands on a remote computer.

## Scripting and Automation

- `.ps1` files: PowerShell script files.
- `Write-Output`: Send output to the pipeline.
- `if`, `else`, `elseif`: Conditional statements.
- `foreach`, `for`, `while`: Looping constructs.
- `Param()`: Define parameters for a script or function.

## Helpful Tips

- Use `Tab` for auto-completion of cmdlet and parameter names.
- Use `Get-Help` and `-Examples` parameter to see usage examples.
- Use `Get-Member` to explore the properties and methods of objects.

For more information and detailed documentation, visit the [official PowerShell documentation](https://docs.microsoft.com/en-us/powershell/).

**Remember:** PowerShell scripts execution policy might need to be adjusted. Use `Set-ExecutionPolicy` to change the policy.

