# State-Space-Model-for-Various-underlying-models
## What is State Space Model
- State space modelling is a method to study evolution in stochastic process using internal state space variables.
- Let us consider the observable variable $y_{t}$, that can be expressed as

$$
y_{t} = Z_{t} S_{t} + \epsilon_{t}
$$ 

- where,
  
  -    $y_{t}$ is k dimensional vector,
  -    $S_{t}$  is m dimensional state space vector at time t
  -    $Z_{t}$ is $k\times m$ dimesional obeservation vector coeffiecient matrix,
  -    $\epsilon_{t} \approx N(0_{k},H_{t})$ is i.i.d with $H_{t}$ is $k\times k$ dimesional positive definite variance matrix.
- The state space transition equation becomes

$$ 
S_{t+1} = T_{t} S_{t} + R_{t} \eta_{t}
$$


- where,
  
  -    $T_{t}$ is $m\times m$ dimensional translational matrix,
  -    $R_{t}$  is $m\times n$ dimensional fixed matrix
  -    $\eta_{t} \approx N(0_{n},Q_{t})$ is i.i.d with $Q_{t}$ is $n\times n$ dimesional positive definite variance matrix.
- This equations can be expressed in matrix form

$$
\begin{bmatrix}
    S_{t+1} \\
    y_{t}
\end{bmatrix}
=\begin{bmatrix}
    T_{t} \\
    Z_{t}
\end{bmatrix} S_{t} + 
\begin{bmatrix}
    R_{t} \eta_{t} \\
    \epsilon_{t}
\end{bmatrix} \\
= \Phi_{t} S_{t} + u_{t}
$$

- where,
  
$$
u_{t} =
\begin{bmatrix}
    R_{t} \eta_{t} \\
    \epsilon_{t}
\end{bmatrix} \\ \approx N(0, \Omega)
$$

  
  - and
 
$$
\Omega=
\begin{bmatrix}
    R_{t} Q_{t} R_{t}^{T}  &&  0\\
    0   &&  H_{t}
\end{bmatrix} 
$$

## State Space model for AR(p)
- We can express AR(p) using lag equation

$$
\phi(L)y_{t} = \epsilon_{t} ,   \phi(L)= 1 - \sum_{j=1}^{p} \phi_{j}L^{j}  ,  \epsilon_{t} \approx N(0, \sigma_{\epsilon}^{2})
$$

- which gives

$$
y_{t} = \sum_{i=1}^{n} \phi_{i} y_{t-j} + \epsilon_{t}
$$

- If we define the state space vector as $\vec{S_{t}} = [y_{t}, y_{t-1}, ..., y_{t-p+1}]^{T}$

$$
S_{t+1} =
\begin{bmatrix}
y_{t+1}  \\
y_{t} \\
y_{t-1} \\
\vdots  \\
y_{t-p+2}
\end{bmatrix} = 
\begin{bmatrix}
\phi_{1} & \phi_{2} & \dots & \phi_{p-1} & \phi_{p} \\
1 & 0 & \dots & 0 & 0 \\
0 & 1 & \dots & 0 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & \dots & 1 & 0 
\end{bmatrix} 
\begin{bmatrix}
y_{t}  \\
y_{t-1} \\
y_{t-2} \\
\vdots  \\
y_{t-p+1}
\end{bmatrix} + 
\begin{bmatrix}
\epsilon_{t+1}  \\
0 \\
0\\
\vdots  \\
0
\end{bmatrix}
=T_{t}S_{t} + R_{t}\eta_{t}
$$

- Which gives

$$
T_{t} = 
\begin{bmatrix}
\phi_{1} & \phi_{2} & \dots & \phi_{p-1} & \phi_{p} \\
1 & 0 & \dots & 0 & 0 \\
0 & 1 & \dots & 0 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & \dots & 1 & 0 
\end{bmatrix} ;
R_{}=
\begin{bmatrix}
1  \\
0 \\
0 \\
\vdots  \\
0
\end{bmatrix}
$$

  -  and i.i.d
    
$$
\eta_{t}=\epsilon_{t+1}\approx N(0,\sigma_{\epsilon}^{2})
$$


- The observed variable equation becomes

$$
y_{t}=\begin{bmatrix}
y_{t}  \\
0 \\
0 \\
\vdots  \\
0
\end{bmatrix}= \begin{bmatrix}
1  & 0 & \dots & 0 & 0
\end{bmatrix} S_{t} = Z_{t}S_{t} + \zeta_{t}
$$

- which implies $Z_{t} = \begin{bmatrix}
1  & 0 & \dots & 0 & 0
\end{bmatrix}$ and $\zeta_{t}=0$
