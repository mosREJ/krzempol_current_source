# Next to do
- [x] clear readmes 
- [ ] check diff btw 18 V and 20 V flyback (if I will be able to easily change output voltage) (https://webench.ti.com/power-designer/switching-regulator/customize/17?noparams=0)
- [ ] clear repo
- [ ] upgrade gitignore
- [ ] analyze voltages, currents and powers of flyback components



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
- **większe footprinty jak lutujemy sami**



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


# To watch:
- Mosfet losses https://www.youtube.com/watch?v=KSOHwVoxpzg&list=WL&index=9
- power losses mosfet https://www.youtube.com/watch?v=RViwOc4g-gw
- pcb tips: https://www.youtube.com/watch?v=kkc8BxL5Eo0&list=WL&index=11
- seperate trans: https://www.youtube.com/watch?v=3rvEdHyAd2k&list=WL&index=23
- thermal pcb design: https://www.youtube.com/watch?v=8v-wC5cM_Yk&list=WL&index=27
- EEV blog pcb review: https://www.youtube.com/watch?v=xhRhsCVF8mE&list=WL&index=30&pp=gAQBiAQB
- TVS: https://www.youtube.com/watch?v=MzxBBXpgwrE&list=WL&index=29
    - just blocks high volatege pulses and converts it to heat (small energy pulses)
    - more power: MOV -> metal oxide varistor
    - GDT Gas Discharge Tube **!! For high voltages +200 V** 
- passive filters: https://www.youtube.com/watch?v=NBLCqqmvy0A&list=WL&index=30
- miller effect: https://www.youtube.com/watch?v=w1PUG_8AsOc&list=WL&index=57
- flyback transformer: https://www.youtube.com/watch?v=VfSc15_XjiQ&list=WL&index=62
- opamp: https://www.youtube.com/watch?v=K03Rom3Cs28&list=WL&index=67&pp=gAQBiAQB
- 2 layers voltage regulator: https://www.youtube.com/watch?v=6AEUxY9QipI&list=WL&index=69&pp=gAQBiAQB
- main volatege + osciloscope: https://www.youtube.com/watch?v=LJ9CO5ViKPI&list=WL&index=70&pp=gAQBiAQB
- how power supply works: https://www.youtube.com/watch?v=cX4q0e124C4&list=WL&index=71&pp=gAQBiAQB
- moc bierna itd: https://www.youtube.com/watch?v=GnGLKBFcxMQ&list=WL&index=68&pp=gAQBiAQB
- ground planes: https://www.youtube.com/watch?v=BsOETPSszJQ&list=WL&index=72&pp=gAQBiAQB
- power planes/routing path: https://www.youtube.com/watch?v=lv8CZSc0o-c&list=WL&index=75&pp=gAQBiAQB
- via stiching: https://www.youtube.com/watch?v=TtSnG-Tl8yM&list=WL&index=74&pp=gAQBiAQB
- pcb ground: https://www.youtube.com/watch?v=Y-WhQ75Tqy4&list=WL&index=76&t=64s&pp=gAQBiAQB
- Feranec:
    - https://www.youtube.com/watch?v=icRzEZF3eZo&list=WL&index=78&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=bU2Ef-2ZIK4&list=WL&index=79&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=vzqZm2IFn6Y&list=WL&index=80&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=vGq4uUtr6Uo&list=WL&index=81&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=vALt6Sd9vlY&list=WL&index=82&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=YounUJvIW04&list=WL&index=83&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=_x2fzKEjUGQ&list=WL&index=84&t=1780s&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=fJCRrEf_IH8&list=WL&index=85&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=qVREULDBtjk&list=WL&index=86&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=fkNa-FejWsQ&list=WL&index=87&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=gHF5JyJF-N4&list=WL&index=88&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=H2eQc4DxK30&list=WL&index=89&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=9lgoL0C7PFc&list=WL&index=90&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=yHn-XOcvJOY&list=WL&index=91&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=2hvMgG6tKdg&list=WL&index=92&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=3L8SaMZxpDw&list=WL&index=93&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=vrt3lL5gEb0&list=WL&index=94&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=kdCJxdR7L_I&list=WL&index=95&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=hNHTwpegFBw&list=WL&index=97&t=5304s&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=j2YGHZG1bLY&list=WL&index=98&t=1299s&pp=gAQBiAQB
    - QFN layout: https://www.youtube.com/watch?v=PsyK1BXdclQ&list=WL&index=99&pp=gAQBiAQB
    - https://www.youtube.com/watch?v=52fxuRGifLU&list=WL&index=100&pp=gAQBiAQB
- heatsink: https://www.youtube.com/watch?v=8ruFVmxf0zs&list=WL&index=101&pp=gAQBiAQB
- emi filters: https://www.youtube.com/watch?v=ABd5O7NJLr0&list=WL&index=105&pp=gAQBiAQB
- parallel mosfets: https://www.youtube.com/watch?v=AOf-i2vLd2o&list=WL&index=107&pp=gAQBiAQB
- design review: https://www.youtube.com/watch?v=eZnyBt2LVoc&list=WL&index=124&pp=gAQBiAQB 
- pcb stackup: https://www.youtube.com/watch?v=QAOEtfvCaMw&list=WL&index=129&pp=gAQBiAQB
- circuit protection: https://www.youtube.com/watch?v=GkXqE4x5Y3A&list=WL&index=132&pp=gAQBiAQB
- pcb options: https://www.youtube.com/watch?v=mT2Vp3HcIP4&list=WL&index=140&pp=gAQBiAQB
- layout fundamentals: https://www.youtube.com/watch?v=HTywk_tlcAk&list=WL&index=142&t=560s&pp=gAQBiAQB
- review deep dive: https://www.youtube.com/watch?v=FztXQ2UwllQ&list=WL&index=144&t=228s&pp=gAQBiAQB
- gate driver: https://www.youtube.com/watch?v=up0lIpZP8cI&list=WL&index=147&pp=gAQBiAQB
- skin effect: https://www.youtube.com/watch?v=FoHD_sW9SiI&list=WL&index=160&pp=gAQBiAQB
- induction satureation: https://www.youtube.com/watch?v=Tl_LH--5Ce8&list=WL&index=158&pp=gAQBiAQB
- proper scope: https://www.youtube.com/watch?v=JTfzgeJYFo8&list=WL&index=165&pp=gAQBiAQB
- power pcb design: https://www.youtube.com/watch?v=56p3_aORiJ0&list=WL&index=179&pp=gAQBiAQB
- how to learn pcb: https://www.youtube.com/watch?v=aODkA2mrimQ&list=WL&index=169&pp=gAQBiAQB
- fft ltspice: https://www.youtube.com/watch?v=rVAvW1Jh2AE&list=WL&index=168&pp=gAQBiAQB
- flyback: https://www.youtube.com/watch?v=-72g1V6v0GQ&list=WL&index=116&pp=gAQBiAQB
- optocoupler: https://www.youtube.com/watch?v=fW0pyb8X0RA&list=WL&index=112&pp=gAQBiAQB
- mosfets parraler: https://www.youtube.com/watch?v=AOf-i2vLd2o&list=WL&index=107&pp=gAQBiAQB
- perferct ppower supply: https://www.youtube.com/watch?v=zf-pvHysroM&list=WL&index=96&pp=gAQBiAQB
- cuuretn: https://www.youtube.com/watch?v=vrt3lL5gEb0&list=WL&index=94&pp=gAQBiAQB
- decouplong caps: https://www.youtube.com/watch?v=u40kX1DYKdA&list=WL&index=184&pp=gAQBiAQB
- mosfet: https://www.youtube.com/watch?v=AwRJsze_9m4&list=WL&index=198&pp=gAQBiAQB
- bypass cap: https://www.youtube.com/watch?v=BcJ6UdDx1vg&list=WL&index=202&pp=gAQBiAQB
- orignal of electronics: https://www.youtube.com/watch?v=FLaTU-t1CQM&list=WL&index=219&pp=gAQBiAQB















