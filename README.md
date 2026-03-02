## 💰 Budget Tracker – Web aplikacija za praćenje osobnog budžeta
### 📌1. Opis projekta
Ovaj projekt predstavlja web aplikaciju za praćenje osobnog budžeta. Cilj aplikacije je omogućiti korisnicima jednostavan, jasan i siguran način evidencije prihoda i rashoda te analizu vlastite potrošnje kroz pregledne statistike i izračun mjesečnog salda.

U današnjem društvu financijska pismenost postaje sve važnija, no velik broj ljudi nema sustavan način praćenja osobnih financija. Troškovi se često pamte okvirno ili se zapisuju nesustavno, što dovodi do netočnih procjena i financijskih poteškoća. Ova aplikacija rješava taj problem omogućujući centralizirano i digitalno upravljanje financijskim podacima.

##### 🎯 Problem koji aplikacija rješava
  Nedostatak kontrole nad potrošnjom,
Nemogućnost brzog pregleda mjesečnog salda,
Nepregledna evidencija troškova,
Nedostatak analize potrošnje po kategorijama

Aplikacija korisniku omogućuje:
unos prihoda,
unos rashoda,
pregled povijesti transakcija,
filtriranje po mjesecu,
pregled ukupnih prihoda, rashoda i salda,
uređivanje i brisanje postojećih zapisa

##### 👥 Ciljana skupina
  učenici i studenti, zaposlene osobe, svi koji žele bolju kontrolu nad osobnim financijama

### 🧩 2. Funkcionalnosti aplikacije
| Funkcionalnost         | Opis                                 | 
| ---------------------- | ------------------------------------ | 
| Registracija           | Kreiranje korisničkog računa         | 
| Prijava                | Autentifikacija korisnika            | 
| Oporavak zaporke       | Reset lozinke putem emaila           | 
| Dodavanje transakcije  | Unos prihoda ili rashoda             | 
| Uređivanje transakcije | Promjena postojećeg zapisa           | 
| Brisanje transakcije   | Uklanjanje zapisa                    | 
| Dashboard              | Pregled ukupnih podataka             | 
| Izračun salda          | Automatski izračun prihodi - rashodi | 
| Profil korisnika       | Pregled i uređivanje podataka        | 

### 🔄 3. Scenarij korištenja
##### 🔹 Registracija
1. Korisnik dolazi na početnu stranicu.
2. Odabire opciju registracije.
3. Unosi email i zaporku.
4. Sustav kreira račun putem Firebase Authentication.
5. Kreira se zapis korisnika u Firestore bazi.

##### 🔹 Dodavanje transakcije
1. Korisnik je prijavljen.
2. Klikne na “Dodaj transakciju”.
3. Unosi iznos, tip (prihod/rashod), kategoriju i datum.
4. Podaci se spremaju u Firestore.
5. Dashboard se automatski ažurira.

##### 🔹 Pregled budžeta
1. Korisnik pristupa Dashboard stranici.
2. Prikazuju se sve njegove transakcije.
3. Sustav automatski izračunava:
ukupne prihode,
ukupne rashode,
saldo
4. Podaci se mogu filtrirati po mjesecu.

### 🗄 4. Model baze podataka
