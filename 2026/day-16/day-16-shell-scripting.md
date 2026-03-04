# Day 16 – Shell Scripting Basics

# Task 1 – First Script

## hello.sh

```bash
#!/bin/bash
echo "Hello, DevOps!"
```

### If we remove #!/bin/bash line the script will run if bash is default shell, shebang explicitly tells systems which interpreter to use. 

# Task 2 – Variables

```
#!/bin/bash
NAME="Dishank"
ROLE="DevOps Engineer"
echo "Hello, I am $NAME and I am a $ROLE"

```
### If we use double quote while printing it will print value store inside variable but if we use single quote then it will print literal string as it is.

# Task 3 - User Input with read

```
#!/bin/bash

read -p "Enter your name: " NAME
read -p "Enter your favourite tool: " TOOL

echo "Hello $NAME, your favourite tool is $TOOL"

```
# Task 4 - If- Else 

```
1. 

#!/bin/bash

read -p "Enter a number: " NUM

if [ $NUM -gt 0 ]; then
    echo "Number is Positive"
elif [ $NUM -lt 0 ]; then
    echo "Number is Negative"
else
    echo "Number is Zero"
fi

```
```
2.

#!/bin/bash

read -p "Enter filename: " FILE

if [ -f "$FILE" ]; then
    echo "File exists."
else
    echo "File does not exist."
fi

```

# Task 5 - Combine It All

```
#!/bin/bash

SERVICE="nginx"

read -p "Do you want to check the status of $SERVICE? (y/n): " CHOICE

if [ "$CHOICE" = "y" ]; then
    if systemctl is-active --quiet $SERVICE; then
        echo "$SERVICE is active."
    else
        echo "$SERVICE is not active or not installed."
    fi
else
    echo "Skipped."
fi

```


