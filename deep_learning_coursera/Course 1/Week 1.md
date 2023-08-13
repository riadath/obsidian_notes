# Binary Classification

$(x,y)$ training set

![[Pasted image 20230813000906.png | 750x400]]



# Logistic Regression


![[Pasted image 20230813003623.png]]

### Output : $\hat{y} = \sigma(\omega^T x + b)$ and $z = \omega^T x + b$

### Sigmoid Function

![[Pasted image 20230813001823.png | 750x300]]


## Loss Function: $L(\hat{y},y)=-(y*log(\hat{y}) + (1-y)*log(1-\hat{y}))$

### <u>Cost Function</u>: $J(w,b) =\frac{1}{m}  \sum_{i=1}^{m} L(\hat{y}^i , y^i) =\frac{1}{m}  \sum_{i=1}^{m} [-(y*log(\hat{y}) + (1-y)*log(1-\hat{y}))]$
