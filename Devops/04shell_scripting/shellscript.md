# Linux Shell Scripting (DevOps Notes)

## 1. What is Shell Scripting?

A shell script is a text file containing a sequence of Linux commands
executed by the shell.

Used for: - Automation - System administration - Deployment tasks -
Monitoring and backups

------------------------------------------------------------------------

## 2. Types of Shells

  Shell   Description
  ------- ----------------------------------
  sh      Bourne Shell
  bash    Bourne Again Shell (Most Common)
  zsh     Z Shell
  ksh     Korn Shell

Check current shell:

``` bash
echo $SHELL
```

------------------------------------------------------------------------

## 3. Creating a Shell Script

### Step 1: Create file

``` bash
nano script.sh
```

### Step 2: Add Shebang

``` bash
#!/bin/bash
```

### Step 3: Give execute permission

``` bash
chmod +x script.sh
```

### Step 4: Run script

``` bash
./script.sh
```

------------------------------------------------------------------------

## 4. Variables

``` bash
name="Pranay"
echo $name
```

### Read user input

``` bash
read username
echo "Hello $username"
```

------------------------------------------------------------------------

## 5. Conditional Statements

### If Statement

``` bash
if [ $a -gt 10 ]
then
  echo "Greater than 10"
fi
```

### If-Else

``` bash
if [ $a -gt 10 ]
then
  echo "Greater"
else
  echo "Smaller"
fi
```

------------------------------------------------------------------------

## 6. Loops

### For Loop

``` bash
for i in 1 2 3 4 5
do
  echo $i
done
```

### While Loop

``` bash
while [ $count -le 5 ]
do
  echo $count
  ((count++))
done
```

------------------------------------------------------------------------

## 7. Command Line Arguments

``` bash
echo $1
echo $2
echo $#
echo $@
```

------------------------------------------------------------------------

## 8. Functions

``` bash
function greet() {
  echo "Hello $1"
}

greet Pranay
```

------------------------------------------------------------------------

## 9. Exit Status

Check previous command status:

``` bash
echo $?
```

0 = Success\
Non-zero = Failure

------------------------------------------------------------------------

## 10. Arithmetic Operations

``` bash
a=10
b=5
sum=$((a+b))
echo $sum
```

------------------------------------------------------------------------

## 11. File Handling

### Check if file exists

``` bash
if [ -f file.txt ]
then
  echo "File exists"
fi
```

### Check directory

``` bash
if [ -d folder ]
then
  echo "Directory exists"
fi
```

------------------------------------------------------------------------

## 12. Case Statement

``` bash
case $1 in
  start)
    echo "Starting"
    ;;
  stop)
    echo "Stopping"
    ;;
  *)
    echo "Invalid option"
    ;;
esac
```

------------------------------------------------------------------------

## 13. Important Operators

  Operator   Meaning
  ---------- ------------------
  -eq        Equal
  -ne        Not equal
  -gt        Greater than
  -lt        Less than
  -ge        Greater or equal
  -le        Less or equal

------------------------------------------------------------------------

## 14. Useful DevOps Shell Script Examples

### Disk Usage Monitor

``` bash
df -h
```

### Memory Usage

``` bash
free -m
```

### Process Monitoring

``` bash
ps -ef
```

------------------------------------------------------------------------

## 15. Debugging Scripts

Run in debug mode:

``` bash
bash -x script.sh
```

------------------------------------------------------------------------

## 16. Best Practices

-   Always use shebang
-   Add comments for clarity
-   Validate user inputs
-   Check exit status of critical commands
-   Use meaningful variable names

------------------------------------------------------------------------

## 17. Interview-Important Commands Summary

``` bash
chmod
read
if
for
while
case
echo
exit
```
