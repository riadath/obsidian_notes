# Binary Classification

$(x,y)$ training set

![[Pasted image 20230813000906.png | 750x400]]



# Logistic Regression


![[Pasted image 20230813003623.png]]

### Output : $\hat{y} = \sigma(z)$ and $z = \omega^T x + b$

### Sigmoid Function

![[Pasted image 20230813001823.png | 750x300]]


## <u>Loss Function</u>: $L(\hat{y},y)=-(y*log(\hat{y}) + (1-y)*log(1-\hat{y}))$

## <u>Cost Function</u>: $J(w,b) =\frac{1}{m}  \sum_{i=1}^{m} L(\hat{y}^i , y^i) =\frac{1}{m}  \sum_{i=1}^{m} [-(y*log(\hat{y}) + (1-y)*log(1-\hat{y}))]$



# Logistic Regression Gradient Descent

![[Pasted image 20230814204205.png|700x300]]


## $dz = \frac{\partial L(a,y)}{\partial z}=a-y$
## $dw_1 = \frac{\partial L}{\partial w_1}=x_1dz$
## $dw_2 = \frac{\partial L}{\partial w_2}=x_2dz$

### <u>Updates</u>
## $w_1 := w_1-\alpha d$