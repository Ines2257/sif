
**Incident Response = proces reagiranja na cyber napade.**

**NIST faze (4):**

1. **Priprema**
2. **Detekcija & analiza**
3. **Konteniranje, uklanjanje & oporavak**
4. **Lekcije naučene**

**SANS faze (6):**
Priprema → Identifikacija → Konteniranje → Uklanjanje → Oporavak → Lekcije.

**Ključno:**

* Sigurnost je **kontinuirani proces**, ne alat.
* Svaki incident daje informacije za sljedeći ciklus.
* Incident responder: riješi prijetnju + dokumentiraj sve da se ne ponovi.
---
---

## 🔍 **Što se događa?

Korisnik prijavio **ekstremno spor laptop** → IT vidi **visok CPU usage** → SOC vidi **stalne outbound konekcije** na sumnjivu IP → nema SIEM/EDR alarma → slučaj ide Incident Response timu.

---

## 🕵️‍♂️ **Analiza (ukratko)**

### **1. Task Manager**

* Jedan čudan proces koristi gotovo sav CPU.
* Naziv: *random niz znakova*, lokacija: **Temp folder → jako sumnjivo**.
* Vjerojatno **malware / cryptominer**.

### **2. Provjera konekcija**

`netstat` → proces stalno pokušava kontaktirati **sumnjivu externu IP adresu**, što potvrđuje sumnju na C2 komunikaciju.

---

## 📥 **3. Pronalaženje vektora infekcije**

U Edge downloadima se nalazi fajl:

`invoice n. 37484567 (1).docm` →

* *.docm = Word dokument s makronaredbama*
* Downloadan s **IP adrese** (ne domene) → jako sumnjivo.

Korisnik ga otvorio → makro se automatski izvršio.

---

## ⚙️ **4. Što makro radi? (kratko)**

Makro **AutoOpen**:

1. Provjerava radi li malware već.
2. Uz pomoć **certutil** (legit Windows alat) *tiho* preuzima malware s URL-a.
3. Sprema ga u **Temp**.
4. Pokreće ga *skriveno*.
5. Dodaje u **Run** registry ključ → **persistencija** (digne se pri svakom loginu).

→ Zato je PC spor čak i nakon restartanja.

---

## 🧩 **Zaključak (ukratko)**

* Korisnik je otvorio **malicious .docm** → makro preuzeo i pokrenuo **cryptominer** → miner troši CPU + pokušava kontaktirati C2.

Ovo je kompletan lanac napada.

---
---

# ✅ **CONTAINMENT**

### **1. Odspoji PC od mreže**

– Već učinjeno (pre-response).

### **2. Ubij zlonamjerni proces**

– Task Manager → desni klik → *End task*
– Zabilježi ime procesa i putanju (za izvještaj).

### **3. Radi na razini organizacije – IoC sweep**

Kompajliraj i potraži sve IoC-eve u SIEM-u, EDR-u i mrežnim uređajima:

**IoCs koje tražimo:**

* C2 **IP + port**
* URL s kojeg je **preuzet .docm**
* URL iz makroa s kojeg je **skinuta EXE datoteka**
* Hash malicioznog **EXE-a**

→ Dodati ih u EDR blocklist / SIEM detekcije.

---

# 🧹 **ERADICATION (ukratko)**

### **1. Obriši sve artefakte**

* Obriši **malware EXE** iz *Temp* foldera.
* Obriši **malicious .docm** iz *Downloads*.
* Očisti **browser download history**
  (da user opet slučajno ne klikne link).

### **2. Ukloni persistenciju**

Registry:

```
Computer\HKEY_CURRENT_USER\
Software\Microsoft\Windows\CurrentVersion\Run
```

– Pronađi ključ koji pokazuje na maliciozni EXE
– Desni klik → **Delete**.

---

# 🔄 **RECOVERY (ukratko)**

* Restart nakon uklanjanja persistence → provjeri da se proces ne vraća.
* Ponovno uključi PC u mrežu.
* Potvrdi da više nema C2 pokušaja i sumnjivih procesa.
* Dokumentiraj sve: imena fajlova, putanje, hash, URL-ovi, registry ključ.

---
---

## **Post-Incident Activity (kratko)**

– Pregledati cijeli incident: što se dogodilo, kako, koliko brzo je detektirano, što je radilo dobro, a što nije.
– Dokumentirati *lessons learned*.
– Ažurirati procedure, playbooke i detekcije.
– Podijeliti nalaze relevantnim timovima (IT, SOC, management).

---

## **Povratak na Preparation (kratko)**

Sve naučeno treba ući u novi, bolji **Incident Response Plan**.

**Preporuke za poboljšanje (iz scenarija):**

* Uvesti ili poboljšati **EDR** (detekcija cryptominera i makro malwarea).
* Uvesti **web filtering / URL kontrolu**.
* Povećati **user awareness** (trening o makro datotekama i sumnjivim linkovima).
* Razmotriti **blokiranje Office makroa** (ako ne remeti poslovne procese).

---

