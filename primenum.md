### Rozloženie čísla na súčin prvočísel
```
M0 ;
I    MIN ; 1 ; KIN1 ; MR ; √x ;
M0 ;
II   K1 ; + ; 1 ; = ; KIN1 ; M1 ; MR ; - ; MR ; ÷ ; K1 ; * ; K1 ; = ;
     M0 ; X>0 ; MR ; ÷ ; K1 ; = ; MIN ; 1 ; X<->K1 ; HLT ; MR ; HLT ; RTN ;
```
- Memory used:
  - `(I)` = 5 steps
  - `(II)` = 27 steps
- Registers used:
  - `K1` = counter
  - `M`  = sem sa uloží skúšané číslo
  
Tento program dokáže rozložiť každé číslo `x ∈ N` na súčin prvočísel. Napíšete na
display číslo, stlačíte `(I)`, následne sa ukáže `√x` a táto hodnota sa zapíše do `M`.
V `K1` sa nastaví hodnota `1`. Stlačením tlačidla `(II)` sa začne odpočítavanie.

Program funguje takto: Hľadá čísla od `2` do `∞`, ktoré delia zadané číslo bez zvyšku.
Akonáhle nejaké číslo spĺňa podmienku, objaví sa a `M` sa ním vydelí. Je to
práve jeden z deliteľov. Nové vyhľadávanie treba potvrdiť tlačidlom `(II)`, alebo
je ešte predtým možné stlačiť `RUN`, čo ukáže zostavajúcu hodnotu v `M`. Ak tam
je číslo `1`, `2`, `3`, `5`, `7`, `11`, ... nie je potrebné ďalšie vyhľadávanie, pretože je to
posledný deliteľ. Ak je to však veľké číslo, a predsa je prvočíslom, program bude
počítať až do jeho hodnoty, preto je dobré zapamätať si `√x` a pri dlhšej zaneprázdnenosti
kalkulačky stlačíte `on/C` a ak sa v `K1` nachádza väčšie číslo ako `√x`,
deliteľ sa nachádza v `M`.
