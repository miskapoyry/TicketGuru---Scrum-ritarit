# TicketGuru

SCRUM-Ritarit

Tiimi: Miska Pöyry, Tuomas Sirviö, Hanna-Riikka Happonen, Roosa Karjalainen, Pekka Näätsaari, Jesse Ritola

## Johdanto

### Projektin aihe:
TicketGuru on lipunmyyntijärjestelmä, joka on suunniteltu lipputoimistolle. Sen pääasiallinen tarkoitus on mahdollistaa lippujen myynti ja tulostus myyntipisteessä. Järjestelmä mahdollistaa tapahtumien määrittämisen, lippujen myynnin sekä niiden käytön tarkastamisen ovella (paperiset liput sekä mobiililiput QR-koodilla).

### Asiakas:
Asiakkaamme on lipputoimisto, joka tarvitsee sähköisen järjestelmän lippujen myyntiin sekä hallintaan. Järjestelmä mahdollistaa lipunmyyjien myyvän ja tulostavan liput asiakkaille sekä hallitsevan lippujen jäljellä olevia määriä. Ennakkomyynnin jälkeen jääneet liput voidaan tulostaa ovella myytäviksi.

### Mitä asiakas saa järjestelmältä:
TicketGuru tarjoaa lipunmyyjille työkalut lipunmyyntiin, tulostukseen ja lipun tarkastukseen. Järjestelmässä on myös mahdollisuus määritellä tapahtumia ja niiden lippumääriä. Tulevaisuudessa järjestelmään aiotaan lisätä verkkokauppa, jonka kautta asiakkaat voivat itse ostaa lippuja.

### Toteutus- ja toimintaympäristö lyhyesti:

-   Palvelinpuolen ratkaisut ja teknologiat: SpringBoot, MariaDB
-   Käyttöliittymäratkaisut ja teknologiat: Desktop (Windows), Mobiililaitteet (Android ja iOS), React, Bootstrap

### Mitä valmiina, kun projekti päättyy?

Projektin päättyessä ovat valmiina seuraavat osa-alueet: lipunmyyntijärjestelmä, tapahtumien hallinta, lipun tulostus ja käytön tarkastaminen. Verkkokaupan integrointi on suunnitteilla seuraavaan vaiheeseen. Projektin päättyessä on valmiina myös kaikki tarvittava dokumentointi projektin kulusta ja siitä kaikesta mitä ollaan tehty. 

## Järjestelmän määrittely

### Käyttäjäryhmät (roolit):

#### Järjestelmän ylläpitäjä (lipputoimisto)
-   Lisää ja hallinnoi tapahtumia järjestelmässä
-   Luo ja tarvittaessa päivittää lipputyypit
-   Tuottaa myyntiraportteja mm. myynnin analysoimiseksi

#### Lipunmyyjä
-   Myy liput asiakkaille myyntipisteessä
-   Tulostaa liput asiakkaille ja ovella myytäviksi ennakkomyynnin jälkeen
-   Tarkastaa liput ovella (merkitään käytetyiksi)

### Käyttäjätarinat

#### Lipunmyyjä
-   Lipunmyyjänä haluan myydä ja tulostaa lippuja asiakkaille, että he voivat osallistua tapahtumaan.
-   Lipunmyyjänä haluan merkitä liput käytetyiksi ovella varmistuakseni, että vain maksaneet asiakkaat pääsevät osallistumaan tapahtumaan.
-   Lipunmyyjänä haluan tarkastella tulevia tapahtumia ja lipputilannetta, että voin etsiä ja tarjota sopivia vaihtoehtoja asiakkaille.
-   Lipunmyyjänä haluan, että järjestelmä on saatavilla 99,9 % ajasta, että voin myydä asiakkaille lippuja ja tarkastaa niitä ilman keskeytyksiä.
-   Lipunmyyjänä haluan, että lipun myyntitapahtuma kestää alle 2 sekuntia, että voin myydä lippuja nopeasti ilman asiakaspalvelun ruuhkautumista.


#### Järjestelmän ylläpitäjä
-   Järjestelmän ylläpitäjänä haluan lisätä järjestelmään uusia tapahtumia, että lippuja voidaan myydä tuleviin tapahtumiin.
-   Järjestelmän ylläpitäjänä haluan luoda ja muokata lipputyyppejä (esim. aikuinen, lapsi, opiskelija), että asiakkailla on sopivia hintavaihtoehtoja.
-   Järjestelmän ylläpitäjänä haluan luoda myyntiraportteja, että pysyn ajan tasalla myynnin tilasta ja siitä, minkälaiset tapahtumat kiinnostavat asiakkaita.
-   Järjestelmän ylläpitäjänä haluan, että tiedonhaku menneiden tapahtumien myyntitiedoista onnistuu muutamalla klikkauksella, että työaikaa ei mene hukkaan.
-   Järjestelmän ylläpitäjänä haluan, että vain ylläpitäjillä on pääsy lippujen ja tapahtumien ylläpitoon, että tietoturva toteutuu asianmukaisesti.

## Käyttöliittymä

### Käyttöliittymäkaavio

Tässä on alustava käyttöliittymäkaavio. Jokainen järjestelmän käyttäjä on velvoitettu kirjautumaan, jonka jälkeen peruskäyttäjän ja adminin käyttötapausten perusteella toiminta eroaa hiukan. Admin toimii siis ikään kuin hallinnoivana elimenä, eikä täten osallistu suoranaisesti lippujen myymiseen. Hän kuitenkin kykenee hallinnoimaan tapahtumia, tarkastelemaan sen tietoja (tilastoja) ja lisäämään uusia tapahtumia. Myyjä voi puolestaan myydä valitsemiaan lippuja valitsemaansa tapahtumaan, mikäli ne ovat vapaana. Hän myös vastaa lippujen tarkastamisesta ja niiden käytetyksi merkitsemisestä. Käyttöliittymäkaaviosta on alustavasti tarkasteltavissa tärkeimmät näkymät ja niiden väliset suhteet.

Admin tasoinen käyttäjä kykenee myös näkemään valitsemansa tapahtuman kaikki ostotapahtumat, klikkaamalla ostotapahtuman ID numeroa, jonka avulla hän kykenee näkemään kaikki kyseisellä ostotapahtumalla ostetut liput samanaikaisesti.

![alustava_kayttoliittymakaavio](kayttoliittyma_kuvat/kayttoliittymakaavio.png)

***Alapuolelle on luotu hahmotelmia, joiden avulla käyttöliittymään saadaan lisää selkeyttä. Huomioithan, että nämä eivät ole tässä vaiheessa vielä lopullisia, ja muutosten tullessa eteen, niitä voi käydä muuttamassa.***

### Kirjatuminen

Näyttöhahmotelma kirjautumisruutuun sekä rekisteröimiseen. Niiden välinen suhde tulee tosin miettiä, sillä kuka tahansa ei voi tehdä käyttäjää järjestelmään, vaan sitä on rajattava jollakin tavalla (admin käyttäjä hyväksyy/luo käyttäjät?).

![kirjautuminen_hahmotelma](kayttoliittyma_kuvat/kirjautuminen_nayttohahmotelma.png)

### Lippujen myynti

Lipunmyynti on avoinna Myyjille ja siellä myyjä kykenee valitsemaan tapahtuman, lippujen määrän ja tyypin sekä tulostamaan liput ostamisen jälkeen.

![lipunmyynti_hahmotelma](kayttoliittyma_kuvat/lipunmyynti_nayttohahmotelma.png)

### Hallinnointi

Hallinnointiin pääsee "admin" tasoisilla tunnuksilla. Siellä käyttäjä kykenee luomaan uuden tapahtuman, tarkastelemaan tapahtumia ja niiden menetystä tai muokkaamaan valitun tapahtuman tietoja.

![hallinnointi_hahmotelma](kayttoliittyma_kuvat/hallinnointi_nayttohahmotelma.png)

### Lippujen tarkastus

Lippujen tarkastus vaatii myyjän roolin. Se toimii yksinkertaisesti syöttämällä käyttäjän antaman lipun hash koodi järjestelmään. Järjestelmä hakee lipun ja sen tiedot. Mikäli lippu on käyttökelpoinen kaikin puolin, voi myyjä tällöin merkitä sen käytetyksi.

![lipuntarkistus_hahmotelma](kayttoliittyma_kuvat/lipuntarkastus_nayttohahmotelma.png)

### Kayttöliittymähahmotelmat

Hahmotelmat ovat löydettävissä ja muokattavissa [täältä](https://www.canva.com/design/DAGQ1kQ8OUA/b28P_8oSvLwuQQcILEEJBg/edit?utm_content=DAGQ1kQ8OUA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

## Tietokanta

Tietokanta on suunniteltu tukemaan käyttäjien, tapahtumien ja lippujen hallintaa tehokkaasti ja joustavasti. Seuraavaksi esitetään tietohakemisto, joka sisältää tärkeimmät taulut, niiden kentät ja kuvaus niiden käyttötarkoituksesta. Ohessa on myös ER-kaavio, joka havainnollistaa tietokannan rakennetta ja suhteita eri taulujen välillä. 

### Tietokantakaavio

![tietokantakaavio_kuva](tietokantakaavio/TicketGuru_tietokantakaavio(korjattu).jpg)

### Tietohakemisto

> ### _app_user_
> _user-taulu sisältää käyttäjätilin tiedot. Tili kuuluu aina vain yhdelle käyttäjälle._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> user_id | Long PK | Käyttäjän yksilöivä tunniste
> role_id | Long FK | Roolin tunniste (viittaus role-tauluun)
> username | varchar(50) |  Käyttäjän käyttäjätunnus
> passwordhash | varchar(255) | Käyttäjän salasana

> ### _role_
> _rooli-taulu sisältää roolien tiedot. Yhdellä käyttäjällä voi olla vain yksi rooli._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> role_id | Long PK | Roolin yksilöivä tunniste
> role_name | varchar(20) |  Roolin nimi

> ### _event_
> _event-taulu sisältää yksittäisen tapahtuman tiedot._
>
> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> event_id | Long PK | Tapahtuman yksilöivä tunniste
> user_id | Long FK | Käyttäjä, joka on luonut tapahtuman (viittaus tauluun app_user)
> event_name | varchar(100) |  Tapahtuman nimi
> event_date | timestamp | Tapahtuman päivämäärä ja aika
> location | varchar(100) | Tapahtuman sijainti
> total_tickets | int | Lippujen määrä tapahtumassa kaikkiaan
> available_tickets | int | Saatavilla olevien lippujen määrä tapahtumassa

> ### _ticket_type_
> _ticket_type -taulu sisältää lipputyyppien tiedot._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> ticket_type_id | Long PK | Lipputyypin yksilöivä tunniste
> ticket_type_name | varchar (50) | Lipputyypin nimi (esim. "aikuinen" tai "lapsi")

> ### _event_ticket_type_
> _event_ticket_type-taulu yhdistää tapahtumat ja lipputyypit mahdollistaen erilaisten lippujen hallinnan tapahtumakohtaisesti. Taulu tallentaa tiedot tietyn lipputyypin saatavuudesta ja määrästä kullekin tapahtumalle sekä lipputyypin hinnan._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> event_ticket_type_id | Long PK | Tapahtuma, johon lippu liittyy (viittaus tauluun event)
> ticket_type_id | Long FK | Lipputyyppi (viittaus tauluun ticket_type)
> event_id | Long FK | Tapahtuma (viittaus tauluun event)
> ticket_quantity | int |  Saatavilla oleva määrä tietylle lipputyypille
> price | decimal (10, 2) |  Lipun hinta

> ### _ticket_
> _ticket-taulu sisältää yksittäisen lipun tiedot._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> ticket_id | Long PK | Lipun yksilöivä tunniste
> ticket_number | varchar (50) | Lipun numero tai tunniste
> ticket_type_id | Long FK | Lipputyyppi (viittaus tauluun ticket_type)
> event_id | Long FK | Tapahtuma (viittaus tauluun event)
> sale_id | Long FK | Myyntitapahtuman id (viittaus tauluun sale)
> sale_timestamp | TIMESTAMP | Lipun myyntiaika
> is_used | BOOLEAN | Lipun käyttötilanne
> used_timestamp | TIMESTAMP | Ajankohta, jolloin lippu on käytetty (null, jos ei ole käytetty)

> ### _sale_
> _sale-taulu sisältää yksittäisen myyntitapahtuman tiedot._

> Kenttä | Tyyppi | Kuvaus
> ------ | ------ | ------
> sale_id | Long PK | Myyntitapahtuman yksilöivä tunniste
> sale_timestamp | TIMESTAMP | Myyntitapahtuman ajankohta
> user_id | Long FK | Myynnin suorittanut käyttäjä (viittaus tauluun app_user)
> payment_method | varchar (20) | Maksutapa (esim. "käteinen", "kortti")
> total_price | double | Myynnin kokonaissumma


## Tekninen kuvaus

Teknisessä kuvauksessa esitetään järjestelmän toteutuksen suunnittelussa tehdyt tekniset
ratkaisut, esim.

-   Missä mikäkin järjestelmän komponentti ajetaan (tietokone, palvelinohjelma)
    ja komponenttien väliset yhteydet (vaikkapa tähän tyyliin:
    https://security.ufl.edu/it-workers/risk-assessment/creating-an-information-systemdata-flow-diagram/)
-   Palvelintoteutuksen yleiskuvaus: teknologiat, deployment-ratkaisut yms.
-   Keskeisten rajapintojen kuvaukset, esimerkit REST-rajapinta. Tarvittaessa voidaan rajapinnan käyttöä täsmentää
    UML-sekvenssikaavioilla.
-   Toteutuksen yleisiä ratkaisuja, esim. turvallisuus.

Tämän lisäksi

-   ohjelmakoodin tulee olla kommentoitua
-   luokkien, metodien ja muuttujien tulee olla kuvaavasti nimettyjä ja noudattaa
    johdonmukaisia nimeämiskäytäntöjä
-   ohjelmiston pitää olla organisoitu komponentteihin niin, että turhalta toistolta
    vältytään

## Testaus

Sovellukseen on tehty yksikkötestejä (JUnit) joihinkin service-kerroksen luokkiin sekä integraatiotestejä joihinkin web-kerroksen luokkiin. Kokonaisvaltaista testausta ei aikataulusyiden ja rajallisten resurssien takia pystytty tekemään. Alla tarkempi erittely siitä, mitä luokkia testattiin.

### Testattavat kohteet (JUnit-yksikkötestit)

- **AppUserService-luokka**: Testit keskittyvät AppUserService-luokan toimintoihin eli käyttäjien luomiseen, päivittämiseen, hakemiseen ja poistamiseen. Tavoitteena on varmistaa, että AppUserService toimii odotetusti ja että mahdolliset virhetilanteet käsitellään oikein.

- **SaleService-luokka**: Testit keskittyvät SaleService-luokan toimintoihin eli myyntitapahtumien käsittelyyn, kuten myynnin luomiseen, päivittämiseen, hakemiseen ja poistamiseen. Tavoitteena on varmistaa, että SaleService toimii odotetusti, ja että virhetilanteet käsitellään oikein.

#### Miten testit toteutettiin?

Testeissä keskittyttiin yksittäisten metodien käyttäytymiseen. Yksikkötesteissä palvelun toiminnallisuus on eristettyä ja testejä suoritetaan ilman, että tarvitaan tietokantaa tai muita ulkoisia resursseja.

Testien suorittamiseen on käytetty mock-objekteja ja Mockito-kirjastoa, joiden avulla voidaan simuloida ulkoisia riippuvuuksia, kuten tietokantakutsuja ja salasanan enkoodauksen logiikkaa.

### Testattavat kohteet (Integraatiotestit)

- **TicketResource-luokka:** Testit keskittyvät lipunhallinnan toimintoihin eli lippujen hakemiseen ja lipun merkitsemiseen käytetyksi. Tämä on ensimmäinen luokka, jolle kirjoitettiin integraatiotesti, joten luokka sisältää myös testin Liquibase-konfiguraatioiden tarkastamiseen. Tavoitteena on varmistaa, että liput voidaan hakea oikein ja että lipun käyttötilan päivittäminen toimii odotetusti.

- **SaleResource-luokka:** Testit keskittyvät Sale-resurssin integraatioon, joka käsittelee myyntitapahtumia, kuten myynnin luomista, hakemista, poistamista ja hakemista eri hakuehdoilla. Tavoitteena on varmistaa, että API toimii odotetusti ja virhetilanteet käsitellään oikein.

- **AppUserResource-luokka:** Testit keskittyvät AppUserResource-luokan käyttäjätoimintojen integroituun testaamiseen, eli varmistetaan, että käyttäjien luominen, päivittäminen, hakeminen ja poistaminen toimivat oikein todellisessa ympäristössä. Testeissä varmistetaan, että järjestelmä käsittelee odotetusti sekä onnistuneita että virheellisiä pyyntöjä API-kutsujen kautta. Testeissä otetaan huomioon myös mahdolliset virhetilanteet, kuten puuttuvat käyttäjät ja virheelliset syötteet.

- **EventResource-luokka:** Testit keskittyvät EventResource-luokan toimintoihin, jotka käsittelevät tapahtumien hakemista, luomista, päivittämistä ja virhetilanteita. Tavoitteena on varmistaa, että EventResource toimii odotetusti ja että tapahtumien käsittelyä varten tehdyt HTTP-pyynnöt tuottavat oikeat vastaukset.

#### Miten testit toteutettiin?

Halusimme testata palvelujen toimintaa kokonaisuutena, sisältäen API-pyyntöjen lähettämisen ja tietokannan kanssa kommunikoimisen. Nämä testit eivät rajoitu vain yksittäisiin metodeihin, vaan ne varmistavat, että sovelluksen eri osat toimivat yhteen ja kommunikoivat oikein.

Testit suoritetaan MockMvc-kirjaston avulla, joka simuloi HTTP-pyyntöjä ja vastaanottaa vastauksia ilman, että tarvitaan oikeaa käyttäjää tai käyttöliittymää. MockMvc-objekti suorittaa API-pyynnöt ja tarkistaa vastauksia käyttäen HTTP-statuskoodeja ja JSON-vastausten sisältöä. Näin varmistetaan, että API-toiminnallisuus on oikea, ja että se palauttaa oikeat virheviestit virheellisissä tilanteissa.

Testin konfiguraatiot on suoritettu application-test.properties-tiedostossa, jossa on määritelty, että testeissä käytetään ajonaikaista H2-kantaa. Kaikkien toiminnallisuuksien onnistumiseksi testeihin on määritelty, että siitä huolimatta käytetään MariaDB-dialectiä. Tietokannan skeemaa hallinnoidaan Liquibasessa, jossa sijaitsee myös testeissä käytettävä testidata.

Testeissä ei testata lainkaan auktorisointia, ja se onkin kytketty pois päältä erillisessä TestSecurityConfig-luokassa, jota testit käyttävät.

### Erillinen testausdokumentaatio

Löydät tarkemman dokumentaation testauksesta ja sen tuloksista täältä.

## Asennustiedot

Järjestelmän asennus on syytä dokumentoida kahdesta näkökulmasta:

-   järjestelmän kehitysympäristö: miten järjestelmän kehitysympäristön saisi
    rakennettua johonkin toiseen koneeseen

-   järjestelmän asentaminen tuotantoympäristöön: miten järjestelmän saisi
    asennettua johonkin uuteen ympäristöön.

Asennusohjeesta tulisi ainakin käydä ilmi, miten käytettävä tietokanta ja
käyttäjät tulee ohjelmistoa asentaessa määritellä (käytettävä tietokanta,
käyttäjätunnus, salasana, tietokannan luonti yms.).

## Käynnistys- ja käyttöohje

Tyypillisesti tässä riittää kertoa ohjelman käynnistykseen tarvittava URL sekä
mahdolliset kirjautumiseen tarvittavat tunnukset. Jos järjestelmän
käynnistämiseen tai käyttöön liittyy joitain muita toimenpiteitä tai toimintajärjestykseen liittyviä asioita, nekin kerrotaan tässä yhteydessä.

Usko tai älä, tulet tarvitsemaan tätä itsekin, kun tauon jälkeen palaat
järjestelmän pariin !
