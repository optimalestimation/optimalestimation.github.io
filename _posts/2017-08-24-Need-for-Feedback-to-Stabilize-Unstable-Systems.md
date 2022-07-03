---
layout: post
title: Need for Feedback to Stabilize Unstable Systems
categories: Control-Theory
---
<!--
[Jekyll](https://jekyllrb.com) is a static site generator, an open-source tool for creating simple yet powerful websites of all shapes and sizes. From [the project's readme](https://github.com/mojombo/jekyll/blob/master/README.markdown):

  > Jekyll is a simple, blog aware, static site generator. It takes a template directory [...] and spits out a complete, static website suitable for serving with Apache or your favorite web server. This is also the engine behind GitHub Pages, which you can use to host your project’s page or blog right here from GitHub.

It's an immensely useful tool and one we encourage you to use here with Lanyon.

Find out more by [visiting the project on GitHub](https://github.com/mojombo/jekyll).
-->


This post addresses the following question with the help of an example: 

>Question: Is  it possible to practically stabilize an unstable system without feedback? 

Let us consider an unstable system with transfer function $P = \frac{1}{s-1}$. This plant has a pole on the right hand side plane in the s-domain, which means it is unstable. A naive (and incorrect way) to stabilize this system will be to employ a controller $K = \frac{s-1}{s+1}$ without any feedback. One might argue that the open loop transfer function $P\times K = \frac{1}{s+1}$ and the new pole now occurs at left hand plane of the s-domain, so this system must become stable. Unfortunately, it does not, due to at least two reasons:

The disturbances in the plant input and output can completely throw away the stability. This can only be corrected using feedback. 
Even in a disturbance free ideal world, all numbers are finite precision and have errors. So while computing $P \times K$, the $s-1$ terms in the numerator and denominator cannot completely cancel each other. 

>Answer: No.

I will put the response of such a system using Matlab to show instability in a future post. 
