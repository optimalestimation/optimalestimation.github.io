---
layout: post
title: How to choose a RAM for your PC
categories: computer-architecture
---

When we think about choosing a computer's memory (RAM), we often think about the type, such as DDR4 or DDR5, size (measured in GBs), and speed (measured in MT/s). 
When you are building a PC yourself, it is important to know some additional memory parameters to carefully optimize your system and get the best performance, such as the memory timing, power and voltage.  
Among these, the the memory timings are critical because they determine the performance and speed of the memory. The memory controller in the CPU plays a critical role in managing the memory, but it relies on the memory timings to know how long to wait for the data to be available, how long to keep the row selected, and how long to wait between refresh cycles. If the memory timings are incorrect or not optimized, the memory may not be able to operate at its maximum speed, which can result in slower performance and reduced efficiency. Therefore, it is important to carefully set and optimize the memory timings in order to ensure that the memory can operate at its maximum speed. Memory timings are typically measured in nanoseconds (ns) or clock cycles. The specific memory timings used can significantly impact the system's overall performance, so manufacturers carefully optimize them to ensure that the memory can operate at its maximum speed. Memory timings are typically specified as a series of numbers, such as "5-5-5-15" or "9-9-9-24," representing the different delays and intervals in accessing the memory.

As an example, the "9-9-9-24" memory timing refers to a specific set of memory timings that are used to determine the performance and speed of a computer's memory (RAM). The four numbers in this timing specification represent the values of four different memory timing parameters, as follows:

* The first number (9) represents the CAS (Column Address Strobe) latency, which is the delay between the time a memory request is made and the time the data is available for reading or writing.

* The second number (9) represents the RAS (Row Address Strobe) to CAS delay, which is the delay between the time a row of memory is selected and the time the data in that row is available for reading or writing.

* The third number (9) represents the RAS pulse width, which is the minimum amount of time that a row must be selected in order to access the data in that row.

* The fourth number (24) represents the RAS to precharge delay, which is the delay between the time a row is no longer being accessed and the time it is precharged (i.e. the charge is removed from the row).

Here is a fantastic [reference](https://www.eetimes.com/understanding-ddr-sdram-timing-parameters/) for that explain these parameters in some more detail. 

When building a PC, I got a DDR5 (2x16 GB to utilize both channels of memory controller) 4800 MT/s memory at 1.1 V. The maximum memory speed supported by my CPU is 4800 MT/s, so I was confident that this was what I needed. However, after I finished the build, the memory speed was only 4000 MT/s. That led me to investigate this further. The BIOS will put the memory in a safer operating zone of 4000 MT/s, and we have to change the memory timings to get maximum performance. Typically, RAMs support Extreme Memory Profiles (XMP) profile that auto lists the memory parameters optimized to get maximum performance. It is as easy as selecting a simple option in BIOS and being done with it. However, in my case, the memory was not XMP read (even though the packet said it was). As a result, I had to rely on the JDEC specification, which had the timing parameters for 4800 MT/s. However, when I tried those parameters, the BIOS hung, and I had to reset it. Then, I got another memory same company and product, except it was rated as 5200 MT/s speed and 1.25 V. This new RAM worked at maximum performance since it had the XMP, and I could enable it.













