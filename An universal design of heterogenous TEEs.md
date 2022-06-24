# An universal design of heterogenous TEEs

## Background

Heterougenous TEEs have been well studied in recent years, e.g., GPU TEEs like Graviton, HIX, H100, Graphcore IPU Trusted Extensions (ITX), FPGA TEEs like SGX-FPGA, ShEF, TEEOD and others like Iceclave, SecNDP, PIM-Enclave. We conclude a common design prototype of them and try to find the chance to optimize them.

<!-- root of trust: hardware feature and firmware for access control, encryption and communication -->
<!-- specialized instructions -->
<!-- PCIe, DMA -->
<!-- X86 adopts the independent addressing method to separate the memory operation from the peripheral IO operation, so that there is a distinction between the memory space and the IO space. The instructions for accessing memory and peripheral registers within the X86 platform CPU are also different. -->

## Memory Encryption: Counter Mode

AES-CTR (Counter mode) is a member of AES cryptography family which turns a block cipher into a stream cipher. It generates the next keystream block by encrypting successive values of a "counter". The counter can be any function which produces a sequence which is guaranteed not to repeat for a long time, although an actual increment-by-one counter is the simplest and most popular [^wiki]. Counter mode can encrypt and tranfer data blocks in parallel and decrypt them as the same manner. Therefore, AES-CTR can be accelerated better than other AES variants.
|![encryption](./assets/CTR_encryption_2.svg)|
|:--:|
| *Counter mode encryption* |
|![decryption](./assets/CTR_decryption_2.svg)|
| *Counter mode decryption* |
