## Prevedenie periodického čísla na zlomok
```
I   KIN1 ; * ; 1 ; EXP ; 10 ; - ; K1 ; = ; KIN1 ; KIN3 ;
    1 ; EXP ; 10 ; - ; 1 ; = ; KIN2 ; KIN4 ;
    
II  M70 ; K2 ; x<->K1 ; x<->K2 ; - ; K2 ; = ; x>0 ;
     K2 ; ÷ ; K1 ; - ; 2 ; 1/x ; = ; RND ;
     * ; K1 ; +/- ; + ; K2 ; = ; KIN2 ; x>0 ;
     M9 ; K1 ; ÷ ; K3 ; x<->y ; = ; HLT ; K4 ; ÷ ; K1 ; = ;
```
