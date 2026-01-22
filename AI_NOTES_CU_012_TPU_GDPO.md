GPU - move computation to data (MICRON / AWS).

Foundation (TPU) - Frontier (GDPO)

- move data to computation.
____

Foundation (TPU):

Ironwood architecture. work horse MXU in TensorCore

How to send data to MXU.

go from bit to byte to 

high capacity to high density memory

HBM and SMEM,

and into Vector Memeory (VMEM)

- move data into working area. 32x32

- 64 bits in MXU.

  #MEM HEIRATCHY

  high bandwidth memory.

  Hugging Face Model Repository.

  - Embedding, Layer, Atention, FFW, 

16 wide highway to move data into HBM Stack.

Closer to TensorCore.

### Shared Memory (SMEM)

compute happens in tensor core.
moving data to compute.

4 controllers across 16, manager of 4 weights.

Sparse Core: looks for more embeddings - 100k word dictionary (only use 100 words).

Sparse is reduced number of embeddings for the core as sparse core.

Google added this for the INFERENCE AGE.

### Vector Memory (VMEM):

Load into vector memory then matrix multiply unit.

select weights.

loads 1024 vectors simultaneously,

as we move closer to the core, data is smaller and faster, and more expensive to make.

### Matrix Multiplicatoin Unit (MXU)

pulls all the  vertex from VMEM,

multiplies into MXU2

VPU - is a chip to control logic movement.

systolic array hardware to perform mmult quickly.



### MICRON

very small .17 mm tiny transistors,

issue is supply of hpm 
non socketed high bandwidth memory

depends on microarchitecture.

PIM = processing in memory. 

PIC = processing in chip.

TPU connected by ICS into large VM.

reduce communication to cpu. 

cpu to gpu is slower,

gpu to gpu is faster.

ICI = inter chip interconnect

9,000 TPUs scale. 

rack and pod level for ai compute.

Micron provides HBM (high bandwidth memory) - on GPUS.

GPU / TPU want lots of HBM at hardware.

LPU - language processing unit.

//---------------------------------------------------

_____

Frontier (GDPO):







____
