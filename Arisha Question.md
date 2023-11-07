# Python Loops
# Time : 1 Hour


## <u>Question 1</u>

Find the sum of the following series : 
(You must use a while loop to solve the problem)
## sum =  $1^2 + 2^2 + 3^2 + ..... + n^2$

take **n** as a input from the user. 
### Example

#### Input
3

#### Output
Sum = 14


## <u>Question 2</u>

Print the digits of a number (given as input) in the reverse order. 
Take the number as input from the user.

(You're not allowed to use strings or lists)


### <u>Example 1</u>

#### Input
7876

### Output
6, 7, 8, 7
### <u>Example 2</u>

#### Input
75319
### Output
9, 1, 3, 5, 7

## <u>Question 3</u>

Take two numbers, 'n1' and 'n2' as input from the user.  (n1 < n2). 
Print all the numbers from n1 up to n2 (inclusive) where the number is divisible by 3 or 4 but not both.

For example the number 9 is divisible by 3 but not divisible by 4. So this will be printed
but 12 is divisible by both 3 AND 4. So 12 will not be printed

### Example

#### Input
4
15

#### Output
4 6 8 9 15


### Explanation : 
Here 4 and 8 are divisible by only 4 and not 3
6, 9 and 15 are divisible by only 3 and not 4

We did not print 12 because it is divisible by both 4 and 3


## Question 4 !!!!! (You get a chocolate \[any brand\] if you can solve this)

Define an operation called 'axing' where we take a number 'a' and look at the sum of its digits and assign the sum to the number itself. 
We call a number 'fine' if you take less than x operations for it to converge to less than 10.
Find the number of 'fine' numbers from l to r.


```python
l = int(input())
r = int(input())
x = int(input())

for i in range(l,r+1):
	n = i
	op = 0
	while(n >= 10):
		sum_dig = 0
		for k in str(n):
			sum_dig += int(k)
		n = sum_dig
	if op < x:
		print(i,"is a fine number")


```