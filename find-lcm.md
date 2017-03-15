## Least common multiple (LCM including GCD)
```
M0;
I x<->K1 ; x<->K2 ; K1 ; * ; K2 ; = ; = ; = ; KIN3 ;
M0;
II  M70 ; K2 ; x<->K1 ; x<->K2 ; - ; K2 ; = ; x>0 ;
  K2 ; ÷ ; K1 ; - ; 0.5 ; = ; RND ; * ; K1 ; +/- ; + ; K2 ; = ; KIN2 ; x>0 ;
  M9 ; K1 ; ÷ ; K3 ; x<->y ; = ; HLT ; K1 ;
```

Napíšete 1. číslo, stlačíte `(I)`, potom napíšete 2. číslo, znova stlačíte `(I)`.
Objaví sa ich násobok `a*b`. Potom stlačte `(II)` a objaví sa ich **LCM**, ak stlačíte
ešte `RUN` objaví sa ich **GCD**.
