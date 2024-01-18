# HBM High Bandwidth Memory

## Paper [1]
### Problem: 
  As the market trend renders integration of various features in one chip, mobile DRAM is required to have not only **low power consumption** but also **high capacity** and **high speed**.
### Solution:
  Stacking of multiple Wide-I/O memories with large number of I/O pins
  Memory density expansion can be achieved by stacking of multiple chips using TSV (Through-Silicon Via) technology.
## Architecture:
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


# Refrences:
[1] Kim JS, Oh CS, Lee H, Lee D, Hwang HR, Hwang S, Na B, Moon J, Kim JG, Park H, Ryu JW. A 1.2 V 12.8 GB/s 2 Gb mobile wide-I/O DRAM with 4$\times $128 I/Os using TSV based stacking. IEEE Journal of Solid-State Circuits. 2011 Sep 23;47(1):107-16.

# Definitions:
- TSV: In electronic engineering, a through-silicon via (TSV) or through-chip via is a vertical electrical connection (via) that passes completely through a silicon wafer or die.
- DQ : DQ is a label for data pins in the DDR circuitry. The DQ pins are used for input and output during a write operation. The memories data bus is bidirectional, so a data pin can be D when it is input or Q when it is output, hence the name DQ3.
