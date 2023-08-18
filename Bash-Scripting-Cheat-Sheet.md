# Bash Scripting Cheat Sheet

## Shebang (Interpreter directive)
```bash
#!/bin/bash
```

## Comments
```bash
# This is a single-line comment

: '
This is a multi-line
comment
'
```

## Variables
```bash
variable_name=value
```

### Variable Types
- **Local Variable:** Visible only within the current shell session.
- **Environment Variable:** Available to any child processes.
- **Readonly Variable:** Cannot be changed or unset.

## Command Substitution
```bash
result=$(command)
```

## Printing
```bash
echo "Hello, world!"
```

## Input
```bash
read variable_name
```

## Conditional Statements
### if-else-fi
```bash
if [ condition ]; then
    # statements
elif [ condition ]; then
    # statements
else
    # statements
fi
```

### Case Statement
```bash
case "$variable" in
    pattern1)
        # statements
        ;;
    pattern2)
        # statements
        ;;
    *)
        # default statements
        ;;
esac
```

## Loops
### For Loop
```bash
for item in list; do
    # statements
done
```

### While Loop
```bash
while [ condition ]; do
    # statements
done
```

## Functions
```bash
function_name() {
    # statements
}
```

## Command Line Arguments
```bash
$0 # Script name
$1, $2, ... # Positional parameters
$# # Number of arguments
$@ # All arguments as separate strings
$* # All arguments as a single string
```

## Arithmetic Operations
```bash
result=$((expression))
```

## String Operations
- Concatenation: `string1="Hello,"; string2=" world!"; result="$string1$string2"`
- Length: `length=${#string}`
- Substring: `substring=${string:start:length}`
- Replace: `new_string=${string/old_pattern/new_pattern}`

## File Operations
- Check if a file exists: `[ -e file_path ]`
- Check if a file is a directory: `[ -d directory_path ]`
- Check if a file is readable: `[ -r file_path ]`
- Check if a file is writable: `[ -w file_path ]`
- Check if a file is executable: `[ -x file_path ]`

## Exit Status
- `0`: Success
- Non-zero: Error

## File Redirection
- Redirect STDOUT: `command > file`
- Append to a file: `command >> file`
- Redirect STDIN: `command < file`
- Redirect STDERR: `command 2> error_file`
- Redirect both STDOUT and STDERR: `command &> output_and_error_file`

## Pipes
```bash
command1 | command2
```

## Permissions
- Change permissions: `chmod permissions file`
- Example: `chmod +x script.sh`

## Useful Commands
- `ls`: List files and directories
- `cd`: Change directory
- `pwd`: Print current directory
- `mkdir`: Create directory
- `cp`: Copy files or directories
- `mv`: Move files or directories
- `rm`: Remove files or directories
- `grep`: Search text
- `sed`: Stream editor for text manipulation
- `awk`: Text processing tool

## Exit Script
```bash
exit
```

---
**Note:** This cheat sheet provides essential commands and syntax for writing Bash scripts. For more in-depth information, consult the Bash documentation.

Copy the entire content above, and when you paste it into your GitHub repository's Markdown file, it should retain the formatting and display as intended.

---
**Note:** This cheat sheet is a reference guide and might not cover all scenarios. Always refer to the official documentation and consult with experienced developers for complex projects.

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.
