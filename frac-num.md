## Computing fractional numbers
Umožňuje prevádzať medzi dvoma zlomkami tieto operácie: `+`, `-`, `*`, `÷`

### Version 1
```
M0 ;
I    ENT ; KIN4 ; ENT ; KIN1 ; ENT ; KIN5 ; ENT ; KIN2 ; K1 ; * ;
     K2 ; = ; KIN3 ; ( ; K4 ; * ; K2 ; ) ; + ; ( ; K5 ; * ;
     K1 ; ) ; = ; KIN6 ; HLT ; K3 ; HLT ; RTN ;
M0 ;
II   ENT ; ÷ ; KIN4 ; ENT ; KIN1 ; ENT ; KIN5 ; ENT ; KIN2 ; K1 ; * ; K2 ;
     = ; KIN3 ; K4 ; * ; K5 ; = ; KIN6 ; HLT ; K3 ; HLT ; RTN ;
```
- Memory used:
  - `(I)`  = 30k
  - `(II)` = 23k

Stlačením tlačidla `(I)` sa zobrazí:
```
┌───────────────────┐
│on deg             │
│          0   ENT I│
└───────────────────┘
```

Program požaduje 4 údaje:
```
 A     C
─── ; ───
 B     D
```
Po zadaní čísel a stlačení `RUN`, sa zlomky spočítajú. Ak ich chceme odpočítrať,
stlačíme pred tým ešte `+/-`

Stlačením tlačidla `(II)` sa znovu zobrazí:
```
┌───────────────────┐
│on deg             │
│          0   ENT I│
└───────────────────┘
```

Program znovu požaduje 4 údaje. Pri zadaní
```
 A     C
─── ; ───  => Vynásobia sa
 B     D

 A     D
─── ; ───  => Vydelia sa
 B     C
```

Stláčaním `RUN` sa ukazujú výsledky: čitateľ/menovateľ

### Version 2
```
M0 ;
I    ENT ; KIN4 ; ENT ; KIN1 ; ENT ; KIN5 ; ENT ; KIN2 ; * ; K1 ; = ;
     KIN3 ; ( ; K5 ; * ; K1 ; ) ; + ; ( ; K4 ; * ; K2 ; = ; KIN6 ; K4 ;
     * ; K5 ; = ; MIN ; K6 ; HLT ; K3 ; HLT ; MR ; HLT ; K3 ; HLT ;
     RTN ;
```
- Memory used: 38 steps
- Registers used:
  - `K1` = čitateľ 1.
  - `K2` = menovateľ 1.
  - `K3` = čitateľ 2.
  - `K4` = menovateľ 2.

Program funguje ako v prvej verzii, ale po zadaní 4 čísel sa postupným stláčaním
zobrazujú čitateľ/menovateľ sčítaných(odčítaných),čitateľ/menovateľ vynásobených
(vydelených).
