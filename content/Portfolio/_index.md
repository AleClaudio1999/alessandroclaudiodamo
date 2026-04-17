+++
draft = false
title = 'Portfolio'

+++

## Projects

A selection of academic projects focused on operating systems, distributed systems, networking, and security. These works emphasize low-level system analysis, performance evaluation, and real-world experimentation.

### Cross-Core Interference in Real-Time Systems  
[Read the project](/alessandroclaudiodamo/Realtime-progetto.pdf)  

This project focuses on the experimental replication of techniques aimed at mitigating cross-core interference in Linux real-time systems. I worked with multiple kernels (Vanilla, RT, and openEuler), applying advanced CPU isolation mechanisms such as `isolcpus`, `nohz_full`, and IRQ affinity. The work involved setting up controlled environments, running latency benchmarks using tools like `cyclictest` and `oslat`, and evaluating schedulability under different configurations. The results show that while interference cannot be fully eliminated, proper kernel tuning significantly improves latency stability. This project provided hands-on experience with kernel-level performance tuning and real-time system behavior.

### Energy Management in the Linux Kernel (Bachelor Thesis)  (Ita)
[Read the thesis](https://thesis.unipd.it/handle/20.500.12608/76157)  

This thesis explores how the Linux kernel manages energy consumption through various subsystems and mechanisms. The work covers ACPI for hardware-level power control, Dynamic Voltage and Frequency Scaling (DVFS) for CPU optimization, and runtime power management for device-level energy savings. I analyzed how these components interact within the kernel, studying both their theoretical design and their practical implementation. The project highlights the trade-offs between performance and energy efficiency, especially in modern computing environments. It strengthened my understanding of operating system internals and low-level resource management.

### TCP Performance: Windows vs Linux  
[Read the project](/alessandroclaudiodamo/Progetto_finale_WNMA.pdf)  

This project presents a comparative analysis of TCP congestion control algorithms across different operating systems. Using the ns-3 network simulator, I evaluated the behavior of BBR (Linux) and CUBIC (Windows) under controlled network conditions. The analysis focused on metrics such as throughput, fairness (Jain Index), and round-trip time. I also examined how the two algorithms interact when competing for shared bandwidth, highlighting differences between model-based and loss-based approaches. The results show that BBR tends to achieve slightly higher throughput while maintaining fairness. This work deepened my understanding of network protocols and performance modeling.

### LLMs & Reverse Engineering  
[Read the project](/alessandroclaudiodamo/REMind_Extended.pdf)  

This project investigates how Large Language Models influence the workflow of novice reverse engineers. I contributed to the refactoring and deployment of an experimental platform based on Flask, Docker, and MySQL, improving both backend structure and user interface. Additional features were implemented to track user interaction patterns and estimate LLM usage during problem-solving tasks. The collected data revealed a strong shift from manual analysis to AI-assisted approaches, along with challenges related to trust and reliability. This project combines elements of security, software engineering, and human-computer interaction.

### Ceph Distributed Storage Analysis  
[Read the project](/alessandroclaudiodamo/Progetto__Running_final.pdf)  

This project analyzes the architecture and performance of Ceph, a distributed storage system designed for scalability and fault tolerance. I explored key components such as RADOS, Object Storage Daemons (OSDs), and the CRUSH algorithm for data placement. A test environment was set up to evaluate how parameters like replication factor, number of OSDs, and object size affect system performance. Through experimental benchmarking, I observed clear trade-offs between reliability and throughput. The project provided practical insight into distributed system design and data storage architectures.

==fixed==
Qui i miei progetti fatti con l'universita

- [Cross-core interference - An Ubuntu and OpenEuler experience](/alessandroclaudiodamo/Realtime-progetto.pdf) *Progetto per Real-Time Kernels and Systems*

- [Gestione del consumo energetico nel kernel Linux](https://thesis.unipd.it/handle/20.500.12608/76157) *Tesi di Laurea Triennale*

- [Comparative Analysis of TCP on Windows and Linux](/alessandroclaudiodamo/Progetto_finale_WNMA.pdf) *Progetto per Wireless Networks for Mobile Applications*

- [Remind Extended: The Impact of LLMs on Novice Reverse Engineers](/alessandroclaudiodamo/REMind_Extended.pdf) *Progetto per Advanced Topics in computer and Network Security*

- [Architectural Analysis and Experimental Evaluation of Ceph Distributed Storage](/alessandroclaudiodamo/Progetto__Running_final.pdf) *Progetto per Runtimes for Concurrency and Distribution*

  

