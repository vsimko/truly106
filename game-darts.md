## Použitie kalkulačky pre hru šípky

### (A) Hra pre 1 hráča (klesanie)
```
M0 ;
I    KIN1 ; KIN6 ; 0 ; MIN ; K1 ;
M0 ;
II   ENT ; - ; K1 ; = ; x² ; √x ; KIN1 ;
     1 ; M+ ; K1 ; X>0 ; M1 ; DEC ; MR ;
     HLT ; M0 ; 0 ; MIN ; K6 ; KIN1 ; RTN ;
```

Hráč napíše počet bodov, ktoré dostane na začiatku a stlačí `(I)`.
Potom stlačí `(II)` a na display sa zobrazí zostávajúci počet bodov. Hráč napíše
vždy po hodení sumu, ktorú trafil a stlačí `RUN`. Program sa takto opakuje, až kým
hráč nedosiahne nulu. Hodená suma sa vzdy odpočítava od hráčových bodov a z
tohto čísla sa spraví `ABS` hodnota. Ak hráč dosiahne nulu, program napíše počet
ťahov a display bude vyzerať takto:
```
┌───────────────────┐
│on                d│
│         BODY     I│
└───────────────────┘
```
Po stlačení `RUN`, hra sa opakuje od začiatku. Ak hráč chce skontrolovať,
koľko má ťahov stlačí `MR`, ak chce prezrieť počet zostávajúcich bodov,
stlačí `KOUT 1`.

- Memory used:
  - `(I)`  = 5 steps
  - `(II)` = 21 steps
- Registers used:
  - `K1` = hráčove body
  - `K2, K3, K4, K5` = nepoužité
  - `K6` = register pre počet začiatočných bodov pre opakovanie hry
  - `M` = počet ťahov

### (A/2) Hra pre 1 hráča (klesanie - redukovaná forma)
```
M0 ;
I    - ; ENT ; = ; x² ; √x ; KIN1 ;
     1 ; M+ ; K1 ; X>0 ;
     M1 ; MR ; HLT ; M0 ; RET ;
```

- Memory used: 15 steps
- Registers used:
  - Same as type (A) above


### (B) Hra pre 2,3,4 hráčov (klesanie)
```
M0 ;
I    MIN ; KIN5 ; 201 ; = ; HLT ; KIN[1] ;
                                  ...
                                  KIN[n] ; KIN6 ;
M0 ;                                                        n={2,3,4}
II   K[1] ; - ; ENT ; = ; x² ; √x ; KIN[1] ;
     ...
     K[n] ; - ; ENT ; = ; x² ; √x ; KIN[n] ;
     1 ; M- ; MR ; X>0 ;
     M80 ; HLT ; M9 ; K[1] ; HLT ;
                      ...
                      K[n] ; HLT ; K6 ; KIN[1] ;
                                        ...
                                        KIN[n] ; K5 ; MIN ; RTN ;
```

Na display treba napísať počet ťahov, ktoré budú mať hráči k dispozícii. Po
stlačení `(I)` sa zobrazí:
```
┌───────────────────┐
│on deg             │
│        200   ENT I│
└───────────────────┘
```
Toto číslo znázorňuje počet bodov, ktoré musia hráči znižovať hádzaním šípiek.
Registre `K1`, `K2`, `K3`, `K4`, podľa toho, koľko je hráčov sa naplnia tymto číslom,
pričom je možné ho aj zmeniť. Po stlačení `RUN` a `(II)` sa na display postupne
zobrazuje počet bodov hráča, ktorý je na ťahu, ten po hodení šípky napíše
trafenú sumu a stlačí `RUN`. Takto postupujú hráči cyklicky v určenom poradí. Ak
sa chce hráč presvedčiť, koľko majú súperi bodov, stlačí `KOUT` + číslo hráča,
ktorého chce prezrieť. Ak hráč chce pozrieť zostávajúci počet ťahov, stlačí `MR`.
Ak hráči už nemajú k dispozícii žiadne body, tak sa na display zobrazí:
```
┌───────────────────┐
│on deg             │
│ 0000000000"" ENT I│ Indicates end of the game
└───────────────────┘
```
Teraz po stláčaní `RUN` sa na display postupne zobrazujú body jednotlivých hráčov.
Ak sa zobrazí hodnota posledného hráča, tak po stlačení `RUN` sa hra začne odznovu.

- Registers used:
  - `M`  = zostávajúci počet ťahov
  - `K1` = body 1. hráča
  - `K2` = body 2. hráča
  - `K3` = body 3. hráča
  - `K4` = body 4. hráča
  - `K5` = začiatočná hodnota pre počet ťahov
  - `K6` = začiatočná hodnota pre počet bodov

### (C) Hra pre 2 hračov (vzostupne)
```
M0;
I    MIN ; 0 ; KIN1 ; KIN2 ;
M0;
II   K1 ; + ; ENT ; - ; KIN1 ; K2 ; = ; x² ; √x ; KIN3 ;
     ÷ ; ( ; 1 ; + ; K3 ; ) ; = ; M70 ; RND ; M9 ;
     √x ; * ; K2 ; + ; KIN2 ;
     ENT ; - ; KIN2 ; K1 ; = ; x² ; √x ; KIN3 ;
     ÷ ; ( ; 1 ; + ; K3 ; ) ; = ; M70 ; RND ; M9 ;
     √x ; * ; K1 ; = ; KIN1 ;
     1 ; M- ; MR ; X>0 ; M80 ; HLT ; M0 ;
     K1 ; HLT ; K2 ;
```

- Memory used:
  - `(I)`  = 4 steps
  - `(II)` = 58 steps
- Registers used:
  - `M`  = counter of turns
  - `K1` = score of player 1
  - `K2` = score of player 2
  - `K3` = temporary register used within the program
  - `K4`, `K5`, `K6` = unused
