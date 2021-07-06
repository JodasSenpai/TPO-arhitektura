# Načrt sistema

|                             |                                                         |
| :-------------------------- | :------------------------------------------------------ |
| **Naziv projekta**          | Dog Walkers                               |
| **Člani projektne skupine** | Koren Aljoša, Škrlj Klemen, Uran Maj, Štrosar Grmek Loris, Tavčar Simon |
| **Kraj in datum**           | Slovenija, 06.04.2021                                    |

## Povzetek

Dokument prikazuje temeljit načrt za sistem DogWalkers. 

Načrt arhitekture sistema je prikazan s pomočjo dveh komponentnih diagramov: diagram logičnega pogleda in diagram razvojnega pogleda. Razvojni pogled prikazuje arhitekturni vzorec MVC, ki razdeli sistem na 3 glavne logične komponente (Model-View-Controller) zadolžene za različne razvojne vidike aplikacije. Iz diagrama logičnega pogleda pa je razvidna delitev funkcionalnosti sistema na več glavnih paketov, in kako ti sodelujejo med seboj.

Načrt strukture sistema je prikazan z razrednim diagramov sestavljenim iz 59 razredov. 8 razredov predstavljajo entitete: Administrator, Registriran uporabnik, Lastnik psa, Sprehajalec, Podjetje, Oglas, Pogovor in Sporocilo. Prikazani so 3 zunanji vmesniki: OpenStreetMapsApi (za iskanje lokacij), MailTo (za pošiljanje elektrosnke pošte) in DogWalkersAPI (za statistiko o uporabnikih). Ostali razredi prikazujejo kontrolerje in zaslonske maske. Za vsak primer uporabe je prikazan še posebaj VOPC diagram z vsemi metodami te funkcionalnosti.Za vsak razred so podrobno opisani njegovi atributi in nesamoumevne metode. Pri razvoju bosta uporabljena tudi dva načrtovalska vzorca: Singleton in Factory Method, kar je tudi razvidno iz razrednega diagrama. 

Obnašanje 27 funkcionalnosti sistema DogWalkers je prikazanih s pomočjo diagramov zaporedja. Prikazani so osnovni, izjemni in alternativni tokovi s 49 diagrami.

## 1. Načrt arhitekture

### 1.1 Logični pogled
Na sliki je prikazan logični model arhitekture naše aplikacije. Njene glavne funkcionalnosti so razdeljene v sedmih komponentah: Avtentikacija, Oglasi, Profil, Administratorske pravice, Pogovor, Razširitve in Zunanji vmesniki. Vsaka od komponent obsega njene glavne funkcionalnosti, običajni prehodi med njimi pa so označeni s puščicami. Tako se naprimer uporabnik prijavi v aplikaciji, si ogleda oglase, stopi v pogovor s potencialnim sogovornikom, tam pa ima možnosti dostopa do različnih razširitev. Prav tako lahko uporabnik iz svoje prve strani dostopa do svojega profila, ga uredi in shrani spremembe. Administrator pa ima set svojih funkcionalnosti, ki so vezane na pregld uporabnikov in upravljanje z njihovimi profili. Do zunanjih vmesnikov sistem dostopa ob proženju specifčnih funkcionalnosti kot so filtriranje oglasov po oddaljenjosti in prijava neprimerne vsebine.
![arhitektura logicni pogled](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/arhitekturaLogicni.png)

### 1.2 Razvojni pogled
Na sliki je prikazan razvojni pogled arhitekture naše aplikacije. Aplikacija uporablja arhitekturni vzorec model-pogled-krmilnik (MVC). Brskalnik neposredno komunicira z pogledom (view). S klikanjem gumbov in drugih interakcijskih elementov se začnejo izvajati funkcije na krmilniku (controller) specifičnega pogleda. Ta nato komunicira z modelom, ki mu vrne podatke oz. naredi neposredne posege na podatkovni bazi. Krmilnik pa nato posreduje podatke nazaj na pogled. Prav tako pa je krmilnik zadolžen za komuniciranje z zunanjimi vmesniki. 
![arhitektura razvojni pogled](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/arhitekturaRazvojni.png)

## 2. Načrt strukture

### 2.1 Razredni diagram

Na spodnji sliki je predstavljen celostni razredni diagram. Za večjo sliko priporočamo da jo odprete v novem zavihku. Razredni diagram vsebuje vse razrede zaslonskih mask (oznaka ZM), zaslonskih vmesnikov (oznaka ZV), kontrolerjev (oznaka K) in entitet. V oranžnem kvadratu je označen razred, kjer je uporabljen načrtovalski vzorec Singleton. V vijola kvadratih pa je označeno kateri razredi bodo uporabljali Factory Method. tu deluje razred Registriran uporabnik kot superclass, razredi "Lastnik psa", "Sprehajalec" in "Podjetje" pa so podrazredi razreda "Registriran uporabnik".

![Celotni razredni diagram](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/celotni_razredni_diagram.png)

### 2.2 VOPC diagrami posameznih funkcionalnosti
### 2.2.1 Registracija
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/registracijaVOPC.png)
### 2.2.2 Prijava
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prijavaVOPC.png)
### 2.2.3 Prikaz seznama lastnikov psov
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prikazSeznamaLastnikovPsovVOPC.png)
### 2.2.4 Prikaz seznama sprehajalcev
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prikazSeznamaSprehajalcevVOPC.png)
### 2.2.5 Prikaz seznama podjetij
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prikazSeznamaPodjetijVOPC.png)
### 2.2.6 Administratorjev pregled profila
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/admnistratorjevPregledProfilaVOPC.png)
### 2.2.7 Brisanje oglasa
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/brisanjeOglasaVOPC.png)
### 2.2.8 Urejanje profila
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/urejanjeProfilaVOPC.png)
### 2.2.9 Brisanje profila
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/brisanjeProfilaVOPC.png)
### 2.2.10 Pregled seznama oglasov in Pregled izbranega oglasa
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/pregledSeznamaOglasovVOPC.png)
### 2.2.11 Zavrni ponudbo
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/zavrniPonudboVOPC.png)
### 2.2.12 Sprejmi ponudbo
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/sprejmiPonudboVOPC.png)
### 2.2.13 Prijava neprimerne vsebine
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prijavaNeprimerneVsebineVOPC.png)
### 2.2.14 Pregled profila sogovornika
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/pregledProfilaSogovornika.png)
### 2.2.15 Filtriranje seznama oglasov po oceni
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/filtriranjeOcenaVOPC.png)
### 2.2.16 Filtriranje seznama oglasov po oddaljenosti
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/filtriranjeOddaljenostVOPC.png)
### 2.2.17 Prikaz seznama pogovorov
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/prikazSeznamaPogovorovVOPC.png)
### 2.2.18 Pogovor med lastnikom psa in sprehajalcem
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/pogovorVOPC.png)
### 2.2.19 Podajanje ocene
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/podajanjeOceneVOPC.png)
### 2.2.20 Ustvarjanje novega oglasa
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/ustvarjanjeNovegaOglasaVOPC.png)
### 2.2.21 Pregled svojih aktivnih oglasov
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/pregledAktivnihOglasovVOPC.png)
### 2.2.22 Urejanje aktivnega oglasa
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/urejanjeOglasaVOPC.png)
### 2.2.23 Brisanje aktivnega oglasa
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/brisanjeAktivnegaOglasaVOPC.png)
### 2.2.24 Generiranje varnostne šifre
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/generiranjeSifreVOPC.png)
### 2.2.25 Izdelava statistike o uporabnikih
![VOPC](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/vopc/statistikaVOPC.png)


### 2.3 Opis razredov

### 2.3.1  E Administrator

#### Atributi

- id:
  - tip int
- uporabnisko_ime
  - tip String
- email:
  - tip String
  - oblika xxxxx@xx.xx
- nakljucna_vrednost:
  - tip String
  - naključni znaki za vsakega uporabnika dolžine 16 znakov
- zgoscena_vrednost:
  - tip String
  - dolžine 64 znakov, generirana s pomočjo naključne vrednosti in dejanskega gesla
- vloga:
  - tipa char
  - vrednost A

#### Metode

- prijavi:
  - metoda vrača string v obliki JWT
  - metoda sprejme email ter geslo
  - metoda preveri ujemanje gesla, v kolikor se ne ujema vrne error
- izbrisRacuna:
  - metoda ne vrača rezultata
  - metoda sprejme ID v obliki int
  - metoda izbriše račun


### 2.3.2 ZM prijava

#### Atributi

- e-mail:

  - String,
  - e-poštni naslov za prijavo

- geslo:
  - String,
  - geslo za prijavo

#### Metode

- klikGumbPotrdi:
  - klik se proži, ko uporabnik klikne gumb prijava,
  - v parameter sprejme podatke obrazca tipa Form,
  - rezultat je tipa void,
  - metoda proži akcijo pošiljanja prijavnih podatkov v krmilniku
- init:
  - metoda proži ustvarjanje ZM
  - metoda ne sprejme parametrov
  - metoda ne vrača rezultata

### 2.3.3 K prijava

#### Metode

- preveriVnesenePodatke
  - metoda sprejme parameter form tipa Form,
  - rezultat je tipa Boolean,
  - metoda preveri vnesene podatke v obrazcu ali so vsi vpisani ali so pravilnega tipa/oblike
- prijaviUporabnika
  - metoda sprejme parameter tipa String z ID-jem uporabnika
  - metoda sproži metodo pripraviMail v ZV MailToVmesnik
  - metoda ne vrača rezultata
- preusmeriNaPregledSeznamaOglasov:
  - metoda ne sprejme parametrov
  - metoda proži init v ZM Pregled seznama oglasov
  - metoda ne vrača rezultata
- preusmeriNaPregledSvojihAktivnihOglasovp:
  - metoda ne sprejme parametrov
  - metoda proži init v ZM Pregled svojih aktivnih oglasov(p)
  - metoda ne vrača rezultata
- preusmeriNaPregledSvojihAktivnihOglasovs:
  - metoda ne sprejme parametrov
  - metoda proži init v ZM Pregled svojih aktivnih oglasov(s)
  - metoda ne vrača rezultata
- preusmeriNaSeznamLastnikovPsov:
  - metoda ne sprejme parametrov
  - metoda proži init v ZM Prikaz seznama lastnikov psov
  - metoda ne vrača rezultata

### 2.3.4 ZM DogWalkersAPI

#### Metode

- GET /ads/number:
  - metoda sprejme query parametre tipa String, in sicer "date", "isActive" in "type"
  - parameter date je v obliki "YYYY-mm-dd", isActive ima vrednost true ali false, type pa sprehajalec ali podjetje
  - metoda vrača JSONObject, ki vsebuje ključ adsNumber in zraven vrednost kot int
  - v primeru napačnega klica metoda vrača standardne HTTP napake
- GET /users/number:
  - metoda sprejme query parametre tipa String, in sicer "type"
  - parameter type je lahko lastnik, sprehajalec ali podjetje
  - metoda vrača JSONObject, ki vsebuje ključ usersNumber, kot vrednost pa število

### 2.2.5 K DogWalkersAPI

#### Metode

- pridobiStatistikoUporabnikov:
  - metoda kot parametre sprejme String type
  - zaloga vrednosti "type" je lastnik, sprehajalec, podjetje
  - vrača JSONObject, ki vsebuje ključ usersNumber in vrednost int
  - metoda glede na podane filtre prefiltrira in poda število uporabnikov, ki ustrezajo filtrom
- pridobiStatistikoOglasov:
  - metoda sprejme 3 parametre tipa String (date, isActive, type)
  - parameter date je v obliki "YYYY-mm-dd", isActive ima vrednost true ali false, type pa sprehajalec ali podjetje
  - vrača JSONObject, ki vsebuje ključ adsNumber in vrednost tipa int
  - metoda glede na podane filtre prefiltrira in poda število oglasov, ki ustrezajo filtrom

### 2.3.6 ZV OpenStreetMapsApi

#### Atributi

- country:
  - tipa String
- city:
  - tipa String
- format:
  - tipa String

#### Metode

- poisciLokacijo:
  - sprejme tri parametre tipa String (country, city, format)
  - vrača JSONArray z JSONObjecti, ki vsebujejo kraje, ki spadajo pod filtre
  - JSONObject ima:
    - place_id : String
    - licence : String
    - osm_type : String
    - osm_id: int
    - boundingbox: array
    - lat : String
    - lon : String
    - display_name : String
    - class : String
    - type : String
    - importance: float
    - icon : String

### 2.3.7 ZM urejanje profila(L)

#### Atributi

- uporabnisko_ime:
  - tipa String
- novo_geslo:
  - tipa String
- lokacija:
  - tipa String
- opis:
  - tipa String
- slika:
  - tipa Image
- filterBlizina:
  - tipa int
- filterOcena:
  - tipa boolean
- id:
  - tipa int

#### Metode

- klikShraniSpremembe:
  - metoda se proži, ko uporabnik klikne na gumb shrani spremembe
  - metoda ne vrača rezultata
  - metoda ne sprejme parametrov
  - metoda proži v kontrolerju shranjevaje sprememb
- klikIzbrisiProfil:
  - metoda se proži, ko uporabnik klikne na gumb izbrisi profil
  - metoda ne vrača rezultata
  - metoda sprejme parameter ID tipa String
  - metoda proži v kontrolerju izbris profila

### 2.3.8 K urejanje profila(L)

#### Metode

- urediProfil:
  - metoda vrača objekt tipa LastnikPsa
  - metoda sprejme v parameter obrazec tipa Form
  - metoda naredi potrebne korake za ureditev profila
- preveriVnesenePodatke:
  - metoda vrača boolean
  - metoda preveri ali so vsi potrebni podatki v obrazcu izpolnjeni ter če so pravilne oblike/tipa
  - metoda sprejme obrazec tipa Form
- shraniSpremembe:
  - metoda ne vrača rezultata
  - metoda ne sprejme parametrov
  - metoda proži shranjevanje sprememb v entiteti
- preveriObstojlokacije:
  - metoda kot parameter sprejme ime kraja tipa String
  - metoda pokliče zunanji API ter preveri, če mu ta ne vrne prazen JSONArray
  - metoda glede na vrnjen rezultat vrne true/false
- preusmeriPrvaStran:
  - metoda ne sprejme parametrov
  - metoda ne vrača rezultata
  - metoda preusmeri na prvo stran (proži init)

### 2.3.9 ZM adminov pregled profila(L)

#### Atributi

- lastnikPsa:
  - tip: LastnikPsa
  - vsebuje informacije glede lastnika psa

#### Metode

- klikOdstraniUporabnika:
  - metoda se sproži ob kliku na gumb odstrani uporabnika
  - metoda sprejme parameter ID tipa String
  - metoda ne vrača rezultata
  - metoda proži metodo odstraniUporabnika v krmilniku
- prikaziPodatkeLastnika:
  - metoda sprejme lastnika psa tipa LastnikPsa
  - metoda izlušči podatke ter napolne zaslonsko masko
  - metoda ne vrača rezultata

### 2.3.10 K adminov pregled profila(L)

#### Metode

- odstraniUporabnika:
  - metoda sprejme parameter ID tipa String
  - metoda ne vrača rezultata
  - metoda proži odstranjevanje lastnikaPsa v entiteti
- pridobiPodatkeLastnika:
  - metoda sprejme ID tipa String
  - metoda pridobi podatke o lastniku psa iz entitete
  - metoda vrača lastnikPsa tipa LastnikPsa

### 2.3.11 ZM prikaz seznama lastnikov psov

#### Atributi

- lastnikiPsov:
  - tip array, ki vsebuje elemente tipa LastnikPsa

#### Metode

- klikPrikazProfila:
  - metoda sprejme ID tipa String
  - metoda sproži proces prikazovanja profila lastnika psa
  - metoda ne vrača rezultata
- klikPrikazSprehajalcev:
  - metoda ne sprejme parametrov
  - metoda ne vrača rezultata
  - metoda preusmeri na zaslonsko masko prikaz sprehajalcev
- klikPrikazPodjetij:
  - metoda ne sprejme parametrov
  - metoda ne vrača rezultata
  - metoda ob kliku na gumb preusmeri na ZM prikaz podjetij

### 2.3.12 K prikaz seznama lastnikov psov

#### Metode

- pridobiSeznamImenInIdjev:
  - metoda iz entity pridobi seznam lastnikov psov tipa array, znotraj pa so elementi tipa LastnikPsa
  - metoda vrača array
  - metoda ne sprejme parametrov

### 2.3.13 ZM podajanje ocene

#### Atributi

- registriran_uporabnik:

  - tipa RegistriranUporabnik
  - uporabnik, ki ga želimo oceniti

- ocena
  - tipa int
  - ocena, ki jo je podal uporabnik
  - zaloga vrednosti od 1 do 5

#### Metode

- klikOceni:
  - metoda se proži, ko uporabnik klikne gumb oceni
  - ne vrača rezultatov
  - kot parameter sprejme oceno
  - proži na kontrolerju ocenjevanje

### 2.3.14 K podajanje ocene

#### Metode

- posodobiOcenoUporabnika:
  - sprejme parameter ID tipa int ter parameter ocene int
  - ne vrača rezultata
  - proži posodabljanje ocene v entiteti
- pridobiIdOcenjevalca:
  - metoda vrača ID tipa int
  - metoda ne sprejme parametrov

### 2.3.15 ZM Registracija

- Zaslonska maska za registracijo uporabnika.

#### Atributi

- e-mail:
  - tipa String
  - e-mail za registracijo

- geslo:
  - tipa String
  - geslo za registracijo

- uporabnisko ime:
  - tipa String
  - uporabnisko ime za registracijo

- vloga:
  - tipa char
  - S-Sprehajalec, L-LastnikPsa

- pogoji:
  - tipa boolean
  - strinjanje s pogoji

#### Metode

- klikGumbPotrdi:
  - ne sprejema parametrov
  - ne vrača rezultata
  - proži ustvarjanje računa

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM


### 2.3.16 ZM Prva Stran

- Prva stran aplikacije.

#### Atributi

- url_prijava:
  - je tipa String
  - link na zaslonsko masko prijava

- url_registracija:
  - je tipa String
  - link na zaslonsko masko registracija

#### Metode

- klikGumbRegistracija:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na registracijo

- klikGumbPrijava:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na prijavo

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.17 ZM Urejanje Profila(S)

- Urejanje profila sprehajalca.

#### Atributi

- uporabnisko_ime:
  - je tipa String
  - spremenjeno uporabnisko ime sprehajalca

- geslo:
  - je tipa String
  - spremenjeno geslo sprehajalca

- opis:
  - je tipa String
  - opis sprehajalca
 
- id:
  - je tipa int
  - id sprehajlca

#### Metode

- klikShraniSpremembe:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži posodobitev uporabniškega profila

- klikIzbrisiProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris profila

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.18 ZM AdminovPregledProfila(S)

- Admin na strani, ki mu omogoča vpogled in spreminjanje profila sprehajalca.

#### Atributi

- sprehajalec:
  - je tipa sprehajalec
  - sprehajalec, katerega si ogleduje admin

- oglasi:
  - je tipa tabela oglasov
  - vsebuje vse oglase, gledanega sprehajalca

#### Metode

- klikOdstraniUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris profila sprehajalca

- klikOdstraniOglas:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris oglasa dotičnega sprehajalca

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

- prikaziSeznamOglasovSprehajalca:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda prikaze oglase sprehajalca

- prikaziPodatkeOSprehajalcu:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda prikaze vse podatke o sprehajalcu

### 2.3.19 ZM PrikazSeznamaSprehajalcev

- Admin lahko pregleda in po potrebi spreminja, kateregakoli sprehajalca.

#### Atributi

- sprehajalci:
  - je tipa tabela sprehajalca
  - vsebuje vse sprehajalca

#### Metode

- pridobiSprehajalce:
  - ne sprejme parametrov
  - vrača rezultat, ki vsebuje vse sprehajalce
  - metoda vrača sprehajalce

- klikPrikaziProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži prikaz profila

- klikPrikazLastnikov:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži prikaz lastnikov

- klikPrikazPodjetij:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži prikaz podjetij

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.20 K PregledProfilaSogovornika(S)

#### Metode

- pridobiIDSprehajalca:
  - ne sprejme parametrov
  - vrača tip int
  - pridobi id sprehajalca

- pridobiOglaseSprehajalca:
  - ne sprejme parametrov
  - vrača tabelo oglasov
  - metoda pridobi vse oglase sprehajalca


### 2.3.21 K PrikazSeznamaSprehajalcev

#### Metode

- pridobiSeznamImenInIdjev:
  - ne sprejme parametrov
  - vrača tabelo sprehajalcev
  - metoda pridobi vse sprehajalce in njihove id-je

### 2.3.22 K AdminovPregledProfila(S)

#### Metode

- odstraniUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris sprehajalca

- odstraniOglas:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris oglasa uporabnika

- pridobiSprehajalca:
  - ne sprejme parametrov
  - vrača dotičnega sprehajalca
  - metoda pridobi dotičnega sprehajalca

- pridobiOglaseSprehajalca:
  - ne sprejme parametrov
  - vrača tabelo oglasov
  - metoda pridobi oglase dotičnega sprehajalca


### 2.3.23 K UrejanjeProfila(S)

#### Metode

- preveriVnesenePodatke:
  - ne sprejme parametrov
  - vrača boolean
  - metoda preveri, če imajo vneseni podatki ustrezno vsebino

- izbrisiPofil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris profila sprehajalca

- urediProfil:
  - ne sprejme parametrov
  - vrača dotičnega sprehajalca
  - metoda proži spreminjanje profila sprehajalca

- preusmeriPrvaStran:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritve na prvo stran aplikacije


### 2.3.24 K Registracija

#### Metode

- preveriVnesenePodatke:
  - ne sprejme parametrov
  - ne vrača boolean
  - metoda preveri, če imajo vneseni podatki ustrezno vsebino

- registrirajUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži registracijo uporabnika

- preusmeriNaPregledSeznamaOglasov:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PregledSeznamaOglasov

- preusmeriNaPregledSvojihAktivnihOglasovP:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PregledSvojihAktivnihOglasovP

- preusmeriNaPregledSvojihAktivnihOglasovS:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PregledSvojihAktivnihOglasovS

### 2.3.25 E Registriran uporabnik

#### Atributi

- id:
  - je tipa int
  - unikaten id, za vsakega uporabnika

- uporabnisko_ime:
  - je tipa String
  - uporabnisko ime za prijavo

- email:
  - je tipa String
  - email uporabnika

- nakljucna_vrednost:
  - je tipa String
  - naključni znaki za vsakega uporabnika dolžina 16 znakov

- zgoscena_vrednost:
  - je tipa String
  - dolžine 64 znakov, generirana s pomočjo naključne vrednosti in dejanskega gesla

- vloga:
  - je tipa char
  - S - Sprehajalec, L - LastnikPsa

- opis:
  - je tipa String
  - vsebuje opis uporabnika

#### Metode

- prijava:
  - ne sprejme parametrov
  - vrača String(JWT)
  - metoda proži prijavo uporabnika, vrne token, s katerim lahko uporabnik interaktira s sistemom

- izbrisRacuna:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži izbris racuna uporabnika

- ustvariRacun:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje racuna uporabnika

- posodobiRacun:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži posodabljanje dotičnega uporabniskega racuna

- preveriAktivnost:
  - ne sprejme parametrov
  - vrača boolean
  - metoda prož preverjanje aktivnosti dotičnega uporabnika

- vrniSteviloUporabikov:
  - ne sprejme parametrov
  - vrača int
  - metoda vrne stevilo registriranih uporabnikov


### 2.3.26 ZM PregledProfila(L)

- Sprehajalec pridobi informacije o lastniku psa.

#### Atributi

- lastnik_psa:
  - je tipa lastnikpsa
  - trenutno ogledovan profil dotičnega lastnika psa

#### Metode

- klikPodajOceno:
  - sprejme parameter int, ki je podana ocena
  - ne vrača rezultata
  - metoda ob kliku proži oddajo ocene uporabniku

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.27 ZM PregledSeznamaOglasov(S)

- Lastnik psa si ogleduje oglase sprehajalcev.

#### Atributi

- oglasi:
  - je tipa tabela oglasov
  - vsebuje vse oglase, namenjene dotičnemu lastniku psa

- trenutniOglas:
  - je tipa oglas
  - oglas, ki si ga trenutno ogleduje lastnik psa

- lastnik:
  - je tipa lastnikpsa
  - informacije o uporabniku, kateri pregleduje to stran

#### Metode

- klikZavrni:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži umik trenutnega oglasa in pregled naslednjega

- klikSprejmi:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži sprejem oglasa in prikaže naslednji oglas

- klikNaProfilOglasevalca:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na profil oglasevalca

- klikPrijaviUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PrijavoNeprimerneVsebine

- klikPogovor:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PrikazSeznamaPogovorov

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.28 ZV MailToVmesnik

- Pripravi mail za prijavo uporabnika.

#### Atributi

- prejemnik:
  - je tipa String
  - prejemnik tega mail-a, ki ga uporabnik spiše za prijavo

- zadeva:
  - je tipa String
  - zadeva problema, domena prijave

- instance:
  - je tipa mailToVmesnik
  - instance MailToVmesnika

#### Metode

- pripraviMail:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži odprje odjemalca mailov z novim mailom in vstavljenim prejemnikom

- getInstance:
  - ne sprejme paramtrov
  - vrne instanco mailToVmesnik
  - vrne instanco

### 2.3.29 ZM PregledSeznamaOglasov(P)

- Lastnik psa si ogleduje oglase podjetij.

#### Atributi

- oglasi:
  - je tipa tabela oglasov
  - vsebuje vse oglase, namenjene dotičnemu lastniku psa

- trenutniOglas:
  - je tipa oglas
  - oglas, ki si ga trenutno ogleduje lastnik psa

- lastnik:
  - je tipa lastnikpsa
  - informacije o uporabniku, kateri pregleduje to stran

#### Metode

- klikZavrni:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži umik trenutnega oglasa in pregled naslednjega

- klikSprejmi:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži sprejem oglasa in prikaže naslednji oglas

- klikPrijaviUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PrijavoNeprimerneVsebine

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.30 ZM PrikazSeznamaPogovorov

- Uporabnik lahko vidi vse svoje pogovore in pošilja sporočila.

#### Atributi

- prikazaniPogovor:
  - je tipa pogovor
  - vse informacije o pogovoru, ki je trenutno odprt

- seznamiPogovorov:
  - je tipa tabela pogovorov
  - vsebuje vse pogovore, dotičnega uporabnika

#### Metode

- posljiSporocilo:
  - sprejme parameter tipa String(vsebina sporočila)
  - ne vrača rezultata
  - metoda proži pošiljanje sporočila sogovorniku

- izberiPogovor:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži pregled izbranega pogovora

- klikPrikaziDodatenMeni:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na RazsiritevPogovora

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

### 2.3.31 ZM RazsiritevPogovora

- Razsiri PrikazSeznamaPogovorov z dodatnimi moznosti.

#### Atributi

- pogovor:
  - je tipa pogovor
  - vsebuje informacije o trenutnem odprtem pogovoru

#### Metode

- preusmeriNaProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeri na profil sogovornika

- klikPodajOceno:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PodajanjeOcene, kjer lahko uporabnik oceni sogovorca

- klikPrijaviUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PrijavoNeprimerneVsebine

- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM

- klikGenerirajSifro:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda generira šest mestno naključno zaporedje znakov in jo poda v pogovor

### 2.3.32 K PrikazSeznamaPogovorov

#### Metode

- vrniPogovor:
  - sprejme parameter ID pogovora
  - vrača pogovor
  - metoda vrne željen pogovor

- vrniSeznamPogovorov:
  - ne sprejme parametrov
  - vrača tabelo pogovorov
  - metoda vrne vse pogovore dotičnega uporabnika

- dodajNovoSporocilo:
  - sprejme parameter String(vsebina sporočila), ID(sogovorca)
  - ne vrača rezultata
  - metoda pošlje sporočilo sogovorcu

- prijaviUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PrijavoNeprimerneVsebine

- generirajSifro:
  - ne sprejme parametrov
  - vrača šest mestno naključno zaporedje znakov
  - metoda generira šest mestno naključno zaporedje znakov in jo poda v pogovor

- preusmeriPregledProfilaSogovornikaS:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PregledProfilaSogovornikaS

- preusmeriPregledProfilaSogovornikaL:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PregledProfilaSogovornikaL

- vrniZadnjiPogovorInSeznamImenSogovorcev:
  - ne sprejme parametrov
  - vrača JSONObject
  - metoda informacije o zadnjem pogovoru in imenih sogovorcev

### 2.3.33 K PregledSeznamaOglasov

#### Metode

- prijavaUporabnika:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PrijavoNeprimerneVsebine

- preusmeriNaPogovor:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na PrikazSeznamaPogovorov in po potrebi ustvari nov pogovor

- filtrirajPoOceni:
  - ne sprejme parametrov
  - vrača tabelo oglasov
  - metoda filtrira vse oglase po njihovi oceni in vrne oglase v tem vrstnem redu

- filtrirajPoOddaljenosti:
  - ne sprejme parametrov
  - vrača tabelo oglasov
  - metoda filtrira po oddaljenosti in vrne oglase v tem vrstnem redu

- pridobiKoordinate:
  - sprejema parameter tabela oglasov
  - vrača JSONArray
  - metoda gre čez vse aktivne oglase in za vsakega kliče poišči lokacijo na openstreetmapu, ki mu vrne koordinate

- vrniFiltriranSeznamOglasov:
  - ne sprejme parametrov
  - vrača tabelo oglasov
  - metoda vrne filtrirano tabelo oglasov po vrsti

- preusmeriNaProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda preusmeri na profil uporabnika

- sprejmiSprehajalca:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži sprejem oglasa sprehajalca in prikaže naslednji oglas

- sprejmiPodjetje:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži sprejem oglasa podjetja in prikaže naslednji oglas

### 2.3.34 K PregledProfilaSogovornika(L)

#### Metode

- pridobiLastnikaPsa:
  - ne sprejme parametrov
  - vrača lastnika psa
  - metoda pridobi lastnikapsa

### 2.3.35 E LastnikPsa

#### Atributi

- lokacija:
  - je tipa String
  - vsebuje lokacijo lastnika psa

- ocena:
  - je tipa int
  - ocena lastnika psa

- filterPoOceni:
  - je tipa boolean
  - preferenca lastnika psa, ali se filtrira ali ne

- filterPoOddaljenosti:
  - je tipa int
  - do koliko razdalje se oglasi za lastnika psa še prikazujejo

- slika:
  - je tipa StringBase64
  - slika od lastnika psa

#### Metode

- urediProfil:
  - sprejme parameter obrazec tipa form
  - vrača lastnikpsa
  - metoda spremeni profil lastnika psa

- nastaviFiltrirajOglasePoOceni:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda spremeni nastavitve lastnika psa

- nastaviFiltrirajOglasePoOddaljenosti:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda spremeni nastavitve lastnika psa

- podatkiLastnika:
  - ne sprejme parametrov
  - vrača lastnikpsa
  - metoda pridobi informacije o lastniku

- vrniSeznamLastnikovPsov:
  - ne sprejme parametrov
  - vrača tabelo lastnikpsa
  - metoda pridobi vse lastnike psov

- posodobiOceno:
  - ne sprejme parametrov
  - vrača int
  - metoda posodobi oceno in vrne posodobljeno oceno

### 2.3.36 E Pogovor

#### Atributi

- id:
  - je tipa String
  - id pogovora

- uporabnik1_id:
  - je tipa int
  - id prvega uporabnika

- uporabnik2_id:
  - je tipa int
  - id drugega uporabnika

- seznamSporocil:
  - je tipa tabela sporocil
  - vsa sporocila v pogovoru

#### Metode

- vrniSporocilaPogovora:
  - ne sprejme parametrov
  - vrača tabelo sporočil
  - metoda pridobi vse sporočila

- vrniSteviloSporocil:
  - ne sprejme parametrov
  - vrača int
  - metoda pridobi število sporočil v pogovoru

- dodajPogovor:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda ustvari nov pogovor

- dodajSporociloVPogovor:
  - ne sprejme parametrov
  - vrača sporočilo
  - metoda doda sporocilo v pogovor in ga vrne

- vrniPogovore:
  - ne sprejme parametrov
  - vrača tabelo pogovorov
  - metoda vrne vse pogovore

### 2.3.37 E Sporocilo

#### Atributi

- id:
  - je tipa String
  - unikaten id sporocila

- avtor_id:
  - je tipa int
  - id avtorja sporocila

- vsebinaSporocila:
  - je tipa String
  - vsebuja vsebino sporočila

### 2.3.38 K ustvarjanje novega oglasa(s)

#### Metode

- objaviOglas()
	- sprejme parameter oglas tipa Form
	- ne vrača rezultata
	- metoda proži dodajanje novega oglasa za prijavljenega sprehajalca
- preveriPrekrivanjeDatumov()
	- sprejme dva paremetra date1 in date2 tipa Date
	- vrača rezultat tipa boolean
	- metoda preveri, da se datuma ne prekrivata in da date1 < date2
- preveriObstojLokacije()
	- sprejme parameter lokacija tipa String
	- vrača rezultat tipa boolean
	- metoda proži poizvedbo poisciLokacijo() na openStreetMapsApi
- preveriPraznoVnosnoPolje()
	- sprejme parameter oglas tipa Form
	- vrača rezultat tipa boolean
	- metoda preveri, da ni nobeno polje prazno
- preusmeriPregledSvojihAktivnihOglasovS()
	- ne sprejme parametrov
	- metoda proži init v ZM Pregled svojih aktivinih oglasov S
	- metoda ne vrača rezultata


### 2.3.39 K ustvarjanje novega oglasa(p)

#### Metode

- objaviOglas()
	- sprejme parameter oglas tipa Form
	- ne vrača rezultata
	- metoda proži dodajanje novega oglasa za prijavljeno podjetje
- preveriObstojLokacije()
	- sprejme parameter lokacija tipa String
	- vrača rezultat tipa boolean
	- metoda proži poizvedbo poisciLokacijo() na openStreetMapsApi
- preveriPraznoVnosnoPolje()
	- sprejme parameter oglas tipa Form
	- vrača rezultat tipa boolean
	- metoda preveri, da ni nobeno polje prazno
- preusmeriPregledSvojihAktivnihOglasovP()
	- ne sprejme parametrov
	- metoda proži init v ZM Pregled svojih aktivinih oglasov P
	- metoda ne vrača rezultata
  
### 2.3.40 K urejanje aktivnega oglasa(s)

#### Metode

- shraniSpremembe()
	- sprejme parameter oglas tipa Form
	- ne vrača rezultata
	- metoda proži posodabljanje aktivnega oglasa za prijavljenega sprehajalca
- izbrisiOglas()
	- sprejme parameter ID tipa String
	- ne vrača rezultata
	- metoda proži izbris oglasa sprehajalca
- preveriPrekrivanjeDatumov()
	- sprejme dva paremetra date1 in date2 tipa Date
	- vrača rezultat tipa boolean
	- metoda preveri, da se datuma ne prekrivata in da date1 < date2
- preveriObstojLokacije()
	- sprejme parameter lokacija tipa String
	- vrača rezultat tipa boolean
	- metoda proži poizvedbo poisciLokacijo() na openStreetMapsApi
- preusmeriPregledAktivnihOglasovS()
	- ne sprejme parametrov
	- metoda proži init v ZM Pregled svojih aktivinih oglasov S
	- metoda ne vrača rezultata
- preveriPraznoVnosnoPolje()
	- sprejme parameter oglas tipa Form
	- vrača rezultat tipa boolean
	- metoda preveri, da ni nobeno polje prazno
  
### 2.3.41 K urejanje profila(P)

#### Metode

- preveriVnesenePodatke()
	- ne sprejme parametrov
	- vrača boolean
	- metoda preveri, če imajo vneseni podatki ustrezno vsebino
- izbrisiProfil()
	- sprejme parameter ID tipa String
	- ne vrača rezultata
	- metoda proži izbris profila podjetja
- urediProfil()
	- ne sprejme parametrov
	- vrača dotičnega podjetja
	- metoda proži spreminjanje profila podjetja
- preusmeriPrvaStran()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži preusmeritve na prvo stran aplikacije

### 2.3.42 K prikaz seznama podjetij

#### Metode

- pridobiSeznamImenInIdejv
	- metoda ne sprejme parametrov
	- metoda vrača array
	- metoda iz entity pridobi seznam sprehajalcev tipa array, znotraj pa so elementi tipa Sprehajalec
  

### 2.3.43 ZM pregled profila sogovornika(s)

#### Atributi

- sprehajalec
	- je tipa Sprehajalec
	- je sprehajalec, katerega profil si ogleduje lastnik psa
- oglasi
	- je tipa Oglas[]
	- je array vseh oglasov sprehajalca tipa Oglas, katerega profil si ogleduje lastnik psa

#### Metode

- klikPodajOceno()
	- metoda se proži, ko sprehajalec klikne na gumb podaj oceno
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda se proži ko uporabnik klikne na gumb podaj oceno
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM podajanje ocene  
  
### 2.3.44 ZM ustvarjanje novega oglasa(s)

#### Atributi

- lokacija
	- je tipa String
	- je text iz vnosnega polja Lokacija
- zacetni_cas
	- je tipa String
	- je text iz vnosnega polja Začetek
- koncni_cas
	- je tipa String
	- je text iz vnosnega polja Konec
- opis_sprehoda
	- je tipa String
	- je text iz vnosnega polja Opis sprehoda
- slika
	- je tipa ByteArray
	- je naložena slika iz vnosnega polja Naloži sliko

#### Metode

- klikObjaviOglas()
	- metoda se proži, ko sprehajalec klikne na gumb objavi oglas
	- sprejme parameter oglas tipa Form
	- ne vrača rezultatov
	- na kontrolerju proži objavljanje oglasa za sprehajalca
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM
	
### 2.3.45 ZM ustvarjanje novega oglasa(p)

#### Atributi

- lokacija
	- je tipa String
	- je text iz vnosnega polja Lokacija
- kontakt
	- je tipa String
	- je text iz vnosnega polja Kontakt
- opis_storitve
	- je tipa String
	- je text iz vnosnega polja Opis storitve
- slika
	- je tipa ByteArray
	- je naložena slika iz vnosnega polja Naloži sliko

#### Metode

- klikObjaviOglas()
	- metoda se proži, ko podjetje klikne na gumb objavi oglas
	- sprejme parameter oglas tipa Form
	- ne vrača rezultatov
	- na kontrolerju proži objavljanje oglasa za podjetje
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM
  
### 2.3.46 ZM urejanje aktivnega oglasa(p)

#### Atributi

- lokacija
	- je tipa String
	- je text iz vnosnega polja Lokacija
- kontakt
	- je tipa String
	- je text iz vnosnega polja Kontakt
- opis_storitve
	- je tipa String
	- je text iz vnosnega polja Opis storitve
- slika
	- je tipa ByteArray
	- je naložena slika iz vnosnega polja Naloži sliko

#### Metode

- klikIzbrisiOglas()
	- metoda se proži, ko podjetje klikne na gumb izbrisi oglas
	- sprejme parameter ID tipa String
	- ne vrača rezultatov
	- na kontrolerju proži brisanje oglasa za podjetje
- klikShraniSpremembe()
	- metoda se proži, ko podjetje klikne na gumb shrani spremembe
	- sprejme parameter oglas tipa Form
	- ne vrača rezultatov
	- na kontrolerju proži posodabljanje oglasa za podjetje
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM
  
### 2.3.47 ZM urejanje aktivnega oglasa(s)

#### Atributi

- lokacija
	- je tipa String
	- je text iz vnosnega polja Lokacija
- zacetni_cas
	- je tipa String
	- je text iz vnosnega polja Začetek
- koncni_cas
	- je tipa String
	- je text iz vnosnega polja Konec
- opis_sprehoda
	- je tipa String
	- je text iz vnosnega polja Opis sprehoda
- slika
	- je tipa ByteArray
	- je naložena slika iz vnosnega polja Naloži sliko

#### Metode

- klikIzbrisiOglas()
	- metoda se proži, ko sprehajalec klikne na gumb izbrisi oglas
	- sprejme parameter ID tipa String
	- ne vrača rezultatov
	- na kontrolerju proži brisanje oglasa za sprehajalca
- klikShraniSpremembe()
	- metoda se proži, ko sprehajalec klikne na gumb shrani spremembe
	- sprejme parameter oglas tipa Form
	- ne vrača rezultatov
	- na kontrolerju proži posodabljanje oglasa za sprehajalca
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM
  
### 2.3.48 ZM urejanje profila(P)

#### Atributi

- uporabnisko_ime
	- je tipa String
	- premenjeno uporabnisko ime podjetja
- novo_geslo
	- je tipa String
	- spremenjeno geslo podjetja
- url_spletne_strani
	- je tipa String
	- spremenjen spletni naslov podjetja
- opis
	- je tipa String
	- spremenjen opis podjetja
- id
	- je tipa int
	- je id podjetja

#### Metode

- klikShraniSpremembe()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži posodobitev uporabniškega profila
- klikIzbrisiProfil()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži izbris profila
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM
  
### 2.3.49 ZM prikaz seznama podjetij

#### Atributi

- podjetja
	- je tipa Podjetje[]
	- je array vseh objektov tipa Podjetje

#### Metode

- pridobiPodjetja()
	- ne sprejme parametrov
	- vrača seznam, ki vsebuje vsa podjetja
	- metoda vrača sprehajalce
- klikPrikaziProfil()
	- sprejme parameter ID tipa String
	- ne vrača rezultata
	- metoda proži prikaz profila na kontrolerju
- klikPrikazLastnikov()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži prikaz lastnikov
- klikPrikazSprehajalcev()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži prikaz sprehajalcev
- init()
	- ne sprejme parametrov
	- ne vrača rezultata
	- metoda proži ustvarjanje ZM

### 2.3.50 E Sprehajalec

#### Atributi

- slika:
  - String Base64,

- ocena:
  - tipa int
  - zaloga vrednosti od 1 do 5

#### Metode

- urediProfil:
  - vrača sprehajalca
  - metoda proži spreminjanje profila sprehajalca
- vrniSeznamSprehajalcev:
  - vrača array
  - metoda vrne seznam sprehajalcev
- vrniSprehajalca:
  - vrača sprehajalca
  - metoda vrne sprehajalca
- posodobiOceno:
  - vrača int
  - posodobi oceno



### 2.3.51 E Oglas

#### Atributi

- id:
  - tipa String
- id_avtor:
  - tipa int
- vloga_avtorja:
  - tipa char
- lokacija:
  - tipa String
  - kraj, kjer se oglas nahaja
- zacetni_cas:
  - tipa java.util.Date
- koncni_cas:
  - tipa java.util.Date
- opis:
  - tipa String

#### Metode

- vrniOglase:
  - vrača array oglasov
- vrniOglaseSprehajalca:
  - vrača array oglasov sprehajalca
- vrniOglasePodjetja:
  - vrača array oglasov podjetja
- vrniSteviloOglasov:
  - vrača število vseh oglasov
- urediOglas:
  - vrača oglas
  - metoda spremeni oglas
  - sprejema parameter obrazec tipa Form
- ustvariOglas:
  - vrača oglas
  - metoda ustvari nov oglas
  - sprejema parameter obrazec tipa Form
- preveriAktivnost:
  - preveri, če je oglas v podatkovni bazi
  - sprejema ID parameter
- izbrisiOglas:
  - izbriše oglas
  - ne vrača rezultata
  - sprejema ID parameter
- vrniVseAktivneOglase:
  - vrača array vseh aktivnih oglasov


### 2.3.52 E Podjetje

#### Atributi

- url_spletne_strani:
  - String
- kontaktni_podatki:
  - String

#### Metode

- urediProfil:
  - vrača podjetje
  - metoda spremeni profil podjetja
  - sprejme parameter obrazec tipa Form
- vrniSeznamPodjetij:
  - vrača array podjetij
- pridobiPodjetje:
  - vrne podjetje podano v parametrih

### 2.3.53 K pregled svojih aktivnih oglasov(s)

#### Metode

- pridobiOglaseSprehajalca:
  - vrača array oglasov
  - metoda proži poizvedbo vrniOglaseSprehajalca()
- izbrisiOglas:
  - sprejme parameter ID tipa String
  - ne vrača rezultata
  - metoda proži poizvedbo izbrisiOglas()
- preusmeriUstvarjanjeNovegaOglasaS:
  - ne sprejme parametrov
  - metoda proži init v ZM ustvarjanje novega oglasa(s)
  - metoda ne vrača rezultata
- preusmeriUrejanjeAktivnegaOglasaS:
  - ne sprejme parametrov
  - metoda proži init v ZM urejanje aktivnega oglasa(s)
  - metoda ne vrača rezultata
- preusmeriNaPogovor:
  - ne sprejme parametrov
  - metoda proži init v ZM prikaz seznama pogovorov
  - metoda ne vrača rezultata

### 2.3.54 K pregled svojih aktivnih oglasov(p)

#### Metode

- pridobiOglasePodjetja:
  - vrača array oglasov
  - metoda proži poizvedbo vrniOglasePodjetja()
- izbrisiOglas:
  - sprejme parameter ID tipa String
  - ne vrača rezultata
  - metoda proži poizvedbo izbrisiOglas()
- preusmeriUstvarjanjeNovegaOglasaP:
  - ne sprejme parametrov
  - metoda proži init v ZM ustvarjanje novega oglasa(p)
  - metoda ne vrača rezultata
- preusmeriUrejanjeAktivnegaOglasaP:
  - ne sprejme parametrov
  - metoda proži init v ZM urejanje aktivnega oglasa(p)
  - metoda ne vrača rezultata


### 2.3.55 K urejanje aktivnega oglasa(p)

#### Metode

- shraniSpremembe:
  - sprejme parameter oglas tipa Form
  - ne vrača rezultata
  - metoda proži posodabljanje aktivnega oglasa za prijavljeno podjetje
- izbrisiOglas:
  - sprejme parameter ID tipa String
  - ne vrača rezultata
  - metoda proži poizvedbo izbrisiOglas()
- preusmeriPregledSvojihAktivnihOglasovP:
  - ne sprejme parametrov
  - metoda proži init v ZM Pregled svojih aktivinih oglasov P
  - metoda ne vrača rezultata
- preveriPraznoVnosnoPolje:
  - sprejme parameter oglas tipa Form
  - vrača rezultat tipa boolean
  - metoda preveri, da ni nobeno polje prazno
- preveriObstojLokacije()
  - sprejme parameter lokacija tipa String
  - vrača rezultat tipa boolean
  - metoda proži poizvedbo poisciLokacijo() na openStreetMapsApi


### 2.3.56 K adminov pregled profila(p)

#### Metode

- odstraniOglas:
  - sprejme parameter ID tipa String
  - ne vrača rezultata
  - metoda proži poizvedbo izbrisiOglas()
- odstraniUporabnika:
  - sprejme parameter ID tipa int
  - ne vrača rezultata
  - metoda proži poizvedbo izbrisiOglas()
- pridobiPodjetje:
  - vrača podjetje
  - metoda proži poizvedbo pridobiPodjetje()
  - sprejme parameter ID tipa int
- pridobiOglasePodjetja:
  - vrača array oglasov
  - metoda proži poizvedbo vrniOglasePodjetja()

### 2.3.57 ZM pregled svojih aktivnih oglasov(s)

#### Atributi

- oglasi:
  - tipa tabela oglasov
  - vsebuje vse oglase prijavljenega sprehajalca

#### Metode

- klikNovOglas:
  - metoda se proži, ko podjetje klikne na gumb nov oglas
  - ne vrača rezultatov
  - na kontrolerju proži ustvarjanje oglasa za sprehajalca
- klikUrediOglas:
  - metoda se proži, ko podjetje klikne na gumb nov oglas
  - sprejme parameter ID tipa String
  - ne vrača rezultatov
  - na kontrolerju proži urejanje oglasa za sprehajalca
- klikIzbrisiOglas:
  - metoda se proži, ko podjetje klikne na gumb izbrisi oglas
  - sprejme parameter ID tipa String
  - ne vrača rezultatov
  - na kontrolerju proži brisanje oglasa za sprehajalca
- klikPogovori:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na PrikazSeznamaPogovorov
- klikMojProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na pregled profila
- pridobiSvojeOglase:
  - vrača array oglasov
  - ne sprejme parametrov
  - metoda proži pridobiOglaseSprehajalca() na kontrolerju
- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM
- osveziSeznam:
  - vrača array oglasov
  - ne sprejme parametrov
  - metoda proži pridobiOglaseSprehajalca() na kontrolerju ter init()

### 2.3.58 ZM pregled aktivnih oglasov(p)

#### Atributi

- oglasi:
  - tipa tabela oglasov
  - vsebuje vse oglase prijavljenega podjetja

#### Metode

- klikNovOglas:
  - metoda se proži, ko podjetje klikne na gumb nov oglas
  - ne vrača rezultatov
  - na kontrolerju proži ustvarjanje oglasa za podjetje
- klikUrediOglas:
  - metoda se proži, ko podjetje klikne na gumb nov oglas
  - sprejme parameter ID tipa String
  - ne vrača rezultatov
  - na kontrolerju proži urejanje oglasa za podjetje
- klikIzbrisiOglas:
  - metoda se proži, ko podjetje klikne na gumb izbrisi oglas
  - sprejme parameter ID tipa String
  - ne vrača rezultatov
  - na kontrolerju proži brisanje oglasa za podjetje
- klikMojProfil:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži preusmeritev na pregled profila
- pridobiSvojeOglase:
  - vrača array oglasov
  - ne sprejme parametrov
  - metoda proži pridobiOglasePodjetja() na kontrolerju
- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM
- osveziSeznam:
  - vrača array oglasov
  - ne sprejme parametrov
  - metoda proži pridobiOglasePodjetja() na kontrolerju ter init()

### 2.3.59 ZM adminov pregled profila(p)

#### Atributi

- podjetje:
  - tipa podjetje
- oglasi: 
  - tipa tabela oglasov
  - vsebuje vse oglase prijavljenega podjetja

#### Metode

- klikOdstraniOglas:
  - metoda se proži, ko admin klikne na gumb izbrisi oglas
  - sprejme parameter ID tipa String
  - ne vrača rezultatov
  - na kontrolerju proži brisanje oglasa za podjetje
- klikOdstraniUporabnika:
  - metoda se sproži ob kliku na gumb odstrani uporabnika
  - metoda sprejme parameter ID tipa String
  - metoda ne vrača rezultata
  - metoda proži metodo odstraniUporabnika v krmilniku
- init:
  - ne sprejme parametrov
  - ne vrača rezultata
  - metoda proži ustvarjanje ZM
- prikaziPodatkePodjetja:
  - metoda sprejme parameter ID tipa String
  - metoda ne vrača rezultata
  - metoda proži metodo pridobiPodjetje v krmilniku
- prikaziSeznamOglasovPodjetja:
  - metoda sprejme parameter ID tipa String
  - metoda ne vrača rezultata
  - metoda proži metodo pridobiOglasePodjetja v krmilniku

## 3. Načrt obnašanja

### 3.1 Registracija

#### 3.1.1 Registracija - osnovni tok
Diagram zaporedja funkcionalsti "Registracija". Glede na vlogo, ki jo uporabnik izbere se razlikuje stran, na katero ga sistem po uspešni registraciji preusmeri.
![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Registracija-osnovni-tok.png)

### 3.2 Prijava

#### 3.2.1 Prijava - osnovni tok 1
Diagram zaporedja funkcionalnosti "Prijava". Glede na vlogo, pod katero je uporabnik prijavljen se razlikuje stran, na katero ga sistem po uspešni prijavi preusmeri.
![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prijava-osnovni-tok-1.png)

#### 3.2.2 Prijava - osnovni tok 2
Diagram zaporedja funkcionalnosti "Prijava" ko je uporabnik tipa Administrator.
![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prijava-osnovni-tok-2.png)

#### 3.2.3 Prijava - izjemni tok 1, 2
Diagram prikazuje možne izjemne toke, ki se zgodijo ob prijavi.
![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prijava-izjemni-tok-1-2.png)

### 3.3 Prikaz seznama lastnikov psov

#### 3.3.1 Prikaz seznama lastnikov psov - osnovni tok
Diagram zaporedja funkcionalnosti "Prikaz seznama lastnikov psov". Prikazani so še kliki na druge gumbe, ki se potem nadaljujejo v drugih diagramih zaporedja.

![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prikaz-seznama-lastnikov-psov-osnovni-tok.png)

### 3.4 Prikaz seznama sprehajalcev

#### 3.4.1 Prikaz seznama sprehajalcev - osnovni tok
Diagram zaporedja funkcionalnosti "Prikaz seznama sprehajalcev". Prikazani so še kliki na druge gumbe, ki se potem nadaljujejo v drugih diagramih zaporedja.


![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prikaz-seznama-sprehajalcev-osnovni-tok.png)

### 3.5 Prikaz seznama podjetij

#### 3.5.1 Prikaz seznama podjetij - osnovni tok
Diagram zaporedja funkcionalnosti "Prikaz seznama podjetij". Prikazani so še kliki na druge gumbe, ki se potem nadaljujejo v drugih diagramih zaporedja.


![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prikaz-seznama-podjetij-osnovni-tok.png)

### 3.6 Administratorjev pregled profila
Diagrami zaporedja funkcionalnosti "Administratorjev pregled profila". Osnovni toki se razlikujejo v začetni lokaciji administratorja.
#### 3.6.1 Administratorjev pregled profila - osnovni tok 1

![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Administratorjev-pregled-profila-osnovni-tok-1.png)

#### 3.6.2 Administratorjev pregled profila - osnovni tok 2

![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Administratorjev-pregled-profila-osnovni-tok-2.png)

#### 3.6.3 Administratorjev pregled profila - osnovni tok 3

![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Administratorjev-pregled-profila-osnovni-tok-3.png)

### 3.7 Brisanje oglasa

#### 3.7.1 Brisanje oglasa - osnovni tok
Diagram  zaporedja funkcionalnosti "Brisanje oglasa" na katerem je označen še izjemni tok dogodka. Ta se zgodi če je oglas bil že izbrisan.


![diagram zaporedja Registracija osnovni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Brisanje-oglasa-osnovni-tok.png)

### 3.8 Urejanje profila
Diagrami zaporedja funkcionalnosti "Urejanje profila". Osnovna tokova se razlikujeta v vlogi uporabnika, ki želi urejati profil. Na diagramih so prikazani še izjemni tokovi in extendi te funkcionalnosti.
#### 3.8.1 Urejanje profila - osnovni tok 1

![diagram zaporedja Urejanje profila osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/urejanjeProfilaOsnovni1.png)

#### 3.8.2 Urejanje profila - osnovni tok 2

![diagram zaporedja Urejanje profila osnovni tok 2](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/urejanjeProfilaOsnovni2(S).png>)
![diagram zaporedja Urejanje profila osnovni tok 2](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/urejanjeProfilaOsnovni2(P).png>)

### 3.9 Brisanje profila

#### 3.9.1 Brisanje profila - osnovni tok 1
Diagrami zaporedja funkcionalnosti "Brisanje profila", ki se razlikujejo v uporabniški vlogi akterja (Lastnik psa, Sprehajalec ali Podjetje).


![diagram zaporedja Brisanje profila osnovni tok 1](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/brisanjeProfilaOsnovni1(L).png>)
![diagram zaporedja Brisanje profila osnovni tok 1](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/brisanjeProfilaOsnovni1(P).png>)
![diagram zaporedja Brisanje profila osnovni tok 1](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/brisanjeProfilaOsnovni1(S).png>)

#### 3.9.1 Brisanje profila - osnovni tok 2


Diagram zaporedja funkcionalnist "Brisanje profila" v osnovnem toku 2, kjer je akter Administrator. Označen je tudi izjemni tok te funkcionalnosti.


![diagram zaporedja Brisanje profila osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/brisanjeProfilaOsnovni2.png)

### 3.10 Pregled seznama oglasov in Pregled izbranega oglasa
Diagram zaporedja funkcionalnist "Pregled seznama oglasov" in "Pregled izbranega oglasa", ki je included v tej funkcionalnosti. Na diagramu je označen alternativni tok glede na filtriranje, ki ga ima Lastnik psa izbranega. Poleg tega je označen še izjemni tok, ki se proži ko ni novih oglasov, in vsi extendi te funkcionalnosti.
#### 3.10.1 Pregled seznama oglasov - osnovni tok

![diagram zaporedja Pregled seznama oglasov](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/pregSeznamaOglasov.png)

### 3.12 Zavrni ponudbo
Diagram zaporedja funkcionlnosti "Zavrni ponudbo", ki samo na zaslonski maski vrne naslednji oglas iz seznama.
#### 3.12.1 Zavrni ponudbo - osnovni tok

![diagram zaporedja Zavrni ponudbo](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/zavrniPonudboOsnovni.png)

### 3.13 Sprejmi ponudbo

#### 3.13.1 Sprejmi ponudbo - osnovni tok 1
Diagram zaporedja funkcionalnosti "Sprejmi ponudbo", ko je lastnik psa sprejel ponudbo Sprehajalca. Označena sta tudi izjemna tokova.
![diagram zaporedja Sprejmi ponudbo - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/sprejmiPonudboOsnovni1.png)

#### 3.13.2 Sprejmi ponudbo - osnovni tok 2
Diagram zaporedja funkcionalnosti "Sprejmi ponudbo", ko je lastnik psa sprejel ponudbo Podjetja. Označena sta tudi izjemna tokova.
![diagram zaporedja Sprejmi ponudbo - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/sprejmiPonudboOsnovni2.png)

### 3.15 Prijava neprimerne vsebine
Diagrami zaporedja funkcionalnosti "Prijava neprimerne vsebine". Osnovna tokova se razlikujeta v akterju, ki jih uporablja, alternativni tok pa ima drugačno pot funkcionalnosti.
#### 3.15.1 Prijava neprimerne vsebine - osnovni tok 1

![diagram zaporedja Prijava neprimerne vsebine - osnovni tok 1 in alternativni tok](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/prijavaNeprimerneVsebineOsnovni1.png)

#### 3.15.2 Prijava neprimerne vsebine - osnovni tok 2

![diagram zaporedja Prijava neprimerne vsebine - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/prijavaNeprimerneVsebineOsnovni2.png)

#### 3.15.3 Prijava neprimerne vsebine - alternativni tok

![diagram zaporedja Prijava neprimerne vsebine - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/prijavaNeprimerneVsebineAlt.png)

### 3.16 Pregled profila sogovornika

#### 3.16.1 Pregled profila sogovornika - osnovni tok
Diagram zaporedja funkcionalnosti "Pregled profila sogovornika" ko je akter Lastnik psa z označenimi alternativnimi in izjemnimi tokovi.
![diagram zaporedja Pregled profila sogovornika](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Pregled%20profila%20sogovornika(L)%20-%20osnovni%20tok.png>)
Diagram zaporedja funkcionalnosti "Pregled profila sogovornika" ko je akter Sprehajalec.
![diagram zaporedja Pregled profila sogovornika S](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Pregled%20profila%20sogovornika(S)%20-%20osnovni%20tok.png>)

### 3.17 Filtriranje seznama oglasov po oceni

#### 3.17.1 Filtriranje seznama oglasov po oceni - osnovni tok

![diagram zaporedja Filtriranje seznama oglasov po oceni](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Filtriranje%20seznama%20oglasov%20po%20oceni.png)

### 3.18 Filtriranje seznama oglasov po oddaljenosti

#### 3.18.1 Filtriranje seznama oglasov po oddaljenosti - osnovni tok

![diagram zaporedja Filtriranje seznama oglasov po oddaljenosti](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Filtriranje%20seznama%20oglasov%20po%20razdaljii.png)

### 3.19 Prikaz seznama pogovorov

#### 3.19.1 Prikaz seznama pogovorov - osnovni tok
Diagram zaporedja funkcionalnosti "Prikaz seznama pogovorov", ki se razlikujeta v akterjih, ki jih uporabljata.
![diagram zaporedja Prikaz seznama pogovorov L](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prikaz%20seznama%20pogovorov(L)%20-%20osnovni%20tok.png>)
![diagram zaporedja Prikaz seznama pogovorov S](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Prikaz%20seznama%20pogovorov(S)%20-%20osnovni%20tok.png>)

### 3.20 Pogovor med lastnikom psa in sprehajalcem

#### 3.20.1 Pogovor med lastnikom psa in sprehajalcem - osnovni tok
Diagram zaporedja funkcionalnosti "Pogovor med lastnikom psa in sprehajalcem", ki se razlikujeta v akterjih, ki jih uporabljata.
![diagram zaporedja Pogovor med lastnikom psa in sprehajalcem L](<https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Pogovor%20med%20lastnikom%20psa%20in%20sprehajalcem(L)%20-%20osnovni%20tok.png>)
![diagram zaporedja Pogovor med lastnikom psa in sprehajalcem S](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/Pogovor%20med%20lastnikom%20psa%20in%20sprehajalcem%20-%20osnovni%20tok.png)

### 3.21 Podajanje ocene

#### 3.21.1 Podajanje ocene - osnovni tok 1, alternativni tok 1
Diagram zaporedja funkcionalnosti "Podajanje ocene", ko je uporabnik Lastnik psa z označenim osnovnim in alternativnim tokom.
![diagram zaporedja Podajanje ocene - osnovni tok 1, alternativni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/PodajanjeOceneOsAltTok1.png)

#### 3.21.2 Podajanje ocene - osnovni tok 2, alternativni tok 2
Diagram zaporedja funkcionalnosti "Podajanje ocene", ko je uporabnik Sprehajalec z označenim osnovnim in alternativnim tokom.
![diagram zaporedja Podajanje ocene - osnovni tok 2, alternativni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/PodajanjeOceneOsAltTok2.png)

### 3.22 Ustvarjanje novega oglasa

#### 3.22.1 Ustvarjanje novega oglasa - osnovni tok 1
Diagram zaporedja funkcionalnosti "Ustvarjanje novega oglasa", ko je uporabnik Sprehajalec z označenimi izjemnimi tokovi.
![diagram zaporedja Ustvarjanje novega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/UstvarjanjeNovegaOglasaOsTok1.png)

#### 3.22.2 Ustvarjanje novega oglasa - osnovni tok 2
Diagram zaporedja funkcionalnosti "Ustvarjanje novega oglasa", ko je uporabnik Podjetje z označenimi izjemnimi tokovi.
![diagram zaporedja Ustvarjanje novega oglasa - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/UstvarjanjeNovegaOglasaOsTok2.png)

### 3.23 Pregled svojih aktivnih oglasov

#### 3.23.1 Pregled svojih aktivnih oglasov - osnovni tok 1

![diagram zaporedja Pregled svojih aktivnih oglasov - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/PregledSvojihAktivnihOglasovOsTok1.png)

#### 3.23.2 Pregled svojih aktivnih oglasov - osnovni tok 2

![diagram zaporedja Pregled svojih aktivnih oglasov - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/PregledSvojihAktivnihOglasovOsTok2.png)

### 3.24 Urejanje aktivnega oglasa

#### 3.24.1 Urejanje aktivnega oglasa - osnovni tok 1
Diagram zaporedja funkcionalnosti "Urejanje aktivnega oglasa", ko je uporabnik Sprehajalec z označenimi izjemnimi tokovi.
![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/UrejanjeAktivnegaOglasaOsTok1.png)

#### 3.24.2 Urejanje aktivnega oglasa - osnovni tok 2
Diagram zaporedja funkcionalnosti "Urejanje aktivnega oglasa", ko je uporabnik Podjetje z označenimi izjemnimi tokovi.
![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/UrejanjeAktivnegaOglasaOsTok2.png)

### 3.25 Brisanje aktivnega oglasa

#### 3.25.1 Brisanje aktivnega oglasa - osnovni tok 1

![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/BrisanjeAktivnegaOglasa_OsnovniTok1.png)

#### 3.25.2 Brisanje aktivnega oglasa - osnovni tok 2

![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/BrisanjeAktivnegaOglasa_OsnovniTok2.png)

#### 3.25.3 Brisanje aktivnega oglasa - alternativni tok 1

![diagram zaporedja Urejanje aktivnega oglasa - alternativni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/BrisanjeAktivnegaOglasa_AlternativniTok1.png)

#### 3.25.4 Brisanje aktivnega oglasa - alternativni tok 2

![diagram zaporedja Urejanje aktivnega oglasa - alternativni tok 2](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/BrisanjeAktivnegaOglasa_AlternativniTok2.png)

### 3.26 Generiranje varnostne šifre

#### 3.26.1 Generiranje varnostne šifre - osnovni tok 1

![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/GeneriranjeVarnostneSifre_OsnovniTok1.png)

#### 3.26.2 Generiranje varnostne šifre - osnovni tok 2

![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/GeneriranjeVarnostneSifre_OsnovniTok2.png)

### 3.27 Izdelava statistike o uporabnikih
Diagram zaporedja funkcionalosti "Izdelava statistike o uporabnikih" s prikazanima dvema vrstama klicev, ki smo jih definirali v opisu Vmesnikov v dokumentu Zajem zahtev.
#### 3.27.1 Izdelava statistike o uporabnikih - osnovni tok

![diagram zaporedja Urejanje aktivnega oglasa - osnovni tok 1](https://github.com/JodasSenpai/TPO-arhitektura/blob/main/docs/img/diagramiZaporedja/IzdelavaStatistikeOUporabnikih.png)
