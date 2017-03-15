### Výpočet pravdepodobnosti výskytu (x)-tice z (d)-tice v (n)-tici z (d+z)-tice
```
M0 ; 1 ;
I/II K1 ; ENT ; KIN1 ;
     K2 ; ENT ; KIN2 ; + ;
     K3 ; ENT ; KIN3 ; = ; nCr ; K1 ; = ; KIN5 ;
     K4 ; ENT ; KIN4 ;
     K2 ; nCr ; ( ; K1 ; - ; K4 ; ) ; = ; ÷ ; K5 ;
     HLT ; RTN ;
```

- Memory used: 30 steps
- Registers used:
  - `K1` = N
  - `K2` = D
  - `K3` = Z
  - `K4` = X
  - `K5` = počet možných
