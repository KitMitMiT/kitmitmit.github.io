---
title: Read papers and notes
---


| paper id  | name | data of reading | relevance|
| --------- |------|-----------------|------------|
| 1         |   Multi-Tag: A Hardware-Software Co-Design for Memory Safety | 27-28sept | high|


# [Multi-Tag: A Hardware-Software Co-Design for Memory Safety based on Multi-Granular Memory Tagging](https://pure.tugraz.at/ws/portalfiles/portal/60390380/multi_tag.pdf)
    
<iframe src="multi_tag.pdf" width="100%" height="600px"></iframe> 

 This papers discusses the combination of hardware and software memory tagging, since software memory tagging would supposedly lead to to much of a performance overhead on its own. Hardware memory tagging alone is possible but does not offer sufficient enthropy. An implementation, more precisely one with ARM MTE, is discussed as an example. Also pointer authentication is mentioned and might be a valuable addition to memory tagging.

### The imaginary example discussed (not ARM MTE):

- tag is in the upper bits of the pointer: first an 8 bit object tag, then a 16 bit page tag
- every object gets a tag in memory that will get checked against the tag in the pointer when accesing the object.
- 8 bit object tag will be checked by the hardware (something like ARM MTE) -> 8 bit page tag leads to an object granularity of 16 bytes on a page (4k bytes/2⁸ = 16 bytes)
- we decrease the size of the virtual address space
- trade of between the size of the virtual address space and security specifications
- the page tag will be checked while getting the information from the page table to avoid a performance overhead, as the page table will need to be accessed anyways to translate the virtual addresss to a physical address
- if we use pseudorandom tag generation, tag colision probability on a page is 2^(-8) = 0.3%. If we use an LFSR(a list to avoid the same tag on the same page), the collision probability is 0%.
- neighbouring memory objects have distinct tags. So memory overflow attacks are avoided
- tag collision probablity over the whole virtual memory address space is 2^(-8) * 2^(-16) = 0.00000596%. (note: I think this paper calculation is wrong. It depends also on the used virtual memory. But this is an ok metric to quantify security nevertheless)
- LFSR can also be used for the page tags (this has implications that I don't fully understand)
- pages will be quarantined until all memory objects, then a new page tag gets assigned to the page. (could be a problem if one memory object stays on the page => run out of memory)


### Spatial memory safety?

- by avoiding tag collisions in neighbouring memory objects
- probalistic spatial security when there is use of non-lineair buffer overflows

### Temporal memory safety?

- UAF and double frees are avoided by having a zero tag
- object tags get changed after frees
- page tags gets changed after all memory objects are freed

### Pointer authentication
This is also used on top of ARM MTE. This seems very intresting; I plan on looking further into this as it is unclear to me at this moment.

### Questions
What is the FPGA implementation for? Are we basicly designing a prototype CPU that offers the hardware and instructionset to make hardware memory tag checking possible?

### Further exploration from here
- stack and global memory tagging
- Pointer authentication (PA)