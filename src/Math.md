
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



P83  
## Rotation Axis and Angle   

![](/assets/02-17.png)    


P85   

## Coordinate Transformation   

![](/assets/02-18.png)    



P86   
## Coordinate Transformation

![](/assets/02-19.png) 


P87   

## Representations of 3D Rotation   

P90  

| degrees of freedom (DoF) = 3 |
|---|


P91   

## Parameterization of Rotation

 - A rotation matrix, 9 parameters: \\(𝑎_{𝑖𝑗}\\)   
 $$
 R=\begin{bmatrix}
 a_{11} & a_{12} & a_{13} \\\\
 a_{21} & a_{22} &a_{23} \\\\
 a_{31} & a_{32} &a_{33}
 \end{bmatrix}
 $$

\\( R^TR=I   \quad \text{det }R=1 \\)  

| degrees of freedom (DoF) = 3 |
|---|


P93  
## Interpolation of Translations


![](/assets/02-20-1.png) 



$$
x_t=(1-t)x_0+tx_1
$$


P95   
##  Interpolation of Rotations    

![](/assets/02-21.png) 

P98   
## Interpolation of Rotations  

 - What is good interpolation?   
    - Rotation is valid at any time \\(t\\)   
    - Constant rotational speed is preferred   


P99   

 - Easy to compose?   \\(\quad \quad \quad {\color{Red} \times } \\)
 - Easy to apply?   \\(\quad \quad \quad \quad {\color{Green}  \surd }\\)
 - Easy to interpolate?  \\(\quad  \quad {\color{Red} \times } \\)


P100  
## Euler angles


 - Basic rotations


![](/assets/02-22.png) 

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


P101  
## [囘] Euler Angles   

 - Any rotation can be represented as a combination of three basic rotations


P102   

## [囘] Euler Axes   


 - Any combination of three basic rotations are allowed   
    - Excluding those rotate twice around the same axis   
    - XYZ, XZY, YZX, YXZ, ZYX, ZXY, XYX, XZX, YXY, YZY, ZXZ, ZYZ    


P103  

## [囘] Conventions of Euler Angles   

intrinsic rotations: axes attached to the **object**

$$
R_x(\alpha )R_y(\beta )R_z(\gamma )
$$

extrinsic rotations: axes fixed to the **world**   


$$
R_z(\gamma )R_y(\beta )R_x(\alpha )
$$

P104   

## [囘] Gimbal Lock    

 - When two local axes are driven into a parallel configuration, 
one degree of freedom is “locked”   

P105  

## [囘] Euler Angles   

![](/assets/02-23.png) 


P107  

## [囬] Rotation Vectors / Axis Angles   


 - Axis angle \\((u,\theta) \\) : represent a rotation using    
    - A vector \\(u\\): rotation axis   
    - A scalar \\(\theta \\): rotation angle   

 - Rotation vector: represent a rotation as
    - \\(\theta =\theta u \\)   
    - Obviously:   
    $$
    \theta=||\theta||  \quad u=\frac{\theta}{||\theta||} 
    $$


![](/assets/02-24.png) 


P110   
## [囬] Interpolating Rotation Vectors / Axis Angles   

![](/assets/02-25.png) 


P111   

## [囬] Interpolating Rotation Vectors / Axis Angles   

Compute offset rotation   

$$
\begin{align*}
 R(\delta \theta )= & R^T(\theta _0)R(\theta _1)\\\\
 \delta \theta _t= & (1-t)0+t\delta \theta \\\\
 R( \theta_t)= & R( \theta _0)R(\delta \theta _t)
\end{align*}
$$

 - \\(\theta _t\\) is valid \\(\quad {\color{Green} \surd } \\)   
 - Constant speed \\({\quad \color{Green} \surd } \\) 

P112  

## [囬] Rotation Vectors / Axis Angles   

$$
(u,\theta) \text{ or } \theta =\theta u
$$

Representation is not unique    

$$
\begin{matrix}
 (u,\theta ), & (-u,-\theta ),  & (u,\theta+2n\pi), 
\end{matrix}
$$


 - Easy to compose?   \\(\quad \quad {\color{Green} \surd } \quad \quad \\)   But hard to manipulate    
 - Easy to apply?   \\(\quad \quad \quad {\color{Red} \times }  \quad \quad \\)     Need to convert to matrix    
 - Easy to interpolate?  \\(\quad \quad {\color{Green} \surd } \quad \quad \\)  Linear interpolation works, but not perfect    
 - No Gimbal lock    \\(\quad \quad {\color{Green} \surd } \quad \quad \\)  need to deal with singularities     
 

P113   

## Quaternions   


P116   
## [𡇌] Quaternions   

 - Extending complex numbers    
 $$
 q =a+bi +cj +dk \in \mathbb{H} ,a,b,c,d\in \mathbb{R}
 $$

 - \\(i^2=j^2=k^2=ijk=-1\\)   
 - \\(ij=k,ji=-k(^*\text{cross product})\\)   
 - \\(jk=i,kj=-i\\)   
 - \\(ki=j,ik=-j\\)   


P117  

## [𡇌] Quaternion Arithmetic

$$
 q =a+bi +cj +dk \in \mathbb{H} ,a,b,c,d\in \mathbb{R}
 $$

Conjugation:   \\(\quad \quad q^*=a-bi-cj-dk\\)   
\\(<br>\\)    
Scalar product:  \\(\quad \quad tq=ta+tbi+tcj+tdk\\)   
\\(<br>\\)  
Addition:  \\(\quad \quad q_1+q_2=(a_1+a_2)+(b_1+b_2)i+(c_1+c_2)j+(d_1+d_2)k\\)   
\\(<br>\\)   
Dot product:  \\(\quad \quad q_1\cdot q_2=a_1a_2+b_1b_2+c_1c_2+d_1d_2\\)   
\\(<br>\\)  
Norm:  \\(\quad \quad ||q||=\sqrt{a^2+b^2+c^2+d^2} =\sqrt{q\cdot q}\\)

P118   

## [𡇌] Quaternion Multiplication   

$$
q_1q_2=(a_1+b_1i+c_1j+d_1k)*(a_2+b_2i+c_2j+d_2k)
$$

$$
q_1q_2=a_1a_2-b_1b_2-c_1c_2-d_1d_2
$$

$$
+(b_1a_2+a_1b_2-d_1c_2+c_1d_2)i   
$$

$$
+(c_1a_2+d_1b_2+a_1c_2-b_1d_2)j  
$$

$$
+(d_1a_2-c_1b_2+b_1c_2+a_1d_2)k
$$


note:   
 - \\(i^2=j^2=k^2=ijk=-1\\)    
 - \\(ij=k,ji=-k (^*\text{cross product})\\)   
 - \\(jk=i,kj=-i\\)   
 - \\(ki=j,ik=-j\\)   

P119   











![](/assets/01-45.png)  

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/