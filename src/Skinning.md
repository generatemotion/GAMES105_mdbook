# Lecture 07


P2   
## Outline   

 - Skinning   
    - Linear Blend Skinning (LBS)   
    - Dual Quaternion Skinning (DQS)   
    - Blendshapes   

 - Examples:   
    - The SMPL model  
    - Facial Animation  

Many images are from: <https://skinning.org/>   
*Alec Jacobson, Zhigang Deng, Ladislav Kavan, and J. P. Lewis. 2014*.   
**Skinning: real-time shape deformation**.     
*In ACM SIGGRAPH 2014 Courses (SIGGRAPH '14)*    



P7  
## Skinning Deformation   


![](/assets/07-01.png)   

![](/assets/07-02.png)   


P12   
## Skinning Deformation    

![](/assets/07-03.png)   


P13   
## Skinning Deformation

![](/assets/07-04.png) 

P15   
## Bind Pose

![](/assets/07-05.png)   


P16   
## Bind Pose


![](/assets/07-06.png)   


P18   
## Skinning Deformation

![](/assets/07-07.png)   


P20   
## Skinning Deformation

![](/assets/07-08.png)   

$$
r_2=Q^T_2(x-o_2)   \quad \quad  r_1=Q^T_1(x-o_1)
$$


P23   
## Skinning Deformation   

![](/assets/07-09.png)   

P29   
## Skinning

![](/assets/07-10.png)   


P31   
## Linear Blend Skinning (LBS)

$$
{x}'_ i= \sum_ {j=1} ^ {m} w _ {ij}({Q}'_ jr_{ij}+{o}'_j)
$$

 - Used widely in industry   
 - Efficient and GPU-friendly  
    - Games like it   


P33  
## Automatic Skinning?

![](/assets/07-11.png)   

![](/assets/07-12.png)   

P37   
## Linear Blend Skinning (LBS)

![](/assets/07-13.png)   


P39   
## Candy-Wrapper Artifact

![](/assets/07-14.png)   



P40  
## Advanced Skinning Methods   


 - Multi-linear Skinning (we will not cover this)   
    - Multi-weight enveloping [Wang and Phillips 2002]   
    - Animation Space [Merry et al. 2006]   
    - ……   

 - Nonlinear Skinning   
    - Dual-quaternion Skinning (DQS)   

![](/assets/07-15.png)   


P41   
## Non-linear Skinning

![](/assets/07-16.png)   

Can we use quaternions and SLERP?    

P42  
## Non-linear Skinning

![](/assets/07-16-1.png)   


P43  
## Non-linear Skinning   

$$
{x}' _i=(\sum_{j=1}^{m}w_{ij}R_j)x_i+ \sum_{j=1}^{m}w_{ij}t_j
$$

$$
R \in SO(3)
$$

$$
T_j=\begin{bmatrix}
 R_j & t_j\\\\
 0 &1
\end{bmatrix} \in SE(3)
$$


P46  
## Interpolation in 𝑆𝑂(3)

![](/assets/07-17.png)   



P49  
## Interpolation in 𝑆𝐸(3)

![](/assets/07-18.png)   


P51  
## Intrinsic Blending

![](/assets/07-19.png)   


P52   
## Dual-Quaternion Skinning (DQS)

Ladislav Kavan, Steven Collins, Jiri Zara, Carol O‘Sullivan. **Geometric Skinning with**    
**Approximate Dual Quaternion Blending**, ACM Transaction on Graphics, 27(4), 2008.   



P54   
## Dual Numbers  

![](/assets/07-20.png)   


P55  
## Dual Quaternion   

 - Dual quaternion   

$$
\hat{q} =q_0 + \varepsilon q_\varepsilon
$$

$$
\text{where } \varepsilon^2=0
$$

A good note of dual-quaternion:   
<https://faculty.sites.iastate.edu/jia/files/inline-files/dual-quaternion.pdf>   


P56   
## Dual Quaternion   

 - Scalar Multiplication   

$$
s\hat{q}=sq_r+sq_\varepsilon\varepsilon
$$

 - Addition   

$$
\hat{q} _ 1 + \hat{q} _2=q _ {r1}+ q _ {r2} + \varepsilon (q _ {\varepsilon 1} + q _ {\varepsilon 2})
$$

 - Multiplication  

$$
\hat{q} _ 1 \hat{q} _ 2 = q _ {r1} q _ {r2} + \varepsilon (q _ {r1} q _ {\varepsilon 2} + q _ {r2} q _ {\varepsilon 1})
$$


P57   
## Dual Quaternion  

 - Dual quaternion   

$$
\hat{q}=q_0+\varepsilon q_\varepsilon
$$

 - Conjugation   

$$
\mathrm{I}:\hat{q}^* =q ^ * _ 0+\varepsilon q ^ * _ \varepsilon
$$

$$
\mathrm{II}:\hat{q}^ {\circ}  =q _ 0 + \varepsilon q _ \varepsilon 
$$


$$
\mathrm{III}: \hat{q} ^ \star    = q ^ * _ 0 + \varepsilon q ^ *_ \varepsilon 
$$

$$
\quad \quad \quad \quad = ({\hat{q} ^ *}) ^ {\circ} = (\hat{q} ^ {\circ}) ^ *
$$



$$
(\hat{q} _1\hat{q}_2)^\times =\hat{q} _1 ^\times \hat{q}_2^\times
$$

 - Norm   

$$
||\hat{q}||=\sqrt{\hat{q}^*\hat{q}} =||q_0||+\frac{\varepsilon (q_0\cdot q_\varepsilon) }{||q_0||} 
$$

P58  
## Dual Quaternion

 - Unit dual quaternion: \\(||\hat{q}||=1\\), which requires:   

$$
||q_0||=1
$$

$$
q_0 \cdot q_\varepsilon=0
$$


P59  
## Dual Quaternion ⇔ Rigid Transformation   

 - Like quaternion, any rigid transformation \\(T \in SE(3)\\) can be converted **into a unit dual quaternion**    

$$
Tx=Rx+t
$$

$$
T=[R\mid t]\to \hat{q} =q_0+\varepsilon q_\varepsilon 
$$

$$
\begin{matrix}
 q_0=r \quad & \text{ quaternion of } R \quad \quad\quad\quad\\\\
 q_\varepsilon =\frac{1}{2} tr & \text{ pure quaternion } t = (0,t)
\end{matrix}
$$


P60   
## Dual Quaternion ⇔ Rigid Transformation   


 - Transform a vector \\(v\\) using unit dual quaternion   

$$
{\hat{v} }' =\hat{q} \hat{v} \hat{q} ^\star 
$$

$$
\begin{align*}
 \hat{v} & = 1+\varepsilon (0,v) \\\\
  & =(1,0,0,0)+\varepsilon (0,v_x,v_y,v_z)
\end{align*}
$$

where   

$$
\mathrm{III}: \hat{q} ^ \star    = q ^ * _ 0 - \varepsilon q ^ *_ \varepsilon 
$$

$$
\quad \quad \quad \quad = ({\hat{q} ^ *}) ^ {\circ} = (\hat{q} ^ {\circ}) ^ *
$$


P61   
## Dual Quaternion ⇔ Rigid Transformation

 - Like quaternion, any rigid transformation \\(T \in SE(3)\\) can be converted **into a unit dual quaternion**    

$$
T=[R\mid t]\to \hat{q} =q_0+\varepsilon q_\varepsilon 
$$

$$
\begin{matrix}
 q_0=r \quad \\\\
 q_\varepsilon =\frac{1}{2} tr 
\end{matrix}
$$

\\(\hat{q}\\) and \\(-\hat{q}\\) represent the same transformation
\\(\hat{Q}\\) is a **double cover** of \\(SE(3)\\)   


P62   
## Double Cover Visualized

![](/assets/07-21.png)   


P63   
## Interpolating Dual-Quaternion

![](/assets/07-22.png)   


P65   
## Dual-Quaternion Skinning (DQS)

![](/assets/07-23.png)   


P66   
## Budging Artifact of DQS

![](/assets/07-24.png)   


P67   
## How to Correct LBS?

![](/assets/07-25.png)   


P69   
## How to Correct LBS?

![](/assets/07-26.png)   


P74   
## Scattered Data Interpolation

![](/assets/07-27.png)   


P76   
## Scattered Data Interpolation  


 - Linear   
    - Least squares   
 - Splines   
 - Inverse distance weighting   
 - Gaussian process   
 - Radial Basis Function   
 - ……   

![](/assets/07-27.png)   


P81   
## Radial Basis Function (RBF) Interpolation

$$
y=\sum_{i=1}^{k} w_i\varphi (||x-x_i||)
$$

![](/assets/07-28.png)   


P83   
## Radial Basis Function (RBF) Interpolation

$$
y=\sum_{i=1}^{k} w_i\varphi (||x-x_i||)
$$

How to compute \\(w_i\\) ? We need \\(f(x_i)=y_i\\)  

$$
\begin{bmatrix}  
  R_{1,1} & R_{1,2} & \cdots & R_{1,K} \\\\  
  R_{2,1} & R_{2,2} &   & \vdots \\\\  
  \vdots &   & \ddots & \vdots \\\\  
  R_{K,1} & \cdots & \cdots & R_{K,K}  
\end{bmatrix} \begin{bmatrix}
 w_1\\\\
w_2 \\\\
 \vdots\\\\
w_K
\end{bmatrix}=\begin{bmatrix}
 y_1\\\\
y_2 \\\\
 \vdots\\\\
y_K
\end{bmatrix}
$$

$$
R_{i,j}=\varphi (||x_i-x_j||)
$$

![](/assets/07-29.png)   


P84   
## Radial Basis Function (RBF)

$$
y=\sum_{i=1}^{k} w_i\varphi (||x-x_i||)
$$







![](/assets/07-30.png)   

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/