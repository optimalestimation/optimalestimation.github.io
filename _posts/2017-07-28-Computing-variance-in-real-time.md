---
layout: post
title: Computing A Signal Variance in Real Time
---

The standard way to compute the variance of a data set is using the sqaure of the standard deviation. When we have scalar values $x_1, x_2, x_3, ..., x_N$, the mean $\mu_N$ standard deviation $\sigma_N$ for all the N values is computed as follows:

$$ \mu_N = \frac{\sum_{k=1}^N x_k}{N} ... (1) $$

$$ \sigma_N = \frac{\sqrt{\sum_{k=1}^N (x_k - \mu_N) }}{N} ... (1) $$

I already described in my previous blog post how to compute the mean in real time using the following algorithm at runtime: 

$$\begin{align} 
& \mu_0 = 0;       \nonumber \\\
& \mathrm{for} \hspace{2mm} k = 1:1:N \nonumber \\\
& \hspace{4mm} \mu_k = \left( \frac{k-1}{k} \right) \mu_{k-1} + \frac{x_k}{k};   \nonumber \\\
& \mathrm{endfor} \nonumber
\end{align}$$

This saves memory and is more elegent. 

Similarly, we can compute the variance of a data set using another recursive algorithm:

$$\begin{align} 
& \mu_0 = 0;       \nonumber \\\
 & S_0 = 0;       \nonumber \\\  
& \mathrm{for} \hspace{2mm} k = 1:1:N \nonumber \\\
& \hspace{4mm} \mu_k = \left( \frac{k-1}{k} \right) \mu_{k-1} + \frac{x_k}{k};   \nonumber \\\
 & \hspace{4mm} S_k = S_{k-1} + \left( (x_k - \mu_k)(x_k -   \mu_{k-1}) \right);   \nonumber \\\  
 & \hspace{4mm} \sigma_k = \sqrt\frac{S_k}{k} ;   \nonumber \\\   
 & \hspace{4mm} Var_k =   \sigma  _k^2 = \frac{S_k}{k};   \nonumber \\\   
& \mathrm{endfor} \nonumber
\end{align}$$ 

Note that, to compute the variance, we also require to compute the mean. 

References: 

[Link](https://www.jstor.org/stable/1266577)