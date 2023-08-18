# Lecture 12

P2   
## Outline   

 - Optimal Control   
 - Model-based Approaches vs. Model-free Approaches   
 - Sampling-based Optimization   
 - Reinforcement Learning   

 - Conclusion  


P3   
## Recap: Trajectory Optimization

![](/assets/12-01.png)


P4  
## Recap: Feedforward Control

![](/assets/12-02.png)   


P5   
## Recap: Feedback Control


![](/assets/12-03.png)  


P7   
## Recap: Feedback Control

![](/assets/12-04.png)  


P9  

![](/assets/12-05.png)  


P10  
## Constrained Optimization

$$
\begin{matrix}
 \min_{x}  f(x)\\\\
𝑠.𝑡. g(x)=0
\end{matrix}
$$

![](/assets/12-06.png)    


P12  
## Constrained Optimization  

Soft constraint?   

$$
\min_{x}  f(x)+ wg(x)
$$

\\(\ast \\) The solution \\(x^\ast\\)  may not satisfy the constraint   

 
P16   
## Lagrange Multiplier    

![](/assets/12-08.png)  

![](/assets/12-07.png)  

Lagrange function   

$$
L(x,\lambda )=f(x)+\lambda ^Tg(x)
$$

P18   
## Lagrange Multiplier 


![](/assets/12-09.png)  


P20   
## Solving Trajectory Optimization Problem   


![](/assets/12-10.png)  



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/