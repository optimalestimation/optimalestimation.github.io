---
layout: post
title: Power Management for MpSoCs
categories: power
---

Emerging applications on mobile systems demand an increase of computational capabilities, which is delivered by the computer industry using higher operating frequency and heterogeneity to the application processors. This leads to increase in the power consumption and temperature of the platform that directly affects the user experience. Therefore, power management has proliferated all aspects of mobile systems. For example, there are multiple ways to control the power consumption of a SoC, such as choosing a process technology, circuit level optimization, system level optimization and application code level optimization. All these granularities require very different skills and methods to optimize any desired objective, such as meeting a power budget and minimizing the energy consumption. Interestingly, the decisions made at each of the granularities are not independent of each other with no single bottom-up or top-down methodology that can be applied. In fact, it is an iterative process, where time to market and business decisions ultimately play a major role. For example, consider a typical OS level power management policy that critically depends on the number of voltage/frequency knobs. To add these knobs in the system, the circuit designers may have to use more voltage regulators that leads to increase in power consumption. Therefore, circuit designers must build a suboptimal design so that on a global scale the whole SoC can be optimized using the OS level power management. Due to continuous growth in the OS level knobs, such as more voltage-frequency levels and number of cores, it looks like the addition has been fruitful and OS level power management is promising. This is not surprising, because dynamic power depends on the switching activity of transistors which in turn depends on the applications running on the platform. For example, a user may want to run a game instead of a web browser, which have very different energy consumptions. Therefore, OS level power management has already become an integral component of the mobile optimization.

I was fortunate to work with Prof. Umit Ogras and many other academic and industry experts in the field to make substantial contributions in the OS level power management. I developed generalized scaling models for power and performance, studied the impact of background power on energy optimization, developed a CPU-GPU power budget allocation algorithm. In fact, there are many other researchers, who have contributed to a plethora of research in this area. This begs some questions, why is this field still open? What is there to research?

One reason is power management algorithms rely heavily on the performance and power models. These models help the power management algorithms to predict the change in power or performance due to change in the knobs. Currently, most models depend on a set of limited characterization data. It is impossible to characterize the data for all the applications in the world and with changing hardware platform, the problem gets aggravated. This leads to a long cycle of collecting data on every board to tune the power and performance models for a certain key performance indicators. Therefore, it is crucial to change the way power and performance models are developed and used.

We contribute to this changing paradigm by developing a fundamentally new approach to learn the performance models for integrated GPUs, which have become indispensable component of mobile systems. We employ online learning of the model, such that the model parameters can change at runtime, providing adaptability to any workload. More details are in our ICCAD paper, which presents a light-weight adaptive runtime performance model that predicts the frame processing time. We use this model to estimate the frame time sensitivity to the GPU frequency. Our experiments on a mobile platform running common GPU benchmarks show that the mean absolute percentage error in frame time and frame time sensitivity prediction are less than 4%.
