### Prevod komplexného čísla z algebraického tvaru na goniometrický tvar

Komplexné číslo `a+b.i`, kde `a` je reálna `b` imaginárna časť, môže byť vyjadrené
niekoľkými spôsobmi. Z toho najviac využívaný je algebrický tvar komplex.
čísla `(a+b.i)` alebo v elektrotechnike sa používa tiež goniometrický tvar.
`|z|(cos(⍺) + i.sin(⍺))`. Na prevod z algebrického tvaru do goniometrického sa
veľmi efektívne dá využiť tento program.
```
algebrický tvar   : z=a+b.i
goniometrický tvar: z=|z|.(cos(⍺)+i*sin(⍺))
```

```
M0 ; 3 ;
I/II ENT ; KIN1 ; = ;
     ENT ; KIN2 ;
     x² ; + ; K1 ; x² ; = ; √x ; HLT ;
     K2 ; ÷ ; K1 ; = ; tan-1 ; DMS ;
```

- Memory used: 18 steps
- Registers used:
  - `K1` = reálna časť komplexného čísla `a`
  - `K2` = Imaginárna časť komplexného čísla `b`

Presne tak isto funguje už zabudovaná funkcia kalkulačky `MODE 6` - komplexné
čísla, pričom po zadaní `a, b` v rectangularnej sustave je
možné ich prekonvertovať na `|z|, ⍺` v polárnej sústave a zároveň aj počítanie s
nimi.
