---
title: Read papers and notes
---

- [Multi-Tag: A Hardware-Software Co-Design for Memory Safety
based on Multi-Granular Memory Tagging](https://pure.tugraz.at/ws/portalfiles/portal/60390380/multi_tag.pdf)
    - <iframe src="multi_tag.pdf" width="100%" height="600px"></iframe> 

    This papers discusses the combination of hardware and software memory tagging, since software memory tagging would supposedly lead to to much of a performance overhead on its own. Hardware memory tagging alone is possible but does not offer sufficient enthropy. An implementation, more precisely one with ARM MTE, is discussed as an example. Also pointer authentication is mentioned and might be a valuable addition to memory tagging. 

    The imaginary example discussed (not ARM MTE):
    - tag is in the upper bits of the pointer: first an 8 bit object tag, then a 16 bit page tag.
    - 8 bit object tag will be checked by the hardware (something like ARM MTE) -> 8 bit page tag leads to an object granularity of 16 bytes on a page (4k bytes/2⁸ = 16 bytes)
    - we decrease the size of the virtual address space
    - trade of between the size of the virtual address space and security specifications
    - the page tag will be checked while getting the information from the page table to avoid a performance overhead, as the page table will need to be accessed anyways to translate the virtual addresss to a physical address.
    - 
