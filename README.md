# LU Decomposition 

## AIM:
To write a program to find the LU Decomposition of a matrix.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Start
2. Input the coefficient matrix A.
3. Input the constant matrix (right-hand side vector) B.
4. Perform LU factorization of matrix A using lu_factor(A), which returns: A combined matrix containing the factors of L and U. A pivoting array P representing row interchanges.
5.Solve the system of equations AX=B using the LU factors and the pivoting array with lu_solve((L, P), B).
6. Store the result in variable X.
7. Print the solution vector X.
8. End
## Program:
(i) To find the L and U matrix
```
/*
Program to find the L and U matrix.
Developed by: RANJITH R
RegisterNumber: 212224240131
*/
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
from scipy.linalg import lu
A = np.array(eval(input()))
P,L,U=lu(A)
print(L)
print(U)
```
(ii) To find the LU Decomposition of a matrix
```
/*
Program to find the LU Decomposition of a matrix.
Developed by: RANJITH R
RegisterNumber: 212224240131
*/
A = eval(input())
B = eval(input())

n = len(A)

L = [[0.0]*n for _ in range(n)]
U = [[0.0]*n for _ in range(n)]

for i in range(n):
    L[i][i] = 1.0

for i in range(n):
    for j in range(i, n):
        s = 0
        for k in range(i):
            s += L[i][k] * U[k][j]
        U[i][j] = A[i][j] - s

    for j in range(i+1, n):
        s = 0
        for k in range(i):
            s += L[j][k] * U[k][i]
        L[j][i] = (A[j][i] - s) / U[i][i]

Y = [0]*n
for i in range(n):
    s = 0
    for j in range(i):
        s += L[i][j] * Y[j]
    Y[i] = B[i] - s

X = [0]*n
for i in range(n-1, -1, -1):
    s = 0
    for j in range(i+1, n):
        s += U[i][j] * X[j]
    X[i] = (Y[i] - s) / U[i][i]

X = [round(i,3) for i in X]

print("[ {:.3f}  {:.3f} {:.3f}]".format(X[0], X[1], X[2]))
```

## Output:
<img width="995" height="966" alt="image" src="https://github.com/user-attachments/assets/19c3a7d4-849d-4f33-931b-5dfb706735fa" />

<img width="983" height="1002" alt="image" src="https://github.com/user-attachments/assets/484535d1-cebd-47b3-a850-f9f47dd07f61" />


## Result:
Thus the program to find the LU Decomposition of a matrix is written and verified using python programming.
