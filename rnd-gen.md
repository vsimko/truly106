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
- **Memory used:** `(I)`-22k + `(II)`-33k = 55k
- **Registers used:**
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

