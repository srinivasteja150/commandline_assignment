# Commanad Line Assignment
The above are the codes for the given questions in the assignemnt and the approach for each code is explained below.

## Question - 1
Write a bash script to get the current date, time, username, home directory and current working directory.

### Apporach - 
We have used the following commands to fetch the desired details, each command is as below.
| Command  | Function |
| ------------- | ------------- |
|$(date +"Year: %Y, Month: %m, Day: %d") | Command to fetch the date
|$(date +"%T") | Command to fetch the time
|$(whoami) | Command to fetch the current working user
|$(echo $HOME) | Command to fetch the Home directory
|$(pwd) | Command to fetch the current wokring directory

### Test run - 
<img width="621" alt="Screenshot 2023-02-05 at 2 34 45 PM" src="https://user-images.githubusercontent.com/122455311/216810564-783cb148-520c-443a-b5f7-d3cb68de1127.png">


## Question - 2
Write a bash script (name Table.sh) to print the Table of a number by using a while loop. It should support the following requirements.
  - The script should accept the input from the command line.
  - If you don’t input any data, then display an error message to execute the script correctly.

### Apporach - 

We verify whether any arguments have been passed, and if not, we issue an error and quit the programme with exit status 1. If not, we run a loop to print all the arguments passed, then another while loop on all the arguments, start a counter internally on the second while loop, increment it after each iteration, fetch the result, and repeat this internal loop for each element in the arguments list until the counter value is less than 10, at which point the programme ends.


n=$1 # Intiliaing the first argument as n
c=1 # Counter Variable
echo "Given number - $n"
echo "Table of $n:"
#### Using while loop to generate the table
while [ $c -le 10 ] # while counter is less than 10
do
  result=$(( $n * $c )) # Calculating the product
  echo "$n x $c = $result" # Printing the product
  c=$(( $c + 1 )) # Incrementing the counter
done

exit 0


### Test run - 

##### Scenorio - 1
When no arguments are passed

<img width="507" alt="Screenshot 2023-02-05 at 2 36 58 PM" src="https://user-images.githubusercontent.com/122455311/216810629-5be00528-f8cd-42fa-8cf2-c4a0af97e846.png">


##### Scenorio - 2
When 1 arguments is passed

<img width="615" alt="Screenshot 2023-02-05 at 2 39 38 PM" src="https://user-images.githubusercontent.com/122455311/216810748-7d749068-5c5d-49bb-802c-ec82a7de2953.png">


##### Scenorio - 3
When more than 1 arguments are passed

<img width="651" alt="Screenshot 2023-02-05 at 2 39 58 PM" src="https://user-images.githubusercontent.com/122455311/216810758-f0c2489c-bddc-46ed-a9de-2387c767a578.png">


## Question - 3
Write a Function in bash script to check if the number is prime or not? It should support the following requirement.
          - The script should accept the input from the User.
### Apporach - 

We created a function called `is prime` to determine whether a number is prime or not. If the number is greater than 2, we indicate that it is not a prime, and if not, we run a loop from `2` to `number/2` to see if any of the above numbers divide the given number. If we found any numbers, we can conclude that the number is not a prime because it has a divisor other than 1 and itself.

We receive user input in the main code, store it in a variable, and then call the function while sending the argument as command line arguments.

### Test run - 

<img width="560" alt="Screenshot 2023-02-05 at 2 42 15 PM" src="https://user-images.githubusercontent.com/122455311/216810827-94810510-70df-4d45-b695-4bf0a78750d0.png">


## Question - 4
Create a bash script that supports the following requirement.
  - Create a folder ‘Assignment’.
  - Create a file ‘File1.txt’ inside ‘Assignment’ Folder.
  - Copy all the content of Table.sh(2nd script) in ‘File1.txt’ without using ‘cp’ and ‘mv’ command.
  - Append the text Welcome to Sigmoid’ to the ‘File1.txt’ file.
  - List all the directories and files present inside Desktop Folder.#### Apporach - 

### Approach - 

We have used the following commands to meet the desired requirements and the function of command is as follows.
| Command  | Function |
| ------------- | ------------- |
| mkdir ~/Desktop/Assignment | Creating folder using mkdir |
| touch ~/Desktop/Assignment/File1.txt | Creating file using touch |
| cat ~/Desktop/Table.sh  >> ~/Desktop/Assignment/File1.txt | Copying data in q2 to file1 using cat |
| echo "Welcome to Sigmoid" >> ~/Desktop/Assignment/File1.txt| Appending given text to file1 |
| ls -la ~/Desktop/ | Printing files and folders in Desktop |

#### Test run - 
<img width="615" alt="Screenshot 2023-02-05 at 2 43 41 PM" src="https://user-images.githubusercontent.com/122455311/216810907-a9b8d726-d983-425e-816b-109334709d42.png">


Text in File1.txt

<img width="716" alt="Screenshot 2023-02-05 at 2 45 18 PM" src="https://user-images.githubusercontent.com/122455311/216810955-53b0f776-6684-4b70-9917-9591cb7c3241.png">


Text in Table.sh

<img width="887" alt="Screenshot 2023-02-05 at 2 46 44 PM" src="https://user-images.githubusercontent.com/122455311/216811032-50887f5a-a54e-4852-8126-4ed192838b21.png">


## Question - 5
Create a bash script that supports the following requirement.
  - Create a folder ‘Assignment’.
  - Create a file ‘File1.txt’ inside ‘Assignment’ Folder.
  - Copy all the content of Table.sh(2nd script) in ‘File1.txt’ without using ‘cp’ and ‘mv’ command.
  - Append the text Welcome to Sigmoid’ to the ‘File1.txt’ file.
  - List all the directories and files present inside Desktop Folder.#### Apporach - 

### Approach - 

We have declared the array internally in the code, we have used the following commands to fetch the required result

| Command  | Function |
| ------------- | ------------- |
| echo ${#arr[@]} | Length of the array|

We have made two methods to find the max and min elements in the given array.
### Method - 1
In order to discover the maximum and minimum elements in the given array, we utilised the sort function. For the maximum, we sorted the array in reverse order and used the head1 command to collect the first member.
| Command  | Function |
| ------------- | ------------- |
| IFS=$'\n' | Internal field separator |
| echo "${arr[*]}" \| sort -nr \| head -n1 | Sorting in reverse and fetch the first element |
| echo "${arr[*]}" \| sort -n \| head -n1 | Sorting  and fetch the first element |

### Method - 2

We use a for loop to get the maximum and minimum element. Using the first element as the maximum, we traverse each element in the loop to see whether it is greater than the maximum value we have assumed.


### Max element
```
for n in "${arr[@]}" ; do
    if [ $n -ge $max ]; then 
		max=$n
	fi
done
```

### Min element
```
for n in "${arr[@]}" ; do
    if [ $n -le $min ]; then 
    	min=$n
	fi
done
```
### Test run - 
<img width="519" alt="Screenshot 2023-02-05 at 2 48 10 PM" src="https://user-images.githubusercontent.com/122455311/216811076-2b124353-d511-475e-ba5b-7db58439298b.png">
