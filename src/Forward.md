
P3   
## Outline   

 - Character Kinematics   
    - Skeleton and forward Kinematics   

 - Inverse Kinematics   
    - IK as a optimization problem   
    - Optimization approaches   
      - Cyclic Coordinate Descent (CCD)   
      - Jacobian and gradient descent method   
      - Jacobian inverse method   


P4   

## Character Kinematics    


kinematics /ˌkɪnɪˈmætɪks/
n. the study of the motion of bodies without reference to mass or force   
-- Collins English Dictionary    

P8   
## Skeleton

![](/assets/03-01.png)  

P9   
## Skeleton

![](/assets/03-02.png)  



P14    
## Kinematics of a Chain

![](/assets/03-03.png)  

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1=I\\\\
 Q_2=I\\\\
 Q_3=I\\\\
Q_4=I
\end{matrix}
$$


P15    
## Kinematics of a Chain


![](/assets/03-04.png)  

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1=I\\\\
 Q_2=I\\\\
 Q_3=I\\\\
Q_4={\color{Red}R_4}
\end{matrix}
$$


P16   

## Kinematics of a Chain

![](/assets/03-05.png) 

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1=I\\\\
 Q_2=I\\\\
 Q_3={\color{Red}R_3}\\\\
Q_4={\color{Red}R_3}R_4
\end{matrix}
$$


P17    
## Kinematics of a Chain

![](/assets/03-06.png) 

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1=I\\\\
 Q_2={\color{Red}R_2}\\\\
 Q_3={\color{Red}R_2}R_3\\\\
Q_4={\color{Red}R_2}R_3R_4
\end{matrix}
$$


P18   
## Kinematics of a Chain

![](/assets/03-07.png)  

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1={\color{Red}R_1}\\\\
 Q_2={\color{Red}R_1}R_2\\\\
 Q_3={\color{Red}R_1}R_2R_3\\\\
Q_4={\color{Red}R_1}R_2R_3R_4
\end{matrix}
$$

P19   
## Kinematics of a Chain

![](/assets/03-08.png)  

$$
\begin{matrix}
 Q_0={\color{Red}R0}\\\\
 Q_1={\color{Red}R_0}R_1\\\\
 Q_2={\color{Red}R_0}R_1R_2\\\\
 Q_3={\color{Red}R_0}R_1R_2R_3\\\\
Q_4={\color{Red}R_0}R_1R_2R_3R_4
\end{matrix}
$$

P20   

## Kinematics of a Chain

![](/assets/03-09.png)  

$$
\begin{matrix}
 Q_0={\color{Red}R0}\\\\
 Q_1={\color{Red}R_0}R_1\\\\
 Q_2={\color{Red}R_0}R_1R_2\\\\
 Q_3={\color{Red}R_0}R_1R_2R_3\\\\
Q_4={\color{Red}R_0}R_1R_2R_3R_4
\end{matrix}
$$






![](/assets/03-10.png)  




---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/