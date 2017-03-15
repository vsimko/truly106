## Here it is! Truly106.
And several programs for the TRULY 106 pocket calculator. Enjoy.

![Truly106](Truly106.png)

The following notation will be used in the text:
```
K1  = KOUT 1
Mx  = mode x (e.g. mode 0, mode ., mode 9,...)
#q# = a variable in our notation, e.g.
      #q# ∈ {1,2,3} or
      #a# = KIN1 ; KIN2 ; KIN3
```

### Find maximum number of a sequence

- PRG SIZE: 4 steps
- REGISTERS: M = contains the maximum entered so far

```
M0 ;
I/II ENT ; X<=M ; MIN ; {RTN} ;
```

### Compute signum of an integer
#q# ∈ {1,2,3,4,5,6} Vypočíta signum čísla. Je možné použť upravenú formu tohto
programu v iných, signum vyžadujúcich programoch.

**Version 1:**
- PRG SIZE: 14 steps
```
M0 ;
I/II KIN#q# ; x² ; √x ; ÷ ;
( ; K#q# ; + ; 1 ; EXP ; 99 ; +/- ; ) ; = ;
```

**Version 2:**
Nevýhoda tejto verzie spočíva iba v tom, že nie je možné zadať číslo v
intervale (-1;0)U(0;1), pretože tieto čísla sa správajú ako 0, resp. 0,0.

- PRG SIZE: 13 steps
```
M0 ;
I/II KIN#q# ; x² ; √x ; ÷ ;
( ; K#q# ; + ; 1 ; ) ; = ;
M70 ; RND ; M9 ;
```

### Primitive timer, clock and alarm
```
 #q# ∈ {36,37,38} podľa vyťaženia baterky
 M0 ;
 I    + ; 1 ; = ; KIN1 ; X<=M ; C ; DEG ; DEG ; MR ; ÷ ; #q# ; ) ; DEG ; DMS
 M0 ;
 II   0 ; DEG ; DEG ; ( ; ( ; K1 ; - ; 1 ; ) ; ÷ ; #q# ; ) ; DEG ; DMS ;
```

- PRG: (I)-15k + (II)-15k = 30k
- REG:
  - K1 = Počítadlo času
  - M = maximálny čas, do ktorého sa bude počítať

Tento program možno použiť ako hodiny, budík a stopky.
Stlačením tlačidla `(I)` sa spustí program a stlačením `on/C` sa zastaví
a zapamätá sa posledná časová hodnota, ktorá je uložená v `K1`.
Po stlačení `(II)` sa zobrazí
```
 ┌───────────────────┐ HH = Hodiny
 │on deg             │ MM = Minúty
 │ HH"MM"SS.xx  ENTII│ SS = Sekundy
 └───────────────────┘ xx = Stotiny
```
Ak chceme použiť kalkulačku ako hodiny, musíme postupovať takto:
Navolíme aktuálny čas `HH:MM:SS = 13320*HH + 2220*MM + 37*SS` Potom stlačíme `(I)`.
Teraz už beží čas! Ak sa chceme naň pozrieť, stlačíme `on/C` a následne `(II)`
nakoniec, aby mohol čas bežať ďalej, stlačíme `K1` a `(I)`.

**POZOR!!!** Hrozí zlyhanie systému. Ak máme nainštalovaný tento program,
vypneme kalkulačku a potom ju zapneme bez resetu (ľubovolné. tlačidlo + `on/C`)
a následne spustíme program `(I)`, začne kalkulačka vykonávať krokovací režim.
Ten však bude zapnuty donekonečna, pretože program obsahuje príkaz skoku na
začiatok a neobsahuje príkaz prerušenia.

**POMOC:** Vybrať baterku.


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

### Pseudo-random number generator
```
M0 ;
I    MR ; ENT ; MIN ;
     K1 ; ENT ; KIN1 ;
     - ; ( ; K1 ; + ; K2 ; ) ; ENT ; x<->y ; = ; KIN2 ;
     K3 ; ENT ; KIN3 ;
     K4 ; ENT ; KIN4 ;
M0 ;
II   MR ; TAN ; * ; K4 ; = ; MIN ;
     M70 ; RND ; * ; K3 ; + ; K4 ; ÷ ; MR ; = ; KIN5 ; ÷ ; K2 ; = ; RND ;
     * ; K2 ; - ; K5 ; + ; K2 ; ÷ ; 2 ; + ; K1 ; = ; RND ; M9 ;
```
- PRG: `(I)`-22k + `(II)`-33k = 55k
- REG:
  - `K1` = min
  - `K2` = (max) rozsah
  - `K3` = const
  - `K4` = delivé
  - `K5` = prechod
  - `K6` = nič
  - `MR` = randomize

Program pozostáva z dvoch programov a to prípravnej fázy a samotného generátora.
Po stlačení tlačidla `(I)` si program bude vyžadovať potrebné údaje a to pomocou
zabrazeného nápisu `ENT` na displeji. Tieto údajé sa zadávajú napísaním čísla
a následným stlačením tlačidla RUN. Program si vyžiada nasledujúce údaje v
takomto poradí:
1.   Úvodné odvíjajúce sa číslo (najlepšie je aktuálny čas a to takto
     hodiny a minúty napr: `12h 36min`  ako `1236`
     Číslo sa zapíše do registra `M`, ktorý je použitý ako generátor. Je to
     najhlavnejší register. Nesmie sa v ňom však vyskytovať číslo, ktoré pre
     funkciu `cos` dáva `0`. čiže je to číslo `90(2k+1)` napr. `90,270` ...
     Toto platí samozrejme pre stupne ( `DEG` ).
2.   Spodná hranica intervalu, z ktorého program vyberie náhodné číslo.
     Pre hru je to číslo `1`.
3.   Vrchná hranica intervalu, z ktorého program vyberie číslo.
     Pre hru je to číslo `10`.
4.   Toto číslo zabezpečuje potrebnú vyváženú frekventovanosť čísel odporúčam
     pre interval `<1; 10>` číslo `20`
5.   Toto číslo je potrebné na kontrolu generátora a používa ho iba program.
     Odporúčam hodnotu `53` alebo `64`

Teraz už prvý program ukončil svoju činnosť a po sláčaní tlačítka `(II)` sa na
displej zobrazí náhodné číslo z požadovaného intervalu.

**Notes:**
Ak zvolíte interval, ktorý bude obsahovať aj číslo `0`, bude sa občas okrem tohto
čísla objavovať aj zvláštne číslo `0.0`. Toto je výhodné, pretože ho možno považo-
vať aj za `0`, aj za akúsi mimoriadnu prémiu.
Niekedy sa po stlačení `(II)` objaví na displeji znak `- E -`. Toto znamená, že
generátor pretiekol(overflow), pri generovaní aktuálneho
pseudonáhodného čísla. Na svedomí to má register `K4`, v ktorom sa nachádza
konštanta na kontrolu generátora. Nemuselo by to nastať zvolením správnej
konštanty, ibaže tá je periodické číslo a vzhľadom na to je ťažko ju dať do
kalkulačky. Nepoznám presnú jej hodnotu. Skúste trochu experimentovať. Ak už
teda svieti `- E -`, stlačte `ON/C` potom tlačítko `I`, napíšte znova aktuálny čas,
stlačte 5-krát tlačítko `RUN` a potom už môžete opäť stláčať `(II)`.
