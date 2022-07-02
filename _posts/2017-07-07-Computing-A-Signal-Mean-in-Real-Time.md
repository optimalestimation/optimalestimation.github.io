---
layout: post
title: Computing A Signal Mean in Real Time
categories: Mathematics
---

The standard way to compute the mean (average) of a data set is to sum all the values and then divide by the total number of values. More explicitly, when we have scalar values $x_1, x_2, x_3, ..., x_N$, the mean $\mu_N$ for all the N values is computed as follows:

$$ \mu_N = \frac{\sum_{k=1}^N x_k}{N} ... (1) $$

Clearly, this is very simple. The simplicity comes at the cost of larger memory usage. This is because we have to store all the values from $x_1$ to $x_N$ in memory in order to compute the mean $\mu_N$. However, for real time systems performance and memory are critical. Therefore, a different method that computes the mean after every sample in a lightweight manner (without using too much memory) is required. One way is to use a recursive algorithm as follows: 

$$\begin{align} 
& \mu_0 = 0;       \nonumber \\\
& \mathrm{for} \hspace{2mm} k = 1:1:N \nonumber \\\
& \hspace{4mm} \mu_k = \left( \frac{k-1}{k} \right) \mu_{k-1} + \frac{x_k}{k};   \nonumber \\\
& \mathrm{endfor} \nonumber
\end{align}$$

Proof: 
The proof is pretty easy. First use the formula for mean assuming $k-1$ values are known. Similarly, write formula of mean assuming $k$ values are known. Perform some simple algebra to obtain the solution of mean at $k$ in terms of mean at $k-1$ and new data $x_k$. Details are shown below:

$$\begin{eqnarray} 
& \mu_k = \frac{\sum_{i=1}^k x_i}{k} \\\
& \mu_{k-1} = \frac{\sum_{i=1}^{k-1} x_i}{k-1} 
\end{eqnarray}$$ 

Now multiply the above equations by the denominator $k$ and ($k-1$),

$$\begin{align} 
 k\mu_k &= \sum_{i=1}^k x_i \\\
(k-1)\mu_{k-1} &= \sum_{i=1}^{k-1} x_i  
\end{align}$$ 

Now subtract the first equation from the second equation and perform simple algebra,

$$ \begin{align} 
k\mu_k - (k-1)\mu_{k-1} &= \sum_{i=1}^k x_i  - \sum_{i=1}^{k-1} x_i  \\\
\Rightarrow k\mu_k - (k-1)\mu_{k-1} &= x_k \\\
\Rightarrow   k \mu_k &=  (k-1)\mu_{k-1} + x_k \\\
\Rightarrow   \mu_k &= \left( \frac{k-1}{k} \right) \mu_{k-1} + \frac{x_k}{k} 
\end{align}$$ 
$\square$

Reference: [Link](https://www.jstor.org/stable/1266577)
