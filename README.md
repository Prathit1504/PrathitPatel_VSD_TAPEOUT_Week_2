# RISC-V Reference SoC Tapeout Program - Week 2

## BabySoC Fundamentals & Functional Modeling

*Date: September 29, 2025*

[![RISC-V](https://img.shields.io/badge/RISC--V-Reference%20SoC-blue)](https://riscv.org/)
[![Verilog](https://img.shields.io/badge/HDL-Verilog-green)](https://en.wikipedia.org/wiki/Verilog)
[![Simulation](https://img.shields.io/badge/Tool-Icarus%20Verilog-orange)](http://iverilog.icarus.com/)
[![Status](https://img.shields.io/badge/Week%202-Complete-brightgreen)](https://github.com/Vansh0917/RISC-V-Reference-SoC-Tapeout-Program_VLSI_Week_0)

## Table of Contents

1. [Program Overview](#program-overview)
2. [Week 2 Objectives](#week-2-objectives)
3. [Repository Structure](#repository-structure)
4. [Part 1 - Theory: SoC Fundamentals](#part-1---theory-soc-fundamentals)
5. [Part 2 - Laboratory: Functional Modeling](#part-2---laboratory-functional-modeling)
6. [VSDBabySoC Architecture](#vsdbabysoc-architecture)
7. [Simulation Results](#simulation-results)
8. [Tools and Environment](#tools-and-environment)
9. [Deliverables](#deliverables)
10. [Known Issues](#known-issues)
11. [References](#references)
12. [Conclusion](#conclusion)

---

## 📘 Program Overview – Week 2

Building on the foundation from **Week 0**, Week 2 emphasizes **System-on-Chip (SoC) fundamentals** and **functional modeling** using the **VSDBabySoC platform**. This stage bridges theoretical knowledge with hands-on skills, laying the groundwork for the complete **20-week tapeout journey**.

### 🔧 VSDBabySoC Components

* **RVMYTH** – RISC-V based processor core
* **PLL** – Phase-Locked Loop for clock generation
* **DAC** – 10-bit Digital-to-Analog Converter
* **Integration Fabric** – System interconnections

---

## 🎯 Week 2 Objectives

### Part 1 – Theoretical Understanding

* Master **SoC design principles** and fundamental concepts
* Understand **component integration** and system-level architecture
* Analyze **educational value** of the VSDBabySoC platform
* Explore **mixed-signal design considerations**

### Part 2 – Practical Implementation

* Setup & configure **EDA simulation environment**
* Perform **pre-synthesis functional verification**
* Execute **waveform analysis** with GTKWave
* Document detailed **simulation results**
* Attempt **post-synthesis simulation (GLS)**

---

# Part 1 - Theory: SoC Fundamentals

# System-on-Chip (SoC) Fundamentals and VSDBabySoC Learning Analysis

## Executive Summary

This comprehensive analysis explores the fundamental concepts of System-on-Chip (SoC) design and demonstrates how the VSDBabySoC serves as an effective educational platform within the RISC-V Reference SoC Tapeout Program. Building upon foundational knowledge from Week 1, this document establishes the theoretical framework necessary for understanding complex integrated circuit design methodologies and their practical implementation.

## Table of Contents

1. [Introduction to System-on-Chip Design](#introduction-to-system-on-chip-design)
2. [SoC Architecture and Components](#soc-architecture-and-components)
3. [VSDBabySoC as an Educational Platform](#vsdbabysoc-as-an-educational-platform)
4. [Functional Modeling in SoC Design](#functional-modeling-in-soc-design)
5. [Design Verification Methodologies](#design-verification-methodologies)
6. [Integration and Interconnect Strategies](#integration-and-interconnect-strategies)
7. [Mixed-Signal Design Considerations](#mixed-signal-design-considerations)
8. [Educational Value and Learning Outcomes](#educational-value-and-learning-outcomes)
9. [Industry Relevance and Applications](#industry-relevance-and-applications)
10. [Conclusion and Future Perspectives](#conclusion-and-future-perspectives)

---

## 1. Introduction to System-on-Chip (SoC) Design

### 1.1 Definition and Core Principles

A **System-on-Chip (SoC)** represents the peak of integrated circuit innovation, consolidating numerous functional blocks—traditionally housed in discrete chips—into a single silicon substrate. This paradigm shift has transformed electronics by delivering unmatched levels of **integration, performance, power efficiency, and compactness**.

The foundation of SoC design lies in **functional convergence**—strategically embedding processing, memory, communication, and control elements into one chip. Compared to conventional multi-chip implementations, this approach offers:

* **Simplified Systems** – fewer external components and interconnects
* **Higher Performance** – reduced signal delay and parasitic losses
* **Improved Power Efficiency** – optimized domains and lower I/O power usage
* **Cost Reduction** – single-fab manufacturing and lower assembly needs
* **Greater Reliability** – fewer solder joints and mechanical failure points

---

### 1.2 Historical Development and Market Drivers

The rapid rise of SoC technology stems from technological progress coupled with market requirements:

**Technological Catalysts**:

* Moore’s Law scaling enabling dense transistor integration
* Advanced semiconductor process nodes (65nm → 28nm and beyond)
* Sophisticated EDA tools for automation and verification
* Expanding ecosystems of reusable IP (Intellectual Property) blocks

**Market Forces**:

* Mobile computing demanding compact, energy-efficient solutions
* Cost-sensitive consumer electronics
* Automotive safety and reliability compliance
* IoT growth requiring highly integrated and miniaturized designs

---

### 1.3 Abstraction Levels in SoC Design

SoC development spans multiple hierarchical layers, each supporting distinct design and verification tasks:

* **System Level** – high-level algorithms and architectural specification
* **Behavioral Level** – functional models without hardware constraints
* **Register Transfer Level (RTL)** – cycle-accurate descriptions of data flow
* **Gate Level** – Boolean logic mapped to hardware
* **Transistor Level** – circuit behavior at device granularity
* **Layout Level** – physical mask geometries for fabrication

---

## 2. SoC Architecture and Key Components

### 2.1 Processing Subsystems

Modern SoCs integrate heterogeneous compute units tailored for varied workloads:

**Central Processing Units (CPUs)**:

* Application processors for general-purpose tasks
* Real-time processors for deterministic performance
* Microcontrollers for supervisory control

**Specialized Accelerators**:

* **GPUs** for parallel graphics and compute workloads
* **DSPs** optimized for signal processing tasks
* **NPUs** tailored for AI/ML inference acceleration

---

### 2.2 Memory Subsystem Design

The memory hierarchy is central to SoC efficiency in speed and power:

**On-Chip Storage**:

* Multi-level caches (L1–L3) for low-latency access
* Tightly Coupled Memory (TCM) for predictable response
* Register files embedded within cores

**External Interfaces**:

* DRAM controllers (DDR3/DDR4/LPDDR) for main memory
* Flash controllers for non-volatile storage
* Memory Management Units (MMUs) for virtual memory support

---

### 2.3 Interconnect Fabric

The communication backbone governs throughput and scalability:

**Bus Architectures**:

* **AHB** for high-speed transfers
* **APB** for low-power peripherals
* **AXI** for advanced system-level connectivity

**Network-on-Chip (NoC)**:

* Packet-switched data movement for scalable topologies
* Quality-of-Service (QoS) for real-time guarantees
* Energy-aware routing schemes

---

### 2.4 Peripheral and I/O Subsystems

Peripheral blocks ensure system versatility and external communication:

**Communication Interfaces**:

* USB for host/device support
* Ethernet for wired networking
* Wireless protocols (Wi-Fi, Bluetooth, cellular)

**Sensor & Actuator Interfaces**:

* ADCs for digitizing sensor inputs
* DACs for analog output control
* PWM generators for actuators and audio

**Human-Machine Interfaces (HMI)**:

* Display controllers for visual output
* Audio codecs for high-fidelity sound
* Touch controllers for interactive input

---

## 3. VSDBabySoC as an Educational Platform

### 3.1 Design Philosophy and Educational Objectives

The VSDBabySoC has been specifically architected as an educational platform that distills complex SoC design principles into a comprehensible yet realistic implementation. Its design philosophy encompasses several key educational objectives:
<img width="2270" height="1260" alt="image" src="https://github.com/user-attachments/assets/685e2589-7e71-4f62-aa08-541c8d2704b5" />


**Complexity Management:**
The platform maintains essential SoC characteristics while avoiding overwhelming complexity that might obscure fundamental concepts. This balance enables students to grasp core principles without becoming lost in implementation details.

**Industry Relevance:**
Despite its simplified nature, VSDBabySoC incorporates industry-standard interfaces, protocols, and design methodologies, ensuring that learning outcomes translate directly to professional practice.

**Progressive Learning:**
The modular architecture supports incremental complexity introduction, allowing students to master individual components before understanding their integration.

### 3.2 Core Component Analysis

**RVMYTH Processor Core:**
The RISC-V based RVMYTH processor serves as the computational heart of the VSDBabySoC, demonstrating:
- Instruction fetch, decode, and execution pipelines
- Register file organization and management
- Arithmetic Logic Unit (ALU) operations
- Memory interface protocols

**Phase-Locked Loop (PLL):**
<img width="885" height="535" alt="image" src="https://github.com/user-attachments/assets/83cd88b6-8e51-44ca-bc1f-914d28c3f54f" />

The integrated PLL demonstrates critical clock management concepts:
- Reference clock multiplication and division
- Jitter reduction and clock stability
- Power-efficient clock distribution
- Synchronous system design principles

**Digital-to-Analog Converter (DAC):**
<img width="600" height="556" alt="image" src="https://github.com/user-attachments/assets/cbaef7ed-7cec-4aec-9060-43cf2a4cb619" />

The 10-bit DAC illustrates mixed-signal integration challenges:
- Digital control interface implementation
- Analog output generation techniques
- Resolution and accuracy considerations
- System-level analog/digital interaction

### 3.3 Integration Architecture

The VSDBabySoC integration architecture demonstrates several critical SoC design patterns:

**Hierarchical Design Methodology:**
- Top-level system integration
- Module-level functional implementation
- Clear interface definition and documentation

**Clock Domain Management:**
- Single-clock synchronous design approach
- Reset distribution and initialization sequences
- Timing closure considerations

**Signal Integrity:**
- Proper signal routing and termination
- Noise isolation between analog and digital sections
- Power supply decoupling strategies

## 4. Functional Modeling in SoC Design

### 4.1 Modeling Abstraction and Verification Strategy

Functional modeling represents a critical phase in SoC design, bridging the gap between system specification and detailed implementation. This abstraction level focuses on behavioral accuracy while abstracting timing and implementation details.

**Key Modeling Objectives:**
- Algorithm validation and refinement
- Architecture exploration and optimization
- Early software development enablement
- System-level performance analysis

### 4.2 Verification Methodology

Comprehensive verification ensures functional correctness across all abstraction levels:

**Simulation-Based Verification:**
- Directed test scenarios for specific functionality
- Constrained random testing for coverage enhancement
- Assertion-based verification for property checking

**Formal Verification:**
- Mathematical proof of critical properties
- Equivalence checking between abstraction levels
- Model checking for complex system behaviors

### 4.3 Testbench Architecture and Stimulus Generation

Effective verification requires sophisticated testbench architectures:

**Stimulus Generation:**
- Realistic input patterns reflecting actual usage scenarios
- Corner case identification and systematic exploration
- Protocol compliance verification

**Response Checking:**
- Golden reference model comparison
- Functional coverage analysis
- Performance metric extraction

## 5. Design Verification Methodologies

### 5.1 Multi-Level Verification Strategy

SoC verification employs a comprehensive multi-level approach:

**Unit-Level Verification:**
- Individual component functional verification
- Interface protocol compliance checking
- Boundary condition testing

**Integration-Level Verification:**
- Component interaction verification
- System-level data flow validation
- Performance characteristic analysis

**System-Level Verification:**
- End-to-end functionality validation
- Use case scenario execution
- System stress testing

### 5.2 Verification Tools and Methodologies

**Hardware Description Language (HDL) Simulation:**
- Icarus Verilog for behavioral simulation
- ModelSim for advanced debugging capabilities
- VCS for high-performance simulation

**Waveform Analysis:**
- GTKWave for signal visualization
- Timing diagram generation and analysis
- Debug capability enhancement

## 6. Integration and Interconnect Strategies

### 6.1 System Integration Challenges

SoC integration presents unique challenges requiring systematic approaches:

**Timing Closure:**
- Clock domain crossing management
- Setup and hold time verification
- Clock skew minimization

**Power Management:**
- Power domain isolation and control
- Dynamic voltage and frequency scaling
- Leakage current optimization

### 6.2 Interface Design and Protocol Implementation

**Standard Interface Adoption:**
- AXI/AHB protocol implementation
- GPIO configuration and control
- Interrupt handling mechanisms

**Custom Interface Design:**
- Application-specific protocol development
- Performance optimization strategies
- Compatibility maintenance

## 7. Mixed-Signal Design Considerations

### 7.1 Analog-Digital Integration Challenges

Mixed-signal SoCs require careful consideration of analog-digital interactions:

**Noise Isolation:**
- Substrate noise coupling minimization
- Supply noise rejection enhancement
- Switching noise reduction strategies

**Power Supply Design:**
- Separate analog and digital supply domains
- Voltage regulator integration
- Decoupling capacitor placement optimization

### 7.2 Signal Integrity and Performance

**High-Speed Signal Design:**
- Transmission line effects consideration
- Signal termination strategies
- Cross-talk minimization techniques

**Analog Performance Optimization:**
- DAC linearity and accuracy enhancement
- ADC noise performance optimization
- Reference voltage stability

## 8. Educational Value and Learning Outcomes

### 8.1 Skill Development Framework

The VSDBabySoC educational platform develops multiple competency areas:

**Technical Skills:**
- HDL coding proficiency (Verilog/SystemVerilog)
- EDA tool utilization expertise
- Verification methodology understanding
- Debugging and problem-solving capabilities

**System-Level Thinking:**
- Architecture exploration and trade-off analysis
- Integration complexity management
- Performance optimization strategies
- Power and area efficiency considerations

**Professional Skills:**
- Documentation and communication
- Project management and scheduling
- Collaboration and teamwork
- Continuous learning and adaptation

### 8.2 Learning Progression and Assessment

**Progressive Complexity Introduction:**
- Individual component understanding
- Interface and protocol mastery
- Integration and system-level comprehension
- Advanced optimization and trade-off analysis

**Assessment Methodologies:**
- Functional simulation results analysis
- Design documentation quality evaluation
- Problem-solving approach assessment
- Innovation and creativity demonstration

## 9. Industry Relevance and Applications

### 9.1 Current Industry Trends

The VSDBabySoC educational approach aligns with current industry developments:

**Open Source Hardware Movement:**
- RISC-V ISA adoption acceleration
- Open source toolchain development
- Collaborative development methodologies

**AI and Machine Learning Integration:**
- Edge AI processor requirements
- Neural network acceleration techniques
- Real-time inference capabilities

### 9.2 Career Preparation and Professional Development

**Industry-Relevant Skills:**
- EDA tool proficiency (Synopsys, Cadence, Mentor Graphics)
- Standard protocol knowledge (AXI, PCIe, USB)
- Verification methodology expertise (UVM, SVA)
- Mixed-signal design understanding

**Career Path Preparation:**
- ASIC/FPGA design engineering
- Verification and validation engineering
- System architecture and integration
- Technical leadership and management

## 10. Conclusion and Future Perspectives

### 10.1 Key Learning Achievements

The VSDBabySoC platform successfully demonstrates how complex SoC design principles can be made accessible through thoughtful educational design. Key achievements include:

**Comprehensive Understanding:**
Students develop thorough comprehension of SoC architecture, component integration, and verification methodologies through hands-on experience with a realistic yet manageable design.

**Practical Skill Development:**
The platform enables students to develop industry-relevant skills using professional EDA tools while working with standard protocols and interfaces.

**System-Level Perspective:**
By working with a complete SoC implementation, students develop critical system-level thinking skills essential for complex integrated circuit design.

### 10.2 Future Learning Trajectory

The VSDBabySoC experience establishes a foundation for advanced topics:

**Physical Design Flow:**
- Floor planning and placement optimization
- Routing and timing closure techniques
- Power analysis and optimization
- Design for manufacturability

**Advanced Verification:**
- Universal Verification Methodology (UVM)
- Formal verification techniques
- Coverage-driven verification
- System-level validation

**Specialized Domains:**
- High-speed interface design
- Memory subsystem optimization
- Power management integration
- Security and reliability enhancement

### 10.3 Impact on Professional Development

This educational experience prepares students for successful careers in the semiconductor industry by providing:

**Technical Foundation:**
Solid understanding of SoC design principles, verification methodologies, and EDA tool usage.

**Problem-Solving Skills:**
Experience with real-world design challenges and systematic debugging approaches.

**Industry Awareness:**
Understanding of current trends, standard practices, and emerging technologies.

**Continuous Learning Framework:**
Ability to adapt to rapidly evolving technology landscape and embrace new design methodologies.

---

The VSDBabySoC educational platform represents an exemplary approach to SoC design education, successfully balancing theoretical depth with practical relevance. Through systematic exploration of its architecture, components, and integration strategies, students develop both technical competency and system-level understanding essential for success in the modern semiconductor industry. This foundation enables continued learning and professional growth in the dynamic field of integrated circuit design and verification.

---

# Part 2 - Laboratory: Functional Modeling

# Week 2 Part 2 - Functional Modeling Laboratory Procedure

## Overview

This document provides comprehensive step-by-step instructions for completing the VSDBabySoC functional modeling laboratory exercises. The lab focuses on practical implementation of pre-synthesis and post-synthesis simulation using industry-standard EDA tools.

## Table of Contents

1. [Environment Setup](#1-environment-setup)
2. [Project Preparation](#2-project-preparation)
3. [Pre-synthesis Simulation](#3-pre-synthesis-simulation)
4. [Waveform Analysis](#4-waveform-analysis)
5. [Post-synthesis Simulation](#5-post-synthesis-simulation)
6. [Results Documentation](#6-results-documentation)
7. [Troubleshooting Guide](#7-troubleshooting-guide)

---

## 1. Environment Setup

### 1.1 System Requirements

**Hardware Requirements:**
- Minimum 4GB RAM (8GB recommended)
- 10GB free disk space
- Intel/AMD x64 processor

**Software Requirements:**
- Ubuntu 18.04 LTS or later
- Python 3.6+
- Git version control

### 1.2 Tool Installation

#### Step 1: Install Base Packages

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install essential development tools
sudo apt install -y build-essential git python3 python3-pip
sudo apt install -y make cmake pkg-config
sudo apt install -y iverilog gtkwave
```
![WhatsApp Image 2025-10-03 at 21 59 35_cc317ff1](https://github.com/user-attachments/assets/3290f6f8-306c-4e27-9849-0aa5885a0028)


**Expected Output:**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
...
Setting up iverilog (10.3-1) ...
Setting up gtkwave (3.3.103-1) ...
```


#### Step 2: Install Python Dependencies

```bash
# Create Python virtual environment
python3 -m venv sp_env

# Activate environment
source sp_env/bin/activate

# Install required Python packages
pip3 install pyyaml click sandpiper-saas


```

**Verification Command:**
```bash
# Check installations
which iverilog
which gtkwave
sandpiper-saas --version
```

**Screenshot Location:** `docs/images/setup/tool-verification.png`

### 1.3 Environment Variables

```bash
# Add to ~/.bashrc for permanent setup
echo 'export VLSI_HOME=$HOME/VLSI' >> ~/.bashrc
echo 'export PATH=$VLSI_HOME/tools/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

---

## 2. Project Preparation

### 2.1 Repository Cloning

```bash
# Create working directory
mkdir -p ~/VLSI
cd ~/VLSI

# Clone VSDBabySoC repository
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC

# Verify repository structure
ls -la
```
<img width="1295" height="860" alt="Screenshot 2025-09-28 205834" src="https://github.com/user-attachments/assets/69f881e3-ddc2-4fe3-b429-d40ada160520" />

**Expected Structure:**
```
drwxrwxr-x  3 user user 4096 Sep 28 20:58 src/
-rw-rw-r--  1 user user 1234 Sep 28 20:58 Makefile
-rw-rw-r--  1 user user 4567 Sep 28 20:58 README.md
drwxrwxr-x  2 user user 4096 Sep 28 20:58 output/
```
<img width="1590" height="1023" alt="Screenshot 2025-09-28 210037" src="https://github.com/user-attachments/assets/fa49f7bc-2ecd-4bc3-9717-7f93f4710398" />

<img width="1919" height="1079" alt="Screenshot 2025-09-28 210159" src="https://github.com/user-attachments/assets/5c47c9e6-3b7b-4fd9-b19d-7e133254eaca" />

### 2.2 Source Code Analysis

#### Key Files Overview:

| File | Purpose | Location |
|------|---------|----------|
| `rvmyth.tlv` | RISC-V processor in TL-Verilog | `src/module/` |
| `vsdbabysoc.v` | Top-level SoC integration | `src/module/` |
| `avsdpll.v` | Phase-locked loop model | `src/module/` |
| `avsddac.v` | Digital-to-analog converter | `src/module/` |
| `testbench.v` | Simulation testbench | `src/module/` |

<img width="1919" height="1079" alt="Screenshot 2025-09-28 210250" src="https://github.com/user-attachments/assets/011d34d2-ec13-4f53-b17d-5df63d219410" />
<img width="1915" height="1079" alt="Screenshot 2025-09-28 211104" src="https://github.com/user-attachments/assets/962a6e32-52d8-4a05-b49c-7ce80dc5fefc" />


### 2.3 TL-Verilog to Verilog Conversion

```bash
# Activate Python environment
source sp_env/bin/activate

# Convert TL-Verilog to standard Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v \
    --bestsv --noline -p verilog --outdir ./src/module/

# Verify conversion
ls -la src/module/rvmyth.v
```
<img width="1920" height="1020" alt="Screenshot 2025-09-28 212154" src="https://github.com/user-attachments/assets/fbcf621c-4c89-4e28-ade7-d3a1c6b4681d" />
<img width="1920" height="1020" alt="Screenshot 2025-09-28 212732" src="https://github.com/user-attachments/assets/998f3327-5c0c-4328-a382-80c76fa9ae23" />



---

## 3. Pre-synthesis Simulation

### 3.1 Create Output Directories

```bash
# Create necessary output directories
mkdir -p output/pre_synth_sim
```
<img width="1920" height="1020" alt="Screenshot 2025-09-28 212732" src="https://github.com/user-attachments/assets/69ad6b23-9e5d-4e03-b031-84457e8f6cf5" />

### 3.2 Compilation Process

```bash
# Navigate to project root
cd ~/VLSI/VSDBabySoC

# Compile Verilog sources using Icarus Verilog
iverilog -o output/pre_synth_sim/pre_synth_sim.out \
    -DPRE_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v \
    src/module/vsdbabysoc.v \
    src/module/rvmyth.v \
    src/module/avsdpll.v \
    src/module/avsddac.v
```

**Expected Output:**
```
src/module/testbench.v:25: warning: Module testbench has no timescale directive in effect.
src/module/vsdbabysoc.v:15: warning: Module vsdbabysoc has no timescale directive in effect.
...
Compilation successful: pre_synth_sim.out generated
```

<img width="1920" height="1020" alt="Screenshot 2025-09-28 212840" src="https://github.com/user-attachments/assets/131553af-c5d7-4be0-a284-e2eb5a428720" />


### 3.3 Simulation Execution

```bash
# Navigate to simulation directory
cd output/pre_synth_sim

# Execute simulation
./pre_synth_sim.out

# Verify VCD file creation
ls -la *.vcd
```

**Simulation Output:**
```
VCD info: dumpfile pre_synth_sim.vcd opened for output.
Time    Reset  CLK    RV_TO_DAC    DAC_OUT
0       1      0      xxxxxxxxxx   0.000000
5       1      1      xxxxxxxxxx   0.000000
10      0      0      0000000000   0.000000
15      0      1      0000000001   0.003223
...
Simulation completed successfully
```

**Screenshot Location:** `docs/images/terminal/simulation-execution.png`

### 3.4 Alternative: Using Makefile

```bash
# Return to project root
cd ~/VLSI/VSDBabySoC

# Use provided Makefile (if available)
make pre_synth_sim
```

---

## 4. Waveform Analysis

### 4.1 Launch GTKWave
<img width="1919" height="1079" alt="Screenshot 2025-09-28 222305" src="https://github.com/user-attachments/assets/07880c85-8465-47b0-a917-8023593dbe44" />

```bash
# Launch GTKWave with VCD file
cd ~/VLSI/VSDBabySoC
gtkwave output/pre_synth_sim/pre_synth_sim.vcd &
```

### 4.2 Signal Selection Process

#### Step 1: Navigate Hierarchy
- In SST (Signal Search Tree) panel, expand `testbench`
- Expand `uut` (unit under test)
- You should see: `core`, `dac`, `pll` modules

**Screenshot Location:** `docs/images/waveforms/gtkwave-hierarchy.png`

#### Step 2: Add Clock Signal
1. Expand `pll` module
2. Click on `CLK` signal
3. Click "Append" button
4. Verify clock appears in waveform viewer

#### Step 3: Add Reset Signal
1. Click on `uut` module
2. In signals panel, find `reset`
3. Click on `reset` and "Append"

#### Step 4: Add Data Bus
1. Expand `core` module
2. Find `OUT[9:0]` signal (10-bit processor output)
3. Click and "Append"

#### Step 5: Add DAC Output
1. Expand `dac` module
2. Find `OUT` signal with type **`real`**
3. Click and "Append"
4. **Important:** Right-click on `uut.dac.OUT` in signals panel
5. Select "Data Format" → "Analog" → "Step"

**Critical Note:** There are two `OUT` signals:
- `uut.core.OUT[9:0]` - Digital bus from processor
- `uut.dac.OUT` - Analog output from DAC (**choose this for analog view**)

**Screenshot Location:** `docs/images/waveforms/signal-selection-process.png`

### 4.3 Waveform Analysis

#### Key Signals to Analyze:

| Signal | Purpose | Expected Behavior |
|--------|---------|-------------------|
| `CLK` | System clock from PLL | Square wave, ~100MHz |
| `reset` | System reset | High initially, then low |
| `OUT[9:0]` | Digital data bus | Changing values after reset |
| `dac.OUT` | Analog output | Step waveform following digital values |

#### Analysis Checklist:
- [ ] **Clock Verification**: Stable, periodic square wave
- [ ] **Reset Operation**: Proper initialization sequence
- [ ] **Data Flow**: Digital values changing over time
- [ ] **Analog Conversion**: DAC output tracking digital input

**Screenshot Location:** `docs/images/waveforms/complete-waveform-analysis.png`

### 4.4 Measurement and Documentation

```bash
# Save GTKWave session
# File → Write Save File → save as "babysoc_analysis.gtkw"

# Export waveform image
# File → Print → [Configure] → Print to File → PNG
```

**Key Measurements:**
- Clock period: 10ns (100MHz)
- Reset duration: ~50ns
- Data transitions: 15+ valid changes
- Analog output range: 0V to 3.3V

---

## 5. Post-synthesis Simulation

### 5.1 Synthesis Process

```bash
# Activate Python environment
source sp_env/bin/activate

# Attempt synthesis using Makefile
make synth
```
<img width="1915" height="1079" alt="Screenshot 2025-09-28 223941" src="https://github.com/user-attachments/assets/f5725955-69a7-4115-8d64-635e944980df" />
<img width="1919" height="1079" alt="Screenshot 2025-09-28 224711" src="https://github.com/user-attachments/assets/424bbffd-9be4-4ddc-82c6-30e46516d20a" />

### 5.2 Known Issue Documentation

**Error Encountered:**
```
7.22. Executing ABC pass (technology mapping using ABC).
ERROR: Assert `p != NULL' failed in kernel/yosys.cc:453.
Makefile:66: recipe for target 'synth' failed
make: *** [synth] Error 1
```
<img width="1919" height="1079" alt="Screenshot 2025-09-28 232139" src="https://github.com/user-attachments/assets/e093b473-5c6a-4c95-90f4-dd09544239d4" />

**Root Cause Analysis:**
- Yosys/ABC assertion failure during technology mapping
- Known issue with specific Verilog constructs
- Not related to user error or environment setup

**Impact:**
- Post-synthesis simulation cannot be completed
- Week 2 objectives can still be met with pre-synthesis simulation

**Screenshot Location:** `docs/images/terminal/synthesis-error.png`

### 5.3 Alternative Approaches

#### Option 1: Manual Synthesis Debugging
```bash
# Generate detailed synthesis log
make synth > synthesis.log 2>&1

# Analyze log for specific error location
grep -n "ERROR\|Failed\|Assert" synthesis.log
```

#### Option 2: Use Pre-synthesized Netlist
- Download working netlist from reference implementation
- Place in `output/synth/vsdbabysoc.synth.v`
- Continue with post-synthesis simulation

---
### Pre-Synthesis vs. Post-Synthesis Simulation

| Characteristic      | Pre-Synthesis Simulation (RTL Simulation)                                    | Post-Synthesis Simulation (Gate-Level Simulation)                                                    |
| :------------------ | :--------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- |
| **Input Design**    | High-level **RTL** (Register Transfer Level) code (Verilog/VHDL).              | **Gate-level netlist** generated by a synthesis tool.                                                |
| **Primary Goal**    | To verify the **functional correctness** of the design's logic and algorithm.  | To verify the synthesized netlist is logically equivalent to the RTL and to check for **timing violations**. |
| **Abstraction Level** | **Behavioral**: Describes *what* the circuit does.                             | **Structural**: Describes the circuit as a connection of specific logic gates from a technology library. |
| **Timing Model**    | **Idealistic**: Assumes zero or unit delays. Does not consider physical delays. | **Realistic**: Includes timing delays of logic gates and can be annotated with wire delays (from an SDF file). |
| **Simulation Speed**  | **Fast**, as it operates at a higher level of abstraction.                  | **Slow**, as it simulates every gate and its associated delay, which is computationally intensive.     |
| **When to Use**     | Early in the design flow to quickly find and fix logical bugs.                 | After synthesis to ensure the tool did not introduce errors and to perform initial timing analysis.       |


## 6. Results Documentation

### 6.1 Required Screenshots

#### Environment Setup:
- [ ] Package installation confirmation
- [ ] Tool version verification
- [ ] Repository structure after cloning

#### Compilation Process:
- [ ] TL-Verilog conversion success
- [ ] Icarus Verilog compilation output
- [ ] VCD file generation confirmation

#### Waveform Analysis:
- [ ] GTKWave signal hierarchy
- [ ] Clock signal visualization
- [ ] Reset operation waveform
- [ ] Complete 4-signal analysis
- [ ] Analog output step waveform

#### Error Documentation:
- [ ] Synthesis error message
- [ ] Error analysis and root cause

### 6.2 Log File Collection

```bash
# Collect all log files
mkdir -p docs/lab/simulation-logs

# Copy compilation logs
cp output/pre_synth_sim/*.log docs/lab/simulation-logs/

# Copy simulation output
cp output/pre_synth_sim/simulation_output.txt docs/lab/simulation-logs/

# Archive synthesis error log
cp synthesis.log docs/lab/simulation-logs/synthesis_error.log
```

### 6.3 Deliverable Checklist

- [ ] **Simulation logs**: Complete compilation and execution logs
- [ ] **GTKWave screenshots**: Annotated waveform analysis
- [ ] **Explanations**: Technical description of each waveform
- [ ] **Issue documentation**: Post-synthesis error analysis

---

## 7. Troubleshooting Guide

### 7.1 Common Environment Issues

#### Issue: `sandpiper-saas: command not found`
**Solution:**
```bash
# Verify Python virtual environment is activated
source sp_env/bin/activate

# Reinstall if necessary
pip install --upgrade sandpiper-saas
```

#### Issue: `iverilog: command not found`
**Solution:**
```bash
# Install Icarus Verilog
sudo apt install iverilog

# Verify installation
which iverilog
iverilog -V
```

### 7.2 Compilation Issues

#### Issue: Include file not found
**Solution:**
```bash
# Check file paths
ls -la src/module/
ls -la src/include/

# Verify include directories in iverilog command
iverilog -I src/include -I src/module ...
```

#### Issue: Module not found during compilation
**Solution:**
```bash
# Ensure all required modules are present
ls src/module/vsdbabysoc.v
ls src/module/rvmyth.v
ls src/module/avsdpll.v
ls src/module/avsddac.v
```

### 7.3 Simulation Issues



#### Issue: No VCD file generated
**Solution:**
```bash
# Check testbench for VCD dump commands
grep -n "\$dumpfile\|\$dumpvars" src/module/testbench.v

# Verify output directory permissions
ls -la output/pre_synth_sim/
```

### 7.4 GTKWave Issues

#### Issue: Cannot see analog waveform
**Solution:**
1. Ensure you selected `uut.dac.OUT` (type `real`)
2. Right-click → Data Format → Analog → Step
3. Verify signal is not `uut.OUT` (digital wire)

#### Issue: Waveform appears corrupted
**Solution:**
```bash
# Regenerate VCD file
cd output/pre_synth_sim
./pre_synth_sim.out

# Reload in GTKWave
# File → Reload Waveform
```

### 7.5 Post-synthesis Issues

#### Issue: ABC assertion failure
**Status:** Known issue, not user error
**Workaround:** Document issue and proceed with pre-synthesis results
**Future Resolution:** Use OpenLANE Docker environment in later weeks

---

## Appendices

### Appendix A: Command Reference

```bash
# Essential commands summary
source sp_env/bin/activate                    # Activate Python environment
sandpiper-saas -i *.tlv -o *.v               # Convert TL-Verilog
iverilog -o sim.out *.v                       # Compile Verilog
./sim.out                                     # Run simulation
gtkwave file.vcd &                           # Launch waveform viewer
make clean                                    # Clean build artifacts
```

### Appendix B: File Locations

```
~/VLSI/VSDBabySoC/
├── src/module/              ← Source Verilog files
├── output/pre_synth_sim/    ← Pre-synthesis results
├── docs/images/             ← Screenshots for documentation
└── logs/                    ← All log files
```

### Appendix C: Success Criteria

**Week 2 Part 2 Success Indicators:**
- [ ] Successful Icarus Verilog compilation
- [ ] VCD file generation and GTKWave visualization
- [ ] Clear waveforms showing clock, reset, data flow
- [ ] Analog DAC output properly displayed
- [ ] Complete documentation with screenshots
- [ ] Professional technical explanations

---

*This laboratory procedure document ensures reproducible results and comprehensive documentation of the VSDBabySoC functional modeling process.*

---

## References

### Course Materials
- [Week 0 Foundation](https://github.com/Vansh0917/RISC-V-Reference-SoC-Tapeout-Program_VLSI_Week_0): EDA tool setup and verification
- [SFAL-VSD-SoC-Journey](https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey/tree/main/11.%20Fundamentals%20of%20SoC%20Design): SoC design fundamentals
- [VSDBabySoC Project](https://github.com/manili/VSDBabySoC): Reference implementation

### Technical Resources
- [Icarus Verilog Documentation](http://iverilog.icarus.com/): Simulation tool reference
- [GTKWave User Guide](http://gtkwave.sourceforge.net/gtkwave.pdf): Waveform analysis
- [RISC-V ISA Specification](https://riscv.org/specifications/): Processor architecture
- [TL-Verilog Documentation](https://www.redwoodeda.com/tl-verilog): Transaction-level modeling

### Academic Sources
- SoC Design Methodologies (Embedded Systems Design)
- Mixed-Signal System Integration Principles
- Digital VLSI Design Flow (Front-end to Back-end)
- Functional Verification Best Practices

## Conclusion

### ✅ Theoretical Understanding

* Solid grasp of SoC design principles and methodologies
* Detailed study of **VSDBabySoC architecture** and components
* Well-documented learning outcomes with industry relevance

### 🛠 Practical Skills

* Hands-on with **Icarus Verilog** & **GTKWave**
* Verilog simulation & functional verification
* Waveform analysis and systematic debugging
* Professional documentation & technical communication

### ⚡ Technical Accomplishments

* Successful **pre-synthesis functional verification**
* Complete simulation environment setup & configuration
* Mixed-signal SoC behavior analysis
* Structured technical problem-solving

### 📈 Professional Development

* Industry-standard documentation practices
* Debugging and issue resolution workflow
* Improved technical communication & presentation skills
* Project management with milestone tracking

---

## 🎯 Learning Outcomes

* **Knowledge**: Strong SoC design & verification methodologies
* **Skills**: Proficiency with EDA tools & HDL simulation
* **Problem-Solving**: Root cause analysis & resolution strategies
* **Career Prep**: Directly applicable to VLSI design roles

---

## 🔮 Next Steps (Program Continuity)

* **Week 3**: RTL design & advanced verification
* **Physical Design Readiness**: Functional → physical flow
* **Tool Ecosystem Mastery**: End-to-end tapeout environment
* **Professional Standards**: Industry-ready documentation & presentations

---

✅ **Week 2 Status: COMPLETE**

---



