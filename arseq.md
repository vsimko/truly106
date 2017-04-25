## Zistenie hodnoty r-tého člena aritmetickej postupnosti pomocou hodnoty s-tého člena a diferencie.
```
M0 ;
I/II ENT ; KIN1 ; ENT ; KIN2 ; ENT ; KIN3 ; ENT ; KIN4 ;
     K3 ; + ; ( ; K1 ; - ; K2 ; ) ; * ; K4 ; = ;
```

`A_r = A_s + (r-s)*d`.

Zadávame postupne `r`, `s`, `A_s`, `d` a dostaneme `A_r`.
- Memory used: 18 steps
- Registers used:
  - `K1` = číslo hľadaného prvku `r`
  - `K2` = číslo niektorého prvku `s`
  - `K3` = hodnota tohto prvku `A_s`
  - `K4` = diferencia `d`
