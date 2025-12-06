# AERO-SENTINEL

Klijent određuje dimenzije senzora ( 65mm*36mm, 90g ) i želi prenositi 10 takvih sennzora. Raspoređujemo ih u raspored 5x2, te dobivamo sljedeće: 

Površina = (6.5 * 5) * (3.6*2) = 234 cm2
Masa tereta = 0.09 * 10 = 0,9kg + 10% = 1kg

Što se tiče fusilagea, s obzirom da motori idu na wingove, jedina dosta teška komponenta koju nosi je baterija. Ako dodamo i sve ostale komponente masa fusilagea ( PCB, gps, receiver, servos, ...) ne prelazi ni 1kg.

Ako sad uzmemo u obzir i one motore na krilima i ostatak tijela aviona, masa bi bila oko 2.5 - 3kg. 

Weight = m * g
weight = 3 * 9,81 
weight = 29.43N 

Ako je težina aviona 29.43N onda nam sila uzgona ( lift ) mora biti veća od toga. 

Required lift = weight *1.1 
Required lift = 35N 

Iz toga i još nekih poznatih podatak poput: 

gustoća zraka - 1,225 kg / m3
brzina zraka - 10m/s - 36km/h
naša minimalna brzina - 16.67 m/s - 60km/h
CL - 0,7


možemo dobiti potreban wing surface area iz ove formule: 

Lift = 1/2 * gustoća * brzina2 * površina krila * CL
površina krila = 2L / (gustoća * brzina2 * CL)
površina krila = 0,3 m2




