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
```