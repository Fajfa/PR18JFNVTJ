# Crimes in Chicago
https://www.kaggle.com/currie32/crimes-in-chicago

## Vmesno poročilo


## Skupina
 * Jože Fortun
 * Neža Vehovar
 * Tomaž Jerman

## Opis problema
Ukvarjali se bomo z problemom kriminala v Chicagu. 
Naši podatki vsebujejo kriminalna dejanja od leta 2001 do leta 2017 in sicer:
  * Datum
  * Tip kriminala
  * Kratek opis kriminalnega dejanja
  * Lokacijo
  * Podatek ali je bil kdo aretiran
  * itd.

Odgovarjali bomo na vprašanja kot so:
  * Kam naj gremo da nas ne bodo oropali?
  * Kje naj raje ne parkiramo avta?
  * Kdaj je mesto najbolj nevarno in kdaj je varno?
  
Ampak začnimo na začetku. Zanima nas kako se število kriminalnih dejanj spreminja glede na različna časovna obdobja:
  * Od leta 2001 - 2016
  * Skozi leto (Januar-December)
  * Po letnih časih.
 
Vprašali smo se kakšna je porazdelitev vrst kriminala, ki se dogaja v Chicagu, na katerih lokacijah je največ kriminala in kakšen je delež aretiranih ljudi.



### Priprava podatkov
Ko smo podatke pregledali za napake smo našli par neveljavnih vrstic, ki so se zgodile zaradi napake pri vnosu. Zato smo te odstranili.
Nato smo podatke zapakirali v slovarje in sicer: 
  * Slovar je razdeljen na leta od 2001 - 2016
  * Vsako od teh let pa vsebuje več podslovarjev v katere preberemo posamezne vrstice.
  
Za vsako leto nastavimo vsebino podslovarja in tega napolnimo.
```python
def setYearDicts ():
    cd = {}
    cd["ID"] = []
    cd["CaseNumber"] = []
    cd["Date"] = []
    cd["Block"] = []
    cd["IUCR"] = []
    cd["PrimaryType"] = []
    cd["Description"] = []
    cd["LocationDescription"] = []
    cd["Arrest"] = []
    cd["Domestic"] = []
    cd["Beat"] = []
    cd["District"] = []
    cd["Ward"] = []
    cd["CommunityArea"] = []
    cd["FBICode"] = []
    cd["XCoordinate"] = []
    cd["YCoordinate"] = []
    cd["Year"] = []
    cd["UpdatedOn"] = []
    cd["Latitude"] = []
    cd["Longitude"] = []
    cd["Location"] = []
```
Podatki so bili pripravljeni, sledila je analiza.

### Začeli smo tako da smo za vsako leto od 2001 do 2016 prešteli število kriminalnih dejanj in jih izrisali v grafu:

```python
# Get crimes/year
years = []
count = []

for year in crimeDict:
    if year not in years and (2001 <= float(year) <= 2016):
        years.append(year)
        
    if (2001 <= float(year) <= 2016):
        count.append(len(crimeDict[year]["ID"]))

count = [(c / crimes) * 100 for c in count]
```
![alt text](./assets/CrimePerYear.png)



### Enako smo naredili za mesece v letu:

```python
seasonDict = {}
for y in crimeDict:
    for d in crimeDict[y]["Date"]:
        parsed = datetime.strptime( d, "%m/%d/%Y %I:%M:%S %p" ).month
        if parsed not in seasonDict:
            seasonDict[parsed] = 0

        seasonDict[parsed] += 1

for m in seasonDict:
    seasonDict[m] = (seasonDict[m] / crimes) * 100
```
![alt text](./assets/CrimePerMonth.png)


### In za letne čase:

```python
seasons = ["Spring", "Summer", "Fall", "Winter"]
seasonCounts = [seasonDict[4] + seasonDict[5] + seasonDict[6], 
                seasonDict[7] + seasonDict[8] + seasonDict[9],
                seasonDict[10] + seasonDict[11] + seasonDict[12], 
                seasonDict[1] + seasonDict[2] + seasonDict[3]]
               
```
![alt text](./assets/CrimePerSeason.png)

### Nato smo izrisali graf vrst kriminala:

```python
crimeTypes = {}
for year, value in crimeDict.items():   
    for type in value["PrimaryType"]:
        if(type not in crimeTypes.keys()):
            crimeTypes[type] = 1
        else:
            crimeTypes[type] += 1

crime = []
count = []
for x,y in dict(sorted(crimeTypes.items(), key=lambda row:int(row[1]))).items():
    crime.append(x)
    count.append(float(int(y) / crimes) * 100)
               
```
![alt text](./assets/CrimeType.png)

### Graf  10 najpogostejših lokacij kriminala:


```python
location = defaultdict(int)
for year in crimeDict:
    for loc in crimeDict[year]["LocationDescription"]:
        location[loc] += 1
#location.keys()
for loc in location:
    location[loc] = (location[loc] / arrests) * 100

location.pop("OTHER")
```
![alt text](./assets/CrimeLocation.png)

### In nazadnje, delež aretacij.

```python
arrests = defaultdict(int)

for year in crimeDict:
    for arr in crimeDict[year]["Arrest"]:
        arrests[arr] += 1

for key in arrests:
    arrests[key] /= crimes
```

![alt text](./assets/Arrests.png)


## Prihodek na gospodinjstvo

![alt text](./assets/WealthMap.png)

## Lokacije tolp v Chicagu

![alt text](./assets/Gangs.jpg)

# Spreminjanje kriminala čez leta na zemljevidu
Skozi leta se je lokacija kriminala v Chicagu spreminjala. Naredili smo "heat map" lokacije kriminala za vsako leto, in z gifom predstavili spreminjanje le tega.

![alt text](./assets/CrimesThroughYears.gif)

## Spreminjanje različnih tipov kriminala čez leta

### Napad
![alt text](./assets/Assault.gif)

### Napad s hudo telesno poškodbo
![alt text](./assets/Battery.gif)

### Ropanje
![alt text](./assets/Theft.gif)

### Vlom
![alt text](./assets/Burglary.gif)

### Prostitucija
![alt text](./assets/Prostitution.gif)

### Kriminal povezan z drogo
![alt text](./assets/Narcotics.gif)

### Kraja motornega vozila
![alt text](./assets/GTA.gif)



## Spreminjanje aretacij čez leta na zemljevidu
Prav tako se lokacija aretacij skozi leta spreminja, ta gif "heat map-ov" nam prikaže kako se je lokacija policajev skozi leta spreminjala. Policaji povečajo prisotnost tam kjer se dogaja več kriminala, ker se kriminal premika a hkrati ostaja prevladujoč na določenih lokacijah (Oak park, Milenium park)

![alt text](./assets/Arrests.gif)

## Ugotovitve nad podatki
Iz teh preprostih grafov smo lahko izpeljali ugotovitve:

### Kriminal čez čas
Po letih:
 * Po letu 2004 je število kriminalnih dejanj naraščalo vse do leta 2008.
 * Iz leta 2010 na leto 2011 se je število praktično prepolovilo, Zakaj ? 
 * Od takrat naprej kriminal upada in je najnižje v 16 letih.
 
Po mesecih:
 * Skozi leto se največ kriminala odvija poleti.
 * V hladnejših mesecih pa ta rahlo upade.
 
Po letnih časih:
 * Kot pričakovano zaradi temperatur poleti in spomladi več kriminala kot jeseni in pozimi.


### Informacije o kriminalu
Glede na tip:
 * Največ je tatvin in napadov z telesnimi poškodbami.
 * Temu sledijo zločini v povezavi z drogami
 * Ko bomo opazovali kako so se tipi zločina spreminjali skozi čas bomo dobili več zanimivejših podatkov.
 
Glede na lokacijo:
 * Večina kriminalnih dejanj se zgodi na ulici ali pločinku.
 * Ostala pa v hiši ali stanovanju.
 
### Podatki o aretacijah
Storilec kriminalnega dejanja je aretiran v 25% primerov. 


## Kako naprej
Zdaj, ko imamo pripravljene podatke in nekatere osnovne statistike o njih lahko začnemo zares.
Iz odgovorov, ki smo jih dobili se pojavijo številna vprašanja:
 * Kateri tip zločina je kriv za največ aretacij ?
 * Kako se je vrsta kriminala spreminjala skozi leta.
 * Kateri tipi kriminala so prevladujoči pozimi in kateri poleti ? 

Ko si odgovorimo na ta vprašanja pa lahko začnemo podrobneje analizirati geografske podatke. 
Točno kje v mestu je največ zločina, kaj je pogosto kje itd.
To bomo tudi vizualizirali na mapi Chicaga za lažjo predstavo.


