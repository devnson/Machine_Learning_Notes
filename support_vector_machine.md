Support Vector Machines (SVM) are again, it is a classification algorithm that decides how to draw a boundary line between two different groups of data, as shown below.

![image](https://user-images.githubusercontent.com/23405520/113813547-bf43b300-978d-11eb-82a4-922b98a7ecaa.png)

The above task seems simple enough for humans because we can sort of see with our eyes what line seems best, but for computers, they can only read 1’s and 0’s. What Support Vector Machines do is represent this line mathematically so that computers can find this line. But how, you may ask?! Well, before we go there, we need to do a bit of brushing up on some basic linear algebra.

## Linear Algebra Representation of Lines

Do you guys remember what matrices are? Well, if you don’t, no need to worry!

A matrix is simply an array or table of numbers, as shown below.


![image](https://user-images.githubusercontent.com/23405520/113813606-d5517380-978d-11eb-9578-725e0dab181f.png)


In the above case the matrix has 4 rows and 4 columns, but they can have any number of rows and columns. All they really do is hold a bunch of numbers.

Whenever we have a matrix with 1 column, we call it a column vector, and whenever we have a matrix with 1 row, we call it a row vector.


![image](https://user-images.githubusercontent.com/23405520/113813632-e1d5cc00-978d-11eb-8818-9cd9bfe3aac9.png)

Whenever we multiply two matrices, such as those depicted in the image, below you take the first row, and first column. Multiply corresponding elements and add them to get the element that goes in both the first row and first column of the resultant matrix. You repeat the procedure for every row and column combination until the resultant matrix is complete. In the image below, we can set that by doing the operation 3 * 1 + 4 * 3 , we get 15 in the 1st row and 1 column position. Similarly for the first row, second column position, we do 3 * 5 + 4 * 7 which resultants in 43 in the first row, second column position. We do the same procedure over for the second row until we get our finalized matrix.

![image](https://user-images.githubusercontent.com/23405520/113813765-22354a00-978e-11eb-9f12-35aa78176b35.png)

Considering all this, you may wonder how matrices tie into the so-called “Linear Algebra Representation of Lines”. Well, normally in algebra, we denote a line in the following form `Ax + By +C = 0` when looking in the x-y plane (some of you may have learned it as y = mx+b, but in reality, they are the same thing)

![image](https://user-images.githubusercontent.com/23405520/113813819-3da05500-978e-11eb-9d4c-3ce97c747537.png)

Now, we can generalize this formulation of a line in higher dimensions, like 3 dimensions or even 4 dimensions, by continuing to add terms. If you don’t understand what I mean, look at the equation of a “line” in 3-Dimensions `Ax+By+Cz + D = 0`. It’s very similar to the equation of 2-D line but with one more `Cz` term. In fact, this is a plane.


![image](https://user-images.githubusercontent.com/23405520/113813883-590b6000-978e-11eb-8aa9-96f646b824d4.png)


![image](https://user-images.githubusercontent.com/23405520/113813966-80fac380-978e-11eb-8a15-e62fbfa69650.png)

![image](https://user-images.githubusercontent.com/23405520/113813988-8c4def00-978e-11eb-92cc-9f595e671cd4.png)

![image](https://user-images.githubusercontent.com/23405520/113814010-97088400-978e-11eb-862c-8e84c1b12e4f.png)

### Finally, how does the SVM algorithm work?!

Consider the data set below (for simplicity’s sake it is in 2-Dimensions) and an SVM wants to divide the red dots and the green dots.

![image](https://user-images.githubusercontent.com/23405520/113814038-a5ef3680-978e-11eb-8649-cc7d4db00d13.png)

![image](https://user-images.githubusercontent.com/23405520/113814080-ba333380-978e-11eb-9afe-28905444ffb9.png)

![image](https://user-images.githubusercontent.com/23405520/113814122-cd460380-978e-11eb-9456-efcdcd9b113c.png)

![image](https://user-images.githubusercontent.com/23405520/113814144-d59e3e80-978e-11eb-8905-7fb702ed8e90.png)

![image](https://user-images.githubusercontent.com/23405520/113814179-e353c400-978e-11eb-9d6f-019d36f8b290.png)

![image](https://user-images.githubusercontent.com/23405520/113814231-f070b300-978e-11eb-9f25-c0b9f6790f38.png)

![image](https://user-images.githubusercontent.com/23405520/113814263-fc5c7500-978e-11eb-894f-1ae3b345b9e3.png)

![image](https://user-images.githubusercontent.com/23405520/113814291-08e0cd80-978f-11eb-8aa1-5820bde991d0.png)

![image](https://user-images.githubusercontent.com/23405520/113814326-18601680-978f-11eb-8f46-78f86fe46755.png)

![image](https://user-images.githubusercontent.com/23405520/113814367-257d0580-978f-11eb-9481-551cd1227950.png)
![image](https://user-images.githubusercontent.com/23405520/113814385-30d03100-978f-11eb-91dc-8c646b784927.png)
![image](https://user-images.githubusercontent.com/23405520/113814405-3cbbf300-978f-11eb-90f2-d166bffb9fbe.png)

![image](https://user-images.githubusercontent.com/23405520/113814436-47768800-978f-11eb-9970-30227e406e0c.png)

![image](https://user-images.githubusercontent.com/23405520/113814464-52c9b380-978f-11eb-9d41-f1a76267ba43.png)

![image](https://user-images.githubusercontent.com/23405520/113814486-5d844880-978f-11eb-988c-091e5bc022b9.png)
![image](https://user-images.githubusercontent.com/23405520/113814512-67a64700-978f-11eb-85f8-41ea119d4545.png)
![image](https://user-images.githubusercontent.com/23405520/113814553-768cf980-978f-11eb-9467-a60f218d354d.png)
![image](https://user-images.githubusercontent.com/23405520/113814583-80aef800-978f-11eb-8974-a878fb080b01.png)








