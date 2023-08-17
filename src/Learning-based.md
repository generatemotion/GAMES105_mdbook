# Lecture 06

P2   
## Outline   

 - Recap: interactive character animation   
     - Motion Graphs   
     - Motion Matching    
 - Statistical Models of Human Motion   
     - Principal Component Analysis   
     - Gaussian Models   
 - Learning-based Models   
     - ……   


P3   
## Recap: Interactive Animation    

How to make a character respond to user command?

P6   
## Motion Graphs

![](/assets/06-01.png)   


P9   
## Motion Graphs

![](/assets/06-02.png)   


P14   
## Need a Faster Response?


|||
|---|---|
| Motion Graphs / State Machines | Motion Fields / Motion Matching |
| ![](/assets/06-03.png) | ![](/assets/06-04.png)   |



P17  

## Motion Fields

![](/assets/06-05.png)   


P20   

## Motion Fields

![](/assets/06-06.png)   


P23   
## Motion Fields

![](/assets/06-07.png)   

![](/assets/06-08.png)   


P24  
## Motion Fields


![](/assets/06-09.png)   

P31   
## Motion Matching


![](/assets/06-10.png)   


P34   
## Motion Matching   

 - We need a distance function / metric to define the nearest neighbor  


$$
\text{next-pose } = \min_{i \in\text{ Dataset}} ||x_{\text{curr}}-x_i||
$$


$$
x: \text{feature vector}
$$

A possible set of feature vectors:  

 - root linear/angular velocity   
 - position of end effectors w.r.t. root joint   
 - linear/angular velocity of end effectors w.r.t. root joint   
 - future heading position/orientation (e.g. in 0.5s, 1.0s, 1.5s, etc.)   
 - foot contacts   
 - ……   



P36   
## Motion Matching   

 - We need a smooth motion   
    - Only do the search every few frames   
    - Smoothly blend current pose to the target pose   
      - Inertialized blending (ref. <https://www.theorangeduck.com/page/spring-roll-call> by Daniel Holden)   

 - We need a good performance   
    - An efficient data structure for searching   
      - e.g. KD-tree   


![](/assets/06-11.png)   


P39   
## Statistical Models of Human Motion   


P43   
## The Low-dimensionality of Human Motions   


 - Coordinated arm/leg movement   
 - Musculoskeletal structure   
 - Laws of physics    
 - ……   


P45   
## Principal Component Analysis (PCA)   

 - A technique for   
    - finding out the correlations among dimensions   
    - dimensionality reduction   
 

P65   

a pose \\(x\\) with smaller \\(\sum _k\frac{((x-\bar{x})\cdot u_k)^2 }{\sigma ^2_k}\\) is more likely to be a good pose   


![](/assets/06-12.png)   



P66  
## Character IK   

$$
F(\theta )=\frac{1}{2} \sum_{i}^{} ||f_i(\theta )-\tilde{x} _i||^2_2+\frac{\lambda }{2}||\theta ||^2_2 
$$

$$
\theta=(t_0,R_0,R_1,R_2\dots  \dots )
$$



P68  
## Character IK with a Motion Prior

$$
F(\theta )=\frac{1}{2} \sum_{i}^{} ||f_i(\theta )-\tilde{x} _i||^2_2
$$

$$
+\frac{w }{2}\sum_{k}^{}(\frac{(\theta -\bar{\theta })\cdot u_k }{\sigma _k} )^2
$$


P71  
## Data Distribution   

\\(p(x)\\) : probability that \\(x\\) is a natural pose    


P75   
## Gaussian Distribution

![](/assets/06-19.png)   


P76   
## PCA and Gaussian Distribution   

$$
\sum =X^TX=U\begin{bmatrix}
 \sigma ^2_1 &  &  & \\\\
  & \sigma ^2_2 &  & \\\\
  &  & \ddots  & \\\\
  &  &  &\sigma ^2_N
\end{bmatrix}U^T
$$

$$
x-\bar{x} =\sum_{k=1}^{n} w_ku_k
$$



P77   
## PCA and Gaussian Distribution


![](/assets/06-13.png)   

P78   
## Character IK with a Motion Prior   

$$
F(\theta )=\frac{1}{2} \sum_{i}^{} ||f_i(\theta )-\tilde{x} _i||^2_2
$$

$$
+\frac{w }{2}\sum_{k}^{}(\frac{(\theta -\bar{\theta })\cdot u_k }{\sigma _k} )^2
$$


P79  

$$
F(\theta )=\frac{1}{2} \sum_{i}^{} ||f_i(\theta )-\tilde{x} _i||^2_2
$$

$$
-w \log \prod_{k}^{}e^{-\frac{1}{2}(\frac{(\theta -\bar{\theta })\cdot u_k }{\sigma _k} )^2 }  
$$



P80  

$$
F(\theta )=\frac{1}{2} \sum_{i}^{} ||f_i(\theta )-\tilde{x} _i||^2_2
$$

$$
-w \log p(\theta )  
$$

$$
\theta=(t_0,R_0,R_1,R_2\dots \dots )
$$


P81   
## Motion Synthesis with a Motion Prior  


Given a motion prior \\(p(x)\\) learned from a set of data points \\(D \\)= {\\(x_i\\)}, Synthesize a motion \\(x\\) that minimize the objective   

$$
f(x)=f(x)-w \log p(x )
$$

Note: \\(x\\) can represent a pose \\(\theta\\)   
or a motion clip → a sequence of poses {\\( \theta t\\)}     
or any features of a motion → e.g. \\(w_k\\) in PCA    



P82   
## Motion Synthesis with a Motion Prior

Given a motion prior \\(p(x)\\) learned from a set of data points \\(D \\)= {\\(x_i\\)}, Synthesize a motion \\(x\\) that minimize the objective   

$$
f(x)=f(x)-w \log p(x )
$$

![](/assets/06-20.png)   


P83   
## Motion Synthesis with a Motion Prior

![](/assets/06-14.png)   


P83   

## Gaussian Distribution is not Enough!   


P86  

![](/assets/06-15.png)   


P87  
Min et al. 2009

P88  

![](/assets/06-16.png)   


P90   

## Gaussian Distribution is not Enough!   

\\(p(x)\\): motion prior   

![](/assets/06-17.png)   


![](/assets/06-22.png)   

[Starke et al 2020, Local Motion Phases for Learning Multi￾Contact Character Movements]


![](/assets/06-23.png)   

[Henter et al. 2020, MoGlow: Probabilistic and Controllable 
Motion Synthesis Using Normalising Flows]

![](/assets/06-24.png)   


[Lee et al 2019, Interactive Character Animation by 
Learning Multi-Objective Control]


![](/assets/06-25.png)   

[Holden et al 2020, Learned Motion Matching]





---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/