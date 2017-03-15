### Game: Hádenie čísel (+;-)
```
#?# ∈ {7,8}
#voľba#: ENT ; SHIFT #?# [opakovať najviac 27-krát]
M0 ;
I    MIN ; 1 ; +/- ; KIN1 ; K6 ; M1 ; HEX ; HLT ; K1 ; #voľba# ; K5
```

Tu sú príklady niektorých možností nastavenia:
```
#?# = 7,8,8,8,7,7,7,8,8,7,8,8,8,8,7,8,7,7,7,8,7,8,7,8,7,8,7,7
#?# = 8,7,7,7,8,8,8,7,7,8,7,7,7,7,8,7,8,8,8,7,8,8,7,7,8,8,8,8
#?# = 8,8,7,8,7,7,7,8,8,7,7,7,7,8,8,8,8,7,8,7,8,7,8,8,7,7,7,8
#?# = 8,8,7,7,8,7,8,8,8,8,7,8,7,7,7,8,7,8,7,8,7,7,8,8,7,7,8,7
```
- PRG: 9k + X*2k
- REG:
  - `K1` = číslo napr. -1
  - `M`  = číslo 0
  - `K6` = číslo, ktoré indikuje začiatok, napr. `8888888888`
  - `K5` = číslo, ktoré indikuje koniec, napr. `1111111111`

Pravidlá hry: Stláčaním `(I)` sa spustí program.
```
┌───────────────────┐
│on deg             │
│ 8888888888   ENT I│
└───────────────────┘
```
Po stlačení `RUN` sa na display zobrazí:
```
┌───────────────────┐
│on deg             │
│         -1   ENT I│
└───────────────────┘
```
Stlačením `+/-` si hráč navolí kladné alebo záporné číslo.
Kódy pre `#?#` znamenajú:
- 7 = vráti sa na začiatok ak `{x>0}`
- 8 = vráti sa na začiatok ak `{x=<M}` (pričom `M=0`)

Tu je tabuľka, ako bude reagovať program na vzniknuté situácie:
```
┌──────┬───┬───────────┐
│voľba │ X │na začiatok│
├──────┼───┼───────────┤
│{x>0} │ + │    ÁNO    │
│{x>0} │ - │    NIE    │
│{x=<0}│ + │    NIE    │
│{x=<0}│ - │    ÁNO    │
└──────┴───┴───────────┘
```

Na konci programu sa zobrazí:
```
┌───────────────────┐
│on deg             │
│ 1111111111   ENT I│
└───────────────────┘
```
