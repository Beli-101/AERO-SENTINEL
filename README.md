# AERO-SENTINEL

Klijent određuje dimenzije senzora ( 65mm*36mm, 90g ) i želi prenositi 10 takvih sennzora. Raspoređujemo ih u raspored 5x2, te dobivamo sljedeće: 

Površina = (a * senzorix) * (b * senzoriy)

Površina = (6.5 * 5) * (3.6*2) = 234 cm²

Masa tereta = 0.09 * 10 = 0,9kg + 10% = 1kg

Što se tiče fusilagea, s obzirom da motori idu na wingove, jedina dosta teška komponenta koju nosi je baterija. Ako dodamo i sve ostale komponente masa fusilagea ( PCB, gps, receiver, servos, ...) ne prelazi ni 1kg.

Ako sad uzmemo u obzir i one motore na krilima i ostatak tijela aviona, masa bi bila oko 3kg. 



![Why-Y-Z_Plane_force-01](https://github.com/user-attachments/assets/d4fb7316-1475-4dfa-876f-1dcdf2761129)

Na ovoj slici vidimo 4 main sile koje djeluju na avion: Lift, Weight, Thrust, Drag
Za sad cemo samo gledat samo dvije sile: Weight i Lift
Weight je sila teza na hrvatskom
Formula za weight je m * g, gdje je m masa objekta(kg), a g je akceleracija sile teze(m/s²)
Weight ce se mijenjati ali skoro je neprimjetna razlika, razlog tome je sto se akceleracija sile teze mijenja oviseci o tome gdje se nalazimo(na ekvatoru je 9.78m/s², a na polovima je 9.83m/s²)

Weight = m * g

weight = 3kg * 9,81m/s² 

weight = 29.43N 

Sljedecu silu koju gledamo je lift odnosno sila uzgona
Razlog zasto gledamo lift i weight je zato jer su to osnovne sile koje odreduju hoce li i koliko nas avion poletjeti
Vidimo na prijasnjoj slici da su lift i weight suprotnoga smjera(lift prema gore, weight prema dole) sto znaci da za rezultantnu ne trebamo racunati kut nego samo zbrajamo i oduzimamo(smjer rezultante je smjer vece sile). Nas avion ce letjeti kada je lift veci nego weight, ali naravno sto je veci, to ide brze prema gore. 

Kada budemo racunali lift, kao potreban lift necemo stavljat iznos jednak weightu nego 5-10% veci jer nikad ne leti u savrsenim uvjetima.
avion treba extra lift da bi skretao, ispravljao ometanja i drzao avion stabilnim, jer da je isti avion bi imao 0 mjesta za promasaj.

Lift = 1.1 * weight

Lift = 1.1 * 29.43N

Lift = 32.373N

Iz toga i još nekih poznatih podatak poput: 

gustoća zraka - 1,225 kg / m³

maksimalna brzina zraka koje avion mora izdrzati - 10m/s = 36km/h(odredeno od strane klijenta)

nasa minimalna brzina mora biti veca od maksimalne brzine zraka koje mora izdrzati ali naravno zelimo putovati idalje na relativno dobroj brzini tako da cemo postaviti:
naša minimalna brzina - 16.67 m/s = 60km/h

CL - 0,7


možemo dobiti potreban wing surface area iz ove formule: 

Lift = 1/2 * gustoća * brzina2 * površina krila * CL

površina krila = 2L / (gustoća * brzina2 * CL)

površina krila = 0,272 m²

S = c * b

površina krila = chord * span

za sada ne mozemo dobiti najpreciznije brojke jer nemamo dovoljno parametara jer chord moze biti 0.52 i span 0.52 a moze biti i totalno drugacije, tako da uvodimo jos jedan parametar: ASPECT RATIO
aspect ratio je omjer izmedu chorda i spana(u pravilu veci aspect ratio znaci bolji glide i bolji lift to drag ratio sto znaci da je efikasniji let.
Shvatili smo da ce na nasim "umanjenim" velicinama nepotrebno otezat ako probamo ic za veci aspect ratio od 20, tako da cemo uzet 20 za ovaj izracun
Zatim imamo formulu

AR = b² / S

aspect ratio = span² / wing area

span² = AR * S

span² = 5.44m²

span = 2.332m

sada imamo i span, a to znaci da preko nje mozemo dobiti chord

S = c * b

c = S / b

c = 0.272m

c = 0.117m² / 2.332m

ovo je prosjecan chord, a mi imamo tapered wing, tako da cemo sad koristiti sljedecu formulu:
sada uvodimo novi parametar λ sto je taper ratio, a on nam je 0.4(sto znaci da je tip 40% od root chorda) i dobili smo ga tako da smo podjelili chord na tipu i chord na rootu(1.0 ima pravokutno krilo, >0.3 je jako suzeno krilo)

MAC = cr * 2/3 * (1 + λ + λ²) / (1 + λ)

gdje je MAC mean aerodynamic chord odnosno prosjecan(to smo izracunali u proslom racunu)

cr je root chord

λ taper ratio


0.117m = 0.7429 cr

cr = 0.1575m

a ako je root chord 0.1575m onda lako izracunamo i tip chord:

ct = λ * cr

ct = 0.063m


Sada racunamo stall speed, odnosno brzina na kojoj se avion krene naginjati prema dole(brzina nije dovoljna da maintaina flight

Vs = √(2W / (ρ * S * Clmax)

vstall = √(2 * Weight / (rho * wing area * max coefficient of lift)

Clmax ≈ 1.3

Vs = √(2 * 29.43 / (1.225 * 0.272 * 1.3)

Vs = 11.657m/s

Vs = 41.97km/h

Sada racunamo drag aviona, tako da imamo formulu:

D = 0.5 * ρ * V² * S * Cd

Tu nam je nepoznat Cd, a formula za drag coefficient je:

Cd = Cd0 + Cdi

drag coefficient = profile drag(parasite drag) + induced drag

prvo racunamo inducirani drag odnosno drag koji se stvori:

Cdi = (Cl² / (π * AR * e))

tu imamo jos jednu nepoznanicu e koja je oswald efficiency factor sto je broj koji pokazuje koliko efikasno wing convertira lift u inducirani drag (uvijek je manji od 1). Prava krila imaju 0.7-0.95 oviseci o obliku i velicini

e ≈ (1.78 * (1 - 0.045 * AR^0.68) - 0.64λ) / (1 + 0.12λ)

e ≈ 0.868

Sada kad imamo oswald efficiency mozemo izracunati inducirani drag:

Cdi = (Cl² / (π * AR * e))

Cdi = (0.7 / (π * 20 * 0.868))

Cdi = 0.09

zato jer imamo lagano krilo koje ce biti smooth i tanko, mozemo estimirati:
Cd0 = 0.02

Onda dobijamo:

Cd = Cd0 + Cdi

Cd = 0.11

Prema tome sada mozemo dobiti drag:

D = 0.5 * ρ * V² * S * Cd

D = 0.5 * 1.225 * 16.67 * 0.272 * 0.11

D = 5.1N

Sto znaci da na brzini od 60km/h imamo drag 5.1N

Preko ovoga mozemo pogledat koji nam motor otprilike treba:

P = D * V

snaga = drag * brzina

P = 83.35W

To znaci da nam treba snaga od 85W da bi maintainali flight 60km/h

Ako cemo imati dva motora, to znaci da ce motori biti snage 42.5W

Mozemo izracunati jos par stvari koje ce nam mozda trebati:

Wing loading odnosno omjer mase aviona na wing area:

W/S = 29.43N / 0.272m² = 108.3 N/m²

Sada krecemo na racunanje thrusta potrebnog za odredenu vertikalnu brzinu(climb rate) i ostale stvari kao baterija, komponenta, propeler

Prvo idemo na racunanje thrusta potrebnog da bi se avion dizao 5m/s vertikalno dok se krecemo brzinom od 60km/h(16.67m/s)

T = D + (W/V) * Vz

Gdje je:

T - thrust(ukupan)

D - Drag

W - Weight

V - velocity

Vz - vertical velocity

Kada uvrstimo brojeve to je:

T = 5.1N + (29.43N/16.67m/s) * 5m/s

T = 13.925N

Odnosno na konfiguraciji sa dva motora:

T = 13.925/2 ≈ 6.96N

Sada trazimo motor, a ovo su requirementi za njega:

Mora handleat 6.96N thrusta po motoru

Mora biti kompatibilan sa 4S LiPo baterijom(14.8V)

Mora biti efikasan da drzi let 3 sata

Izabrao sam motor: FW‑B3536

Slaze se sa requirementima, ima masu 105.8g i u puno konfiguracija moze je dovoljan za nase potrebe struje i proizvodi dovoljno thrusta

Sada trazimo kombinaciju takvog motora i propelera:

cilj je dobiti balans izmedu thrusta(za dizanje i ubrzanje) i efikasnosti(za cruise)

Na stranici motora imaju podaci o tocno onome sto trebamo odnosno postoji tablica sa razlicitim setupovima motora i propelera i svi ostali parametri koji ce nam trebat(snaga, thrust itd.)

Nakon provjere tablice izabrali smo APC 10x5 propeler sa 1000KV(koliko rpma ima po voltu) motorom

Sad mozemo estimirati okretaje po minuti odnosno RPM:

RPM = KV * Vbaterije

RPM = 1000 * 14.8

RPM ≈ 14800

Sada racunamo brzinu propelera dok se vrti

V = RPM * r * 2π / 60
V = 196.8m/s

Sto je ova brzina veca to je veci thrust i brzina nebi trebala biti brza od brzine zvuka u zraku(oko 340m/s) jer se onda zrak nebi mogao dovoljno brzo pomaknuti pa bi se formirale vibracije i efikasnost se jako smanji

Polijetanje i uzdizanje

Sad cemo racunati neke bitne stvari vezane uz sami let, kao sto su stall odnosno takeoff speed i koliko ce avionu vremena trebati da poleti

Prvo moramo izracunati stall speed odnosno potrebna brzina da avion generira dovoljno lifta da ostane u zraku(ako je brzina ispod stall speeda avion pada, ako je visa onda se dize)

Vs = √2W / (ρ * S * Clmax)

Vs = √2*29.43 / (1.225 * 0.272 * 1.3)

Vs ≈ 11.66m/s ≈ 46km/h

Onda racunamo akceleraciju aviona, pomocu 2. Newtonovog zakona:

a = F(thrust) / m

a ≈ 4.44m/s²

Sada racunamo vrijeme za polijetanje:

t = V/a

t ≈ 2.88s

Racunamo potrebnu distancu za polijetanje:

s = 1/2 * a * t²

s - put(m)

s ≈ 18.4m


## KONTROLNE POVRŠINE


Kako bi dobili površine, duljine i širine kontrolnih površina ( elevator, ailerons, rudder) prvo računamo wing area. 
<br>

Wing area = span * chord 


Wing area = 2,332m * 0,272m


Wing area = 0,63m² 


Iz toga možemo dobiti površinu horizontalne stabilizacije koja je:
<br>
Horizontal stabiliser area = 20% od Wing area

Horizontal stabiliser area = 0.2 * 0,63m²

Horizontal stabiliser area = 0,125m²

Iz sljedećeg izraza dobivamo horizontal lenght i onda iz općeg izraza za površinu i širinu: 

Horizontal lenght = (wingspan /2 ) * 0,35

Horizontal lenght =(2,32 /2 ) * 0,35

Horizontal lenght = 0,41m

Horizontal width = Horizontal area / Horizontal lenght

Horizontal width = 0,125m² / 0,41m

Horizontal width = 0,30m 



Nakon toga računam površinu, duljinu i širinu elevatora: 

Elevator area = 35% od Horizontal stabiliser area 

Elevator area = 0,35 * 0,125mm²

Elevator area = 0,044m²


Elevator lenght = Horizontal lenght = 0,41m 

Elevator width = Elevator area / elevator lenght 

Elevator width = 0,044m² / 0,41m

Elevator width = 0,11m


<img width="610" height="272" alt="image" src="https://github.com/user-attachments/assets/16b2b80e-db13-4f78-9bd0-6de797e1c1f7" />


 Vertical stabiliser 

Vertical stabliser area = 33% of Horizontal area stabliser

Vertical stabiliser area = 0,125m² * 0,33

 Vertical stabiliser area = 0,042m²

Rudder area is equal to 

Rudder arrea = 33% of Vertical stabiliser area 

Rudder area = 0,33 * 0,042m²

 Rudder area = 0,015m²

Considering vertical width is equal to horizontal width we can calculate the vertical height of the stabiliser and rudder. 

 Vertical width = Horizontal width = 0,41m 

Vertical area = Vertical width * Vertical width 

Vertical height = Vertical area / Vertical width

Vertical height = 0,042m² / 0,41m

Vertical height = 0,1m

Iz vertical height i rudder area, možemo izračunati  širinu ruddera. 

Rudder area = Vrtical height * rudder width

Rudder width = Rudder area / vertical height

Rudder width = 0,015m² / 0,1 

 Rudder width = 0,15m 

 <img width="672" height="402" alt="image" src="https://github.com/user-attachments/assets/b52aca3f-4eb6-469c-be99-47fe52be5999" />

