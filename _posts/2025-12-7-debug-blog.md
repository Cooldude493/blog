Welcome back 



Now, let's get a little professional. Debugging is the act of testing your code to check for any errors that might pop up. In this blog, I'll be going over four blocks of code that I have recently debugged, and walk you through the thought process on how I successfully did so. The first, most important step of debugging is to know what exactly the code is supposed to do. In doing so, you will have an easier time finding out why the code isn't working. Then we would have to find what error is making our code output wrong.

Example 1
```python
text = "Hello, world, my name is"
count = 0


for char in text:
    if char == "":
       count += 1


print(count)
```
Here, the code is supposed to count the number of spaces within the string; however, even though there are 4 spaces within the string "Hello, world, my name is", when the code is run, the output says that there are 0 spaces in the string. In this specific case, where there is no error visible, we would need to use the debug tool in your specific code space to find the logic error, while in this space, it will go line by line to show the operation of the code and the changing of the variables. If we take a look at the variable count and continue to each iteration of the code, the value of count never increases, signifying that there is an error within the for loop, specifically the if statement of char == "": because there is no value within the quotes, the loop doesn't check the string for anything. To fix this part of the code, we would need to put a space within the quotes, making the If statement char == “ ”: correcting the error, making the output correct with 4.

Here is the corrected code in full
```python
print("--------Task 1--------")
print()
print()


text = "Hello, world, my name is"
count = 0


for char in text:
    if char == " ":
       count += 1


print(count)
```

Example 2 
```python
print("give me a number")
n = input()


for num in range(1, n):
    if num % 2 < 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")
```
In this example, the code is supposed to list whether the numbers between 1 and the imputed number are even or odd; however, when we run the code, it gives the user an error, ending the program immediately, giving the coder a type error in the terminal on line 4. This notation gives us the area to look for the error, and heading into the debugger, we see that the data type that we input for n stays as a string, and when we call back to it in the for loop, it stays as a string causing the error when we fix the error by putting the function int() around the input looking something like n = int(input()) another problem arises in that it marks every value between 1 and the given number as odd wheel looking back at the for loop, specifically the if statement that controls the floor division the section if num % 2 < 0: doesnt equate anything as every value that is divided by 2 will be greater than 0 so every value will be considered odd. To fix this problem, we just need to change the if statement to num % 2 <= 0:


Here is the corrected code in full
```python
print("give me a number")
n = int(input())


for num in range(1, n):
    if num % 2 <= 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")
```
Example 3 
```python
num = int(input("Enter an integer: "))


if num < -1:
  print("No negative numbers.")
else:
  result = 1
  for i in range(1, num):
    result *= i  


  print("Factorial of " + num + "is" + result)
```

This code snippet is supposed to calculate the factorial of the imputed number, but when the code is run, there is another Type error within the terminal on line 11, narrowing our search for the error to the last print statement, and once again going into debug mode, we can see that when trying to add both the variables num and result to the string they dont get formatted correctly. To fix this issue, we would need to put the for format function in front of the quotes in the string and put both variables in these {} brackets. Looking something like this:

print(f"Factorial of {num} is {result}")

However, still, when we try to find the factorial of a number, for example, 5, the output value isn't 120, it's only 24. When looking at the code in debugger mode and examining the for loop, we see that when the loop reaches the value of 5, it just stops running and prints the output, so we would have to change the range to be range(1, num):.

Here is the corrected code in full
```python
num = int(input("Enter an integer: "))


if num < -1:
  print("No negative numbers.")
else:
  result = 1
  for i in range(1, num + 1):
    result *= i  


  print(f"Factorial of {num} is {result}")
```

Example 4 
```python
attempts = 0
correct_password = "secret"


while True:
    password = input("Enter your password: ")
    attempts += 1


    if password == "incorrect_password":
        print("Correct password!")
    else:
        print("Incorrect password")


    if attempts > 3:
        print("Too many attempts")
        break
```

Our final example is this password-guessing game that requires the user to guess the given password within 3 attempts. However, our first problem arises when the user attempts to guess the password and gets past 3 attempts; the code doesn't stop running and only stops after the 4th attempt. That being said, even if the user guesses the right password, the code doesn't stop running till all attempts are used, and lastly, the code never recognises the correct password of “secret” as the correct answer. To fix the 4 attempt problem, we would need to change the last if statement to set attempts == 3 so that once 3 attempts are made, the code automatically shuts down. Similarly, to fix the password not working properly, we would need to change the variable in the first if statement to be “correct_password” instead of “incorrect_password”. Our final problem of having to use all the attempts given can simply be fixed by placing a break after the print statement of (“Correct password”).
Here is the corrected code in full
```python
attempts = 0
correct_password = "secret"


while True:
    password = input("Enter your password: ")
    attempts += 1


    if password == correct_password:
        print("Correct password!")
        break
    else:
        print("Incorrect password")


    if attempts == 3:
        print("Too many attempts")
        break
```