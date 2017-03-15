### Výpočet vektorového súčinu vektorov u x v a výpočet císla d v analytickom vyjadrení priamky ax+by+cz+d=0;
```
M0 ;
I    ENT ; KIN1 ; ENT ; KIN2 ; ENT ; = ; = ; KIN3;
     ENT ; KIN4 ; ENT ; KIN5 ; ENT ; KIN6 ;
     * ; K2 ; - ; K5 ; * ; K3 ; = ; MIN ; HLT ;
     K3 ; * ; K4 ; - ; K6 ; * ; K1 ; = ; KIN3 ; HLT ;
     K1 ; * ; K5 ; - ; K4 ; * ; K2 ; = ; KIN6 ;
M0 ;
II   MR ; +/- ; * ; ENT ; - ; K3 ; * ; ENT ; - ; K6 ; * ; ENT ; = ;
```

Povedzme, že máme:
```
Vektory u=[u1,u2,u3] v=[v1,v2,v3]
        w=(u x v)    w=[w1,w2,w3]
Bod M=[x,y,z]
```

Chceme vypočítať priamku `p: w1*x+w2*y+w3*z+d=0`, ktorá prechádza bodom `M` a jej
normalový vektor (tu je `w`) je kolmý na vektory `u` a `v`.

Po stalčení `(I)` zadávame postupne `u1`, `u2`, `u3`, `v1`, `v2`, `v3` a dostávame `w1`, `w2`, `w3` pri
stlácaní tlacidla `RUN`. Po stlačení `(II)` zadávame postupne `x`, `y`, `z` a dostaneme
císlo `d` a má celé analytické vyjadrenie tejto priamky.

- Memory used:
  - `(I`)  = 42 steps
  - `(II)` = 13 steps
