# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Read the number of unknowns n and the augmented matrix entries from user input.
2. Reshape the input into an n\times (n+1) augmented matrix A.
3. For each pivot row i, eliminate entries below the pivot by subtracting a factor times the pivot row.
4. Initialize solution vector x with zeros.
5.Perform back substitution: compute each variable from the last row upwards using the formula in the code.
6.Print the solution values of all variables in formatted output.


## Program:
~~~
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: G chaithanya
RegisterNumber: 212225230087
*/
~~~
~~~
import os 
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def solve_gaussian(data):
    n=int(data[0])
    A=np.array(data[1:],dtype=float).reshape(n,n+1)
    for i in range(n):
        for j in range(i+1,n):
            factor=A[j,i]/A[i,i]
            A[j]-=factor*A[i]
    x=np.zeros(n)
    for i in range(n-1,-1,-1):
        x[i]=(A[i,-1]-np.dot(A[i,i+1:n],x[i+1:n]))/A[i,i]
    return x
data=[]
for i in range(13):
    data.append(input())
result=solve_gaussian(data)
print("".join([f"X{i} = {val:.2f} " for i,val in enumerate(result)]))
~~~

## Output:
<img width="753" height="494" alt="{DACF2D9E-2955-4AE9-8A89-1C16C75F88C1}" src="https://github.com/user-attachments/assets/86c33f03-bbda-420b-a04f-1133d38804b8" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

