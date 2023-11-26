![[Pasted image 20230831110258.png | 800x250]]




## Question 4 !!!!! (You get a chocolate \[any brand\] if you can solve this)

Define an operation called 'axing' where we take a number 'a' and look at the sum of its digits and assign the sum to the number itself. 
We call a number 'fine' if you take less than x operations for it to converge to less than 10.
Find the number of 'fine' numbers from l to r.


```python
l = int(input())
r = int(input())
x = int(input())
count_fine = 0
for i in range(l,r+1):
	n = i
	op = 0
	while(n >= 10):
		sum_dig = 0
		for k in str(n):
			sum_dig += int(k)
		n = sum_dig
	if op < x:
		count_fine += 1

print(count_fine)

```