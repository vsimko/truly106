## Compute signum of an integer
#q# ∈ {1,2,3,4,5,6} Vypočíta signum čísla. Je možné použť upravenú formu tohto
programu v iných, signum vyžadujúcich programoch.

### Version 1
```
M0 ;
I/II KIN#q# ; x² ; √x ; ÷ ;
( ; K#q# ; + ; 1 ; EXP ; 99 ; +/- ; ) ; = ;
```
- PRG SIZE: 14 steps

### Version 2
Nevýhoda tejto verzie spočíva iba v tom, že nie je možné zadať číslo v
intervale `(-1;0)U(0;1)`, pretože tieto čísla sa správajú ako `0`, resp. `0,0`.
```
M0 ;
I/II KIN#q# ; x² ; √x ; ÷ ;
( ; K#q# ; + ; 1 ; ) ; = ;
M70 ; RND ; M9 ;
```
- PRG SIZE: 13 steps
