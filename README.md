# HBM High Bandwidth Memory

## Paper Wide I/O DRAM [1]: 
### Problem: 
  As the market trend renders integration of various features in one chip, mobile DRAM is required to have not only **low power consumption** but also **high capacity** and **high speed**.
### Solution:
  Stacking of multiple Wide-I/O memories with large number of I/O pins
  Memory density expansion can be achieved by stacking of multiple chips using TSV (Through-Silicon Via) technology.
### Architecture:
 - mono or multiple stacked Wide-I/O DRAMs:
 
 <img width="634" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/f4d300cf-d751-4ee1-94ad-a56b01b05388">

- 1 Gb Wide-I/O DRAM and SEM image of micro bumps:

 <img width="451" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/f896589d-1b81-4236-8b1e-73219c48f499">

1. Figure shows the chip architecture with 4-channels and 16 segmented 64 Mb arrays. The whole chip is made up of 4 partitions which are symmetric with respect to the chip center, and each partition consists of 4x64 Mb **arrays, peripheral circuits and micro bumps**.
2. **Test pads**: Direct access (DA) mode is implemented to support failure analysis in SIP type packages. In DA mode, only 32 pins are needed to test all 4 channels.
3. All 4 channels are totally independent, and each channel can be made up of 2 or 4 banks with 128 DQs. Column addresses are fixed
as CA[0:6] and each channel has 46x6 microbump:

As the image below is showing DQ0 to DQ127 is connected through bump.
  <img width="764" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/2e0affdb-dbb5-484d-9203-b4708b756a52">

## Paper HBM-DRAM [2]:  
### problems:
One of the major obstacles is the testability. Due to small diameter, it is very difficult to directly test the microbump. 

In addition, in wide I/O memory, stacked chip on system-in-package(SiP) cannot be detached. One cell or TSV failure makes the whole system failu. 

Managing the power is also a problem. Large IR drop and SSO noise can cause severe trouble in transmitting and receiving data.

### solutions:
In this paper, one solution to solve these problems is using base logic die on the memory chip, which supports better testability and improves reliability.

It is also advantageous to allocate PHY interface logic in base logic chip between the interposer and stacked-DRAM with thousands of TSV. The PHY located in the base logic chip
of HBM decreases the repairs the chip-to-chip connection failure, and provides power redistribution.

  <img width="405" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/5b518bae-6039-451f-89f8-95a224fce885">

### Architecture:
- The fundamental structure of HBM is composed of 4-Hi (high) **core DRAM and base logic die** at the bottom.
- The core DRAM consists of two channels, where each channel has 1 Gb density with 128 I/Os and eight independent banks.
- Each channel of core DRAM die has independent address and data TSV with point-to-point (P2P) connection, isolating the operation of every channel.
- The power and ground of each channel are not isolated and have common plane.
  <img width="647" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/093ff998-c3c2-47ad-a0f8-5cc07e473ff3">

- Ballout area is located at the center as a blue rectangle. The size of the ballout is about 6 mm 3 mm.
- **PHY (Physical layer)** located at the top of the die is for the **main interface between DRAM and memory controller**.
- PHY has a total of eight channels where a channel consists of an AWORD and four channel-interleaved DWORD. A total of eight AWORD and 32 DWORD are located in the PHY area.
- MBIST (Memory BIST) and IEEE1500, RTL-based circuit, for the purpose of reliability and testing is located at the bottom.

  <img width="635" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/c158ab99-dc71-456e-b336-6bd40d6376ea">

## Paper HBM-GEN2(HBM2) [3]: 
### Problems:

higher bandwidth

### Solutions:

double the bandwidth from 128GB/s to more than 256GB/s

support pseudo-channel mode and 8H stacks

  <img width="300" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/686fe140-1b2a-431d-8fdd-55dba6b53df7">
  <img width="374" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/5be90d5d-ad09-400f-a1ae-fc6a9d2688ac">


### Architecture:
- In the pseudo-channel
- A legacy channel is divided into two pseudo channels and the two pseudo channels share the command-address pins. Thus, one HBM has 16 pseudo channels instead of 8 legacy channels.
- In 4H/8H case the HBM is composed of two channels and each channel has two pseudo channels (PC0/PC1) which consists of 16 banks (4 bank-groups and 4banks per group).
- 1 channel = 2 pseudo channel = 2x(4 bank groups) = 2x(4x(4 banks)) = 32 banks
- 128 bit bandwidth per each bank
- In case of 2H, one pseudo channel is divided into two different channels and each channel has eight banks which is necessary to keep the same bandwidth as in 4H/8H case.

  <img width="520" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/bdf4fc4c-11e9-46d1-91be-d88bd1c00579">


## Paper HBM-PIM [4]:
### Problems:

 The energy consumption from interconnections limits the scaling of the system performance, because the on-chip interconnection is increased by the tremendous accelerator size and the power overhead is caused by DRAM bandwidth expansion.

### Solutions:
Processing-in-memory (PIM) architecture.

<img width="571" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/28dec9b4-909b-40c3-93f0-49319192acfc">

### Architectuure:
- Embedding processing units into a logic base.
- PIM core for the proposed PIM-HBM architecture is assumed to be a streaming multiprocessor (SM), which is a unit core of a graphics processing unit (GPU).
  
  <img width="267" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/5ad6eb1a-31ab-4e51-8760-88e7b1ede0c1">
  <img width="468" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/4ad48aa6-104c-40f4-8b69-335eb069ba3c">

### SM Architecture [5]:

 <img width="394" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/83a7b99c-d0ad-483a-9bf0-16553139e976">

## Paper HBM2E [6]:
### Problems:

higher bandwidth

### Solutions:

increase its bandwidth up to 640GB/s (5Gb/s/pin)

stable bit-cell operation

### Architecture: 

 <img width="408" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/5d1d85f5-bea1-40c8-b795-6b5b3db0350a">

## Paper FIM-DRAM [7]:

### problems:
GPUs and TPUs can only operate at their peak performance when they get the necessary data from memory as quickly as it is processed: requiring off-chip memory with a high bandwidth and a large capacity. HBM has thus far met the bandwidth and capacity requirement, but recent AI technologies such as recurrent neural networks require an even higher bandwidth than HBM. 

Further increase in off-chip bandwidth is often limited by power constraints.

### solution: 
 Decrease demand for off-chip bandwidth with unconventional architectures: such as processing-in-memory.
 
 Integrating a 16-wide single-instruction multiple-data engine within the memory banks.

### Architecture:
- Half of the cell array in each bank was removed and replaced with the programmable computing unit (PCU).
- Two banks share one PCU, and there are 8 PCUs per pseudo-channe

 <img width="444" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/3b3d9fa6-849e-4b42-9c1c-fa22e2096365">

- According to the table below, in normal mode we have read and write operations. But in FIM mode, we can move data from PCU block to the cell and from cell to PCU block, or write into the PCU register directly.

 <img width="570" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/5f7faecf-b66a-42fd-b0f1-8e9b13cbfdc5">

- Architecture of PCU is shown below:
  
  - The register group consists of:
      1. A command-register file (CRF) for instruction memory
      2. A general-purpose register file (GRF) for weight and accumulation
      3. A scalar register file (SRF) to store constants for MAC operation
  - The PCU is controlled by conventional memory commands from the host via the **newly implemented control paths** to enable the in-DRAM computations.
  - The execution unit in the PCU uses a variable four-stage pipeline operation.
  - The execution unit has a one stage pipeline for the JUMP instruction, which supports looping.
  - Computed results from the execution units are directed by the destination operand and stored in the GRF.
  - The PCU can save 32 instructions in the CRF

  <img width="541" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/7293ae15-4d99-4f62-8de6-d044b3bfb0d7">

- Flow of FIM-DRAM:

  <img width="560" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/91ac79d1-46ab-4647-b980-eebed45e7834">

 
# Refrences:
[1] Kim JS, Oh CS, Lee H, Lee D, Hwang HR, Hwang S, Na B, Moon J, Kim JG, Park H, Ryu JW. A 1.2 V 12.8 GB/s 2 Gb mobile wide-I/O DRAM with 4x128 I/Os using TSV based stacking. IEEE Journal of Solid-State Circuits. 2011 Sep 23;47(1):107-16.

[2] Lee DU, Kim KW, Kim KW, Lee KS, Byeon SJ, Kim JH, Cho JH, Lee J, Chun JH. A 1.2 V 8 Gb 8-channel 128 GB/s high-bandwidth memory (HBM) stacked DRAM with effective I/O test circuits. IEEE Journal of Solid-State Circuits. 2014 Oct 14;50(1):191-203.

[3] Sohn K, Yun WJ, Oh R, Oh CS, Seo SY, Park MS, Shin DH, Jung WC, Shin SH, Ryu JM, Yu HS. A 1.2 V 20 nm 307 GB/s HBM DRAM with at-speed wafer-level IO test scheme and adaptive refresh considering temperature distribution. IEEE Journal of Solid-State Circuits. 2016 Sep 13;52(1):250-60.

[4] Kim S, Kim S, Cho K, Shin T, Park H, Lho D, Park S, Son K, Park G, Kim J. Processing-in-memory in high bandwidth memory (PIM-HBM) architecture with energy-efficient and low latency channels for high bandwidth system. In2019 IEEE 28th Conference on Electrical Performance of Electronic Packaging and Systems (EPEPS) 2019 Oct 6 (pp. 1-3). IEEE.

[5] NVIDIA, Tesla. "V100 GPU architecture." (2017) ([link](https://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf)).

[6] Oh CS, Chun KC, Byun YY, Kim YK, Kim SY, Ryu Y, Park J, Kim S, Cha S, Shin D, Lee J. 22.1 A 1.1 V 16GB 640GB/s HBM2E DRAM with a data-bus window-extension technique and a synergetic on-die ECC scheme. In2020 IEEE International Solid-State Circuits Conference-(ISSCC) 2020 Feb 16 (pp. 330-332). IEEE.

[7] Oh CS, Chun KC, Byun YY, Kim YK, Kim SY, Ryu Y, Park J, Kim S, Cha S, Shin D, Lee J. 22.1 A 1.1 V 16GB 640GB/s HBM2E DRAM with a data-bus window-extension technique and a synergetic on-die ECC scheme. In2020 IEEE International Solid-State Circuits Conference-(ISSCC) 2020 Feb 16 (pp. 330-332). IEEE.

# Definitions:
- TSV: In electronic engineering, a through-silicon via (TSV) or through-chip via is a vertical electrical connection (via) that passes completely through a silicon wafer or die.
- DQ : DQ is a label for data pins in the DDR circuitry. The DQ pins are used for input and output during a write operation. The memories data bus is bidirectional, so a data pin can be D when it is input or Q when it is output, hence the name DQ3.
