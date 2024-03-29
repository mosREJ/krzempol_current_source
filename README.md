


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
- OPAMP rail to rail
- dlaczego nie można łączyć wejść https://electronics.stackexchange.com/questions/87780/driving-high-and-low-inputs-of-a-mosfet-driver-with-a-single-pwm-signal

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



# praca impulsowa 
https://www.ti.com/lit/ml/slua618a/slua618a.pdf?ts=1709092997696 

## YT
> https://www.youtube.com/watch?v=DXyTHhUjxjk
- 3:46 -> spoko rozumiem inducka bd wprowadzała zakłócenia (wyższe napięcia) -> i przez to bd niszczyć bramkę?
- sprawdzic czy powermosfety rzeczywiscie maja wieksza pojemnosc bramki (sprawdzic z czego to moze wynikac)
- sprawdzic jak sie bd ładował cap jak mu mocno ogranicze prąd ale zostawie takei same napięcie
- ten efekt z 5:47
- low vs high side
> https://www.youtube.com/watch?v=wY6eGoBea9Y&list=PLbGlpmZLQWJceSkQv96j-L4YyuxS-E0Wm&index=2
- 1:52
- 2:39
> https://www.youtube.com/watch?v=YeUbmOKi0Q4&list=PLbGlpmZLQWJceSkQv96j-L4YyuxS-E0Wm&index=3
- 5:04 może o tym bardziej poczytac/czy to nam grozi przy DC (które na koniec dnia bd AC bo switch)
- 6:16 jak to ma niby działać?
>4 video
- 5:21

> Totem pole 5 video 
- 
> increase speed https://www.youtube.com/watch?v=6pp1jj2oDvo&list=PLbGlpmZLQWJceSkQv96j-L4YyuxS-E0Wm&index=5 
- fast switch = determined by reverse recovery characteristics of diode 
- 3:10 niby jak ta dioda ma jest szybsza niż rezysotor? 
- 5:40 niby jak eliminuje skoki od indukcji?
- 

> Pmos https://www.youtube.com/watch?v=S6-WRdviEwA&list=PLbGlpmZLQWJceSkQv96j-L4YyuxS-E0Wm&index=6
- chujowe be większa Rdson i pojemność 
- ??? krzempol: dlaczego tak?  
  - jaki to może mieć wpływ na cmos?

> https://www.youtube.com/watch?v=em5BuCFSuBw&list=PLbGlpmZLQWJceSkQv96j-L4YyuxS-E0Wm&index=7 

- video od EEV o bypas cap



# TO LEARN/TODO 
- tns elektryka 
  - jak mierzyć oscylem/napięcie siecowe po wyprostowaniu (EEVblog)
- ogarnąć założenia projektowe np. opór minimalny 16 



# Problemy aktualnego rozwiazania:
- jak wygląda SSR w środku: https://www.youtube.com/watch?v=DxEhxjvifyY 

- jak w triak
       - przez to, że można odpalać traka w dowolnej fazie -> zakłócenia = może odpalać się za szybko/za wolno
       - dlatego używa się snubber circuit https://en.wikipedia.org/wiki/Snubber
       -?? czy my jesteśmy w stanie dać tyle miody na SSR przez pin od RPpico? -> ANS: chyba tak, bo optoizolacja to ogarnia, ale sprawdze dla sportu

**!!!!!!!!!!!!!!!!! POMIERZYC PIEC PODCZAS PRACY OSCYL, PRĄD NAPIĘCIA ITD , SOFT POD OSCYL ***************



# Ile prundu ze sterownika

I = dQ/dT 
e.g. 620 nC /

# Temp 
temp rosnie -> Vds rosnie 


- Pmosfety większa Rdson on
- ???? efekt millera?

# Plan wykład:
- obliczanie temperatury pod Robudowy, radiatory itd
- max temp danej obudowy
- moze ten LL jak dziala ciepło
- kalkulator pod sciezki
- o tym, ze na poczatku chcialem dzialac na pradzie stalym i chujnia z moca -> dlaczego impulsowa
-      - analiza tego jaka bd moc (na lini DS) jezeli napiece X
-  dlaczego wyszło hujowo -> bo w stanie on tak czy siak bd dużo mocy + przełąanie dużo wygeneruje śmieci
- o tym czym sa tranzysotry ibgt
- jak dziala opamp -> moja droga jak to zrozumialem
       - moze o tym jak dzial para roznicowa
- jak dziala mosfet
- wplyw temp na mosfet
- konwerter prad napiecie
- jak obliczy łe
- o tym jak czegoś nie ma w ltspice od innych producentów to szukajcie od analgoa (miałem problem z odczytaniem schematu jak to się powinno podłącząć)
- o tym zjawisku millera
