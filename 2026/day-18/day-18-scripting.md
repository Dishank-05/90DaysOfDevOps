# Day 18 – Shell Scripting: Functions & intermediate Concepts

### Task 1: Basic Functions

### functions.sh

```bash
#!/bin/bash

greet(){

        echo "Hello, $1!"
}

add(){

        sum=$(( $1 + $2 ))
        echo "Sum is : $sum"
}

#call function

greet Dishank
add 5 7
```

### Task 2: Functions with Return Values

### disk_check.sh

```bash

#!/bin/bash

check_disk(){

        echo "Disk Usage:"
        df -h /
}

check_memory(){

        echo "Memory Usage:"
        free -h
}

main() {

        check_disk
        echo ""
        check_memory
}

main


```
### Task 3: Strict Mode — set -euo pipefail

```bash

#!/bin/bash

set -euo pipefail

echo "Strict mode"

#echo "1. Testing set -u (exit on undefined variable)"

#echo "Using undefined variable"

#echo "$MY_VAR"

#echo "This line should not run"

#echo "2. Testing set -e (exit on error)"

#ls /directory_idk

#echo "This line wont run as above directory doesnt exist"

echo "3. Testing set -o pipefile"

cat missingfile.txt | grep "hello"

echo "This line wont run because pipefile has detected pipeline failure"


```

- set -e means Script will fail once there is any error in script and further line wont get execute 
- set -u means error will occured if using undefined variables
- set -o pipefail means pipeline fails if any commands in pipe fail

### Task 4: Local Variables

```bash

#!/bin/bash

localfunc() {

        local name="Dishank"
        echo "Inside localfunc: name = $name"
}

globalfunc() {

        city="Mumbai"
        echo "Inside globalfunc: city = $city"
}

localfunc
echo "Printing name variable present in localfunc: $name"
globalfunc
echo "Printing city variable present in globalfunc: $city"


```
### Task 5: Build a Script — System Info Reporter

```bash
#!/bin/bash

set -euo pipefail

print_header(){
        echo
        echo "==================================="
        echo "$1"
        echo "==================================="
}

system_info(){
        print_header "System Info"
        hostname
        uname -a
}

system_uptime(){
        print_header "System Uptime"
        uptime
}

system_diskusage(){
        print_header "System Disk Usage"
        #du -h / --max-depth=1 2>/dev/null | sort -rh | head -5
        du -h / --max-depth=1 2>/dev/null | sort -rh | head -5 || true

}

system_memory_usage(){
        print_header "System Memory Usage"
        free -h
}

system_cpu_process(){
        print_header "Top CPU Processes"
        ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head -6
}

main (){
        system_info
        system_uptime
        system_diskusage
        system_memory_usage
        system_cpu_process
}

main
                   

```
