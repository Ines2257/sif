
## **CTI za SOC **

### **Uloga CTI-ja u SOC-u**

CTI pomaže L1 analitičaru da:

* brzo prepozna maliciozne IP/domene/hash-eve,
* razlikuje FP od stvarne prijetnje,
* shvati *kontekst* (tko napada, zašto i kako),
* bolje eskalira prema L2/L3.

---

## **Osnove**

### **Od podataka do inteligencije**

| Razina           | Što znači           | Primjer             | L1 akcija         |
| ---------------- | ------------------- | ------------------- | ----------------- |
| **Data**         | sirovi IOC          | IP 45.155.205.3     | prikupi           |
| **Information**  | obogaćen IOC        | Hetzner, first-seen | zabilježi         |
| **Intelligence** | kontekst + značenje | C2 BumbleBee        | blokiraj/escalate |

---

### **Vrste indikatora**

* **IOC** — artefakt (IP, hash, domena)
* **IOA** — nešto *radi* (PowerShell beacon)
* **TTP** — metoda napadača (MITRE ATT&CK)

---

### **Alati za provjeru IOC-a**

* **IP**: WHOIS, Shodan, VT
* **Domain**: Passive DNS, urlscan
* **URL**: URLhaus
* **Hash**: VT, Hybrid Analysis
* **Email**: MXToolbox

---

### **Feeds vs Platforms**

* **Feed** = dolazni IOC-i
* **Platforma (MISP/OpenCTI)** = centralna istina

---

## **CTI Lifecycle (SOC verzija)**

### **1. Direction**

Definiraj:

* što štitimo
* koji IOC-i su bitni
* koja pitanja CTI treba odgovoriti

### **2. Collection**

Prikupljanje IOC-a iz feedova, internih logova, reportova.

### **3. Processing**

Čišćenje, normalizacija, deduplikacija, TLP oznake.

### **4. Analysis**

Procjena relevantnosti:

* ≥2 izvora + lokalni hit = **high**
* 1 izvor = **medium**
* samo OSINT = **low**

### **5. Dissemination**

Slanje intel-a:

* firewall timu
* EDR timu
* CTI platformi
* menadžmentu

### **6. Feedback**

Provjera učinka i poboljšanje procesa.

---

## **TLP kratko**

* **CLEAR** – javno
* **GREEN** – zajednica
* **AMBER** – organizacija
* **RED** – samo određene osobe

---

## **Standardi i Okviri**

### **MITRE ATT&CK**

Mapira *što napadač radi* → koristiš u tiketima i analizi.

### **MITRE D3FEND**

Mapira *kako se braniti*.

### **Cyber Kill Chain (7 faza)**

1. Recon
2. Weaponisation
3. Delivery
4. Exploitation
5. Installation
6. C2
7. Actions on Objectives

---

## **CVE / CVSS / NVD**

* **CVE** → ID ranjivosti
* **CVSS** → ocjena (0–10)
* **NVD** → detalji + exploit info

---

## **STIX / TAXII**

* **STIX** — standardizirani threat intel format
* **TAXII** — protokol za dijeljenje feedova

---

## **Threat Reports (bitni izvori)**

* **Mandiant**
* **Recorded Future**
* **Unit42**

Koriste se za: kampanje, TTP-ove, C2 infrastrukture, malver analize.

---

## **Adversary Mapping – kako sve spajaš**

1. Povuci IOC-e iz logova
2. Obogati ih (VT/MISP/OTX…)
3. Mapiraj na ATT&CK
4. Usporedi s poznatim threat actorima
5. Zapiši u tiket / CTI platformu

---

## **Static Site Lab – što točno radiš**

* Analiziraš alarme i IOC-e
* Puniš:

  * IOC-e
  * ATT&CK tehniku
  * Kill Chain fazu
  * Mogućeg aktera
* Cilj: primijeniti CTI lifecycle u praksi

---
---
---



# **Što je Threat Intelligence?**

Threat Intelligence je proces analiziranja podataka i informacija kako bi se otkrili **uzorci napada**, razumjele prijetnje i odredile **mjere obrane** protiv postojećih i nadolazećih rizika koji ciljaju organizacije, industrije ili države.

Da bismo smanjili rizik, CTI pokušava odgovoriti na 4 ključna pitanja:

1. **Tko te napada?**
2. **Zašto te napada?**
3. **Što napadač može?** (sposobnosti)
4. **Koje IOC-e (indikatore) trebaš pratiti?**

---

# **Vrste Threat Intelligence-a**

### **1. Strategic Intel**

* Visok nivo, “big picture”.
* Fokus na trendovima, uzorcima, industrijskim rizicima.
* Koristi se za donošenje poslovnih odluka.

### **2. Technical Intel**

* Tehnički artefakti napada (IP, hash, domena).
* Korisno za Incident Response i kreiranje detekcija/pravila.

### **3. Tactical Intel**

* TTP-ovi napadača (taktike, tehnike, procedure).
* Koristi se za jačanje sigurnosnih kontrola i analizu napada u realnom vremenu.

### **4. Operational Intel**

* Motivacija, namjera i ciljevi konkretnog protivnika.
* Pomaže razumjeti *što je meta* (ljudi, procesi, tehnologije).

---
---


## **urlscan.io — Sažetak za SOC/CTI analitičare**

**urlscan.io** je **besplatan alat** za analizu web stranica. Automatizirano “posjeti” URL i bilježi sve što stranica radi.

Kada pošalješ URL, urlscan prikuplja:

* Sva **kontaktirana IP-ovi i domene**
* **HTTP zahtjeve** i tipove resursa (JS, CSS, slike…)
* **Screenshot** stranice
* **Tehnologije** i metapodatke (frameworkovi, cookies, JS varijable)
* Sve **linkove**, **redirectove** i **indikatore**

---

# 🔎 **Najvažniji dijelovi rezultata**

### **1. Summary**

* IP adresa i hosting
* Domenski podaci (registrar, ASN)
* Screenshot stranice
* Povijest prethodnih skenova

### **2. HTTP**

* Svi HTTP zahtjevi koje je scanner napravio
* Koji su resursi preuzeti (mime types)

### **3. Redirects**

* HTTP i client-side preusmjeravanja

### **4. Links**

* Svi outgoing linkovi sa stranice

### **5. Behaviour**

* Cookies, JS varijable, tehnologije
* Pomaže otkriti framework (npr. Cloudflare, Next.js…)

### **6. Indicators**

* IP, domene, hash-evi povezani sa stranicom
  (*Napomena: nisu nužno zlonamjerni!*)

---

# **Scenarij: TryHackMe URL Scan**

U zadatku dobivaš sliku urlscan rezultata za *tryhackme.com*.
Na temelju te slike odgovaraš na pitanja kao:

* Koji je **IP** hosta?
* Koji je **ASN / hosting provider**?
* Koji **domain registrar**?
* Koliko outgoing linkova?
* Postoje li redirectovi?
* Koje tehnologije stranica koristi?

---
---


# **Abuse.ch — Sažetak platformi (SOC/CTI fokus)**

**Abuse.ch** je istraživački projekt švicarskog BFH-a koji pruža **besplatne platforme za praćenje malwarea, C2 infrastrukture i IOC-a**. Koristi se svaki dan u SOC-ovima za provjeru sumnjivih IP-ova, domena, hash-eva i certifikata.

---

## **1. MalwareBazaar**

Platforma za **dijeljenje i preuzimanje malware sampleova**.

**Koristiš je za:**

* Pretragu malware hash-eva
* Provjeru tagova i vendor detekcija
* YARA/ClamAV hunting
* Upload vlastitih uzoraka

**Idealno za:** hash analizu u incident responseu.

---

## **2. Feodo Tracker**

Praćenje **botnet C2 infrastrukture** za:

* Emotet
* Dridex
* TrickBot
* QakBot
* BazarLoader

**Koristiš je za:**

* Provjeru sumnjivih IP adresa
* Preuzimanje C2 blocklista
* Detekciju aktivnih botnet servera

---

## **3. SSL Blacklist**

Baza **malicioznih SSL certifikata + JA3/JA3s fingerprintova**.

**Koristiš je za:**

* Detekciju sumnjivog TLS prometa
* Blokiranje poznatih botnet certifikata
* Threat hunting prema JA3 otiscima

---

## **4. URLhaus**

Baza **malware distribucijskih URL-ova**.

**Koristiš je za:**

* Pretragu URL-ova, domena, IP-ova i hash-eva
* Provjeru je li URL povezan s malwareom
* Preuzimanje feedova po zemlji, TLD-u i ASN-u

---

## **5. ThreatFox**

Platforma za **IOC razmjenu**.

**Koristiš je za:**

* Pretragu i eksport IOC-eva
* MISP event format
* Suricata pravila
* DNS RPZ, CSV, JSON izlaz

**Najkorisnije kod:** brze provjere IP, domena i hash-eva tijekom SOC alert triagea.

---
---


# **Email Phishing & PhishTool Overview (SOC L1)**

**Phishing:**

* A primary attack vector, tricking users to click links, open attachments, or enter credentials.
* Leads to malware, credential theft, ransomware, financial fraud, etc.

---

## **PhishTool Purpose**

* Tool for **analyzing suspicious emails**.
* Helps SOC analysts uncover **IOCs, TTPs**, and report findings.
* Community version focuses on **email analysis**; Enterprise adds reporting and workspace integration.

---

## **Core Features (Community)**

1. **Email Analysis:**

   * Extracts metadata, attachments, URLs, and headers.
2. **Heuristic Intelligence:**

   * Uses OSINT to show attacker methods and evasions.
3. **Classification & Reporting:**

   * Flag malicious indicators.
   * Generate forensic reports.

---

## **Dashboard Tabs**

* **Analysis:** Upload email (.eml, .msg, etc.) for investigation.
* **History:** Past submissions and resolutions.
* **In-tray:** Enterprise-only, integrates with Gmail/Outlook for user reports.

---

## **Analysis Sub-Tabs**

| Tab            | Purpose                                        |
| -------------- | ---------------------------------------------- |
| Headers        | Source, destination, originating IP, timestamp |
| Received Lines | Email path across SMTP servers                 |
| X-Headers      | Extra mailbox info                             |
| Security       | SPF, DKIM, DMARC validation                    |
| Attachments    | Files included in email                        |
| Message URLs   | External URLs found in email                   |

* **Plaintext / Source:** View email content.
* **Resolve Checkmark:** Classify email, flag malicious artefacts, and log results.

