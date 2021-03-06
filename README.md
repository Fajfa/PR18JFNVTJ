# Crimes in Chicago
https://www.kaggle.com/currie32/crimes-in-chicago

## Končno poročilo

## Skupina

 * Jože Fortun
 * Neža Vehovar
 * Tomaž Jerman

# Osnovne statistike

### Začeli smo tako da smo za vsako leto od 2001 do 2016 prešteli število kriminalnih dejanj in jih izrisali v grafu:
![alt text](./assets/CrimePerYear.png)
Na grafu se vidi, da se je število krimninalnih dejanj iz leta 2005 do 2011 naraslo. Od leta 2011 pa je v padcu. 
Ta padec v kriminalu lahko pripišemo novemu županu, ki je naredil velike reforme v policiji.
Trenuto Chicago beleži 14 zaporedni mesec, ki ima nižjo stopnjo kriminala kot prejšnji.

### Enako smo naredili za mesece v letu:
![alt text](./assets/CrimePerMonth.png)

### In za letne čase:
![alt text](./assets/CrimePerSeason.png)
Logično se zdi, da se stopnja kriminala poveča ko je zunaj bolj vroče in zmanjša, ko je mrzlo.

Zanimalo nas je tudi, če polna luna vpliva na kriminal. Izkazalo se je, da nima takega velikega vpliva. 
Število kriminalnih dejanj se je povečalo za manj kot procent, v primerjavi z dnevom, ko ni bilo polne lune.



### Nato smo izrisali graf vrst kriminala:
![alt text](./assets/CrimeType.png)
V Chicagu prevladuje kraja, ki je kar 22% vseh zločinov. 
Na drugem mestu so napadi s hudo telesno poškodbo, ki predstavljajo malo manj kot petino zločinov.
Blizu za njimi sta kriminalna škoda in zločini povezani z drogami.
Ostale vrste kriminala so manj pogoste. 
Chicago ima kar 11% kriminala, ki je nasilne vrste. Državno poprečje ZDA je 4%.


### Graf  10 najpogostejših lokacij kriminala:
![alt text](./assets/CrimeLocation.png)
Chicago ima veliko tolp zato nismo presenečeni da se kar 30% vsega kriminala zgodi na cesti. Od kraje, do preprodaje drog in strelskih obračunov med tolpami. 
Stopnja kraje in vlomov je velika zato so prebivališča drugo najpogostejše mesto kjer se odvija kriminal.


### In nazadnje, delež aretacij.
![alt text](./assets/Arrests.png)
Delež aretacij je 25%. To je lahko zato ker ne odkrijejo storilca kriminalnega dejanja, ali pa dejanje ne zahteva aretacije. 
Z dodatno raziskavo smo ugotovili, da veliko umorov, kraje in napadov ostane nerešenih, kar posledično vpliva na delež aretiranih glede na vse zločine.
Če sklepamo da so aretacije število zločinov, ki jih rešijo, je Chicago pod državnim povprečjem, ki je 40%


# Podatki prikazani na zemljevidu
Za lažjo vizualizacijo smo poiskali zemljevide Chicaga, ki so vsebovali informacije zanimive za naš projekt.
Nato pa smo z pomočjo GoogleMaps API izrisali "heat mape" kriminala na sploh in določenih tipov. Te slike smo spremenili v gife za lažjo simulacijo časa.


## Prihodek na gospodinjstvo
![alt text](./assets/WealthMap.png)

Zanimalo nas kako prihodek vpliva na stopnjo kriminala.

## Lokacije tolp v Chicagu
![alt text](./assets/Gangs.jpg)

Predeli kjer so tolpe najbolj aktivne.

# Spreminjanje kriminala čez leta na zemljevidu
![alt text](./assets/CrimesThroughYears.gif)
Gif prikazuje kako se je lokacija vsega kriminala spreminjala skozi leta. 

## Spreminjanje različnih tipov kriminala čez leta

### Napad
![alt text](./assets/Assault.gif)
Lokacija napadov po mestu.

### Napad s hudo telesno poškodbo
![alt text](./assets/Battery.gif)
Lokacija napadov s hudo telesno poškodbo po mestu.

Zanimivo je da se lokacije obeh vrst napadov pokrivajo z lokacijo tolp v Chicagu.

### Ropanje
![alt text](./assets/Theft.gif)
Lokacija ropov v mestu. Teh je največ tam kjer so bolj premožni ljudje, kar je tudi logično.

### Vlom
![alt text](./assets/Burglary.gif)
Lokacija vlomov v mestu. Te pa niso najbolj pogosti tam kjer so bogati, sklepamo za to ker je težje priti v bogato stanovanje, kot pa bogatega človeka oropati na cesti.
Boljše stanovanje, več je tudi varnosti pred vlomilci in večja je prisotnost policije.

### Prostitucija
![alt text](./assets/Prostitution.gif)
Eden izmed najbolj zanimivih gifov. Vidi se kot pričakovano, da je največ prostitucije na glavnih ulicah, tam kjer so ljudje manj premožni. Zanimivo pa je, da bolj ko gremo k sedanjosti, manj je prostitucije. V letu 2016 je skoraj ni več. 
Razlogov za to nismo našli. 

### Kriminal povezan z drogo
![alt text](./assets/Narcotics.gif)
Lokacije kjer je v Chicagu največ droge. Ta gif vključuje proizvodnjo, preprodajo in uživanje drog. 
Te je največ tam kjer se zadržujejo tolpe(Vice kings, Gangster disciples). 
Kar je tudi logično saj je to njihov glavni vir prihodka.
Prav tako je droge najmanj tam kjer so doma prebivalci srednjega razreda. 
Droge se pojavljajo predvsem v revnih predelih mesta, v bogatih pa zmeraj manj.

### Kraja motornih vozil
![alt text](./assets/GTA.gif)
Kot večino kriminala se tudi kraja motornih vozil največ dogaja tam kjer se zadržujejo tolpe. 
Sicer se čez leta dosti lokacij spreminja, ampak žarišča ostajajo enaka.

## Spreminjanje aretacij čez leta na zemljevidu
![alt text](./assets/Arrests.gif)
Največ aretiranih je spet tam kjer se najbolj pojavljajo tolpe.
V vzhodnem delu Chicaga je povečana prisotnost policajev ker so to premožne četrti.



# Zaključki
Ugotovili smo par pomembnih stvari:
  - Kriminal v zadnjih letih upada v primerjavi z pred 2011. Povprečje kriminala je kljub temu še zmiraj nad državnim.
  - Za kriminal v Chicagu so v večini primerov odgovorne tolpe. Delujejo predvsem v predelih zahodnega in južnega Chicaga
  - Prostitucija je v zadnjih letih iz Chicaga skoraj izginila.
  - Če hočete ostati varni, se držite predelov, ki niso preveč revni ali preveč bogati.
  - Avta ne parkirajte v mestu, raje ga pustite doma. Če že greste v mesto parkirajte v "Chinatownu"
  - Najbolj varen predel Chicaga je na severu zahodu mesta.
  - Stay OUT of Garfield!
