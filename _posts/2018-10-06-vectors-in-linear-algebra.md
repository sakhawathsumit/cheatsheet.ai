---
layout: post
comments: false
title: "Vectors in Linear Algebra"
date: 2018-04-08 00:15:06
tags: vector linear-algebra math review
---

>    Topic covered in this cheat sheet are - Vector operations, Modulus/ Length/ Magnitute/ Norm (L2-Norm), Dot Product, Angle and Projection with Source Code in Julia Language.


<!--more-->

{: cla$ss="table-of-content"}
* TOC
{:toc}


### Vector Addition
$$\vec{r} = [r_i, r_j], \vec{s} = [s_i, s_j]$$ <br>
$$\vec{r} + \vec{s} = [r_i + s_i, r_j + s_j]$$
#### Property
- Associative - $$\vec{r} + \vec{s} = \vec{s} + \vec{r}$$


```julia
r = [1, 2]
s = [1, 2]
print(r + s)
```

    [2, 4]

### Vector Subtraction
$$\vec{r} - \vec{s} = [r_i - s_i, r_j - s_j]$$


```julia
print(r - s)
```

    [0, 0]

### Scaler Multiplication
$$a\vec{r} = [a*r_i, a*r_j]$$


```julia
r = [1, 2]
print(2 * r)
print('\n')
print(1/2 * r)
print('\n')
print(-1 * r)
```

    [2, 4]
    [0.5, 1.0]
    [-1, -2]

### Modulus/ Length/ Magnitute/ Norm (L2-Norm) of Vector
$$|\vec{r}| = \sqrt{\vec{r}.\vec{r}} = \sqrt{r_i^2 + r_j^2}$$


```julia
import LinearAlgebra
LinearAlgebra.norm(r)
```




    2.23606797749979



### Dot Product
$$\vec{r}.\vec{s} = \sum_{all \ c}{r_c * s_c} = r_i s_i + r_j s_j$$ <br>
here, c is the components of vector.
#### Properties
- Cummutative - $$\vec{r}.\vec{s} = \vec{s}.\vec{r}$$
- Distributive of addition - $$\vec{r}.(\vec{s} + \vec{t}) = \vec{r}.\vec{s} + \vec{r}.\vec{t}$$
- Associative over scalar mutiplication - $$\vec{r}.(a \vec{s}) = a(\vec{r}.\vec{s})$$


```julia
print(LinearAlgebra.dot(r,s))
```

    5

### Angle Between Two Vectors
![vector angle]({{ '/assets/images/posts/2018-10-06-vectors-in-linear-algebra/vector_angle.png' | relative_url }})
Cosine rule - $$c^2 = a^2 + b^2 - 2ab\cos\theta$$ <br>
$$|r - s|^2 = |r|^2 + |s|^2 - 2|r||s|\cos\theta$$ <br>
$$(\vec{r} - \vec{s}).(\vec{r} - \vec{s}) = \vec{r}.\vec{r} - \vec{s}.\vec{r} - \vec{s}.\vec{r} -\vec{s}.-\vec{s}$$ <br>
$$\quad\quad\quad\quad\quad \  = |\vec{r}|^2 -2\vec{s}.\vec{r} + |\vec{s}|^2$$ <br>
$$\vec{r}.\vec{s} = |\vec{r}||\vec{s}|\cos\theta$$ <br>
$$\theta = \cos^{-1}\dfrac{\vec{r}.\vec{s}}{|\vec{r}||\vec{s}|}$$ <br>

#### Note 

- $$\vec{r}.\vec{s} > 0$$ vectors are in same direction. <br>
- $$\vec{r}.\vec{s} < 0$$ vectors are in oposite direction. <br>
- $$\vec{r}.\vec{s} == 0$$ vectors are perpendicular. <br>


```julia
r = [4, 0]
s = [0, 4]
radian = acos(LinearAlgebra.dot(r, s) / (LinearAlgebra.norm(r) * LinearAlgebra.norm(s)))
print(rad2deg(radian))
```

    90.0

### Projection
