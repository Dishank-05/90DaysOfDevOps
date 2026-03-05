# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

# Task 1 - For Loop

### 1. for_loop.sh 

```bash

#!/bin/bash

for fruit in MuskMelon Grapes Apple Lichi Orange
do
        echo "Fruit: $fruit"
done

```

### 2. count.sh

```bash

#!/bin/bash

for i in {1..10}
do
        echo $i
done


```
# Task 2 - While Loop

### countdown.sh

```bash

#!/bin/bash

read -p "Enter a num for countdown: " num

while [ $num -ge 0 ]
do
        echo $num
        ((num--))
done
echo "Done!"


```
# Task 3 - Command-Line Arguments

### 1. greet.sh

```bash

#!/bin/bash

if [ -z "$1" ]
then
        echo "Usage: ./greet.sh"
else
        echo "Hello, $1!"
fi

```

### 2. args_demo.sh

```bash

#!/bin/bash

echo "Total Arguments: $#"
echo "All Arguments: $@"
echo "Script name: $0"


```
# Task 4 - Install Packages via Script

```bash 

#!/bin/bash

if [ "$EUID" -ne 0 ];
then
        echo "Please run as root"
        exit 1
fi

packages=(nginx curl-minimal wget)

for pkg in "${packages[@]}"
do
        if dpkg -s $pkg &> /dev/null
        then
                echo "$pkg is already installed. Skipping"
        else
                echo "Installing $pkg..."
                yum install -y $pkg
        fi
done


```
# Task 5 - Error Handling 

```bash

#!/bin/bash

set -e

mkdir /tmp/devops-test 2>/dev/null || echo "Directory already exists"

cd /tmp/devops-test || { echo "Failed to enter directory"; exit 1; }

touch testfile.txt || echo "Failed to create file"

echo "Script completed successfully!"


```

# What I learned 

- How to use for and while loops in bash scripting.

- How to handle command-line arguments using $1, $#, $@.

- How to implement basic error handling using set -e and root checks.
