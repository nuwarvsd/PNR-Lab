# PNR-Lab
## Day 1
### SKY130_D1_SK1 - How to talk to computers

The computers can perform the intruction, which are given externaly and some hardware is there which convert the external instruction into understandable language of computers. For example FPGA board, Arduino board etc. are provides the medium for external inputs and outputs.
FPGA Board in Embedded System, etc.
Example Board is 
	
![image](https://user-images.githubusercontent.com/123365818/215948656-82e2d02f-4aba-406b-a0eb-ddb0d8809bc6.png)
	
Arduino consists of both a physical programmable circuit board (often referred to as a microcontroller) and a piece of software, or IDE (Integrated Development Environment) that runs on the computer, used to write and upload computer code to the physical board.
Basically microcontroller is made from package, inside the package chip is there.Chip is made by pads, core, die and foundary IP's.
	
	VCC, GND , SDRAM . etc. are inside the chip on the board
	
![image](https://user-images.githubusercontent.com/123365818/216331554-9bd595aa-d794-4691-b242-72beca0c87d6.png)

	
	
**Basic Terms:**
	**Packages **
	The package is a case that surrounds the circuit material to protect it from corrosion or physical damage and allow mounting of the electrical contacts connecting it to the printed circuit board (PCB). here what we are seeing in the black color is the Package of the microcontroller.
	
	Pin location
	
![image](https://user-images.githubusercontent.com/123365818/216331498-49a65676-4412-4069-b4ee-566942d7b290.png)


	Chip in the center of package
	Inside the Package, chip is available which contains, foundary IP's (for example, RISC-V Soc, PLL, ADC, DAC, SRAM, SPD), core (core contains AND, OR etc. all gates and digital logics), pads (through which input and output signals are communicates).


   **Wire bonding**
	
![image](https://user-images.githubusercontent.com/123365818/216331386-57f4ff1e-0d82-4b39-a2ab-e6b03b5dd6ac.png)

	
	Look Inside the chip , pads, die and core can be found
	
**Pads:** signal can go inside the chip and outside of the chip through the pads
	
**Core:** digital logics are placed in the area
	
**Die:** manufacturing on the silicon wafer 
	
![image](https://user-images.githubusercontent.com/123365818/216331658-17a47c88-257f-42c3-bd76-4d75ccf09e79.png)
	
	ADC, DAC, SRAM,PLL are called as Foundry IP’s.
	
Digital Block such as SPI and SOC are called as **Macro** (pure digial logic)
	
![image](https://user-images.githubusercontent.com/123365818/216331704-dcfc9ecf-a86b-4fb5-ae44-8e6d0ee2f2da.png)
	
	
**Foundry IP**: all Intellectual Property, whether Background IP or Foreground IP, regardless of when or for what purpose it is developed, pertaining to genetic components, pathways, and strains; and methods and tools for design, genetic engineering, testing and/or small-scale fermentation of microbial strains. Notwithstanding the foregoing, this category shall exclude Ginkgo Background IP, Collaboration Strain and Process IP, and Foreground Application IP.

### SKY_L2 - Introduction to RISC-V

	Talk to computer

**ISA (instruction set architecture)**
RISC-V, where five refers to the number of generations of RISC architecture that were developed at the University of California, Berkeley. RISC is an open standard instruction set architecture (ISA) based on established RISC principles. Unlike most other ISA designs, RISC-V is provided under open source licenses that do not require fees to use. A number of companies are offering or have announced RISC-V hardware, open source operating systems with RISC-V support are available, and the instruction set is supported in several popular software toolchains.

The instruction set is designed for a wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions, and the ISA supports variable length extensions where each instruction can be any number of 16-bit parcels in length. The instruction set specification defines 32-bit and 64-bit address space variants. The specification includes a description of a 128-bit flat address space variant, as an extrapolation of 32 and 64 bit variants, but the 128-bit ISA remains "not frozen" intentionally, because there is yet so little practical experience with such large memory systems.
	
![image](https://user-images.githubusercontent.com/123365818/215950361-185a069d-950b-4874-aec6-5da7c2dcad54.png)

	C program to assembly language program (hex format or binary format) map  particular layout.

	Implementation in RTL 
	
![image](https://user-images.githubusercontent.com/123365818/215950696-dc6762a2-9fdd-4d39-b1ab-a052fc4cd9d6.png)

### SKY_L3 - From Software Applications to Hardware

**Application software to Hardware by using ISA**
	
	Between apps or software (in our mobilephones and computers or laptops) and Hardware (in our mobilephones and computers or laptops), One full channel is there, which contains O.S. (operating system), compiler and assembler. This channel proccesses the inputs from the apps and gives the outputs to the Hardware. And according to the output of assembler, the hardware will perform.

![image](https://user-images.githubusercontent.com/123365818/215951076-eccf91cf-8180-49e8-bb44-4a0598340eda.png)

	Application Software to System Software to Hardware
	Major components of system software : OS, Compiler, Assembler
	OS: Handle IO operations
	    Allocate memory
            Low level system functions
	
When the inputs is given from the software, inputs is in the C,C++,JAVA etc. languages. Hardware not understand this language. So, this inputs goes throuth the system software cahnnel, where O.S. handles the input/output operations, it allocates the memory to for the codes and low level systems functions are there in O.S. Then program goes to the compiler, where program will compile and generate the HDL program.This HDL program is basically the sets of Instructions which can hardware is able to understand. The instructions are basically depends on what kind of hardware we are using. For example if we are using Mips processor then instruction formaate will be according to the Mips processor, if Hardware is RISC-V then the instruction formate will be according to the RISC-V and similerly for Arm and intel processors also.

This sets of instrusctions is now given to the Assembler. here according to the instruction set, assembler will generate the Binary code (contains only 0s and 1s). this binary code can be understandable for hardware. And according to this code, hardware will gives the output.
	
![image](https://user-images.githubusercontent.com/123365818/215951335-c3f0bf51-6179-4837-82c5-3001d2c509a9.png)
	
![image](https://user-images.githubusercontent.com/123365818/215951393-748d0a2f-877e-4aed-b101-be493de83d06.png)
	
#### SoC Design using Openlane
	
To design Digital ASIC, few tools or things which are required from the day one. These are

RTL Design
EDA tools
PDK data
	
![image](https://user-images.githubusercontent.com/123365818/215955732-7c2649e9-3005-44ae-ad5a-114ed08c0b29.png)

1. RTL Designs: In digital circuit design, register-transfer level (RTL) is a design abstraction which models a synchronous digital circuit in terms of the flow of digital signals (data) between hardware registers, and the logical operations performed on those signals.for this designs many open sorces are available. like, librecores.org, opencores.org, github.com, etc...
	
	Librecores.org
	
	Opencores.org
	
	Github.com
	
2. EDA Tools : The term Electronic Design Automation (EDA) refers to the tools that are used to design and verify integrated circuits (ICs), printed circuit boards (PCBs), and electronic systems, in general. many open sorces tools are available like Qflow, OpenROAD, OpenLANE, etc...
	
	Qflow
	
	OpenROAD
	
	OpenLANE
3. PDK :PDK is process design kit. It is interface between FAB and design. 
	
See Pure Play Fabs and Fabless design companies
	
![image](https://user-images.githubusercontent.com/123365818/215955099-250dd64f-c082-4e92-9053-f1b107559892.png)

	
PDK = the interface between the FAB and the designers
	
PDK=Process Design Kit
	
	Collection of files used to model a fabrication process for the EDA tools used to design an IC
This data is collections of files like,
	
	* Process Design Rules: DRC, LVS, PEX
	
	* Device Models
	
	* Digital standard Cell Libraries
	
	* I/O Libraries
	which are used to model a fabrication process for the EDA tools used to design an ICs. for example, in 2020, google release the open source PDK for FOSS 130nm production with the skywater technology. But right now it is at cutting age of the 5 nm also. But in many applications, the advance node is not required, and the cost of advanced node is also high as compared to 130nm processors. This 130nm processors are also fast processor. for example,
intel: P4EE @3.46 GHz(Q4'o4)
sky130_OSU (single cycle RV32i CPU) pipeline version can achieve more than 1 GHz clock
	
	
#### SKY_L2 - Simplified RTL2GDS flow
	
	

**Simplified RTL to GDSII Flow**
	
	
	Synthesis 
	
	Floor/Power Planning
	
	Placement
	
	Clock Tree Sysnthesis
	
	Routing 
	
	Sign Off
	
![image](https://user-images.githubusercontent.com/123365818/215955821-fa250fa4-17c9-4e18-ad46-a05a76027c6f.png)
	
**Synthesis**
	
Converts RTL to a circuit out of components from the standard cell library (SCL)

	Synthesis In the synthesis, the design RTL is translated to a circuit out from the SCL. 

	The resultant circuit is describes in HDL and usualy refered to the gate level netlist. 
	
	The gate level netlist is functionaly equivelent to the RTL.
	
	"standard Cells" have regular layouts.
	
![image](https://user-images.githubusercontent.com/123365818/215956556-26e16513-ffed-4932-9634-1df362fa3af4.png)

Standard Cell have regular layout

	Each has different views/models

	Electrical,HDL,SPICE

	Layout(Abstract and Detailed)
	
![image](https://user-images.githubusercontent.com/123365818/215956668-36826493-8eed-4dda-97c7-aeca3fc45fc1.png)
	
**Floor and Power Planning**

The main objective here is that to plan silicon area and distribute the power to the whole circuit. In the chip floor planning, the partition chip die between different system building blocks and place the i/o pads. In micro floor planning, we define the dimensions, pin locations, rows.
	
	**Chip Floor Planning:** Partition the chip die between different system building blocks and place the I/O Pads
	
![image](https://user-images.githubusercontent.com/123365818/215957005-9d814e3c-3911-4e8a-b2d5-31cbcabee6a6.png)
	
	**Macro floor Panning:** Dimensions, pin locations, row definition
	
![image](https://user-images.githubusercontent.com/123365818/215957152-91fbbdc8-b710-4b17-9e6e-f3f4583734b6.png)
  
	**Power Planning**
	
	In power planning, the power network is connstructed. tipically, the chip is power by multiple VDD and GND. so, total components are connected to power supply horizontaly and vertically by metal streps. here parallel structures are used to reduce the resistance. To address the electromagnetization problem, power distribution network uses upper metal leyers, which are thicker than lower metal layers. Hence have less resistance.
	
![image](https://user-images.githubusercontent.com/123365818/215957377-3b962e4a-052c-4170-ae43-7fae90e60719.png)
	
	**Placement:** Place the cells on the floorplan rows, aligned with the sites
	
![image](https://user-images.githubusercontent.com/123365818/215957542-2131deca-7ae1-4647-a43b-dfa04478e423.png)
	
	In this process, we place the gate level netlist on the floor planning rows, alligned with the sites. cells should be placed very closed to eachother to reduce the interconnnect delay. 
	
	Usually done in two steps: Global and Detailed
	
![image](https://user-images.githubusercontent.com/123365818/215958746-8db624eb-4887-4c06-8b96-4b8557548038.png)

	**Global placement** is very first stage of the placement where cells are placed inside the core area for the first time looking at the timing and congestion. Global Placement aims at generating a rough placement solution that may violate some placement constraints while maintaining a global view of the whole Netlist.
	
	In **detailed placements**,  the exact route and layers are determined for each netlist. the objective of detailed placement is valid routing, minimize area and meet timing constrains. Additional objective is minimum via and less power.

**Clock tree Synthesis**

Create a clock distribution network

	To deliver the clock to all sequential elements (e.g., FF)

	With minimum skew (zero is hard to achieve)

	And in a good shape

	Usually a Tree (H,X,..)
	
![image](https://user-images.githubusercontent.com/123365818/215958873-0ddec3a8-f6aa-45dd-b579-31ca65289f72.png)
	
Before routing the signals, we have to route the clock. In the process of clock synthesis, we have distribute the clock to the every sequential elements. for example flipflops, registers, ADC, DAC ete. basically clock netwroks looks likes a tree. where the clock source is roots and the clock elements are end leaves. Synthesization should be done in a manner that with minimum skew and in a good shape.To minimize the clock skew by using the low-skew global routing resources for clock signals.Microsemi devices provide various types of global routing resources that significantly reduce skew.Usually a tree is a H tree, X tree etc.
	
**Routing : ** Implement the interconnect using the available metal layers.
	
	After routing the clock, the signal routing comes. Making physical connections between signal pins using metal layers are called Routing. Routing is the stage after CTS and optimization where exact paths for the interconnection of standard cells and macros and I/O pins are determined. There are two types of nets in VLSI systems that need special attention in routing:


	Clock nets

	Power/Ground nets

The sky130 PDK defines the 6 routing leyers. the lowest leyer is called local interconnect layer (titanium nitride layer). Other five layers are alluminium layers.
	
![image](https://user-images.githubusercontent.com/123365818/215958966-0d1ca977-c966-428b-bce3-c097cdf2871a.png)

	* Metal tracks from a routing grid

	* Routing grid is huge

	* Divide and Conquer

		Global Routing: Generates routing guides

		Detailed Routing: Uses the routing guides to implement the actual wiring
In the proccess of routing, metal trackes forms a routing grids and these grids are huge. So, devide and conquer approach is use for routing. 
	
**Sign Off**
Once the routing is done, we can construct the final layout. This final layout will goes under the verification. Two types of verifications are there:
	
	* Physical Verifications : Here design rule checking will done and it will check the final layout and owners layout

		* Design Rules Checking (DRC)

		* Layout vs. Schematic (LVS)

	* Timing Verification : Here Static Timing Analysis will done

		* Static Timing Analysis (STA)
	

### SKY_L3 - Introduction to OpenLANE and Strive chipsets

**Problem**

	The Problem is tougher when using Open Source EDA

	* Tools Qualification?

	* Tools Calibration?

	* Missing Tools?

**OpenLANE**
Started as an Open-Source Flow for a True Open Source Tape-out Experiment
	
StriVe is a family of open everything SoCs 
	
	Open PDK, Open EDA, Open RTL
	
	OPENLANE is an automated RTL to GDSII flow that is composed of several tools such as OpenROAD, Yosys, Magic, Netgen, Fault, CVC SPEF-Extractor, CU-GR, Klayout and a number of scripts used for design exploration and optimization. It is started as an Open-source flow for a true Open Source tape-out Experiment. 
	striVe is a family of open everything SoCs:


	* Open PDK

	* Open EDA

	* Open RTL

	
![image](https://user-images.githubusercontent.com/123365818/215960300-7c212c71-8332-41b0-ab3c-82ecd7c58db8.png)
	
striVe SoC Family
	
![image](https://user-images.githubusercontent.com/123365818/215960416-08c4ee0b-5e27-4f6a-9826-8554a6ed6612.png)
	
**Main Goal:**

The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop). 
	
	**Produce a clean GDSII with no human intervention (no-human-in-the-loop)**

	Clean means:

	* No LVD Violation

	* No DRC Violations

	* Timing Violations
	
	Tuned for SkyWater 130nm Open PDK

	Containerized

	* Functionl out of the box

	* Instructions to build and run natively will follow
	
OPENLANE is tuned for skyWter130nm open PDK. it can be used to harden Macros and chips.there is two mode of operation

	**Autonomus :** it is the push botton flow. with the push botton , it is a some time base design and due to this push botton, we get final GDSII

	**interactive :** here we can run comamds and steps one by one.

It has large number of design examples(43 designs with their best configurations).
	
###  Introduction to OpenLANE detailed ASIC design flow
	
![image](https://user-images.githubusercontent.com/123365818/216004054-b8001334-ed60-47d9-909f-41c504fcd6e1.png)

The design exploration utility is also used for regression testing(CI). we run OpenLANE on ~ 70 designs and compare the results to the best known ones.
	
	DFT(Design for Test)
it perform scan inserption, automatic test pattern generation, Test patterns compaction, Fault coverage, Fault simulation.
	After that physical implementation is done by OpenROAD app. physical implementation involves the several steps:


	Floor/Power Planning

	End Decoupling Capacitors and Tap cells insertion

	Placements: Global and Detailed

	Post Placement Optimization

	Clock Tree synthesis (CTS)

	Routing: Global and Detailed

	Every time the netlist is modified.(CTS modifies the netlist and Post Placements optimization also modifies the netlist).so for that verification must be performed. The LCE(yosys) is used to formally confirm that the function did not change after modifying the netlist. ### Dealing with antenna rules Violation: when a metal wire segment is fabricated, it can act as antenna.as an antenna, it collect charges which can demaged the transister gates during the fabrication.
	
	Static Timing analysis(STA)
	
It involves the interconnect RC Extraction(DEF2SPEF) from the routed layout, followed by STA on OpenSTA(OpenROAD) tool. resulting report will shows the timing violations if any violations is there.

Physical Verification (DRC and LVS)
	
Magic is used for design Rules checking and SPICE Extraction from Layout. Magic and Netgen are used for LVS.

### SKY130_D1_SK3 - Get familiar to open-source EDA tools

#### SKY_L1 - OpenLANE Directory structure in detail

**cd command**
	
cd means change directory. this command will help us to go inside the directory.
	
**ls command**
	
ls means listing the directory. It is used to find the list of total details of directory.
	
**ls --ltr**
	
This command will help to list the details in cronological order.
	
       cd Desktop
	
	cd work/tools
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/216004162-93652469-0c44-461d-9f10-25f6e571ffc9.png)


	cd openlane_working dir
	
	cd pdks
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215980582-68a8c5ce-706d-49ca-876c-4b22506b4e12.png)
	
	cd sky130A
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215981089-2748cca8-587e-42b2-b757-dc38c41a6cd3.png)
	
	libs.ref ---specific to technology
	
![image](https://user-images.githubusercontent.com/123365818/215981550-62b3f4e7-30ea-4ba5-9160-57b581a0bf09.png)

	
	libs.tech --specific to tool
	
![image](https://user-images.githubusercontent.com/123365818/215981821-4e0b9509-4176-4e33-8162-c6b79688a140.png)
	
	cd sky130_fd_sc_hd
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215982319-ac1fd81f-f3a6-49a7-846f-27137e891b80.png)
	
Here we are working in Sky130_fd_sc_hd PDK varient. where, "sky130" is process name or node name."fd" is a foundary name (skyWater foundary)."sc" means standerd cell librery files and the last one "hd" stands for high density(basically one type of varient).
	
	cd lib
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215982743-2b7a50e3-9ea2-4790-8855-04ed412672e8.png)
	
	cd ..
	cd lef
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215983086-ffa8e288-6eee-4750-9fc0-a1b771b9bae5.png)
	
	tlef is technology lef
	
	cd ..
	cd ..
	cd ..
	cd  openlane
	
![image](https://user-images.githubusercontent.com/123365818/215983750-7e7f54b9-8a8e-4df8-99b9-16e23a1b0291.png)
	
Sky130_fd_sc_hd varient contains many technology files like verilog, spice, techlef, meglef,mag,gds,cdl,lib,lef,etc. (techlef file contains the layer information).
	
#### SKY_L2 - Design Preparation Step
	
when we enter in the OpenLANE, we have to use flow.tcl because as a name says, it will goes with the flow using the script. And by using interactive switch, we will do step by step process. without interactive switch, it will run complete flow from RTL to GDSII. 
	
go to bash shell

	**docker**
	
![image](https://user-images.githubusercontent.com/123365818/215984216-cde75248-5d1a-4759-a179-e5b8db9a5307.png)
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215984582-80da5808-1a5f-479d-9ed8-8fa38ff19f44.png)
	
	**./flow.tcl -interactive**
	
![image](https://user-images.githubusercontent.com/123365818/215985044-1da04e4a-5648-45a4-80b1-90e91c9ed66e.png)

Now OpenLANE is open and we can see that prompt will change now.
	**changing promt to percentage symbol %**
	
Required to input the package
	**package require openlane 0.9**

Now we have to input all the packages which required to run the flow. here we are ready to execute the command.
	
![image](https://user-images.githubusercontent.com/123365818/215985890-b8198df9-15b2-4805-b095-ed48b914c143.png)
	
	Look into the design flolder
	
![image](https://user-images.githubusercontent.com/123365818/215986426-3662ae6d-bc47-49c9-a6ac-e9e10558cfdc.png)
	
	cd picorva32a
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215986711-71426a30-2217-43e2-b9e0-bd0cc5079f5e.png)
	
	src file : source file
	
	tcl file
	
	config.tcl
	
	Now, if we are going into the design folder in openlane, there are nearly 30-40 designs are already builted. Out of them we can open any of the design. for example, here we are opening the picorv32a.v design. In this design we can see many files are available. i.e., scr, config.tcl, etc. This config.tlc file contains every details about the design. for example, details about enrollment, clock period, clock period port etc.
	
looking into configuration file
	**less config.tcl**
	
![image](https://user-images.githubusercontent.com/123365818/215987238-86dd541c-8fc1-4abe-997b-255bbc1732b0.png)
	
	Here we can see that the time period is set to the 5.00 nsec. but is we see in the openlane sky130_fd_sc_hd folder, the period is set about 24 nsec. so it is not override to the main file. If it override then give first priority to the main folder.
	
	20 ns clock period, etc are in the config file 

	And then go to bash shell
	Now, in openlane, we are going to run the synthesis, but before synthesis, we have to prepare design setup stage. for that command is " prep -design picorv32a".
	
	**prep -design picorv32a**
	
mergelef.py: Merging LEFs
	
![image](https://user-images.githubusercontent.com/123365818/215988574-f4d3c42e-4694-40a5-935f-674b74763c56.png)
	
so, here it is shown that preparation is completed.
	
#### SKY_L3 - Review files after design prep and run synthesis
	
After completing the preparation, in the picorv32a file, the run terictory is created. 
	
	**cd runs**
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215989065-d72c517c-d9a0-4bd5-995a-72c44f4955e9.png)
	
Inside the folder, Today's date is created. so in this terictory some folders are available which is required for openlane.
	
	**cd 01.02_08.19 ( today)**
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215989310-fbc9ff9a-0b61-4c3f-a7bf-dba3796d83ce.png)
	
In the temp file, merged.lef file is available which was created in preparation time. if we open this merged.lef file, we get all the wire or layer level and cell level information.
	
	**cd tmp**
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215989833-26d87d1a-a54e-422a-be2d-f38d69920777.png)
	
	less merged.ref
	
![image](https://user-images.githubusercontent.com/123365818/215990017-c15e3022-ae2c-4aa0-b08d-ec4b542f04e8.png)

While, in the result folder is empty because till we have not run anything and in the report folder all the folders are there about synthesis, placement, floorplanning,cts,routing,magic,lvs.
	
	**cd results**
	
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/215992243-11c80cc4-782f-48a8-b6d7-61e3df11411e.png)
	
	**cd reports**
	
	ls -ltr

![image](https://user-images.githubusercontent.com/123365818/215990668-2b7bbf25-5b98-4acc-9503-7bf0ce64958a.png)
	
Now here also one config.tcl file is available similar like design folder. But this config.tcl file contains all default parameter taken by the run.
	
	**less config.tcl**
	
![image](https://user-images.githubusercontent.com/123365818/215997708-dbabaea5-6eaf-4127-8e69-3a591e34634e.png)
	
when we make some change in the origional configuration and then we run, for example if we make a change in core utilization in the floorplanning and then we run the floorplanning, at this time in the congig.tcl file, the core utility will change and by cross checking it we can check that the modification is reflected in the exicution or not.

Now, cmds.log file takes all the record of the commands, what we have fab.
	
	pdk information
	min max library info
	
	to look the command file
	**less cmds.log**
	
![image](https://user-images.githubusercontent.com/123365818/216001600-3127261c-b967-4ec2-ac8e-d1d3edba8d7d.png)
	
	Coming back to the openlane
	after preparation complete
	we can run the synthesis
Now coming to the openlane, we are going to run the synthesis. It will take some 3-4 mnts to run the synthesis and finally synthesis will complited.
	
	**run_synthesis**
	
	It take 2 to 3 minutes
	
![image](https://user-images.githubusercontent.com/123365818/216002594-af4cc725-e46c-4d6e-abb1-17ca2fcfab08.png)
	
	Successfully synthesis
	
![image](https://user-images.githubusercontent.com/123365818/216004700-cf966074-05c8-4cfd-a4bc-5cf4dc285a73.png)

Before run, we saw that the result folder is empty. but now, after running the synthesis, we can see that all the mapping have been done by ABC.
	
![image](https://user-images.githubusercontent.com/123365818/216371442-f953af10-a68c-466d-bcc9-3bcaef94501c.png)

	And in the report, we can see when the actual synthesis has done. and the actual statistics synthesis report is showing below, which is same as what we have seen before.
	
	cd results
	
	cd synthesis
	
	ls
	
less picorv32a.synthesis.v
	
![image](https://user-images.githubusercontent.com/123365818/216372361-bcac3c83-ecad-4e92-9f8e-e6491cf5ed9d.png)
	
less merged_unpadded.lef
	
![image](https://user-images.githubusercontent.com/123365818/216375660-da546ce9-70b2-42e6-8a62-6b1be13ee28b.png)



	
##Day 2
	
##Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells
	
### SKY130_D2_SK2 -Chip floorplanning considerations
	
####SKY_L1 - Utilization factor and aspect ratio
	
	**Defining the width and height of core and Die**
	
![image](https://user-images.githubusercontent.com/123365818/216350712-db0ddcf2-dd6f-4b32-9cb1-94f7e94716f2.png)

	let's begin with netlist( Netlist describes the connectivity of an electronic designs). Considering a netlist with 2 flops and 2 gates.
	
![image](https://user-images.githubusercontent.com/123365818/216350880-9917062c-aaa0-43f7-9626-616da276249c.png)
	
![image](https://user-images.githubusercontent.com/123365818/216351471-ffa5b0ce-63c9-47a8-8f8b-a06e7d20b4b4.png)

	
	lets giving the height and width of standerd cell is 1 unit. So, area of standerd cell is 1 square unit.
	And assuming the same area for the flip flops also.
	
![image](https://user-images.githubusercontent.com/123365818/216351584-009604df-56e0-4400-aea2-ef758dbbe2ce.png)


Now lets calculate the area occupied by the netlist on a silicon wafer by arranging them together. The total area occupied by netlist in silicon wafer is 4 square units.
	
![image](https://user-images.githubusercontent.com/123365818/216352266-56e4a9e6-7b6a-4b9f-b776-ccb434be3331.png)

	
A 'core' is the section of the chip where the fundamental logic of the design is placed.

A 'Die', which is consist of core, is small semiconductor material specimen on which the fundamental circuits is fabricated.

![image](https://user-images.githubusercontent.com/123365818/216352607-c39020ba-df7a-435c-9bca-66978a3a7a10.png)

If we put the 'arranged netlist' in the core, then whole core is occupied by netlist. that means utilization of core is 100%.
	
![image](https://user-images.githubusercontent.com/123365818/216353279-1925f7db-b8d3-42e7-afcf-ec5e588ecbf5.png)

**Utilization factor**
	
it is defined as, 'the area occupied by netlist' devided by the 'total area of core'.

so, in above case, the utilization factor is 1.

practically, we don't go with 100% uti;ization. practically utilization factor is about 50%-60% to add other extra cells (like buffer) in the core after netlist is placed.

**Aspect Ratio**
	
it is defined as (height)/ (width). here in above example the aspect ratio is 1.
	
Another Example,
	
![image](https://user-images.githubusercontent.com/123365818/216353574-3f9db10a-cf55-4623-b20a-d49b1474893c.png)
	
Utilization is 0.5 and the aspect ratio is also 0.5.

#### SKY_L2 - Concept of pre-placed cells

**Define locations of preplaced cells**
	
to define the preplaced cells, let's take a combinational logic i.e., mux, multiplier, clock devider, etc. and assuming that the output of the circuit is huge and assuming that the circuit has some 100k gates. so let devides in two blocks of 50k gates. 	
	This both blocks are implimented separatly. Now, extending the input and output pins from the both blocks. now, let's detached these box. we will black box the boxes and detached them. After black boxing, the upper portion is invisible from the top or invisible to the one , who is looking into the main netlist. now we make separate them out.
	
![image](https://user-images.githubusercontent.com/123365818/216355603-d60fe28f-622a-4a74-9cca-7c70f14ab8db.png)
	
This blocks are implemented in netlist once and then we can reuse it multiple time. Similarly, there are other modules or IPs also readily available.i.e.,memory, clock gating cell, comparater, mux. these all are part of the top level netlist.They recieve some signals, they perform some functions, they deliver the outputs but the functionality of the cell is implemented only once. That what we called as preplaced cells.

The arrangement of these ip's in a chip is refferd as floorplanning.These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called "preplacement cells".These cells are place din such fashion that, the placement and routing tool not touch the location of the cell.

![image](https://user-images.githubusercontent.com/123365818/216355861-f352dcdb-88b3-42d1-82e7-0d8cc0abb69d.png)

Let consider memory as a preplaced cells as a block 'a', block 'b' and block 'c'. Memory of any device is implemented once and reused multiple times. these preplaced cells are located as per the design bacckground. the location of the cells are never touched.

#### SKY_L3 - De-coupling capacitors
surround pre-placed cells with Decoupling capacitors
Let consider some circuit, which is part of the blocks which were defined above. When some gate (let consider AND gate) switched from 0 to 1 ot 1 to 0, considered amount of the switching current required because of small capacitance is available there. this capacitor should be completely charged to represent logic 1 and completly discharged to represent logic 0. the required amount of the charge is suplied from the Vdd and absorb from the Vss. during supplying the current, wire has some drop of voltage due to resistence and inductunce of the physical wire.	
	
![image](https://user-images.githubusercontent.com/123365818/216356320-bd877901-f750-4b39-b14b-e6ae1415a37f.png)

So, due to this if ideal logic 1 = 1 volt then here practically it can be less then 1 volt i.e., 0.97 volts (Vdd').
	
![image](https://user-images.githubusercontent.com/123365818/216356690-ea76b1c4-dfab-4c95-b845-f5ab28398eb4.png)

So, for any signal to be considered as Logic '0' and '1' in the NM low and NM high range. It is danger case.
	Noise Margin

![image](https://user-images.githubusercontent.com/123365818/216358817-cec293eb-ae17-4888-92c8-e3b9480772a6.png)
	
To solve this problem,, we have to put De-coupling capacitor in parallel with the circuit. 
Decoupling capacitor
	
![image](https://user-images.githubusercontent.com/123365818/216358224-9142e58c-3a0a-4d35-b440-a15fcfb7169a.png)

Every time the circuit switches, it draws current from Cd, whereas, the RL network is used to replacenish the charge into Cd.
	
![image](https://user-images.githubusercontent.com/123365818/216358911-59af7516-ee2e-4b49-935a-052cb69f458a.png)
	
#### SKY_L4 - Power Planning

	Demanding current in four macro
	Driver to Load	
![image](https://user-images.githubusercontent.com/123365818/216360287-2407a300-1576-4b2c-8b50-2c5afa267339.png)
	
	How to do power planning?

	Up to here, we have taken care of local communication. Now let consider that local circuitory as a black box and it can be repeat multiple times and power supply is also connected to all of them as shown below,

![image](https://user-images.githubusercontent.com/123365818/216361087-b591625d-fbf5-433b-a948-7b50c005748e.png)


Now 16 bit bus has to retain the same signal from driver to the load. so it should get the sufficient power from the supply. But at this bus, there is no de-coupling capacitor is available because it is not physible to put capacitor at all over the place. now, power supply is far away from the bus, that is why some drop between them will definalty occurs.
	
Let consider this 16 bit bus connected to inverter.
	
![image](https://user-images.githubusercontent.com/123365818/216361444-f44c7bbf-5275-4474-a755-5999f13ddd78.png)

 So, all capacitor are initially charged will get discharged and vice-versa due to inverter.
But the problem is occurs due to all capacitor is connected to the single ground. This will cause a bump in 'ground' tap point during discharging.
	
![image](https://user-images.githubusercontent.com/123365818/216362068-f449bd42-21ae-4fad-a080-cc8ed3fb0c87.png)
	
Same problem will occurse during the charging time also. at that time lowering of voltage occurse at 'Vdd' tap point.

![image](https://user-images.githubusercontent.com/123365818/216362301-ffe05ff1-f8f8-41f2-8523-6f77db01235d.png)

The solution of the problem is use multiple power supply. So, every block will take charge from neartest power supply and similarly dump the charge to the nearer ground. this type of power supply is called mesh.
	
![image](https://user-images.githubusercontent.com/123365818/216362834-2e3c0c63-be67-4b2d-8130-831ec4b5e4af.png)

	
	And the power planning is shown below,
![image](https://user-images.githubusercontent.com/123365818/216363015-fecad710-7058-4cba-8cd8-3eb2e1fb96ed.png)
	

#### SKY_L5 - Pin placement and logical cell placement blockage	
Pin Placement
Lets take below designs for example that needs to implemented.	

![image](https://user-images.githubusercontent.com/123365818/216365564-b38bdefd-c5a9-4c91-83e8-633fcdc4985f.png)

Both the sections has different inputs like Din1 and Din2 and operated from different clocks like clock 1 and clock 2. along with that we have preplaced cells as well. So, basically now we have 4 input ports and 3 output ports.
	

let's have one more design that needs to be implemented. this types of circuits are very much helpful to understand the timing analysis of inter clocks.

![image](https://user-images.githubusercontent.com/123365818/216366421-6aa48ebb-c80f-4f8e-a535-73447044a0c3.png)

	preplaced cell Block C
	
![image](https://user-images.githubusercontent.com/123365818/216366749-7335f6c9-7c00-4069-839f-c27f55d7bab9.png)


Now complete design becomes like given below which has 6 input ports and 5 output ports. it is called the 'Netlist'.
	
![image](https://user-images.githubusercontent.com/123365818/216369269-881effe3-b473-4489-818c-508af465910b.png)


Let's put this netlist in the core which we have designed before and let's try to fill this empty area between core and die with the pin information. The frontend team who decides the netlist input and output and the backend team who done the pin placements. So according to the pin placements, we have to locate the preplaced blocks nearer to the inputs of the preplaced blocks.

![image](https://user-images.githubusercontent.com/123365818/216368847-262e22d9-0f5a-4184-8992-e1607cc67836.png)

	
Here one thing that we noticed is that clock-in and clock-out pins are bigger in size as compared to input and output pins. reason behind this is that, input clocks are conntinuously provides the signal to the every elements of the chip and output clock should out the signal as fast as possible. So, we need least resistance path for the clocks inputs and clocks outputs. So, bigger the size, lower the resistance.

One more thing is need to take care about is that, this pin placement area is blocked for routing and cell placements. so we nned to do logical cell placement blockage. this blockage is shoown in above image in between pins.

So, floor plan is ready for Placement and Routing step.	

#### SKY_L6 - Steps to run floorplan using OpenLANE
	
	in the openlane, 
	run_floorplan
Before doing floor plann, we required some switches for the floorplanning. these we can get from the configuration from openlane.
	
	cd configuration
	ls -ltr
![image](https://user-images.githubusercontent.com/123365818/216378049-d7e68d8f-99a1-4ed9-8087-ac5d0bfed702.png)
	
	less README.md
	
![image](https://user-images.githubusercontent.com/123365818/216379083-e42efe3a-d0e3-4fc4-baaf-8bda19bd3175.png)

	
less floorplan.tcl
	
![image](https://user-images.githubusercontent.com/123365818/216380173-44fe6497-fb60-41a7-831a-87f4b620974a.png)
	
Here we can see that the core utilization ratio is 50% (bydefault) and aspect ratio is 1 (bydefault). similarly other information is also given. But it is not neccessory to take these values. we need to change these value as per the given requirments also.

Here FP_PDN files are set the power distribution network. These switches are set in the floorplane stage bydefault in OpenLANE.

	Go to the design file, and open config.tcl
	cd ..
	cd Designs
	cd picorv32a
	ls -ltr
	
![image](https://user-images.githubusercontent.com/123365818/216381314-4d4c3427-62de-49fb-9c88-d2b29292b428.png)
	
less config.tcl
	
![image](https://user-images.githubusercontent.com/123365818/216381635-5a0fb196-b7ea-425c-8701-ac9a01ae48d7.png)
	cd runs
	cd 01-02_08-19/ .....Dates
	less config.tcl
	
![image](https://user-images.githubusercontent.com/123365818/216383023-1a57794e-d30e-4b24-9eea-22ad68b27716.png)
	
![image](https://user-images.githubusercontent.com/123365818/216383153-2ec8354d-cce2-4a00-a7c7-59f6dac4fa25.png)


Here, (FP_IO MODE) 1, 0 means pin positioning is random but it is on equal distance.

In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).

Now we see, with this settings how floorplan run.
	
In the bash window
	
	run_floorplan
	
![image](https://user-images.githubusercontent.com/123365818/216384452-7be3938f-d784-48a6-8a58-9c14d4bd4a54.png)

	
#### SKY_L7 - Review floorplan files and steps to view floorplan
      
	In the run folder, we can see the connfig.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.
	
	cd runs
	
	cd 01-02_08-19/ 
	
	ls -ltr
	
	cd logs/floorplan
	
![image](https://user-images.githubusercontent.com/123365818/216385616-2c8ba300-45fd-49ce-b23b-cc4b4f3668bc.png)
	
	less 4-ioPlacer.log
	
![image](https://user-images.githubusercontent.com/123365818/216388273-30be6c44-ef19-481f-8341-40716621fa4a.png
	
	cd ../../
	ls
	less config.tcl
	
![image](https://user-images.githubusercontent.com/123365818/216388933-cec297c7-b626-4fb6-94c2-d421a6af681f.png)

here we can see that, the core utilization is 35%, aspect ratio is 1 and core margin is taken as 0. while in default the core utilization is 50%. this is the issue. because this design is override the system. but it is the taken from PDK varient.tcl file. so priority vise it is true.

To watch how floorplane looks, we have to go in the results. in the result, one def( design exchange formate) file is available. if we open this file, we can see all information about die area (0 0) (660685 671405), unit distance in micron (1000). it means 1 micron means 1000 databased units. so 660685 and 671405 are databased units. and if we devide this by 1000 then we can get the dimensions of chips in micrometer.
	
	cd ..
	cd ..
	cd results/floorplan
	ls -ltr
	less picorvs2a_floorplan.def
	
![image](https://user-images.githubusercontent.com/123365818/216387768-5521d282-5862-4c0c-af2f-0d138290876d.png)
	
	To see the actual layout after the flow, we have to open the **magic** file by adding the command 
**magic -T /home/nikson/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def**

![image](https://user-images.githubusercontent.com/123365818/216392389-84c4ee7e-7ec4-4b3f-98b2-43d8d2c6707f.png)

And then after pressing the enter, Magic file will open. here we can see the layout.	
	
![image](https://user-images.githubusercontent.com/123365818/216392213-63760ed7-0822-4f84-98bc-6f4a8c6334ad.png)


### SKY130_D2_SK2 - Library Binding and Placement
	
#### SKY_L1 - Netlist binding and initial place design
	
** Bind netlist with physical cells

	Taking netlist as what we taken before,
	
![image](https://user-images.githubusercontent.com/123365818/216430251-9d5de493-558e-4f2b-9a2e-d437aa828dad.png)
	
Here, we can see that every gate or flip-flops have a shape to understand the functionality of the element.
	
![image](https://user-images.githubusercontent.com/123365818/216430900-875080a7-9dc1-43ee-a94e-52c72a298476.png)

But practically, this cells are square or rectangular boxes which has internally some logic to perform. 
	
![image](https://user-images.githubusercontent.com/123365818/216430966-efbd0fa5-2493-4d9a-af1b-8e8d94be7e72.png)

So, here we are taking all the elements from netlist and giving them a perfact height and width with perticular dimention. 
	
![image](https://user-images.githubusercontent.com/123365818/216431343-b65068e2-4c4b-4907-82d0-39b0a8c278a5.png)

These all cells together are called 'self'. And this self are stored in the lybrary. Library have all the innformation about all the blocks, like height, width , time delay, conditional innformation, etc. 

![image](https://user-images.githubusercontent.com/123365818/216431544-b775044e-ed51-4d2e-86f0-11b870637363.png)

library also have a option for the similar cells (with same functionality) like this with different height and width. According to our space available at floorplanning we can choose out of them.
	
![image](https://user-images.githubusercontent.com/123365818/216431646-d76b7f31-17e1-45f8-9769-87a7724cbfe1.png)

After giving size and shape to each and every box, next step is to take the boxes or element from library and placed in the floorplan. 
This is called placements of the cells.
	
According to the design of the netlist, we have to put physical blocks in the floorplan which we have design before.
	
![image](https://user-images.githubusercontent.com/123365818/216431958-db66c6eb-9908-4bce-86ea-9be4926fd371.png)


	
![image](https://user-images.githubusercontent.com/123365818/216432090-589e7dc8-4bdb-470d-b80e-d510189ab310.png)

Put all the blocks according to the input and output of that perticular blocks.
	
![image](https://user-images.githubusercontent.com/123365818/216432284-a90fc34c-7411-4eec-85e3-ad98e3a20fb4.png)
	
Data input 1 and output 1
	
![image](https://user-images.githubusercontent.com/123365818/216432636-a019c4ba-84fb-46f4-b1ee-cbddf98c9380.png)

Data input 2 and output 2
	
![image](https://user-images.githubusercontent.com/123365818/216432830-b16f88bd-c8d2-4b39-adb0-597acafac97a.png)
	
up to here we have done stage one and stage two placement. Now we will going for stage 3 and 4. here we have to place FF1 of stage 3 nearer to the Din3 and FF2 of stage 3 nearer to the Dout3. But Din3 and Dout3 are at somme distance from eachother. 

data out 3
	
![image](https://user-images.githubusercontent.com/123365818/216433017-ec0835cc-6be7-4e35-96b8-b44c2d28ae81.png)

Same thing is there for FF1 and FF2 of stage 4. Let's we placed these all element in such manner that all elements are closed to it's input and output pins.
Data out 4
	
![image](https://user-images.githubusercontent.com/123365818/216433197-c9876c41-2fce-4b5a-a0c2-b92eb18e5e65.png)

But, the distance of FF1 of Stage 4 and Din4 is still far them others. By optimizing the placement, we can solve this problem.
	
#### SKY_L2 - Optimize placement using estimated wire-length and capacitance

** Optimize Placement
	
As we seen that the distance from Din2 to FF1 of stage 2 is higher. 
	
![image](https://user-images.githubusercontent.com/123365818/216433966-358a7bdf-8447-4bac-98a7-6ac2cfaa85ce.png)

so if we connect the wire between them then resistance and capacitance of the wire comes in to the picture. and due to this the signal integrity can not maintain.

To maintain the integrity of the signal out from Din2 to FF1, we have to put some repeaters like buffers on between Din2 and FF1. But it will cause of loss of area.
	
![image](https://user-images.githubusercontent.com/123365818/216434242-95e66a4b-e0da-4a9c-acce-954e9e37aca0.png)

In the stage 1, there is no need of any repeater to transmit the signal. 
	
![image](https://user-images.githubusercontent.com/123365818/216434395-ed47b3b6-fc16-49c8-bf23-230fa39ff9e5.png)

But in stage 2, due to high distance, the lenth of wire is high and signal is not transmitted in perticular range. so we required repeater. sender to buffer.
	
#### SKY_L3 - Final placement optimization
	
Similar as stage 2, in Stage 3 also we required the buffer between gate 2 and FF2.
	
![image](https://user-images.githubusercontent.com/123365818/216434596-3e22a8ad-507a-4f32-b43a-1fda7691acdc.png)
	
Reproduce the same signal . Stage 4 is bit tricky as compared to other stages.
	
![image](https://user-images.githubusercontent.com/123365818/216435466-523c103d-0e83-49cd-b25f-d49e561aef31.png)
	
	Now we have to check that, what we have done is correct or not. For that we need to do Timing analysis by considering the ideal clocks and according to the data of analysis, we will understand that, the placement is correct or not.

#### SKY_L4 - Need for libraries and characterization
	
**Library charactorization and modelling**

	In whole IC design, we have to go through synthesis, floor/power planning, placement, routing , STA. 
	
Logic Synthesis
	
![image](https://user-images.githubusercontent.com/123365818/216436066-cdedd1a3-dfa5-4120-b0af-3b908f629480.png)

Floor Planning
	
![image](https://user-images.githubusercontent.com/123365818/216436209-e207f234-21cc-4708-a164-0680da2e2ef0.png)

Placement & CTS
	
![image](https://user-images.githubusercontent.com/123365818/216436389-c765f982-318f-44bb-84e0-cd5df050b468.png)

Routing
	
![image](https://user-images.githubusercontent.com/123365818/216436523-1b983bd3-7156-4028-9e4a-d3ceaea7b005.png)

STA

![image](https://user-images.githubusercontent.com/123365818/216436717-daa8b4ca-940d-49bb-a17b-c829dcf1e9f6.png)

In all this steps one thing remain common, which is "Gates or Cells". That is where the library charactorization becomes very important.
	
Gates or Cells
	
![image](https://user-images.githubusercontent.com/123365818/216436871-52cda67f-fbcb-4b73-b4d8-f225297875be.png)

Library
	
![image](https://user-images.githubusercontent.com/123365818/216437017-be45a140-23ca-4baf-b463-63f1601e1099.png)
	
#### SKY_L5 - Congestion aware placement using RePlAce
	
	
	
### SKY130_D2_SK3 - Cell design and characterization flows

#### SKY_L1 - Inputs for cell design flow
	
**Cell design flow**

![image](https://user-images.githubusercontent.com/123365818/216437791-36271765-c301-4b0c-b033-1e6a3b440f89.png)
	
As we know that standerd cells are placed in the library.  
	
![image](https://user-images.githubusercontent.com/123365818/216437937-becde403-32da-47e0-80ef-d2a3faea2777.png)
	
And in the library many other cells are available which have same functionality but the size is different.
	
![image](https://user-images.githubusercontent.com/123365818/216438540-edd89d95-34fc-4615-bf1a-cd1e08617449.png)

As size is different the parameters like hVt, Ivt also different for each standerd cells.
	
![image](https://user-images.githubusercontent.com/123365818/216438628-f187da5d-60c8-44d2-9885-e4de2ed2a29c.png)


If we take one of the standerd cells called inverter, it has their own design flow by this it can be understandable to EDA tool.
	
![image](https://user-images.githubusercontent.com/123365818/216438846-3ff83088-bfb2-41e0-8e4b-8de4cb77948a.png)

The cell design flow is devided into three part.

	* Inputs
	
	* Design steps
	
	* Outputs
**Inputs**
inputs required for cell design is PDKs, DRC and LVS rules SPICE models, library and user defined specs.
	
![image](https://user-images.githubusercontent.com/123365818/216439061-848302b8-461c-496f-8445-16cf32725757.png)
	
![image](https://user-images.githubusercontent.com/123365818/216439266-0661e012-3044-4247-a3fd-5b0f3eca933f.png)

![image](https://user-images.githubusercontent.com/123365818/216439514-221bf5e7-626c-4581-8a7c-ec8dcd27aadf.png)

![image](https://user-images.githubusercontent.com/123365818/216439552-a7e0aeb5-f232-459c-ba33-93a1154bac0f.png)

#### SKY_L2 - Circuit design step


**Design steps**

Steps are circuit design, layout design, characterization

User defined specification

	Supply Voltage, Cell height
	
![image](https://user-images.githubusercontent.com/123365818/216440183-95d8a299-9917-4dc6-9527-86ef6e8dacea.png)

	Metal Layers
	
![image](https://user-images.githubusercontent.com/123365818/216440238-c1df2d15-fd6e-4f4e-832d-489756b30540.png)

**Outputs**

	The typical output what we get from the circuit design is CDL(circuit description language) file,GDSII,LEF,extracted spice netlist(.cir).

Layout design steps
	
implement function
	
Circuit design
	
![image](https://user-images.githubusercontent.com/123365818/216441132-c449697f-7668-41fd-9e80-dc7f05abc0fe.png)
	
Derive the NMOS and PMOS network graph
	
![image](https://user-images.githubusercontent.com/123365818/216441760-74a03fcb-a602-43dc-ae6e-97e28e3e65db.png)


Layout Design
	
Obtain the Euler's path
	
![image](https://user-images.githubusercontent.com/123365818/216441935-6f17e121-f424-485a-ad7b-f4b24d43d613.png)

Stick diagram
	
![image](https://user-images.githubusercontent.com/123365818/216442040-b1b9a2e9-8d37-440d-8a36-09891d9ba630.png)

Convert stick diagram into proper layout
	
![image](https://user-images.githubusercontent.com/123365818/216442173-26a7ba89-c8dc-42ae-87ec-04018915724f.png)

After layout design, we have to ecxtract the layout and characterize it. In characterization step, we can get the information about Timing, Noice,power.libs and function.
	
![image](https://user-images.githubusercontent.com/123365818/216442534-35a87900-3789-4feb-a13b-10c76b5da1cc.png)

#### SKY_L4 - Typical characterization flow
**Characterization Flow**

	
![image](https://user-images.githubusercontent.com/123365818/216442962-6b4a80d2-9b06-405e-8e92-2303e3ef58a7.png)
	
As of now, from the circuit design and layout design, we have final layout of buffer cell. where two buffers are connected in series with each other.

![image](https://user-images.githubusercontent.com/123365818/216443033-2cfdd0fc-59d5-4c2e-ae72-123f1f609ad9.png)

	Buffer
	
![image](https://user-images.githubusercontent.com/123365818/216443235-25f1f1f3-3a1e-4b48-a65e-a088fe00edf9.png)

	
Now steps of flow is:

1.Read the model file
	
2. read the extracted spice netlist
	
3. reconize the behavior of buffer
	
4. Read the subcircuit of the inverter
	
5. Ateched the neccessory power source
	
6. Apply the stimulus
	
7. Provide the necessory of output capacitance
	
8. Provide the necessory simulatin command
	
This all steps we have to give in "GUNA" software. and this software will give the timing, noise, power.libs and functions.
	
![image](https://user-images.githubusercontent.com/123365818/216443405-67ebe0a1-36ec-4005-812a-299bb0b76526.png)

![image](https://user-images.githubusercontent.com/123365818/216443795-025ba6b4-86e3-41cf-96b2-1471c480cd39.png)

![image](https://user-images.githubusercontent.com/123365818/216443825-b57ad95a-6485-4fdb-9bf2-a79060458eb2.png)

![image](https://user-images.githubusercontent.com/123365818/216443909-2e5da8e0-bd61-4e25-ad07-2552655b3bc9.png)

![image](https://user-images.githubusercontent.com/123365818/216443983-430daf61-7f2c-4dd3-aa3d-0914fd98c6e2.png)
	
### SKY130_D2_SK4 - General timing characterization parameters

#### SKY_L1 - Timing threshold definitions
	
**Timing threshold defination**
	
![image](https://user-images.githubusercontent.com/123365818/216444784-97b6997e-ca41-42d7-ae8e-cc84ca52f113.png)

	
Let we take the waveform from the output of the first buffer and it will be input of the second buffer and taking output of the second buffer also.
	
![image](https://user-images.githubusercontent.com/123365818/216445037-f2c139b1-b526-4fb2-b23a-b9284068557c.png)

**slew_low_rise_threshold**
	
here low means nearer to the ground, and rise tresold means we want to measer the slope of the increasing graph. typical value of slew low rise thr is around 20-30%.

![image](https://user-images.githubusercontent.com/123365818/216445219-39ad7cf2-c297-4457-9bf9-574d038e7ec5.png)

**slew_high_rise_thr**
	
same as above, high means nearer to high value.
	
![image](https://user-images.githubusercontent.com/123365818/216445303-3e27b403-7ca1-44b9-b76c-e3dd1760648c.png)

whenever we want to calculate the slew, take the point at 20% from the low and take the point at 20% from the high. according to these point, take the time data and the time difference between them will helps to calculate the slew.

**slew_low_fall_thr**
	
![image](https://user-images.githubusercontent.com/123365818/216445929-5bd71110-ccf6-45ed-a4c0-a469155682dc.png)
	
**slew_high_fall_thr**

![image](https://user-images.githubusercontent.com/123365818/216446056-041058ac-d2d4-4db9-b851-c985c6fff778.png)

NOw, taking the waveform of input stimulus which is input of the first buffer and with that taking output of the first buffer.

Similar as a slew, thresolds are for delay also available. for that same as slew, we have to take some rise and fall points from the waveforms. this tresolds are almost 50%.

**in_rise_thr**
	
![image](https://user-images.githubusercontent.com/123365818/216446187-3bde77f6-6baa-4319-a20d-509bbce3aa39.png)

**out_rise_thr**

![image](https://user-images.githubusercontent.com/123365818/216446406-24c28667-9811-4fdc-a8ce-b3a1f7b0d4f0.png)
	
**in_fall_thr**	
	
![image](https://user-images.githubusercontent.com/123365818/216446863-5292d604-9faa-4b93-a998-1af0e18cd941.png)

	
**out_fall_thr**
	
![image](https://user-images.githubusercontent.com/123365818/216446622-72cb82b9-eb3f-4175-9511-93ac9478d8ea.png)

#### SKY_L2 - Propagation delay and transition time
	
propogation delay
	
![image](https://user-images.githubusercontent.com/123365818/216447363-c60f65ec-bdc9-4133-bdbe-98c055067606.png)

let's take the same setup for understand the propogation delay. **Time delay = Time(out_thr)-time(in_thr)**
	
![image](https://user-images.githubusercontent.com/123365818/216447556-0f8d0348-8653-41dc-91c0-e525f2f8ff24.png)


Let's take waveform on which we can apply above formula.
	
![image](https://user-images.githubusercontent.com/123365818/216447744-aeb92af6-60c7-47d7-885a-9660cb25fdec.png)

	
In any case if thresold point move at the top, at that time we get negative delay because output comes before input. so reason behind the negative delay is the poor choice of the tresold points. which is not acceptable. so, choosing the thresold point is very important.
	
![image](https://user-images.githubusercontent.com/123365818/216448479-bcdd75bc-f46f-44d8-8fd1-66f1d5a7e0c5.png)
	
negative delay

Taking another example where the wire delay is very high because of high distance between two elements. so, here by choosing correct thresold point then also we get the negative delay.	

![image](https://user-images.githubusercontent.com/123365818/216448075-c3138912-b768-4ac2-a155-3936d2348b24.png)
	
**Transition time**
	
transition time = time(slew_high_rise_thr)- time(slew_low_rise_thr)

or

transition time = time(slew_high_fall_thr)- time(slew_low_fall_thr)

let's take waveform for understand the slew calculation.
	
slew rise
	
![image](https://user-images.githubusercontent.com/123365818/216449357-863c4fea-0ed0-416c-956e-61b846366a87.png)
	
slew fall
	
![image](https://user-images.githubusercontent.com/123365818/216449386-18f21cba-c912-4ba5-94f4-d58970f2164c.png)
	
Threshold Definition
	
![image](https://user-images.githubusercontent.com/123365818/216449702-e16fc22c-8561-4190-8bd4-eaeb3529b140.png)


Input slew /Output Slew	
	
![image](https://user-images.githubusercontent.com/123365818/216449200-0a497609-b085-464a-9cf8-1ffed5530169.png)



	



	









	

	

	

   




	












