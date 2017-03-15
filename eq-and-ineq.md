## Skúška správnosti pri rovniciach a nerovniciach

### ROVNICE: Ľ=P
```
M0 ;
I    C ; C ; C ; C ; C ; C ; C ;
M0 ;
II   ( ; Ľavá strana ; ) ; - ; ( ; Pravá strana ; ) ; = ;
```

- Registers used:
  - `K1`, `K2`, `K3`, `K4`, `K5`, `K6` = Slúžia ako premenné alebo parametre

Program odčíta Pravu stranu od Ľavej strany. Ak sa výsledok = 0 alebo veľmi malé číslo
napr. `3.10^-12` => Ľ=P

### NEROVNICE: Ľ>=P
```
M0 ;
I    - ; MR ; = ; KIN6 ; KIN4 ; + ; MR ; = ;
M0 ;
II   K6 ; + ; MR ; = ; KIN6 ;
     ( ; Pravá strana ; ) ; = ; KIN5 ;
     ( ; Ľavá  strana ; ) ; = ; - ; K5 ; = ; X>0 ; K6 ; HLT ; MR ; = ;
     +/- ; MIN ; K4 ; KIN6 ; RTN ;
```

- Registers used:
  - `K1`, `K2`, `K3` = Slúžia ako parametre
  - `K4` = Hodnota počiatočnej pozície počítadla na začiatku je zhodná s `K6`
  - `K5` = Je to nosič pravej strany
  - `K6` = Slúži ako počítadlo, ku ktorému sa pripočítava reg. `M`
  - `M` = Slúži ako krokovač `STEP`

Pri tomto programe treba dávať pozor na štruktúru programovania.
Treba začať počítadlom. je to premenná v nerovnici. Ostatné `K1`, `K2`, `K3`, `K4` sú len
parametre, ktoré budú nemenné. Ďalej treba dávať pozor, aby bola prvá PRAVÁ
STRANA a potom ĽAVÁ STRANA. Nerovnica je vždy Ľ>=P, teda ak máme  príklad
P>=Ľ treba ho prerobiť na Ľ>=P  => P->Ľ a Ľ->P. Na konci sa na displey napíše
krajný bod intervalu:    ak `M>0 => ...,x>`
                         ak `M<0 => <x,...`
do pamäte `M` si zapíšeme veľkosť krokov, po ktorých bude program postupovať pri
určovaní intervalu. Ak je kladné číslo postupuje dopredu, ak je záporné číslo,
postupuje dozadu.
