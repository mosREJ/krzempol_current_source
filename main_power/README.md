# Shourcut
- measure:
    - measure -> space -> dx/dy
    - measure -> ctrl+shift+m 
    - change value -> v
    - change wire settings -> E

https://login.ti.com/as/authorization.oauth2?response_type=code&scope=openid%20email%20profile&client_id=DCIT_ALL_WEBENCH&state=zmGa_QvdwrxxyaEzjCNcNcGsxm8&redirect_uri=https%3A%2F%2Fwebench.ti.com%2Foidc%2Fredirect_uri%2F&nonce=JZkHs6HarKipyuITWvLmF3UyMggR8fZSRZZmQNaUnbE&response_mode=form_post
# Layers
- Courtyard -> element safe zone
- F/B.Fab -> info for fab (guess dont care this case)
- F/B.Adhesive -> jeżeli element wymaga dodatkowego łączenia np. kleju
- F/B.Paste -> pod solder paste
- EdgeCuts -> PCB edges 
- Margin -> boards for elements

## Phisical Stackup
- based on pcb manufacuter e.g. jlcPcb

## Design rules -> Constrains
- based on pcb manufacuter 

## ?? Net classes?
1. do this on schematic 
2. or "schematic setup option" (left top icon on schematic view)

> How about other/non labaled connections

- NetClass Derivative tool (right side, under lablel option)
    - dotted option, smaller one -> even **hide**

## Edge layer 
- choose correct layer
- **use lock**

> !! **Selection filter**


# Rat lines 
- right top under cursor icon -> will show ratlines only for choosen pin

# Mark and allign (properties)


# Adding 3D model 
1. choose footprint -> properties -> 3dmodels

# Via 
- right side icon

# Nets in pcb view
- right side, near "layers" view 




# things to do/check:
- led wskaźniki 
- jumpery to lutowania 
- o co cho z tym, recovery diody
- layout z zasilacza ATX obczaić jak oni to zrobili (co jest power plane)



# power/current limitations/considerations

## rectifier bridge
- 2 first pictures are based on wrong diode (fast recovery + big Vf) 
- **!! choose diodes with OK Vf/power/curr + ok rec time**
- **!!! learn how to count power diss**
- prop: https://www.mouser.pl/ProductDetail/Panjit/RPMS310_R2_00601?qs=pBunHO6%252BwtENZQeToJ4UFg%3D%3D 
- have forgotten: we will swich so power on bridge will decrease (but care on rec time) 




# Filtraton
- ferrite 
- varistor
- inside old atx powesupply:
    - 


# Safety 


# Potenial to buy
- diode rect: prop: https://www.mouser.pl/ProductDetail/Panjit/RPMS310_R2_00601?qs=pBunHO6%252BwtENZQeToJ4UFg%3D%3D 
    - connect to heatsink 
- AC connector 15 A (just to be safe)

# PE, N, L
- PE as separate line e.g. for heatsinks (as in ATX)


# YT tips

- IBOM plugin


> https://www.youtube.com/watch?v=ycT-PItAzNk&pp=ygURZmx5YmFjayBjb252ZXJ0ZXI%3D

1. Add comment of LED's color (in case of other componets might be Vf, brakdown etc)
2. Stay consits in nameing convenion
3. Info what connectors do
4. Set all this way other ppl/you dont need to bend their head (poiting up/horizontal)
5. Dont need to add units e.g. F/H for passive components
6. Flag type (outptu/input)
7. Label usefull connections (e.g. for debuggin purpose)
8. Puts decupling caps
9. Have space on PCB -> use it, avoid crasstalks
10. Power/GDN vias:
    1. track width same as pad widt 
    2. quite close to pad
11. Avoid sharp 
12. Be carefull: signal/power loops
13. Non top1% pcb: TOP: GND 
14. Via hole vs diamater !! (annular ring)
15. ! Silkscreen on copper 
16. End vias connection as fast as possible to avoid emc


> https://www.youtube.com/watch?v=ywBPm7TMpfk Schmeatic tips and tricks

1. Section schematic if nedded 
    1. What connection used (SPI, I2C etc)
2. Subsections
3. Text of baisc calculations
4. Symbol -> pin set in logical way (left - input, right outputs)
5. Try to labal as much as possible - it's usefull when routing
6. HORIZONTAL !!!
7. max 3 juncions in schematic
8. Take care of elements order in schematic and how they close are (e.g. low C (high Freq capacitor should be closer to elements)) than high capacity 
9. decupling caps -> in shcematic and pcb -> close to element
10. Color labels on schmeatic 
11. At the end he shows whats wrong in example

> https://www.youtube.com/watch?v=D0X76Kbf8fQ

1. Spacing !! 
2. Via size/dimenssn
    1. always at least hole size > 0.3 mm + diamater 
3. **!! TEN TOOL OD SATURN**
4. decupling caps -> close and thick traces


> https://www.youtube.com/watch?v=XkFncBaFlB8

1. Power/gnd plane with digital 
2. It's ok to mix power traces/power planes
3. digital signal btwn layers -> dont trace them pararelly
Do: layer1 horizontaly layer2 verticaly -> It's called **Ortogonal routing**

> https://www.youtube.com/watch?v=1XpJwICKz2M

1. 





# OVERALL PLAN/TO REMB

- [ ] images like "primary"/"secondary" !! HIHG voltage
- [ ] testpoints/testhooks
- [ ] important info on schmeatic 
- [ ] indent like on ref pcb
- [ ] ??? near 330 V intends?
- [ ] Rgate not fitted
- [ ] ??how to power plane/PE/L/N?
- [ ] fuse
- [ ] 0 ohm?
- [ ] additional footprints for 330V cap/other caps
- [ ] jumper for mosfet independed work
- [ ] opamp as current measure
    - [ ] limit it's input voltage mabye using zener diodes?
- [ ] led indicators
- [ ] stedown 20 V/flyback -> linear 5 V 
    - [ ] how to deal with USB? (maybe usb cable by defu?)
- [ ] temperature sensor?
- [ ] filtering + safety elements
- [ ] ?? current safaty cutoff??
- [ ] gatedriver with enable (pull down?)
    - [ ] good if optoisolatin
- [ ] electrostatic? safry tvs?
- [ ] hihg curr/freq -> avoid sharp degre
- [ ] learn how to use power plane 
    - [ ] think how use it in our case 
- [ ] via stiching
- [ ] TVS for pi pico
- [ ] gnd under pico 
- [ ] switch for 5V bord vs usb





# Pytania doktor
- dławik po stronie 230?
- capy na lini 230 (100nF i 1nF)



