
P2  
## Outline   

 - Review of Linear Algebra    
    - Vector and Matrix   
    - Translation, Rotation, and Transformation   

 - Representations of 3D rotation   
    - Rotation matrices   
    - Euler angles   
    - Rotation vectors/Axis angles   
    - Quaternions   

P3

## Review of Linear Algebra    

#### Vectors and Matrices   

* a few slides were modified from GAMES-101 and GAMES-103   


P26   

## How to find the rotation between vectors?   


![](/assets/02-01.png)  


P27   

Any vector in the bisecting plane can be the axis


P28   

The minimum rotation:    
$$
𝒖 =\frac{𝒂 × 𝒃}{||𝒂 × 𝒃||}  \quad \quad  \theta = \mathrm{arg} \cos \frac{a\cdot b}{||a||||b||} 
$$

![](/assets/02-02.png)  


P33   
## How to rotate a vectors?

![](/assets/02-3.png)  



$$
𝒗 \gets  𝒖 \times  𝒂
$$

$$
𝒕 \gets 𝒖 \times 𝒗 = 𝒖 \times( 𝒖 \times 𝒂)
$$

![](/assets/02-04.png)  


P35   
## How to rotate a vectors?

![](/assets/02-05.png)  






$$
𝒗 = (\sin \theta) 𝒖 \times  𝒂
$$

$$
𝒕 =(1-\cos \theta ) 𝒖 \times( 𝒖 \times 𝒂)
$$


Rodrigues' rotation formula    

$$
𝒃 = 𝒂 + (\sin \theta) 𝒖 × 𝒂 + (1-\cos \theta ) 𝒖 \times( 𝒖 \times 𝒂)
$$

P53   

## Matrix Form of Cross Product



$$
\begin{align*}
 c=a\times b= & \begin{bmatrix}
a_yb_z-a_zb_y \\\\
a_zb_x-a_xb_z \\\\
a_xb_y-a_yb_x
\end{bmatrix}\\\\
 = & \begin{bmatrix}
  0 & -a_z & a_y \\\\
  a_z & 0 & -a_x \\\\
  -a_y & a_x & 0
\end{bmatrix}\begin{bmatrix}
 b_x \\\\
b_y  \\\\
b_z
\end{bmatrix}=[a]_\times b
\end{align*}
$$

$$
\quad 
$$


$$ 
[a]_\times +[a]^ \mathbf{T} _\times =0 \quad \quad \mathrm{skewsymmetric} 
$$ 


P56  
## Matrix Form of Cross Product




$$
\begin{align*}
a \times b = &[a] _ \times b  \\\\
 a \times (b \times c) = & [a] _ \times ( [b] _ \times c ) \\\\
        =  & [a] _ \times [b] _ \times c  \\\\
 a \times (a \times c) = & [a] ^2 _ \times  b \\\\
 (a \times b) \times c = & [a\times b] _ \times  c \\\\
\end{align*}
$$

P57   
## How to rotate a vectors?   

![](/assets/02-06.png)  


$$
\begin{align*}
v = &(\sin \theta )u\times a  \\\\
 t = & (1-\cos \theta)u \times (u\times a) 
\end{align*}
$$

$$
\begin{align*}
b = & a+(\sin \theta )u \times a +(1-\cos \theta)u \times(u \times a) \\\\
 b = & (I+(\sin \theta ))[u]_ \times + (1-(\cos \theta )[u]^2_ \times ) a \\\\
 = & Ra
\end{align*}
$$



P58
## How to rotate a vectors?

Rodrigues' rotation formula

$$
R = I+(\sin \theta )[u]_ \times + (1-\cos \theta )[u]^2_ \times
$$

P63   
## Determinant of a Matrix   


 - det \\(I = 1\\)     
 - det \\(AB = \text{ det } A ∗ \text{det } B\\)    
 - det \\(A^T\\) = det \\(A\\)   
 - If \\(A\\) is invertible，det \\(A^{−1}\\) = \\((\text{det } A)^{−1}\\)   
 - If \\(U\\) is orthogonal，\\(\text{det } U = ± 1\\)   


P64   
## Cross Product as a Determinant

$$
\begin{align*}
 c=a\times b= & \begin{bmatrix}
a_yb_z-a_zb_y \\\\
a_zb_x-a_xb_z \\\\
a_xb_y-a_yb_x
\end{bmatrix}\\\\
 = & \text{det } \begin{bmatrix}
  i & j & k \\\\
  a_x & a_y & a_z \\\\
  b_x & b_y & b_z
\end{bmatrix}
\end{align*}
$$

P66   
## Eigenvalues and Eigenvectors  

For a matrix \\(A\\), if a **nonzero** vector \\(x\\) satisfies    
$$
Ax=\lambda x
$$

Then:   
\\(\lambda\\): an eigenvalue of \\(A\\)    
\\(x\\): an eigenvector of \\(A\\)   

Especially, a \\(3\times 3\\) **orthogonal** matrix \\(U\\)    
has at least one real eigenvalue: \\(\lambda=\text{det } U = ±1\\)   


P67   

## Rigid Transformation   

Translation, rotation, and coordinate transformation 


P68   

## Rigid Transformation: Translation + Rotation

![](/assets/02-07.png)  


P69  
## Scaling   

![](/assets/02-08.png)  

P70   

## Translation   

![](/assets/02-9.png)    



P72   
## Rotation   

![](/assets/02-10.png)    

P73   
## Rotation Matrix    

 - Rotation matrix is orthogonal:   

 $$
 R^{-1}=R^{T}  \quad R^TR=RR^T=1
 $$

 - Determinant of \\(R\\)    
 $$
 \text{det } R = + 1
 $$
 - Rotation maintains length of vectors
 $$
 ||Rx|| = ||x||
 $$


P75   
## Combination of Rotations   

![](/assets/02-11.png)    


P76   
## Rotation around Coordinate Axes

![](/assets/02-12.png)    

$$
R_x(\alpha )=\begin{pmatrix}
 1 & 0 & 0 \\\\
 0 & \cos\alpha  & -\sin \alpha \\\\
 0 & \sin \alpha  & \cos \alpha 
\end{pmatrix}
$$

$$
R_y(\beta )=\begin{pmatrix}
 \cos \beta & 0 & \sin \beta \\\\
 0 & 1  & 0  \\\\
 -\sin \beta & 0   & \cos \beta 
\end{pmatrix}
$$

$$
R_z(\gamma  )=\begin{pmatrix}
 \cos \gamma & -\sin \gamma & 0 \\\\
 \sin \gamma & \cos \gamma  & 0  \\\\
 0 & 0   & 1 
\end{pmatrix}
$$


P79   

## Rotation Axis and Angle   

Rotation matrix \\(R\\) has a real eigenvalue: +1   
$$
Ru=u
$$


In other words, \\(R\\) can be considered as a rotation around axis \\(u\\) by some angle \\(\theta \\)   
How to find axis 𝒖 and angle \\(\theta \\)?   

![](/assets/02-13.png)    

P80   

## Rotation Axis and Angle   

![](/assets/02-14.png)    


P81  

![](/assets/02-015.png)   


P82  

$$
u\gets {u}' =\begin{bmatrix}
r_{32}-r_{23}  \\\\
r_{13}-r_{31}  \\\\
r_{21}-r_{12} 
\end{bmatrix}
$$

$$
\text{When }  R\ne R^T \Leftrightarrow \sin \theta \ne 0\Leftrightarrow \theta \ne 0^{\circ} 
\text{ or }  180^{\circ} 
$$






![](/assets/01-45.png)  

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/