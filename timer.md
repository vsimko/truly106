### Primitive timer, clock and alarm
```
 #q# ∈ {36,37,38} depends on the battery power level (calibrate for yourself)
 M0 ;
 I    + ; 1 ; = ; KIN1 ; X<=M ; C ; DEG ; DEG ; MR ; ÷ ; #q# ; ) ; DEG ; DMS
 M0 ;
 II   0 ; DEG ; DEG ; ( ; ( ; K1 ; - ; 1 ; ) ; ÷ ; #q# ; ) ; DEG ; DMS ;
```

- PRG: (I)-15k + (II)-15k = 30k
- REG:
  - K1 = Time counter
  - M = Maxiumum value of K1 to count to

This program can be used as a clock, alarm or timer.
By pressing `(I)` the program starts counting from the current value stored in register `K1`.
Display turns off, but don't worry.
If you press `on/C`, the programm stops counting and shows the last time value stored in the
counter `K1`. To convert the value into Hours/Minutes/Seconds, press `(II)`:
```
 ┌───────────────────┐ HH = Hours
 │on deg             │ MM = Minutes
 │ HH"MM"SS.xx  ENTII│ SS = Seconds
 └───────────────────┘ xx = Hundredths
```
If you want to use your calculator as a real clock, follow these instuctions.
Type your current time, e.g. by looking at your wrist watch, using this formula:
```
HH:MM:SS = 13320*HH + 2220*MM + 37*SS
```

Then, press `(I)` and the clock is now ticking in the background. Of course, you cannot
see anything on the display when the calculator is computing.
To see the current time, press `on/C` and `(II)`.
Be quick though, any seconds that you spend looking at the current time will add to the overall imprecission of the clock.
To continue, press `K1` and `(I)`.

**WARNING!!!** System might fail when this program is installed.
It usually happens if you turn off the device, then turn it on without
reseting the calculator (Reset = any key + `on/C`).
Then, if you start the programm by pressing `(I)`, the calculator goes into
a "stepping mode" which loops forever because the progam does not contain
any jumps nor breaks.

**HELP:** Take out the battery.
