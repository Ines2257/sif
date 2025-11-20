Offensive Security
-
- provjera u računalne sustave, iskorištavanje softverskih grešaka i pronalaženje rupa u aplikacijama kako bi dobili neovlašteni pristup

- dirb--> alat koji koristipristup grube sile, uzimajući popis potencijalnih naziva stranica i testirajući jedan po jedan 



Defensive security
-
- koristi se za pripremu i proaktivnu zaštitu IT infrastrukturne organizacije
- bavi se dvama glavnim zadacima:
    - sprječavanje upada
    - otkrivanje upada kada se dogode i pravilno reagiraju
-neki zadaci: Cyber Security Awareness, Documenting & Managing Assets, Preventative Security, Logging & Monitoring, Frameworks, Policies & Procedures


Security Operations Centre (SOC)
- 
- tim stručnjaka za kibernetičku sigurnost koji prati mrežu i njezine sustave kako bi otkrio zlonamjerne događaje u kibernetičkoj sigurnosti

Digital Forensics Technique
- 
- oristi se za analizu digitalnih uređaja radi pronalaženja i očuvanja dokaza, posebno u slučajevima napada
- naliza memorije sustava koristi se za otkrivanje zlonamjernih programa koji ne spremaju podatke na disk, već rade izravno u memoriji (RAM)
- Ova tehnika može pomoći u razotkrivanju ponašanja zlonamjernog koda i povezanim procesima


- Definicija: Primjena forenzičkih metoda na digitalne uređaje za očuvanje i analizu digitalnih dokaza (npr. kod sigurnosnih incidenata).
- File System (Datotečni sustav):
    - Analiza kopije pohrane otkriva instalirane programe, obrisane i djelomično prebrisane datoteke.
- System Memory (Memorija sustava):
    - Ako zlonamjerni kod radi samo u RAM-u, analizom memorije otkriva se njegovo ponašanje i rad.
- System Logs (Sistemski zapisi):
    - Zapisi pokazuju radnje na sustavu; ostaju tragovi i ako ih napadač pokuša obrisati.
- Network Logs (Mrežni zapisi):
    - Analiza mrežnog prometa pomaže utvrditi odvija li se napad i u kojem obliku.


* **Cyber Kill Chain**: sigurnosni okvir iz 2011. od Lockheed Martina, inspiriran vojnim “kill chain” konceptom
* Pomaže organizacijama razumjeti i braniti se od cyber napada
* **7 faza napada:**

  1. **Reconnaissance** – prikupljanje informacija o cilju
  2. **Weaponisation** – stvaranje ili prilagodba malicioznog payloada prema ranjivostima cilja
  3. **Delivery** – slanje weaponiziranog payloada cilju
  4. **Exploitation** – iskorištavanje ranjivosti u ciljevom sustavu
  5. **Installation** – instalacija backdoora ili malwarea za održavanje pristupa
  6. **Command & Control (C2)** – kontrola kompromitiranog sustava preko backdoora
  7. **Actions on Objectives** – krajnji ciljevi: krađa podataka ili daljnja eksploatacija
* Razumijevanjem svake faze, organizacija može **prekinuti lanac i zaustaviti napad** u tijeku
* **Ciljevi učenja:**

  * Naučiti 7 faza Kill Chaina
  * Istražiti primjere napada po fazama
  * Pogledati primjere obrane po fazama
* Preporuka: završiti *Cyber Security 101* put za bolje razumijevanje.



* **Reconnaissance** = prikupljanje informacija o cilju, traženje ranjivosti i potencijalnih ulaza
* **Dva tipa:**

  * **Pasivna:** napadač ne ostavlja tragove

    * Primjeri: WHOIS, DNS, web crawling, social media, Google Dorking
  * **Aktivna:** napadač mora stupiti u interakciju, može biti „bučna“


    * Primjeri: port scanning, vulnerability scanning, fizičko izviđanje cilja
* **Protumjere / obrana:**

  * Minimizirati javno dostupne informacije (web, društvene mreže, DNS)
  * Korištenje WHOIS privatnosti
  * Aktivno praćenje mrežnog prometa i logova
  * Otkrivanje skeniranja portova i pokušaja izviđanja

---


* **Weaponisation** = kreiranje malicioznog payloada na temelju ranjivosti cilja
* Napadači mogu:

  * Koristiti gotove exploit-e
  * Prilagoditi postojeće exploit-e
  * Kreirati exploit od nule
* Često koriste **obfuscation** ili **enkripciju** da izbjegnu otkrivanje
* Payload se može sakriti u „neškodljivim“ datotekama (Word, PDF)
* **Primjeri weaponizacije:**

  * Exploit kits za automatizirano kreiranje payloada
  * Maliciozne makronaredbe u Office dokumentima
  * Phishing emaili s attachmentima, web stranice, USB uređaji
* **Protumjere / obrana:**

  * Edukacija korisnika o opasnim attachmentima i enkriptiranim datotekama
  * Onemogućavanje nepotrebnih funkcionalnosti, deinstalacija softvera i pluginova
  * Ograničavanje makronaredbi na potpisane i pouzdane izvore (Windows group policy)

---


- Internet = golema mreža sastavljena od mnogih manjih mreža

- Primjer s Alice, Zaynom i Tobyjem pokazuje kako mreže međusobno komuniciraju putem “posrednika”

- ARPANET (1960-e) – prvi oblik interneta, financiran od strane američkog Ministarstva obrane

- 1989. – Tim Berners-Lee stvara World Wide Web (WWW), što omogućuje pohranu i dijeljenje informacija

- Internet je spoj privatnih i javnih mreža:

- Privatna mreža – manja, zatvorena mreža

- Javna mreža (Internet) – povezuje privatne mreže

- Uređaji u mreži imaju oznake (identifikatore) za međusobno prepoznavanje


* Uređaji na mreži trebaju biti **identificirani i prepoznatljivi**.
* Dva načina identifikacije (poput imena i otisaka prstiju):

  * **IP adresa** (promjenjiva, identificira uređaj na mreži; javna vs. privatna; IPv4 vs. IPv6)
  * **MAC adresa** (stalna, tvornička, 12-znamenkovni heksadecimalni identifikator)
* IP adresa se sastoji od okteta (IPv4: 4 okteta), može se mijenjati i koristi protokole; javne IP adrese dodjeljuje ISP.
* IPv4 ima ~4.29 milijarde adresa; **IPv6** rješava nestašicu (2^128 adresa).
* MAC adresa: prvih 6 znakova identificira proizvođača, zadnjih 6 su jedinstveni broj; može se **spoofati** (lažirati).
* Spoofing MAC adrese može zaobići loše postavljene sigurnosne mjere (npr. firewall koji se oslanja samo na MAC).
* Primjer/praktični lab: hotel Wi‑Fi koji blokira neplaćene uređaje — pokušaj promjene Bobove MAC adrese u Aliceinu.

IP address and MAC address
=======
* **Delivery** = metode isporuke malicioznog payloada.
* Primjeri metoda:

  * Phishing emailovi (attachment ili link; varljive nazive datoteka)
  * Spear phishing (ciljani, lažno prikazani pošiljatelj)
  * Zlonamjerne web poveznice (domain spoofing, skraćene URL-ove)
  * Platforme za dijeljenje datoteka (upload zlonamjernih fajlova)
  * Malvertising (zlonamjerne reklame na legitimnim stranicama)
  * SMS phishing / smishing
  * Social engineering (pripovijedanje da se korisnik prevari i pokrene fajl)
  * Fizička isporuka (USB, DVD itd.)
* Protumjere: edukacija korisnika, filtriranje emailova i weba, WAF, mrežno praćenje i pravovremeno patchanje.


* **Exploitation** = iskorištavanje ranjivosti ciljnog sustava
* Primjeri:

  * Slabe ili default lozinke (password-based attacks)
  * Phishing i sofisticirane metode krađe lozinki
  * Softverske ranjivosti (client ili network services)
  * Zero-day exploits (ranjivost iskorištena prije nego što vendor zna za nju)
  * SQL injection, buffer overflow i druge ranjivosti
* **Protumjere / obrana:**

  * Primjena jakih lozinki i **multi-factor authentication (MFA)**
  * Patch management i redovito zakrpavanje sustava
  * Vulnerability scanning za otkrivanje ranjivosti
  * **Intrusion Prevention Systems (IPS)** – blokira poznate exploit pokušaje
  * **Web Application Firewalls (WAF)** – blokira napade na web aplikacije (SQLi, XSS, CSRF)

---

* **Installation** = osiguravanje trajnog pristupa sustavu nakon iskorištavanja ranjivosti
* Metode održavanja pristupa: zakazane zadaće (Windows scheduled tasks), cron jobovi, izmjene startup skripti, instalacija servisa/daemona
* Napadi često uključuju: instaliranje malwarea, backdoora, rootkita ili web shellova
* Napadači koriste i legitimne alate sustava (LOLBins) za prikrivanje aktivnosti
* Protumjere: praćenje novih procesa i servisa, Endpoint Detection and Response (EDR), redovite revizije i usporedbe sa sigurnosnom bazom, te application allowlisting



* **Command & Control (C2)** = infrastrukturna taktika za upravljanje kompromitiranim uređajima
* Taktike C2:

  * Korištenje uobičajenih protokola (HTTP, HTTPS, DNS, SMTP) za prikrivanje aktivnosti
  * Šifrirani kanali (HTTPS) za skrivanje od mrežnog nadzora
  * DNS tunnelling – kodiranje podataka unutar DNS zahtjeva
  * Korištenje društvenih mreža i cloud servisa (Dropbox, Google Docs)
  * Registracija vlastitih domena s **Domain Generation Algorithms (DGA)**
  * **Fast Flux** – izmjena IP adresa vezanih za jednu domenu; kompromitirani uređaji djeluju kao proxy
* **Protumjere / obrana:**

  * Praćenje mreže putem firewall-a, IDS i IPS
  * Analiza DNS prometa i neuobičajenih upita
  * Praćenje web prometa i filtriranje sumnjivih URL-ova
  * Inspekcija šifriranog prometa za HTTPS C2
  * Honeypots za detekciju i analizu C2 komunikacije

---



* **Actions on Objectives** = faza u kojoj napadač ostvaruje svoj glavni cilj
* Primjeri ciljeva:

  * Destruktivni napadi: brisanje ili oštećenje podataka
  * Financijska dobit: ransomware, neovlašteni transferi
  * Krađa podataka (data exfiltration)
  * Lateralno kretanje kroz mrežu
  * Manipulacija Industrial Control Systems (ICS)
  * Dugoročna prisutnost za kasnije izvođenje napada
* **Protumjere / obrana:**

  * Data Loss Prevention (DLP) za zaštitu podataka
  * Redovite sigurnosne kopije i plan oporavka
  * Segmentacija mreže i stroge kontrole pristupa (princip najmanjih privilegija)
  * Praćenje aktivnosti korisnika i endpointa (EDR)

---



* **Cyber Kill Chain** = 7 faza napada; najveća šteta događa se u posljednjoj fazi
* **Plava ekipa (defensive/blue team):** fokus na otkrivanju i blokiranju napada u ranim fazama
* **Crvena ekipa (offensive/red team):** simulira stvarne napadače da testira obranu i učinkovitost sigurnosnih kontrola
* Cilj: naučiti koliko dobro tim može detektirati i spriječiti napad

---











* **Linux** = široko korišten u serverima, ugrađenim sustavima i cloud okruženjima
* **SOC analitičari** često istražuju Linux alarme i incidente
* **Ciljevi učenja:**

  * Istražiti **authentication, runtime i system logove** na Linuxu
  * Naučiti **komande i zamke** pri radu s logovima
  * Razumjeti kako **auditd** prati i prijavljuje događaje
  * Vježbati sve izvore logova u VM-u
* **Preporučene sobe:** Linux Fundamentals, Linux Shells, Logs Fundamentals
* **Pristup stroju:**

  * Klik na **Start Machine**, zatim **Show Split View** ako je potrebno
  * Moguće je koristiti root privilegije: `sudo su`

---


* **Linux distribucije**: Debian, Ubuntu, CentOS, RHEL
* Fokus: **Linux serveri bez GUI-a**, ne desktop logging
* **Log format**:

  * Većina događaja zapisuje se u **plain text** datoteke
  * Nema strogo definiranih kodova događaja ili formata
  * Većina logova nalazi se u **/var/log**
  * Primjer: `/var/log/syslog` sadrži agregirane sustavne događaje
* **Filtriranje logova:**

  * Koristi se `grep` za traženje ključnih riječi (npr. `CRON`)
  * `grep -v CRON` za isključivanje određenih događaja
* **Otkrivanje logova:**

  * Logovi su u **/var/log/**, može se pretraživati ključnim riječima: `login`, `auth`, `session`
  * Komanda: `grep -R -E "auth|login|session" /var/log`
* **Upozorenja:**

  * Linux omogućuje prilagodbu formata, detaljnosti i lokacije logova
  * Različite distribucije mogu imati različite logove ili formate

---

* **/var/log/auth.log** (RHEL: `/var/log/secure`) bilježi autentikacijske i user-management događaje.
* Zapis sadrži: vrijeme, hostname, servis i poruku (plain text).
* **Login/logout:** `session opened` / `session closed` za lokalne, SSH i cron sesije.
* **SSH događaji:** `Accepted` i `Failed` zapisi (npr. `Failed password for ...`, `Accepted publickey for ...`).
* **Sudo/COMMAND=** zapisi pokazuju koje su naredbe pokrenute s privilegijama.
* **User management:** događaji `useradd`, `usermod`, `userdel`, `passwd` za promjene korisnika/lozinki.
* Pretraživanje: `grep -E 'session opened|session closed' /var/log/auth.log`, `grep "sshd" /var/log/auth.log`, `grep -E '(passwd|useradd|usermod|userdel)\[' /var/log/auth.log`.

* **Opći sistemski logovi**: `/var/log/kern.log`, `/var/log/syslog` (ili `/var/log/messages`), `/var/log/dpkg.log` (Debian) ili `/var/log/dnf.log` (RHEL).
* **App-specifični logovi**: baza podataka, mail, containeri, web server (npr. `/var/log/nginx/access.log` prikazuje sve HTTP zahtjeve: IP, vrijeme, ruta, status, veličina).
* **Bash history**: `~/.bash_history` i `history` prikazuju unesene naredbe; zapis se upisuje pri odjavi.
* **Ograničenja Bash historyja**: naredbe mogu biti sakrivene dodavanjem vodećeg razmaka, korištenjem skripti ili prelaskom na shell koji ne zapisuje povijest.
* **SOC napomena**: mnogi logovi su korisni za DFIR, ali su često bučni i zahtijevaju filtriranje; app-logovi i sistemski logovi treba kombinirati za učinkovitu istragu.


* **Problem**: Standard Linux logs ne prate runtime događaje (kreiranje procesa, promjene datoteka, mrežne aktivnosti).
* **Rješenje**: Koristi se **auditd** ili slični alati za praćenje runtime događaja.
* **System calls**: Pozivi OS-u za resurse (npr. `execve` za pokretanje programa).
* **Važnost**: EDR i alati za praćenje logova bilježe sistemske pozive, što omogućava detekciju napada koji se ne vidi u običnim logovima.


* **Auditd** je Linuxov ugrađeni alat za praćenje runtime događaja (kreiranje procesa, promjene datoteka, mrežne aktivnosti).
* **Pravila** se nalaze u `/etc/audit/rules.d/` i definiraju koje sistemske pozive i događaje pratiti.
* **Logovi** se čuvaju u `/var/log/audit/audit.log`, a pregled je lakši s `ausearch -i -k <key>` (pretvara zapis u čitljiv format i filtrira po ključu).
* **Tipična polja u auditd logu**:

  * `pid/ppid`: PID procesa i roditelja
  * `auid`: korisnik koji se prijavio (originalni login)
  * `uid`: korisnik koji je izvršio radnju
  * `tty`: identifikator sesije
  * `exe`: apsolutna putanja izvršnog programa
  * `key`: ključ za filtriranje događaja
* **Praćeni događaji**: pokretanje procesa (`wget`), promjene kritičnih datoteka (`/etc/ssh/sshd_config`), mrežne aktivnosti itd.
* **Alternativni alati**: Sysmon za Linux, Falco, Osquery, EDR rješenja – svi prate sistemske pozive i pružaju sličnu funkcionalnost s boljim formatom za SIEM.







**Klijentske (client-side) napade** izazivaju slabosti na strani korisnika ili na njegovom uređaju. Oni iskorištavaju ranjivosti u preglednicima ili varaju korisnika da napravi nesigurne radnje kako bi napadač dobio pristup računima ili osjetljivim podacima. Takvi napadi mogu dovesti do gubitka podataka. Širenje web aplikacija i integracija trećih stranih dodataka povećava površinu napada u preglednicima.

**Primjer:** Dok pregledavate e-trgovinu, napadač može sakriti zlonamjerni prozor u pozadini stranice koji krade vaše kolačiće za prijavu. Vi ništa ne primijetite, ali napadač sada može pristupiti vašem računu.

**Ograničenja SOC-a:**

* SOC alati poput server logova i mrežnog snimanja obično **ne vide što se događa unutar korisničkog preglednika**.
* Napadi se odvijaju na korisnikovom sustavu, što otežava ili onemogućava detekciju bez dodatnih sigurnosnih kontrola ili endpoint nadzora.

**Uobičajeni klijentski napadi:**

1. **XSS (Cross-Site Scripting)** – izvršavanje zlonamjernih skripti u pregledniku korisnika preko ranjivih web elemenata (npr. komentar box).
2. **CSRF (Cross-Site Request Forgery)** – preglednik šalje neautorizirane zahtjeve u ime korisnika.
3. **Clickjacking** – napadač preklapa nevidljive elemente preko legitimnog sadržaja, zavaravajući korisnika.





**Napadi na strani servera (server-side attacks)** iskorištavaju ranjivosti u web serveru, kodu aplikacije ili backendu koji podržava web stranicu/aplikaciju. Za razliku od klijentskih napada koji manipuliraju korisnikom, server-side napadi ciljaju **sustave i njihovu logiku**. Napadači mogu iskoristiti propuste u konfiguraciji, logici servera ili obradi unosa da dođu do osjetljivih podataka ili oštete usluge.

**Primjer:** Ako web stranica nepravilno obrađuje unos u formularu (npr. login ili tražilicu), napadač može pristupiti osjetljivim informacijama u backend bazi podataka.

**Prednost za obrambene timove (SOC):**

* Server-side napadi ostavljaju **trag u logovima i mrežnom prometu**, što omogućava detekciju.

**Uobičajeni server-side napadi:**

1. **Brute-force** – ponavljani pokušaji različitih korisničkih imena i lozinki da bi se dobio neautorizirani pristup. Često se koriste automatizirani alati.
2. **SQL Injection (SQLi)** – napad na bazu podataka kada aplikacija koristi nesigurno spajanje stringova za kreiranje SQL upita. Napadači mogu mijenjati SQL naredbe i pristupiti podacima.
3. **Command Injection** – napadač ubacuje naredbe u korisnički unos, a server ih izvršava s privilegijama aplikacije.

* **Access log** bilježi svaki HTTP zahtjev: IP klijenta, vremenski žig, traženu stranicu, status kod, veličinu odgovora, referrer i User‑Agent.
* Polja loga mogu ukazivati na sumnjivo ponašanje (npr. sumnjive IP adrese, neobično vrijeme, povratni kodovi 404, veliki/sitni odgovori, nepoznati referreri, alati u User‑Agentu).
* **Tipični attack chain u logovima:**

  * Directory fuzz → pronalazak validnih ruta (200).
  * Brute‑force na login formu → ponovljeni POST zahtjevi u kratkom roku; 302 može značiti uspješnu prijavu i preusmjeravanje (npr. na /account).
  * SQLi napadi → zabilježeni payloadi u query stringu kod GET zahtjeva (npr. `OR '1'='1'`).
* **Ograničenje:** access logovi često ne bilježe tijelo POST zahtjeva (npr. lozinke), pa ne vide stvarni payload za POSTove; GET ponekad bilježi query string ovisno o konfiguraciji.
* **Istraga (zadatak):** otvoriti `access.log` na desktopu VM‑a i analizirati zapise da bi se rekonstruirao napad i utvrdilo kako je došlo do proboja.


* Captures pokazuju sve (HTTP headeri, POST tijela, kolačići) — logovi često ne.
* Filtriraj u Wiresharku: `http` ili `ip.addr == <target> && http`.
* Desni klik → **Follow → HTTP Stream** za kompletan request/response.
* Traži: directory fuzz GET-ove, brze POST-ove za `/login.php` (uspješan POST s lozinkom), SQLi payload u URL‑u ili tijelu.
* Koristi `tshark` za brzo ekstraktiranje URL‑ova i potencijalnih lozinki iz `traffic.pcap`.















