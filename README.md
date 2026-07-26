# AUTODIAG PRO

Consolă de diagnoză auto care rulează integral în browser. Fără server, fără cont, fără urmărire.
Toate datele sunt în fișier — aplicația funcționează și fără internet.

**Demo:** înlocuiește cu adresa ta după publicare.

---

## Ce conține

| | |
|---|---|
| Coduri de eroare | 621 (P / B / C / U + specifice mărcilor), cu note din practică pe 68 dintre ele |
| Motorizări | 1.180, pe 173 de modele și 32 de mărci, cu coduri de motor |
| Ghiduri de diagnoză | 27, structurate: ordinea verificărilor → capcane → concluzie |
| Referințe tehnice | 42 de secțiuni, 481 de intrări |
| Diagrame de principiu | 12 (pinout OBD, releu, CAN, common-rail, EGR, răcire, frânare) |
| Probleme cunoscute | 52, pe model și motorizare |
| Reguli de corelație DTC | 17 |
| PID-uri OBD-II | 53, cu formulele din standard |

## Funcții

- **Diagnoză pe simptome** — selectezi ce observi, primești cauzele probabile ordonate după gravitate
- **Analizor de coduri** — introduci codurile de la tester, primești ordinea de lucru cauză → efect
- **Decodor VIN** — offline (ISO 3779, cu validarea cifrei de control) și online (catalogul NHTSA vPIC)
- **Decodor răspuns OBD brut** — traduce ce îți arată un adaptor ELM327 ieftin
- **Service în apropiere** — service, vulcanizare, piese, ITP, benzinării (OpenStreetMap)
- **Raport printabil** — cu antet, vehicul, dată și număr de referință

## Surse de date

| Sursă | Licență | Folosire |
|---|---|---|
| SAE J2012 / J1979, ISO 15031, ISO 3779 | standarde publice | coduri, PID-uri, structura VIN |
| [NHTSA vPIC](https://vpic.nhtsa.dot.gov/api/) | domeniu public (SUA) | decodare VIN online |
| [NHTSA Recalls](https://api.nhtsa.gov/) | domeniu public (SUA) | campanii de rechemare |
| [OpenStreetMap](https://www.openstreetmap.org/) | ODbL | service în apropiere |
| [NHTSA TSB](https://www.nhtsa.gov/recalls) | domeniu public (SUA) | buletine tehnice de service |
| [TÜV Report](https://www.tuev-nord.de/en/knowledge/advice-and-tips-mobility/tuev-report/) | statistici publice | rate de defecte pe model |
| [KBA](https://www.kba.de/) | date publice (Germania) | rechemări europene |
| [EU Safety Gate](https://ec.europa.eu/rapex) | CC BY 4.0 | legătură pentru rechemări europene |

Nu conține date copiate din baze comerciale (auto-data.net, ALLDATA, Autodata, HaynesPro, TecDoc).
Schemele electrice pe model sunt proprietatea producătorilor și nu sunt reproduse — sunt incluse
doar diagrame de principiu, desenate de la zero.

---

## Publicare

### GitHub Pages

1. Creează un depozit nou pe GitHub (public).
2. Încarcă toate fișierele din acest folder (`index.html`, `sw.js`, `manifest.webmanifest`, pictogramele, `.nojekyll`).
3. **Settings** → **Pages** → la *Source* alege **Deploy from a branch**, ramura `main`, folderul `/ (root)`.
4. Salvează. În 1–2 minute apare adresa: `https://NUMELE-TAU.github.io/NUMELE-DEPOZITULUI/`

### Vercel

1. Intră pe [vercel.com](https://vercel.com) și conectează-ți contul de GitHub.
2. **Add New** → **Project** → alege depozitul.
3. Framework Preset: **Other**. Build Command: gol. Output Directory: gol.
4. **Deploy**. Primești o adresă `https://numele-proiectului.vercel.app`

Alternativ, fără GitHub: instalează `npm i -g vercel`, apoi rulează `vercel` în acest folder.

### Netlify

Trage folderul peste [app.netlify.com/drop](https://app.netlify.com/drop). Gata.

---

## De ce contează găzduirea pe HTTPS

Deschis ca fișier local, browserul blochează câteva lucruri din motive de securitate.
Găzduit, aplicația câștigă:

- **Localizare** — butonul „Lângă mine" funcționează
- **Instalare reală** — apare butonul de instalare, aplicația stă pe ecranul principal ca oricare alta
- **Offline garantat** — service worker-ul păstrează aplicația în memorie după prima vizită
- **Cereri de rețea** — decodarea VIN online și căutarea de service merg fără restricții
- **Distribuire prin link** — trimiți o adresă, nu un fișier de 900 KB

## Confidențialitate

Nu există server propriu și nu se colectează nimic. Vehiculul, profilurile și istoricul de scanări
se salvează exclusiv în browserul tău (`localStorage`), pe dispozitivul tău.

Cererile către NHTSA și OpenStreetMap pleacă direct din browserul tău către acele servicii, doar când
apeși butoanele respective, și conțin doar ce ai introdus (VIN sau localitate).

## Licență

Codul: MIT. Datele preluate din surse externe păstrează licențele lor, menționate mai sus.

## Avertisment

Instrument de orientare, nu înlocuiește diagnoza la un service autorizat.
Pentru frâne, direcție, airbag sau supraîncălzire, oprește deplasarea și cere ajutor calificat.
