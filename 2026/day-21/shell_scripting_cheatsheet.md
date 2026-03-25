# Shell Scripting Cheat Sheet

## Quick Reference Table

| Topic    | Key Syntax             | Example                          |
| -------- | ---------------------- | -------------------------------- |
| Variable | VAR="value"            | NAME="DevOps"                    |
| Argument | $1, $2                 | ./script.sh arg1                 |
| If       | if [ condition ]; then | if [ -f file ]; then             |
| For loop | for i in list; do      | for i in 1 2 3; do               |
| Function | name() { ... }         | greet() { echo "Hi"; }           |
| Grep     | grep pattern file      | grep -i "error" log.txt          |
| Awk      | awk '{print $1}' file  | awk -F: '{print $1}' /etc/passwd |
| Sed      | sed 's/old/new/g' file | sed -i 's/foo/bar/g' config.txt  |

---

## Basics

### Shebang

```bash
#!/bin/bash
```

Defines interpreter used to run script.

### Running Script

```bash
chmod +x script.sh    # Makes file executable
./script.sh           # Execute the script file
bash script.sh
```

### Comments

```bash
# This is a comment
echo "Hello" # inline comment
```

### Variables

```bash
NAME="Dishank"        # Assign Value Dishank to variable NAME
echo $NAME            # Print Dishank 
echo "$NAME"          # Print Dishank
echo '$NAME'          # Print $NAME as it is
```

### User Input

```bash
read name             # reads value from user and assign it to name variable
echo "Hello $name"    # Print Hello Dishank
```

### Command-line Arguments

```bash
echo $0               # Prints script name
echo $1               # Print 1 arg
echo $#               # Print Total Args
echo $@               # Print all args
echo $?               # Print 0 if success or non zero if error
```

---

## Operators & Conditionals

### String Comparison

```bash
[ "$a" = "$b" ]       # Condition to check string value same 
[ "$a" != "$b" ]      # Checks if string value is not same
[ -z "$a" ]           # Checks if a variable is empty
[ -n "$a" ]           # Checks if a variable is not empty
```

### Integer Comparison

```bash
[ $a -eq $b ]         # Checks whether integer value is same 
[ $a -ne $b ]         # Condition to check whether integer value should not be same
[ $a -lt $b ]         # Checks if a is less than b
[ $a -gt $b ]         # Checks if a is greater than b
[ $a -le $b ]         # checks if a is less than equal to b
[ $a -ge $b ]         # Checks if a is greater than equal to b
```

### File Tests

```bash
[ -f file ]             # Checks whether file exist or not
[ -d dir ]              # Checks whether directory exist or not
[ -e file ]             # Checks if file/directory exist
[ -r file ]             # Checks if file is readable
[ -w file ]             # Checks if file is writable
[ -x file ]             # Checks if file is executable
[ -s file ]             # Checks if file is not empty
```

### If-Else

```bash
if [ -f file ]; then    # Checks if file exist or not then it will print exists
  echo "Exists"
elif [ -d file ]; then  # if above condition fails it will check this condition and will check whether directory exist or not
  echo "Directory"
else
  echo "Not found"      # if non of above condition are true it will print not found
fi
```

### Logical Operators 

```bash
[ condition ] && echo "True"        # Runs Second command if first succeeds
[ condition ] || echo "False"       # Runs Second command even if first fails 
[ ! condition ]                     # Negates the condition
```

### Case Statement

```bash
case $var in                    
  start) echo "Start";;             # Executes when $var = start
  stop) echo "Stop";;               # Executes when $var = stop    
  *) echo "Unknown";;               # Default case (just like else)
esac
```

---

## Loops

### For Loop

```bash
for i in 1 2 3; do                  #iterates over whole list
  echo $i
done
```

### While Loop

```bash
while read line; do                  #keeps reading file line by line
  echo $line
done < file.txt
```

### Until Loop

```bash
until [ $a -gt 5 ]; do              # Runs until condition becomes true
  echo $a
done
```

### Loop Control

```bash
break                               # breaks logic and exits loop
continue                            #Skips current iteration
```

### Loop Files

```bash
for file in *.log; do               #iterates through all log file
  echo $file
done
```

---

## Functions

### Define Function

```bash
greet() {
  echo "Hello"                      # Function Definition
}
```

### Call Function

```bash
greet                               # Function Called
```

### Arguments

```bash
add() {
  echo $(($1 + $2))                 #Uses arguments
}
add 2 3
```

### Return vs Echo

```bash
return 1                            # returns status code not output
echo "value"                        # prints output
```

### Local Variables

```bash
myfunc() {                          
  local var="test"                  # Variable scope inside function only
}
```

---

## Text Processing

### grep

```bash
grep "error" file              # Search for "error"
grep -i "error" file           # Case-insensitive search
grep -c "error" file           # Count matches
grep -n "error" file           # Show line numbers
grep -v "error" file           # Exclude matching lines
grep -E "error|fail" file      # Multiple patterns (OR)
```

### awk

```bash
awk '{print $1}' file           # Prints first column
awk -F: '{print $1}' /etc/passwd    # Use ':' as delimiter
```

### sed

```bash
sed 's/foo/bar/g' file          #Replace foo with bar
sed -i 's/foo/bar/g' file       # Replace in file 
```

### cut

```bash
cut -d',' -f1 file.csv          # Extract column 1 using ',' delimiter
```

### sort

```bash
sort file                       # Sort alphabetically
sort -n file                    # Sort numerically
sort -r file                    # Reverse order sort
sort -u file                    # Sort in unique manner
```

### uniq

```bash
uniq file                       # Remove duplicates
uniq -c file                    # Count Occurences
```

### tr

```bash
echo "abc" | tr 'a-z' 'A-Z'     # Coanvert lower case to upper case
```

### wc

```bash
wc -l file                      # Count lines
wc -w file                      # Count Word
wc -c file                      # Count Character
```

### head / tail

```bash
head -n 10 file                 # Print starting 10 lines of file
tail -n 10 file                 # Print ending 10 lines of file
tail -f file                    # Live log Monitoring
```

---

## Useful One-Liners

### Delete files older than 7 days

```bash
find . -type f -mtime +7 -delete
```

### Count lines in logs

```bash
wc -l *.log
```

### Replace string in files

```bash
sed -i 's/foo/bar/g' *.txt
```

### Check service running

```bash
ps aux | grep nginx
```

### Disk usage check

```bash
df -h | grep '/$'
```

### Real-time error monitoring

```bash
tail -f app.log | grep "ERROR"
```

---

## Error Handling & Debugging

### Exit Codes

```bash
echo $?     # Get last command exit code
exit 0      # Exit with success
exit 1      # exit with Failure
```

### Strict Mode

```bash
set -e      # Exit script on error
set -u      # Error on undefined variable
set -o pipefail     # Fail in any command in pipe fails
```

### Debug Mode

```bash
set -x      # Debg Mode
```

### Trap

```bash
trap 'echo "Cleaning up"' EXIT          # Run command on script exit
```

---

## Tips

* Always use quotes: "$VAR"
* Prefer functions for reusable logic
* Use `set -euo pipefail` in production scripts
* Log outputs for debugging

