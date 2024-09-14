---
title: TODO
---


  - watch remaining classes veilige software en hacking
  - finish [paper](https://pure.tugraz.at/ws/portalfiles/portal/60390380/multi_tag.pdf)
  - get familiar with LLVM: 
      - [dit](https://mapping-high-level-constructs-to-llvm-ir.readthedocs.io/en/latest/) heb ik al nuttig gevonden, en de associated github [repo's README](https://github.com/f0rki/mapping-high-level-constructs-to-llvm-ir/) bevat nog enkele links naar introducties.
      - Mijn [eigen hands-on getting-started repo](https://github.com/adriaanjacobs/llvm-getting-started)
      - De [LLVM Language Reference](https://llvm.org/docs/LangRef.html) en [LLVM Programmer's Manual](https://llvm.org/docs/ProgrammersManual.html) zijn geweldige resources, maar helpen misschien pas echt zodra je iets meer ervaring hebt.

  - further readings about memory tagging
      - [dit](https://haehyun.github.io/papers/vik-asplos22.pdf), heeft een ~gelijkaardig idee, maar focust op _temporal_ safety, eerder dan _spatial_ safety.
      - Een iets [oudere paper](https://faculty.cc.gatech.edu/~orso/papers/clause.doudalis.orso.prvulovic.pdf), heeft ook gelijkaardige ideeën, maar gebruikt slechts 2 tags.
      - Een historische paper, [WIT](https://www.doc.ic.ac.uk/~cristic/papers/wit-sp-ieee-08.pdf), gebruikt 256 tags. WIT propageert de tags niet dynamisch (als onderdeel van de pointer) maar berekent statisch welke accessible moeten zijn, net zoals in Data Flow Integrity (je tweede keuze). Er staan nog altijd wel enkele coole tricks in, zoals de deterministische linear buffer overflow protection (met hun "guards").
      - [CryptSan](https://dl.acm.org/doi/pdf/10.1145/3555776.3577635) is recent werk op ARM, en bevat eigenlijk opnieuw gelijkaardige ideeën. Clever use of PAC om de integrity van de pointer tag bits te bewaren.

  - setup slack
