# Day-1
## How to talk to computers
### Introduction to QFN-48 package, chip, pads, core, die and IPs
The thing that we call a chip is actually a package. The chip is only a part inside the package.
  
![A chip](git3.png)  
The chip is connected to the outside world by wires and it is known as a wire-bound connection.
  
![A chip](git4.png)  
Die: A die is a piece of semiconducting material on which the circuit is fabricated.  
Core: The core is the part of the chip where all the logic is present.  
Pads: The pads are the area that encompass the core.  
  
![A chip](git5.png)  
The core consists of 2 types of parts : Foundry IPs and Macros.  
Parts such as the ADCs, SRAM, etc. are known as Foundry IP(Intellectual Property)s and parts such as the RISC-V SoCs and SPIs are called Macros.  
IPs are the parts which require intelligence to build. Macros do not require any intelligence to build.  
  
![A chip](git6.png)

### Introduction to RISC-V
An Instruction Set Architecture (ISA) is a conceptual model that defines how a computer's software controls its hardware. It's a set of rules that specify what a processor can do and how it does it. RISC-V is an open-source Instruction Set Architecture (ISA).

### From Software to Hardware
Now let us see how the instructions we give to the computer in a programming language such as C, C++, Java, etc. or from apps are conveyed to the processor.
![](git7.png)  
The Operating System (OS) of the computer consists of a Compiler and an Assembler. When we give inputs from applications or in a programming language, the Compiler converts the code into Instruction files (*.exe files). This is passed into the Assembler, which converts the instruction file in to Binary numbers. This is then fed to the processor which performs the operation.
  
## SoC flow and openLANE
### Components of ASIC design
ASIC stands for Application-Specific Integrated Circuit. It is a chip used to perform a specific task.  
ASIC design requires 3 important parts:  
1. EDA (Electronic Design Automation). It consists of the tools we need to design an ASIC. Some open-source EDA tools include : Qflow, openROAD and openLANE.  
2. RTL (Register Transfer Level). It consists of the designs we need to design an ASIC. Some open-source RTLs include : librecores.com, opencores.com and github.com.  
3. PDK (Process Design Kit). It consists of the data we need to design an ASIC. An open-source PDK is Skywater 130nm.  
![](git9.png)
### Simplified RTL to GDS flow
GDS files are the final output of the ASIC design cycle.  
The process from RTL to GDS contains 6 important steps.They are:  
1. Synthesis : It is the process of converting the RTL to a circuit out of components from the Standard Cell Library (SCL).  
2. Floor and Power Planning : It is the process of partitioning the chip die between different system building blocks and placing the Input/Output pads and placing the Power pads.  
3. Placement : It is the process of placing the cells on the floorplan rows, aligned with the sites.  
4. Clock Tree Synthesis : It is the process of creating a Clock distribution network.  
5. Routing : It is the process of implementing the interconnect using the available metal layers.  
6. Sign-Off : It is the process of verifying the ASIC by verifying the physical design using 2 methods : Design Rule Checking (DRC), and Layout vs. Schematic (LVS). and verifying the timing with Static Timing Analysis.  
