# NVIC Functions

### Enable / Disable 
![[Pasted image 20230808004646.png]]

```
Set bit[0] of NVIC->ISER[0] = 1:
	Enable Interrupt_0
Set bit[1] of NVIC->ISER[0] = 1:
	Enabel Interrupt 1	
.
.
.

Set bit[0] of NVIC->ISER[0] = 1:
	Enable Interrupt 32
```


