# Web stranica Instituta Sveti Ivan Zlatousti: upute

## Što je u paketu

| Datoteka / mapa | Namjena |
|---|---|
| `index.html` | Cijela stranica: naslovnica, Studij (`#studij-duhovnosti`), Privatnost (`#privatnost`) |
| `content/sadrzaj.json` | Sav promjenjivi sadržaj: novosti, događanja, projekti, fotografije, obavijesti, raspored, predavači, društvene mreže |
| `admin/` | Urednik sadržaja (Sveltia CMS), dostupan na `…netlify.app/admin/` |
| `uploads/` | Fotografije koje urednici dodaju kroz urednik |
| `favicon.svg`, `og-image.png` | Ikona stranice i slika za dijeljenje na Facebooku i WhatsAppu |
| `robots.txt`, `sitemap.xml` | Za tražilice |

## Adresa stranice

Stranica je podešena na `https://institutsvetiivanzlatousti.netlify.app`. Ako kasnije uzmete vlastitu domenu, zamijenite tu adresu u `index.html` (oznake u zaglavlju), `admin/config.yml`, `robots.txt` i `sitemap.xml`.

## Objava (GitHub + Netlify)

1. GitHub repozitorij: `institutsvetiivanzlatousti-maker/institut-web`. Na njegovoj stranici kliknite *uploading an existing file*, povucite **sadržaj** ove mape (ne ZIP) i kliknite **Commit changes**.
2. U Netlifyju, projekt **institutsvetiivanzlatousti** → *Project configuration → Build & deploy → Link repository* → GitHub → `institut-web`. Build naredba ostaje prazna, mapa za objavu je korijen (`/`).
3. Svaka promjena na GitHubu (i svako spremanje u uredniku) za minutu-dvije pojavi se na stranici.

## Prijava urednika (GitHub ključ)

Urednik je **Sveltia CMS** na adresi `…netlify.app/admin/`. Ne treba Netlify Identity.

1. Na GitHubu: slika profila gore desno → **Settings** → na dnu lijevo **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
2. Ime npr. `urednik-weba`, *Expiration* npr. 1 godina. Pod *Repository access* odaberite **Only select repositories** → `institut-web`.
3. Pod *Permissions → Repository permissions* postavite **Contents: Read and write**. Kliknite **Generate token** i kopirajte ključ (počinje s `github_pat_`). Spremite ga na sigurno mjesto, GitHub ga više neće prikazati.
4. Otvorite `…netlify.app/admin/`, kliknite **Sign In with Token**, zalijepite ključ. Preglednik vas pamti.
5. Kad ključ istekne ili ga izgubite, napravite novi istim putem. Ključ nikome ne šaljite.

## Rubrike stranice

Stranica ima devet rubrika, a svaka ima svoju adresu:

| Rubrika | Adresa |
|---|---|
| Naslovnica | `#pocetna` |
| O Institutu (povijest, misija, vizija, vodstvo) | `#o-institutu` |
| Studij istočne kršćanske duhovnosti | `#studij-duhovnosti` |
| Projekti | `#projekti` |
| Priča pored Griča | `#price-ispod-grica` |
| Novosti i događanja | `#novosti` |
| Dokumenti | `#dokumenti` |
| Donacije | `#donacije` |
| Kontakt | `#kontakt` |

Prekidač **HR / EN** u zaglavlju mijenja jezik cijele stranice, a preglednik pamti odabir.

## Ulaz za administratora

- U podnožju je gumb **Prijava za administratore**, a urednik je i izravno na `…netlify.app/admin/`.

## Što se može uređivati

U uredniku postoje tri skupine:

1. **Novosti, događanja, projekti, dokumenti…** (`content/sadrzaj.json`):
   - novosti, događanja, projekti (sa slikom i dužim opisom)
   - **Institut i Studij u medijima**: arhiva poveznica na članke (naslov, godina, izvor, vrsta, poveznica); prikazuje se na stranici Novosti s pretraživanjem i filtrima
   - dokumenti (prenesite PDF ili upišite poveznicu)
   - vodstvo Instituta, fotogalerija
   - obavijesti, raspored i predavači Studija
   - predmeti Studija po godinama (s opisima) i vodstvo Studija
   - društvene mreže, Tajništvo SIKD-a

   Polja s oznakom **(EN)** su engleska verzija i nisu obavezna: ako su prazna, na engleskoj verziji prikazuje se hrvatski tekst.
2. **Tekstovi stranice (hrvatski)** (`content/tekstovi.json`): svaki tekst na stranici, po rubrikama, te kontakt podaci Instituta i podaci za uplatu.
3. **Texts (English)** (`content/tekstovi.en.json`): engleska verzija svih tekstova. Ispod svakog polja vidi se hrvatski izvornik.

**Kalendar nastave (stranica Studija):** termine upisujete u *Raspored Studija (kalendar nastave)*:
- **Datum, početak i završetak:** npr. 12.12.2026., 9:00 – 13:30.
- **Vikend nastava:** popunite i polje *Do datuma*, pa se termin prikaže na svim danima.
- **Što posjetitelji vide:** termini se pojavljuju u mjesečnom kalendaru. Posjetitelji mogu listati mjesece, kliknuti dan i dodati pojedini termin ili cijeli raspored u svoj kalendar (Google, Apple, Outlook).
- **Događanja vrste „Nastava Studija“** također se prikazuju u ovom kalendaru.

**Kalendar događanja (Novosti i događanja):**
- **Što se prikazuje:** sva događanja Instituta osim nastave Studija, u kalendaru ili kao popis.
- **Posjetitelji:** filtriraju po vrsti i dodaju jedno ili sva nadolazeća događanja u svoj kalendar.
- **Višednevna događanja** (npr. konferencija): popunite i polje *Do datuma*.

**Priča pored Griča:** dodajte ih kao događanje s vrstom **„Priča pored Griča“**. Takva se večer prikazuje na stranici Priče pored Griča (nadolazeće i održane), a i u općem kalendaru.

**Oblikovanje teksta:** `*kurziv*`, `**podebljano**`, `[tekst poveznice](https://adresa)`. Novi red u polju postaje novi red na stranici, a prazno polje vraća izvorni tekst.

## Obrazac za upite (Netlify Forms)

- Obrazac na stranici Kontakt šalje upite u Netlify. Netlify ga sam prepozna pri prvoj objavi, ništa ne treba posebno uključiti.
- Upiti se vide u Netlifyju pod *Forms → upit*.
- Da upiti stižu i e-poštom: *Site configuration → Notifications → Emails and webhooks → Form submission notifications → Add notification → Email notification*, pa upišite e-adresu Instituta.
- Besplatni Netlify paket uključuje ograničen broj upita mjesečno, što je za ovakvu stranicu obično dovoljno.
- Obrazac ima zaštitu od neželjenih poruka (skriveno polje). Izvan Netlifyja obrazac ne može slati, nego posjetitelju nudi slanje e-poštom.

## Kako urednici rade

- Na `/admin/` se prijave, otvore **Sadržaj stranice** i dodaju ili mijenjaju zapise.
- Klik na **Objavi** sprema promjenu, a stranica se osvježi za minutu-dvije.
- Za fotografije koristite JPEG širine do 1600 px. Prije objave fotografija s prepoznatljivim osobama provjerite imate li pristanak.
- **Događanja** se sama razvrstavaju na nadolazeća i prošla prema datumu.

## Napomene

- Otvaranje `index.html` izravno s diska prikazuje ugrađeni početni sadržaj. Sadržaj iz `content/sadrzaj.json` učitava se tek kad je stranica na poslužitelju.
- Google karta učitava se tek kad posjetitelj klikne „Prikaži kartu“, zbog GDPR-a.
- Tekst o privatnosti napisan je prema stvarnom radu stranice. Prije objave neka ga pregleda osoba zadužena za zaštitu podataka.
- Stranica može raditi i na drugom hostingu; urednik i dalje radi jer sprema izravno na GitHub.

## Donacije i barkod

- Rubrika „Podržite nas“ (`#podrzite`) sama izrađuje HUB-3 2D barkod (PDF417) prema odabranom iznosu i svrsi. Posjetitelj ga skenira aplikacijom mobilnog bankarstva.
- Barkod (PDF417, HUB-3: 9 stupaca, razina zaštite 4, UTF-8) izrađuje sama stranica, bez vanjskih biblioteka, pa radi i bez interneta.
- Podatke primatelja, IBAN, iznose i svrhe mijenjate u uredniku (*Tekstovi stranice → Podaci za uplatu i barkod*). Naziv i ulica u barkodu smiju imati najviše 25 znakova.
- Šifra namjene je `CHAR` (dobrotvorno plaćanje), a model `HR99`.
- Prije objave napravite probnu donaciju od 1 € i provjerite kako se podaci prikazuju u vašoj banci.

## Logotipi i datoteke

- `img/logo-institut.jpg`: logo Instituta (stranica O Institutu).
- `img/znak.png`, `favicon.png`, `apple-touch-icon.png`: znak u zaglavlju i ikona stranice.
- `img/kriz.png`: zlatni križ iz loga (naslovnica).
- `img/sikd-zlatni.png`, `img/sikd-tamni.png`: logo Studija za tamnu i svijetlu podlogu.
- `uploads/dokumenti/vodic-kroz-studij-sikd.pdf`: Vodič kroz Studij, povezan sa stranice Studija i s popisa Dokumenti.
