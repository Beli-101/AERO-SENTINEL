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

P = 85W

To znaci da nam treba snaga od 85W da bi maintainali flight 60km/h

Ako cemo imati dva motora, to znaci da ce motori biti snage 42.5W

Mozemo izracunati jos par stvari koje ce nam mozda trebati:

Wing loading odnosno omjer mase aviona na wing area:

W/S = 29.43N / 0.272m² = 108.3 N/m²

Mozemo izracunati i bateriju koja nam je potrebna:

tflight(hours) = energy(Wh) / Power(W)

tflight je vrijeme leta u satima, energija je energija baterije potrebna, power je snaga motora

E = 255Wh
