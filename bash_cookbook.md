# Lesson 1
- To be able to execute script you need to write this at the top of script
    ```sh
     #!usr/bin/env bash
    ```
- After that you need to make your script executable for enviroment
    ```sh
    $ chmod +x path\to\script
    ```

There are 2 types of writting commands:

1. ```sh
    pwd; ls; ... 
   ```
2. ```sh
    pwd
    ls
    ....
    ```

to write something in output use this:

```sh
echo "some string $variable"
```

There are to 2 ways to save command output in variable:
1. ```sh
     variable_name=  `command`
    ```
2. ```sh 
     variable_name= $(command)
   ```

There is a specific way to manipulate with arithmetic operators
```sh
 num1=2
 num2=10
 sum_var=(($num1 + $num2 ))
```

# Lesson 2

## if construction
```sh
if [[ CONDITION ]]
then
....
elif [[ CONDITION ]]
then
....
else
....
fi
```

## Condition Keys (for integers)

```sh
1. -eq is =
2. -gt is >    
3. -ge is >=
4. -lt is <
5. -le is <=
6. -ne is !=
```

## Enviromental variables
```sh
$0 - 'specific' path to script
${integer} - {integer} var given to script
$# - amount of vars given to script
${!#} - last var in list of vars
$* - not-iterable list of vars
$@ - iterable list of vars
```



to read input from console use `read`

### Example
```sh
#!/bin/bash
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program."

LESSON 3.


CYCLE FOR:
The loop diagram with a similar approach looks like this:

for (( the initial value of the variable ; end of cycle condition; variable change))

Example:
for (( a = 1; a < 10; a++ ))

Working example in the program:
#!/bin/bash
for (( i=1; i <= 10; i++ ))
do
echo "number is $i"
done

This code will display a list of numbers from 1 to 10.




CYCLE WHILE:
The for statement isn't the only way to organize loops in bash scripts. You can also use while loops here.


Here is a diagram of how the while loops are organized
while condition check command
do
other teams
done

Working example in the program:
#!/bin/bash
var1=5
while [ $var1 -gt 0 ]
do
echo $var1
var1=$[ $var1 - 1 ]
done

This code will display a list of numbers from 5 to 1



NESTED LOOPS:

Any commands can be used in the body of the loop, including launching other loops. Such constructs are called nested loops

Working example in the program:

#!/bin/bash
for (( a = 1; a <= 3; a++ ))
do
echo "Start $a:"
for (( b = 1; b <= 3; b++ ))
do
echo " Inner loop: $b"
done
done

As you can see, first, the first iteration of the outer loop is performed, then three iterations of the inner one, after its completion, the outer loop comes into play again, then the inner loop again.



File content processing:
The most common use of nested loops is to process files.
So, the outer loop is busy iterating over the lines of the file, and the inner one is already working with each line.

Working example in the program:
#!/bin/bash
IFS=$'\n'
for entry in $(cat /etc/passwd)
do
echo "Values in $entry –"
IFS=:
for value in $entry
do
echo " $value"
done
done

There are two loops in this script. The first is traversed through the lines, using a line feed as a separator. The inner one is busy parsing strings whose fields are separated by colons.



CYCLE CONTROL:
Perhaps, after entering the loop, it will be necessary to stop it when the loop variable reaches a certain value, which does not correspond to the initially specified condition for the end of the loop.

In such cases, the following two commands come in handy:

1)break
2)continue

COMAND BREAK:
This command allows you to interrupt the execution of the loop. It can be used for both for loops and while loops:

Working example in the program:
#!/bin/bash
for var1 in 1 2 3 4 5 6 7 8 9 10
do
if [ $var1 -eq 5 ]
then
break
fi
echo "Number: $var1"
done

Such a loop, under normal conditions, will go through the entire list of values ​​from the list. However, in our case, its execution will be interrupted when the variable $ var1 equals 5.

COMAND CONTINUE:
When this command is encountered in the body of the loop, the current iteration ends early and the next one starts, and the loop does not exit.

Working example in the program:
#!/bin/bash
for (( var1 = 1; var1 < 15; var1++ ))
do
if [ $var1 -gt 5 ] && [ $var1 -lt 10 ]
then
continue
fi
echo "Iteration number: $var1"
done

When the condition inside the loop is met, that is, when $var1 is greater than 5 and less than 10, the shell will execute the continue command. This leads to the skipping of the remaining commands in the body of the loop and proceeding to the next iteration.




DONE:
The data output from the loop can be processed either by redirecting the output or by piping it. This is done by adding output processing commands after the done statement.

Working example in the program.
#!/bin/bash
for (( a = 1; a < 10; a++ ))
do
echo "Number is $a"
done > myfile.txt
echo "finished."

The shell will create a file called myfile.txt and redirect the output of the for construct to that file.
=======
```

