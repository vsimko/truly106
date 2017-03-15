## Here it is! TRULY 106.
And several programs for the TRULY 106 pocket calculator. Enjoy.

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
