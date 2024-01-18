# HBM High Bandwidth Memory

## Paper [1]: Wide I/O DRAM
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
2. All 4 channels are totally independent, and each channel can be made up of 2 or 4 banks with 128 DQs. Column addresses are fixed
as CA[0:6] and each channel has 46x6 microbump:

As the image below is showing DQ0 to DQ127 is connected through bump.
<img width="764" alt="image" src="https://github.com/zahrayousefijamarani/HBM_high_bandwidth_memory/assets/45602698/2e0affdb-dbb5-484d-9203-b4708b756a52">

## Paper [2]: HBM 
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
- The fundamental structure of HBM is composed of 4-Hi (high) core DRAM and base logic die at the bottom.
- The core DRAM consists of two channels, where each channel has 1 Gb density with 128 I/Os and eight
independent banks.
- Each channel of core DRAM die has
independent address and data TSV with point-to-point (P2P)
connection, isolating the operation of every channel.
- The power
and ground of each channel are not isolated and have common
plane


# Refrences:
[1] Kim JS, Oh CS, Lee H, Lee D, Hwang HR, Hwang S, Na B, Moon J, Kim JG, Park H, Ryu JW. A 1.2 V 12.8 GB/s 2 Gb mobile wide-I/O DRAM with 4$\times $128 I/Os using TSV based stacking. IEEE Journal of Solid-State Circuits. 2011 Sep 23;47(1):107-16.
[2] Lee DU, Kim KW, Kim KW, Lee KS, Byeon SJ, Kim JH, Cho JH, Lee J, Chun JH. A 1.2 V 8 Gb 8-channel 128 GB/s high-bandwidth memory (HBM) stacked DRAM with effective I/O test circuits. IEEE Journal of Solid-State Circuits. 2014 Oct 14;50(1):191-203.

# Definitions:
- TSV: In electronic engineering, a through-silicon via (TSV) or through-chip via is a vertical electrical connection (via) that passes completely through a silicon wafer or die.
- DQ : DQ is a label for data pins in the DDR circuitry. The DQ pins are used for input and output during a write operation. The memories data bus is bidirectional, so a data pin can be D when it is input or Q when it is output, hence the name DQ3.
