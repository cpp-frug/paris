[C++FRUG #14](https://www.meetup.com/fr-FR/User-Group-Cpp-Francophone/events/236788136/)
================
`auto happy = new Year(2017)`
----------------------------

> 19:30 &nbsp; **Accueil**  
> 19:45 &nbsp; **Trois courtes présentations**  
> 20:15 &nbsp; **Pause Dinatoire**  
> 20:45 &nbsp; **C++17 abstractions for heterogeneous computing**  
> 21:30 &nbsp; **Prolongation du Meetup et discussions avec les conférentiers**

[**cppfrug.org**](http://cppfrug.org/paris/events/2017-01-19_n14/) [github.com](https://github.com/cpp-frug/paris/blob/master/events/2017-01-19_n14/README.md) [![le logo C++FRUG est consitué du drapeau de la francophonie avec C++ au centre](http://cpp-frug.github.io/images/Cpp-Francophonie.svg "Logo C++FRUG")](https://github.com/cpp-frug/cpp-frug.github.io/blob/master/images/Cpp-Francophonie.svg) **Communauté C++ francophone**


Trois courtes présentations
---------------------------

&nbsp;

1. [**Articles C++17 sur LinuxFr.org**](LinuxFr.org) par Oliver
2. [**Sérialisation à la compilation et à l'exécution**](Serial) par Guss
3. [**Framework Boson**](Boson) par JB

&nbsp;

Ces trois présentations sont sous licence [**CC BY-SA 4.0**](https://creativecommons.org/licenses/by-sa/4.0/deed.fr).  
Et leur code *Mardown* est disponible sur [le dépôt Git C++FRUG](https://github.com/cpp-frug/paris/blob/master/events/2017-01-19_n14).


Post-modern C++17 abstractions for heterogeneous computing with Khronos OpenCL SYCL
-----------------------------------------------------------------------------------

http://www.gipsa-lab.grenoble-inp.fr/thematic-school/gpu2015/presentations/GIPSA-Lab-GPU2015-R-Keryell-01.pdf

[Ronan Keryell](https://www.linkedin.com/in/ronankeryell) travaille pour Xilinx Research Labs afin de permettre à Clang/LLVM de compiler le C++17/C++20 pour des FPGA.

Computing architectures nowadays are huge multi-processor system-on-chips with different kind of processors, GPU, configurable specific accelerators (video CODEC...), reconfigurable programmable logic (FPGA), various hierarchies of memory and memory interfaces, configurable IO and network support, security support, power control, etc. High-performance applications may use a hierarchy of such system up to fill up a full-scale data-center.  So the programmer is facing nowadays a fractal architecture, demanding  also more and more control for power efficiency. This tends to require a dense fractal set of skills and tools. 

OpenCL SYCL C++ is a new open standard from Khronos Group aiming at solving some of the programming issues related to heterogeneous computing.  This pure C++17 domain-specific embedded language allows the programmer to write single-source C++17 host code with accelerated code expressed as functors. The data accesses are described with accessor objects that implicitly define a task graph that can be asynchronously scheduled on a distributed-memory system including several CPU and accelerators. Since this programming model is quite generic, we will end by introducing some extensions we study at Xilinx within the https://github.com/xilinx/triSYCL open source implementation to optimize FPGA usage with the concept of pipes to define 1-to-1 connections between kernels in the task graph without requiring expensive memory bandwidth. 

As this talk is focused on C++, we will also introduce some interesting features of C++17 and other C++ frameworks to address the issue of heterogeneous computing.
