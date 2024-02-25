


# TODO:
-    praca z wyprostowanym sieciowym: (230 * 1.41) + 100 V zapasu (max napięcie Uds mosfeta)
-    prąd do 10 A ciągłego (przy takim prądzie temp max 40 stC)
-    feedback prądu do MCU
-    MCU przez DAC (może pwm) zadaje prąd
-    zabezpieczenie, że jak DAC nie nadaje, to domyślnie możemy sobie wybrać np. zworką prąd max
-    układ do HW do odcinania powyżej prądu X
-    filtr 230 przed mostkiem
-    układy przeciwprzepięcieowe np. warystor
-    zapewne jakiś driver do mosfeta albo separacja galwaniczna, aby nie zabijało rasberki
     - albo dodatkowy pin odpala mosfeta, który odpala głównego mosfeta
- wykres mocy w zależnosci od warunków 
- update ltspice
- 2 uncjowa miedz -> kalkulator 
- dummy load electronics stack exchange
- projektowanie pcb pod optotranzystor 
- jakas blokada na pin od dac, aby np. przez jakis czas nie pluj 1
- zabzp temperaturowe 
- jakieś zabezpieczenie, że jak rasbar się wywali to piec powoli opada (duża stała RC + gpio które zawsze powinno podtzymywac)
- analiza temp + może jakieś pomiary
- jaka temp/watów bez radiatora ogarnie TO-92 220


# notes 

- current limiter (as ref): https://www.ti.com/lit/ds/symlink/tl4242-q1.pdf?ts=1708331096759&ref_url=https%253A%252F%252Fwww.google.com%252F 







# How to opamp
- jak dziala para różnicowa 
- konwerter prąd napięcie 


## EEblog 
> rules

1. inputs: no current flow in 
    - why this rule is used? -> Rwe jest na tyle duże, że przez dzielnik napięcia tak czy siak większość napięcia odłoży się na dolnej częśći
2. opamp tries to keep inputs the same voltage
    - !! oonly id closed loop with negative feedback?? !!! 
    - tries to do it with feedback 
* gain is huge


- ?? dlaczego zapomnieć o tym jako wzmacniaczu różnicowym

- ?? co jeżeli weźmiemy odwracajac/nieodwraca przy napięciu symetryczyn ale 1 z inputów do masy

- symulacja gdy wrzucimy jakis impuls a w układzie bd capy  (duży cap 100uf ogarnie noise  31:34-> sprawdzic jaka bd wtedy czestotliwosc)

### Buffer 
[ ] done in LTspice?? 
- podobno używane, bo duża impedancja wewnt nie zabuża sygnału z czujnika albo filtru -> buffor i cyk do układu
[ ] ale jeżeli na wejściu mamy mocno impedancyjny układ (filtr z dużym R) ? to tak czy siak nie wpłynie












# Prototyp, test na małych napięciach 
- [ ] pomierzyć dokładnie rezystancje elementów w temp pok przed pomiarem np. 4W siglentem 
- [ ] przy testach na większych prądach (np. przy zasilaniu 48V) -> lepsze radiatory + radiator na rezystor Rl)

> Obserwacja: 
- odłączyłem Vin (wcześniej 0.1 V) - prąd podskoczył do 0.6 A -> przenalizować i obczaić jaki to bd miało wpływ gdy np. DAC się wyjebie 
- ogólnie zrobić analize co się stanie jak X 



## Docs 
- opamp: https://pdf1.alldatasheet.com/datasheet-pdf/view/7456/NJRC/JRC4558D.html   https://www.rcscomponents.kiev.ua/datasheets/jrc45584i743ncft874nfdt34ufguygf43.pdf
- tran: https://www.vishay.com/docs/91070/91070.pdf 


## Pomiary po ostygnięciu 
- Rs: 0.270 - 0.268
- Rl: 22.09

