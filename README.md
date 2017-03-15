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

Vnútorné registre kalkulačky:
```
┌───────────────────────┐
│  Registre:            │
├───────────────────────┤
│  X  =  Display        │
│  Y  =  Prenosný (L1)  │
│  M  =  Norm. pamäť M  │
│  K1 =  Konšt. mem 1   │
│  K2 =  Konšt. mem 2   │
│  K3 =  Konšt. mem 3   │
│  K4 =  Konšt. mem 4   │
│  K5 =  Konšt. mem 5   │
│  K6 =  Konšt. mem 6   │
│  L2...L6 registre     │
└───────────────────────┘
```

```
X-register:    Je to register údajov zobrazovaných na displeji, pričom je použí-
               vaný pri aritmetických operáciách spolu s Y-registrom.
Y-register:    Dočasný register, do ktorého sa uschová hodnota a operácia sa
               uskutoční medzi X a Y registami. Tento register možno nazvať aj
               ako L1-register.
M-register:    Nezávislá pamäť, ktorá je známa aj zo starších typov kalkulačiek.
K1..K6-reg.:   Pamäť pre konštanty (constant memory) alebo registre pre medzi-
               výsledky, poprípade registre používané pre mód STATICAL CALCULATION.
L2..L6-reg.:   Tieto registre sú používané v operáciách, kde sa používajú zátvor-
               ky, delenie alebo násobenie spolu s sčítavaním alebo odčítavaním
               prípadne iné operácie využívajúce vedľajšie výsledky, ktoré je
               treba uskladniť v registroch.
```

Základné aritmetické výpočty:
- Sčítanie,Odčítanie,Násobenie,Delenie
- Počítanie s percentami
- Operácie s číslami s pohyblivou čiarkou (floating points)
- Vrátane počítania s viac ako 15 zátvorkami v max 6 úrovniach

Programy pre kalkulačku Truly106 by som rozdelil do niekoľkých skupín:
1. Doplňujúce funkcie kalkulačky
2. Výpočet vzorcov
3. Využívajúce podmienené skoky
4. Konvertujúce
5. Pre zábavu

Samozrejme niektoré programy obsahujú prvky viacerých skupín, preto nie je možné
jednoznačné zaradenie do určitej skupiny.
