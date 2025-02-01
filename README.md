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

![](git10.png)

### OpenLane detailed ASIC design flow
This is the diagram of the detailed openLANE ASIC design flow.  
![](git11.png)   

### Flop Ratio
Flop Ratio = Number of D Flip Flops / Total Number of cells  
           = 1613 / 14876  
           = 0.1084  
Flop Percentage = Flop Ratio x 100  
                = 0.1084 x 100  
                = 10.84  

# Day-2
## Chip Floor-Planning Considerations
### Utilization Factor and Aspect Ratio
Utilization Factor is defined as the total area occupied by the circuit by the total area of the core.  
Utilization Factor = Total area occupied by circuit / Total area of core  
The Aspect ratio is defined as the height of the core by width of the core.  
Aspect ratio = Height / Width  
Let us take an example of a circuit which occupies 4 sq.units placed in a core of dimensions 2units x 2units.  
Utilization factor = total area occupied by circuit / total area of core  
                   = 4 sq.units / 2units x 2 units  
                   = 4 sq.units / 4 sq.units  
                   = 1  
Aspect Ratio = Height / Width   
             = 2 / 2  
             = 1  
A Utilization Factor of 1 indicates that the area of the core is totally occupied and additional components cannot be added.    
An Aspect Ratio of 1 indicates that the core is square-shaped.  

  ### Pre-Placed Cells
  A large circuit or netlist can be divided into 2 parts to simplify the connections.  
    
  ![](git13.png)
  These 2 parts are now 2 circuit blocks.  Now we can remove the connections between the 2 different blocks and extend them as I/O pins. These 2 modules can be used separately as IPs (Intellectual Property) or modules.    
    
  ![](git12.png)  

- The arrangement of these IPs in a chip is referred to as floor-planning.
- These IPs have user-defined locations and hence, are placed in chips before automated placement-and-routing and are known as "Pre-Placed Cells"

  
