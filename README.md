## AERO-SENTINEL

### APROXIMACIJA MASE
Prvo što smo krenuli raditi je bilo aproximirati masu cijelog našeg UAV-a. Zaključili smo da će masa tereta biti oko 1kg,
a to smo zaključili zbog klijentovog zahtjeva da nosi 10 paketa seznora od 900g. Nakon toga odredili smo masu baterije – 1.5kg.
Još smo nadodali masu senzora – 0,4kg i masu konstrukcije oko 2kg, te s tim ukupnu masu od 5kg. 

 **mass (m) = 5kg** 

### SILE - WEIGHT I LIFT 
![Why-Y-Z_Plane_force-01](https://github.com/user-attachments/assets/d4fb7316-1475-4dfa-876f-1dcdf2761129)

Na ovoj slici vidimo 4 main sile koje djeluju na avion: **Lift, Weight, Thrust, Drag**
Nakon što smo dobili masu izračunali smo težinu po općoj formuli:


W ( Weight)  = m*g. --> (g = 9,81m/s) 

W = 5 * 9,81

**W = 49,05N**

Sljedecu silu koju gledamo je lift odnosno sila uzgona (LIFT). Razlog zasto gledamo lift i weight je zato jer su to osnovne sile koje odreduju hoce li i koliko nas avion poletjeti. 
Vidimo na prijasnjoj slici da su lift i weight suprotnoga smjera(lift prema gore, weight prema dole) sto znaci da za rezultantnu ne trebamo racunati kut nego samo zbrajamo i oduzimamo(smjer rezultante je smjer vece sile). Nas avion ce letjeti kada je lift veci nego weight, ali naravno sto je veci, to ide brze prema gore. Kada budemo racunali lift, kao potreban lift necemo stavljat iznos jednak weightu nego 5-10% veci jer nikad ne leti u savrsenim uvjetima.
Avion treba extra lift da bi skretao, ispravljao ometanja i drzao avion stabilnim, jer da je isti avion bi imao 0 mjesta za promasaj.



Lift = 1.1 * W 

Lift = 1.1 * 49.05N

**Lift = 53,955N**


### POVRŠINA KRILA 

Za izračun daljnjih vrijednosti  poput ove prve koje računamo ( površina krila - S ) uzimamo neke konstante i vrijednosti koje smo dobili na prikazane načine:  

NAvedene vrijednosti smo dobili iz tablica za izračun upravo tih vrijednosti. 

 **CL** - coefficent of lift - **0,67**
 <img width="1279" height="293" alt="image" src="https://github.com/user-attachments/assets/66873edc-702a-4d21-9fc8-1bcc1fca6217" />

 
 **CLmax** - maximum coefficient of lift - **1,29** 
 <img width="1249" height="303" alt="image" src="https://github.com/user-attachments/assets/219177c5-61b6-4f35-bee9-476ab26137ac" />

 
 **Cd** - coefficient of draag - **0,11**

 Navedene vrijednosti su neke konstante: 

**ρ0** - gustoća zraka at 0km - **1,225 kg/m**

**ρ** - gustoća zraka at 1km  - **1,11 kg/m**

Wing area (S) računa se iz sljedćeg izraza:

Tu imamo jos jednu nepoznanicu e koja je oswald efficiency factor sto je broj koji pokazuje koliko efikasno wing convertira lift u inducirani drag (uvijek je manji od 1). Prava krila imaju 0.7-0.95 oviseci o obliku i velicini

e ≈ (1.78 * (1 - 0.045 * AR^0.68) - 0.64λ) / (1 + 0.12λ)

e ≈ 0.868

<img width="420" height="87" alt="image" src="https://github.com/user-attachments/assets/47544915-41b6-448e-8b17-0cad9ba3a9ef" />

Kada preformiramo formulu dobimo izraz za S ( Wing Area).

**S = ρ * v * CL * 0,5**

**S = 0,48m2**


### IZRAČUN SPANA I CHORDA

SLjedeće vrijednosti smo si zadali, s obzirom da nam je cilj imati ih takve.

**Aspect ratio - AR** - omjer između lenghta wingspana (span - b)  i widtha wignspana (chord - c). Mi smo odlučili da želimo što veći AR jer to značiu da imamo dugačka tanka krila koja su povoljna za cruisanje. 
Dakle, **AR = 20**. 

Span (b) = SQRT (AR * S) 
**s = 3,0761 m**

Chord (c) = S / b 
**c = 0,1538m**

### WING LOAD 

Wing load = S / b 
**Wing load = 103,67 N /m2**


### STALL SPEED

Stall speed je minimalna brzina kojom se avion mora gibati. 

Vstall = SQRT(2W / (S * ρ * CLmax) --> ρ - 1,11kg / m3  (at 1km) 

**Vstall = 12,0334 m/s** 

### DRAG AND TRUST 

**DRAG**

Sad krećemo na druge dvije dosta bitne sile, **DRAG I TRUST**.

Drag (D) = 0,5*ρ*v2*S*CD
**Drag = 8,0235N**

**TRUST**

Razlikovat ćemo 3 vrste trusta - trust cruising, trust asceding and trust until liftoff. 

First for **trust cruising**: 

Tc = W / (Cl / Cd) 

**Tc = 8,05N**

**Trust ascending**

Vv = 5m/s

V = 16m/s

Tasc = D + W*sin(Vv/V)
**Tasc = 22,5187N**

**Trust until liftoff:**

That is the trust we need to get to liftoff.

Ovo su svi faktori koje moramo uzeti u obzir : sila trenja, sila temeljnog zakona gibanja, i drag koji moramo beatat. 

Dakle: 

T = ma + D + Ftr

**Ftr = μ * m * g --> μ = 0,8 ( između suhog betona i gume )  = 39,24N**

**T = 69,2635N**


### OPĆI PODATCI 

- vrijeme, distanca i brzina lifotffa:

#### brzina poleta (vf): 

vf = sqrt(2W/(rho*S*CL)

**vf = 15,8924m/s**

#### vrijeme poleta

tf = vf/a --> a = 4,4m/s2

**tf = 3,61s**

#### distanca poleta (s)

s = 0.5*a*t2

**s = 28,7075m**





## KONTROLNE POVRŠINE

#### Horizontal stabiliser

Nakon toga krenuli smo na kontrolne površine. Njihove dimenzije dobili smo uspoređivanjem omjera s drugima, tj. kada smo dobili wingarea (S), horizontalni stabilizator je bio npr. upola manji, pa smo tako računali i ostalo. 


Horizontal stabiliser area (Hsa) = 20% od Wing area

Horizontal stabiliser area = 0.2 * 0,48m²

**Horizontal stabiliser area = 0,09426m²**


Iz sljedećeg izraza dobivamo horizontal lenght i onda iz općeg izraza za površinu i širinu: 

Horizontal lenght = (wingspan /2 ) * 0,35

Horizontal lenght =(2,32 /2 ) * 0,35

**Horizontal lenght = 0,5383m**



Horizontal width = Horizontal area / Horizontal lenght

**Horizontal width = 0,1758m**



Nakon toga računam površinu, duljinu i širinu elevatora: 

Elevator area = 35% od Horizontal stabiliser area 

**Elevator area = 0,03311m²**


**Elevator lenght = Horizontal lenght = 0,5383m**


Elevator width = Elevator area / elevator lenght 

**Elevator width = 0,0615m**
<img width="743" height="392" alt="image" src="https://github.com/user-attachments/assets/540f4cba-7e62-4a82-8180-80a37a17e682" />





 #### Vertical stabiliser 

Vertical stabliser area = 33% of Horizontal area stabliser

**Vertical stabiliser area = 0,03127m²**


Rudder arrea = 33% of Vertical stabiliser area 

**Rudder area = 0,0103m²**


Considering vertical width is equal to horizontal width we can calculate the vertical height of the stabiliser and rudder. 

**Vertical width = Horizontal width = 0,1758m**



Vertical height = Vertical area / Vertical width

**Vertical height = 0,1776m**


Iz vertical height i rudder area, možemo izračunati  širinu ruddera: 



Rudder width = Rudder area / vertical height

**Rudder width = 0,0580m**

<img width="720" height="369" alt="image" src="https://github.com/user-attachments/assets/52b06d1d-26d4-401b-b787-8c63ebe5e8e5" />




