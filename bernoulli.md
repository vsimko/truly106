### Bernoulliho schéma
```
M0 ; 1 ;
I/II ENT ; KIN3 ; ENT ; KIN2 ; ENT ; KIN1 ;
     nCr ; K2 ; * ; K3 ; x^w ; K2 ; * ; ( ; 1 ; - ; K3 ; ) ; x^w ; ( ; K1 ;
     - ; K2 ; ) ; = ; C ; = ;
```

- Memory used: 27 steps
- Registers used:
  - `K1` = pravdepodobnosť udalosti
  - `K2` = nastane práve k-krát
  - `K3` = pri nezávislom n-násobnom opakovaní
