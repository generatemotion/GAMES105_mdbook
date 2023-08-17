# Lecture 06+

P2   
## Outline  

 - Learning-based Character Animation (cont.)   
    - Motion Models   
    - Autoregressive models: PFNN   
    - Generative models   


P4   
## Learning Motion Models  

\\(p(x)\\): probability that 𝒙 is a natural motion     


Given a set of example motions {\\(x_i\\)}∼ \\(p(x)\\)   

P5   
## Learning Motion Models

![](/assets/06a-01.png)   


P6   
## Learning Motion Models   


![](/assets/06a-02.png)  


P7   
## Learning Motion Models


$$
p(X\mid z)=p(x_1,\dots ,x_T\mid z
$$

$$
\begin{align*}
 𝑧: & \text{ control parameters} \\\\
  & \text{ latent variables} \\\\
  & …… 
\end{align*}
$$


P8   

$$
(x_1,\dots ,x_T)=f(z)
$$

$$
\begin{align*}
 𝑧: & \text{ control parameters} \\\\
  & \text{ latent variables} \\\\
  & …… 
\end{align*}
$$


P14   
## Two Perspectives on a Motion Sequence

$$
p(X\mid z)=p(x_1,\dots ,x_T\mid z)
$$

$$
=p(x_1)\prod_{t}^{} p(x_t\mid x_{t-1},\dots ,x_1;z)
$$

*The chain rule of conditional probabilities:   

$$
\begin{align*}
 p(x_1,x_2,x_3) & = p(x_2,x_3 \mid x_1)p(x_1) \\\\
   & = p(x_3 \mid x_2, x_1)p( x_2 \mid x_1)p(x_1)
\end{align*}
$$


P15  

$$
x_t=f(x_{t-1},x_{t-2},\dots x_1;z)
$$


P17   

$$
x_t=f(x_{t-1};z)
$$

Markov Property   


P18   
## Two Perspectives on a Motion Sequence

|||
|---|---|
|![](/assets/06a-03.png) |![](/assets/06a-04.png) |
|![](/assets/06a-05.png) |![](/assets/06a-06.png) |


P25   

## Learning Motion Models

$$
x_t=f(x_{t-1})
$$

![](/assets/06a-07.png)   


P40   
## Ambiguity Issue   

$$
x_t=f(x_{t-1})
$$

![](/assets/06a-08.png)   


P41   
## Hidden Variables

$$
x_t=f(x_{t-1};z)
$$

![](/assets/06a-09.png)    


P42  

## PFNN: Phase-Functioned Neural Networks

![](/assets/06a-10.png)   


P43  
## PFNN: Phase-Functioned Neural Networks


![](/assets/06a-11.png)  


P44  
## PFNN: Phase-Functioned Neural Networks

 
![](/assets/06a-12.png) 

phases of a walking gait cycle   
Pirker and Katzenschlager 2017.    
*Gait disorders in adults and the elderly*   


P45  
## PFNN: Phase-Functioned Neural Networks

$$
x_t=f(x_{t-1};z_t)  \quad \quad z_t=(c_t,\phi _t)
$$

![](/assets/06a-13.png)   


P47    
## Mixture of Experts

![](/assets/06a-14.png)   

$$
y=\sum_{i}^{} w_if(x;\theta _i)
$$


P48  

## Weighted-Blended Mixture of Experts


![](/assets/06a-15.png)   

$$
y=f(x;\sum_{i}^{} w_i\theta _i)
$$


P49   
## PFNN: Phase-Functioned Neural Networks

$$
x_t=f(x_{t-1};c_t,\theta _t=\sum_{i}^{} w_i(\phi _t)\theta _i)
$$

![](/assets/06a-16.png)   


P50   
## PFNN: Phase-Functioned Neural Networks

![](/assets/06a-18.png)   

Cubic Catmull-Rom Spline:   

$$
\begin{align*}
 \theta _t & = \theta _2 \\\\
  & +\phi (-\frac{1}{2} \theta _1 + \frac{1}{2} \theta _3) \\\\
  & +\phi^2 (\theta _1-\frac{5}{2} \theta _2 + 2\theta _3-\frac{1}{2} \theta _4)\\\\
  & +\phi^3 (-\frac{1}{2} \theta _1+\frac{3}{2} \theta _2 - \frac{3}{2} \theta _3+\frac{1}{2} \theta _4)
\end{align*}
$$



P53   
## Advanced Phase Functions


![](/assets/06a-19.png)     


P54  
## Advanced Phase Functions


![](/assets/06a-20.png)   



P55   
## Advanced Phase Functions

|||
|---|---|
|![](/assets/06a-21.png)  | *SIGGRAPH 2018 |
| ![](/assets/06a-22.png)  | *SIGGRAPH 2020 |
| ![](/assets/06a-23.png)  | *SIGGRAPH 2022 |


P57  
## Generative Models

![](/assets/06a-24.png)   


P59   
## Generative Models


![](/assets/06a-025.png)   



P60   
## Generative Models

|||
|--|--|
| Variational Autoencoders |![](/assets/06a-25.png)   |
| Generative Adversarial Network |![](/assets/06a-26.png) |


P61   
## Generative Models

|||
|--|--|
| Normalizing Flows |![](/assets/06a-27.png)   |
| Diffusion Models  |![](/assets/06a-28.png)   |


P62  
## Generative Models

![](/assets/06a-29.png) 

[Ling et al. 2021 Character Controllers Using Motion **VAEs**] 


![](/assets/06a-30.png) 

[Henter et al. 2020, MoGlow: Probabilistic and Controllable 
Motion Synthesis Using **Normalising Flows**]


P63  
## Generative Models  

![](/assets/06a-31.png)   

[Zhang et al. 2022, **arXiv**, MotionDiffuse: Text-Driven Human Motion Generation with **Diffusion Model**]


![](/assets/06a-32.png)   

[Tevet et al. 2022, **arXiv**, MDM: Human Motion **Diffusion Model**]  


---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/