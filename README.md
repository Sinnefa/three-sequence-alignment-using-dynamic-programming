# Formulation and Implementation of Three String Alignment Using 3D Dynamic Programming

We want to extend the Needleman Wunsch algorithm  algorithm to three strings. Let <img src="https://latex.codecogs.com/svg.image?A=a_1a_2...a_n" title="A=a_1a_2...a_n" />, <img src="https://latex.codecogs.com/svg.image?B=b_1b_2...b_m" title="B=b_1b_2...b_m" /> and <img src="https://latex.codecogs.com/svg.image?C=c_1c_2...c_l" title="C=c_1c_2...c_l" /> be the strings to be aligned, where n, m and l are A, B ad C lengths. gap is the penalty of opening a gap between two strings. We construct a substitution matrix which contains substitution scores, for example 1 matching -1 non matching. We call this matrix $s$. Tto hold the values for matching and non matching characters as follows (any value can be applied):

<img src="https://latex.codecogs.com/svg.image?s(a_i,b_j)&space;=&space;\begin{cases}&plus;1,&space;\quad&space;a_i=b_j&space;\\&space;-1,&space;\quad&space;a_i\ne&space;b_j\end{cases}" title="s(a_i,b_j) = \begin{cases}+1, \quad a_i=b_j \\ -1, \quad a_i\ne b_j\end{cases}" />

Let's now construct a scoring matrix H with size <img src="https://latex.codecogs.com/svg.image?(n&plus;1)&space;*&space;(m&plus;1)&space;*&space;(l&plus;1)" title="(n+1) * (m+1) * (l+1)" /> and initialize its first row and, column and depth to decreasing numbers to find global alignment as per Needleman–Wunsch). Then, compute the scoring matrix as follows:

<img src="https://latex.codecogs.com/svg.image?H_{i,j,k}&space;=&space;\max\limits_{(1\le&space;i\le&space;n,&space;1\le&space;j\le&space;m,&space;1\le&space;k\le&space;l)}\begin{cases}&space;H_{i-1,j,k}&space;-&space;gap&space;-&space;gap,&space;&space;&space;&&space;\text{up}\\H_{i,j-1,k}&space;-&space;gap&space;-&space;gap,&space;&&space;&space;\text{left}\\H_{i,j,k-1}&space;-&space;gap&space;-&space;gap,&space;&&space;&space;\text{back}\\H_{i-1,j-1,k}&space;&plus;&space;s(a_i,b_j)&space;-&space;gap,&space;&&space;\text{diagonal}\\H_{i-1,j,k-1}&space;&plus;&space;s(a_i,c_k)&space;-&space;gap,&space;&&space;\text{back&space;up}\\H_{i,j-1,k-1}&space;&plus;&space;s(b_j,c_k)&space;-&space;gap,&space;&&space;\text{back&space;left}\\H_{i-1,j-1,k-1}&space;&plus;&space;s(a_i,b_j)&space;&plus;&space;s(b_j,c_k)&space;&plus;&space;s(a_i,c_k),&space;&&space;\text{back&space;diagonal}\end{cases}" title="H_{i,j,k} = \max\limits_{(1\le i\le n, 1\le j\le m, 1\le k\le l)}\begin{cases} H_{i-1,j,k} - gap - gap, & \text{up}\\H_{i,j-1,k} - gap - gap, & \text{left}\\H_{i,j,k-1} - gap - gap, & \text{back}\\H_{i-1,j-1,k} + s(a_i,b_j) - gap, & \text{diagonal}\\H_{i-1,j,k-1} + s(a_i,c_k) - gap, & \text{back up}\\H_{i,j-1,k-1} + s(b_j,c_k) - gap, & \text{back left}\\H_{i-1,j-1,k-1} + s(a_i,b_j) + s(b_j,c_k) + s(a_i,c_k), & \text{back diagonal}\end{cases}" />

**Cells nomenclature**

<p align="center">
<img src="fig1.png" width="400">
 </p>

**Example**

<p align="center">
<img src="fig2.png" width="400">
</p>
