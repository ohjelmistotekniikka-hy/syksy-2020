% Ohjelmistotekniikka
% Matti Luukkainen, Riku Honkanen ja 7 ohjaajaa
% 26.10.2020

# Ohjelmistotekniikka

- Kurssilla tutustutaan ohjelmistokehityksen periaatteisiin sekä menetelmiin ja sovelletaan niitä toteuttamalla pienehkö harjoitustyö

. . .

- Kurssi osa _aineopintoja_
- Pakollisina _esitietoina_
  - Ohjelmoinnin jatkokurssi
  - Tietokantojen perusteet
- Hyödyllinen esitieto: Tietokone työvälineenä

. . .

- Kurssimateriaali https://github.com/ohjelmistotekniikka-hy/syksy-2020

# Suoritusmuoto

- Kolmella ensimmäisellä viikolla ohjauksessa tai omatoimisesti tehtävät **laskarit**
  - palautetaan "internettiin"
- Viikolla 2 aloitetaan itsenäisesti tehtävä **harjoitustyö**
- Työtä edistetään pala palalta _viikoittaisten tavoitteiden_ ohjaamana
- Kurssilla ei ole koetta

. . .

- Harjoitustyö tulee tehdä kurssin aikataulujen puitteissa
- Kesken jäänyttä harjoitustyötä ei voi jatkaa seuraavalla kurssilla (keväällä 2021)
- Muista siis varata riittävästi aikaa (10-15h viikossa) koko periodin ajaksi!

# Luento, deadlinet ja ohjaus

- Kurssilla on vain yksi luento
- Laskareiden ja harjoitustyön välitavoitteiden viikoittaiset deadlinet _tiistaina klo 23:59_

. . .

- Pajaa salissa zoomissa, ks kurssisivu
- Myös kurssin Telegramissa voi kysellä apua ongelmatilanteissa

# Arvosteluperusteet

- Jaossa 60 pistettä jotka jakautuvat seuraavasti
  - Viikkodeadlinet 17p
    - osa viikkopisteistä tulee laskareista
  - Koodikatselmointi 2p
  - Dokumentaatio 12p
  - Testaus 5p
  - Lopullinen ohjelma 24p
    - laajuus, ominaisuudet ja koodin laatu
- Arvosanaan 1 riittää 30 pistettä, arvosanaan 5 tarvitaan noin 55 pistettä.
- Läpipääsyyn vaatimuksena on lisäksi vähintään 10 pistettä lopullisesta ohjelmasta

#

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TEORIA

# Ohjelmistotuotanto

- Kun ollaan tekemässä suurempaa ohjelmistoa jonkun muun kuin koodarin itsensä käyttöön, tarvitaan systemaattinen työskentelymenetelmä
  - muuten riskinä mm. että lopputulos ei vastaa käyttäjän tarvetta

. . .

- Menetelmästä riippumatta ohjelmiston systemaattinen kehittäminen, eli _ohjelmistotuotanto_ (engl. software engineering) sisältää useita erilaisia aktiviteettejä/vaiheita

. . .

  - _vaatimusmäärittelyä_ 
  - _suunnittelu_ 
  - _toteutus_ 
  - _testaus_
  - _ylläpito_

# Vaatimusmäärittely

- Kartoitetaan ohjelman tulevien käyttäjien tai tilaajan kanssa, mitä toiminnallisuutta ohjelmaan halutaan

. . .

- Tämän lisäksi kartoitetaan ohjelman toimintaympäristön ja toteutusteknologian järjestelmälle asettamia rajoitteita

. . .

- Tuloksena jonkinlainen dokumentti, johon vaatimukset kirjataan
- Dokumentin muoto vaihtelee: paksu mapillinen papereita tai joukko postit-lappuja tai ...

# Vaatimusten kirjaaminen

- On olemassa lukuisia tapoja dokumentoida vaatimuksen

. . .

- Kurssin ennen vuotta 2018 pidetyissä versioissa käyttäjien vaatimukset dokumentointiin _käyttötapauksina_ (engl. use case)
  - tapa on jo vanhahtava ja olemme jo hylänneet sen sen
- Kurssilla _Ohjelmistotuotanto_ tutustumme nykyään yleisesti käytössä oleviin _käyttäjätarinoihin_ (engl. user story)

. . .

- Käytämme tällä kurssilla hieman kevyempää tapaa
- Kirjaamme järjestelmältä toivotun toiminnallisuuden vapaamuotoisena ranskalaisista viivoista koostuvana feature-listana

# Kurssin referenssisovellus: TodoApp

https://github.com/mluukkai/OtmTodoApp havainnollistaa monia kurssin asioita ja toimii myös mallina omalle harjoitustyölle

- _todoapp_ eli sovellus, jonka avulla käyttäjien on mahdollista pitää kirjaa omista tekemättömistä töistä, eli _todoista_

Katsotaan esimerkkinä Todo-sovelluksen vaatimusmäärittelyä

. . .

- Aloitetaan tunnistamalla järjestelmän _käyttäjäroolit_
- Todo-sovelluksella kaksi käyttäjäroolia
  - _normaalit käyttäjät_
  - laajemmilla oikeuksilla varustetut _ylläpitäjät_

. . .

- Mietitään mitä toiminnallisuuksia kunkin käyttäjärooli tarvisee

# TodoApp:in vaatimusmäärittely

- Todo-sovelluksen _normaalien käyttäjien_ toiminnallisuuksia ovat esim. seuraavat
  - käyttäjä voi luoda järjestelmään käyttäjätunnuksen
  - käyttäjä voi kirjautua järjestelmään
  - kirjautumisen jälkeen käyttäjä näkee omat tekemättömät työt eli _todot_
  - kirjaantunut käyttäjä voi luoda uuden tehtävän eli _todon_
  - kirjaantunut käyttäjä voi merkitä _todon_ tehdyksi, jolloin se häviää listalta

. . .

- _Ylläpitäjän_ toiminnallisuuksia esim. seuraavat
  - ylläpitäjä näkee tilastoja sovelluksen käytöstä
  - ylläpitäjä voi poistaa normaalin käyttäjätunnuksen

# Vaatimusmäärittely: toimintaympäristön rajoitteet, käyttöliittymä

- Ohjelmiston vaatimuksiin kuuluvat myös _toimintaympäristön rajoitteet_
- Todo-sovellusta koskevat seuraavat rajoitteet:
  - ohjelmiston tulee toimia Linux- ja OSX-käyttöjärjestelmillä varustetuissa koneissa
  - tuteutetaan Java FX -kirjaston avulla
  - käyttäjien ja todojen tiedot talletetaan paikallisen koneen levylle

. . .

- Vaatimusmäärittelyn aikana hahmotellaan yleensä myös sovelluksen käyttöliittymä

# Todo-sovelluksen käyttöliittymäluonnos

![](https://raw.githubusercontent.com/mluukkai/OtmTodoApp/master/dokumentaatio/kuvat/v-1.png){ width=370 }

# Suunnittelu

- Suunnittelu jakautuu kahteen erilliseen vaiheeseen

. . .

- _Arkkitehtuurisuunnittelussa_ määritellään ohjelman rakenne karkealla tasolla
  - mistä suuremmista rakennekomponenteista ohjelma koostuu
  - miten komponentit yhdistetään, eli minkälaisia komponenttien väliset rajapinnat ovat
  - mitä riippuvuuksia ohjelmalla on esim. ohjelmakirjastoihin, tietokantoihin ja ulkoisiin rajapintoihin

. . .

- Arkkitehtuurisuunnittelua tarkentaa _oliosuunnittelu_
  - minkälaisisista luokista komponentit koostuvat
  - miten luokat kutsuvat toistensa metodeja sekä mitä apukirjastoja ne käyttävät
- Myös ohjelmiston suunnittelu, erityisesti sen arkkitehtuuri dokumentoidaan

# Testaus

- Toteutuksen yhteydessä ja sen jälkeen järjestelmää testataan
- Testausta on monentasoista

. . .

- _Yksikkötestauksessa_ tutkitaan yksittäisten metodien ja luokkien toimintaa.
  - ohjelmoijan vastuulla

. . .

- Kun erikseen ohjelmoidut luokat yhdistetään, suoritetaan _integraatiotestaus_
  - varmistetaan erillisten osien yhteentoimivuus
  - ohjelmoijan vastuulla

. . .

- _Järjestelmätestauksessa_ testataan ohjelmistoa kokonaisuutena: toimiiko se vaatimusdokumentin mukaisesti
  - suoritetaan ohjelman todellisen käyttöliittymän kautta
  - saattaa tapahtua erillisen laadunhallintatiimin toimesta

# Vesiputousmalli

- Ohjelmistoja on 70-luvulta asti tehty vaihe vaiheelta etenevän _vesiputousmallin_ (engl. waterfall model) mukaan

. . .

- Vesiputousmallissa edellä esitellyt ohjelmistotuotannon vaiheet suoritetaan peräkkäin
  ![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-1.png){ width=400 }

. . .

- Eri vaiheet ovat yleensä erillisten tiimien tekemiä
- Edellyttää perusteellista ja raskasta dokumentaatiota

# Vesiputousmallin ongelmat

- Mallin toimivuus perustuu siihen oletukseen, että vaatimukset pystytään määrittelemään täydellisesti etukäteen

. . .

- Näin ei useinkaan ole
  - Asiakkaat eivät osaa ilmaista kaikki ohjelmistolle asettamansa vaatimukset
  - Vasta käyttäessään valmista ohjelmistoa asiakkaat ymmärtää, mitä he haluavat
  - Vaikka vaatimukset kunnossa laatimishetkellä, toimintaympäristö voi muuttua ja valmistuessaan ohjelmisto on vanhentunut

. . .

- Toinen suuri ongelma on myöhään aloitettava testaus
  - Erityisesti integraatiotestauksessa löytyy usein pahoja ongelmia, joiden korjaaminen on hidasta ja kallista

# Ketterä ohjelmistokehitys

- Vesiputousmallin heikkoudet ovat johtaneet 2000-luvun alun jälkeen _ketterien (engl. agile) menetelmien_ käyttöönottoon
- Alussa kartoitetaan pääpiirteissään ohjelmiston vaatimuksia ja hahmotellaan ohjelmiston alustava arkkitehtuuri

. . .

- Tämän jälkeen suoritetaan useita, joiden aikana ohjelmistoa rakennetaan pala palalta eteenpäin
- Kussakin iteraatiossa suunnitellaan ja toteutetaan valmiiksi pieni osa ohjelmiston vaatimuksista

. . .

- Asiakas pääsee kokeilemaan ohjelmistoa jokaisen iteraation jälkeen
- Voidaan jo aikaisessa vaiheessa todeta, onko kehitystyö etenemässä oikeaan suuntaan
- Vaatimuksia voidaan tarvittaessa tarkentaa ja muuttaa

# Ketterä ohjelmistokehitys

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-2.png){ width=400 }

. . .

Teemme kurssin harjoitustyötä ketterässä hengessä viikon mittaisilla iteraatioilla

#

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;TYÖKALUJA

# Työkaluja

- Tarvitsemme ohjelmistokehityksessä suuren joukon käytännön työkaluja.
- Komentorivi ja versionhallinta
  - olet jo ehkä käyttänyt muilla kursseilla komentoriviä ja git-versionhallintaa
  - molemmat ovat tärkeässä roolissa ohjelmistokehityksessä
  - harjoitellaan viikon 1 laskareissa

. . .

- Maven
  - Olet todennäköisesti ohjelmoinut Javaa NetBeansilla ja tottunut painamaan "vihreää nappia" tai "mustaa silmää"
  - tutkimme kurssilla hieman miten Javalla tehdyn ohjelmiston _hallinnointi_ tapahtuu NetBeansin "ulkopuolella"
    - koodin kääntäminen, koodin sekä testin suorittaminen ja koodin paketoiminen NetBeansin ulkopuolella suoritettavissa olevaksi jar-paketiksi
  - Java-projektien hallinnointiin on olemassa muutamia vaihtoehtoja, käytämme joillekin TiKaPesta tuttua _mavenia_

# JUnit

- Ohjelmistojen testaus tapahtuu nykyään  automatisoitujen testityökalujen toimesta

. . .

- Java-maailmassa testausta dominoi lähes yksinvaltiaan tavoin JUnit
- Tulet kurssin ja myöhempienkin opintojesi aikana kirjoittamaan paljon JUnit-testejä
- Viikon 2 laskareissa harjoitellaan JUnitin perusteita

# Checkstyle

- Automaattisten testien lisäksi koodille voidaan määritellä erilaisia automaattisesti tarkastettavia tyylillisiä sääntöjä
  - ylläpidetään koodin luettavuutta ja varmistetaan, että koodi noudateta samoja tyylillisiä konventioita

. . .

- Käytämme kurssilla tarkoitukseen _Checkstyle_-nimistä työkalua

. . .

- Ohjelmoinnin perusteet ja jatkokurssi käyttivät Checkstyleä valvomaan ohjelman sisennystä
- Kurssilla kontrolloimme mm. muuttujien nimentää, sulkumerkkien sijoittelua ja välilyönnin käytön systemaattisuutta

# JavaDoc

- Osa ohjelmiston dokumentointia on lähdekoodin luokkien julkisten metodien kuvaus
- Javassa lähdekoodi dokumentoidaan käyttäen _JavaDoc_-työkalua
- Dokumentointi tapahtuu kirjoittamalla koodin yhteyteen sopivasti muotoiltuja kommentteja

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/k-1.png){ width=400 }

# JavaDoc

Sovelluksen JavaDocia voi tarkastella selaimen avulla

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-7.png){ width=400 }

# JavaDoc

NetBeans osaa näyttää ohjelmoidessa koodiin määritellyn JavaDocin

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-14.png)

#

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UML

# UML ja dokumentointi

- Dokumentoinnissa ja suunnittelun tukena tarvitaan ohjelman rakennetta ja toimintaa havainnollistavia kaavioita

. . .

- _UML_ eli _Unified Modeling Language_ on 1997 standardoitu olio-ohjelmistojen mallintamiseen tarkoitettu mallinnuskieli
- UML sisältää 13 erilaista kaaviotyyppiä
- UML oli aikoinaan todella suosittu, nyt sen suosio on hiipumaan päin, muutama tärkein kaaviotyyppi kannattaa kuitenkin osata

. . .

- Käytämme kurssilla luokka-, pakkaus- ja sekvenssikaavioita

# Luokkakaaviot

- Kurssin Tietokantojen perusteet aiemmista versioista tuttujen _luokkakaavioiden_ käyttötarkoitus on luokkien ja niiden välisten suhteiden kuvailu
- Todo-sovelluksen oleellista tietosisältöä kuvaavat luokat

```java
public class User {
    private String name;
    private String username;
    // ...
}

public class Todo {
    private int id;
    private String content;
    private boolean done;
    private User user;
    // ...
}
```

# Todo-sovelluksen tietosisällön luokkakaavio

- Yhdellä käyttäjällä voi olla montoa Todoa
- Todo liittyy aina yhteen käyttäjään

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-3a.png){ width=450 }

# Todo-sovelluksen tietosisällön luokkakaavio

- Yleensä ei ole mielekästä kuvata luokkia tällä tarkkuudella, eli **luokkakaavioihin riittää merkitä luokan nimi**

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-4.png){ width=300 }

- Kaaviota parempi paikka metodien kuvaamiselle on koodiin liittyvä JavaDoc-dokumentaatio

# Rajapinnan toteutus ja perintä luokkakaaviossa

- Jos Todo-sovelluksessa olisi normaalin käyttäjän eli luokan _User_ perivä ylläpitäjää kuvaava luokka _SuperUser_, merkattaisiin se luokkakaavioon seuraavasti

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-9.png){ width=300 }

- Rajapinnan toteutus merkitään samalla tavalla eli valkoisella nuolenpäällä

# Pakkauskaavio

- Ohjelmiston korkeamman tason rakenne näkyy yleensä siinä miten koodi on jaettu _pakkauksiin_

. . .

- Todo-sovelluksen koodi on sijoitettu _pakkauksiin_ seuraavasti:

:::::::::::::: {.columns}
::: {.column width="50%"}
![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/k-2.png){ width=150 }
:::
::: {.column width="50%"}

:::
::::::::::::::

# Pakkauskaavio

- Pakkausrakenne voidaan kuvata UML:ssä pakkauskaaviolla

:::::::::::::: {.columns}
::: {.column width="50%"}
![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/k-2.png){ width=150 }
:::
::: {.column width="50%"}
![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-11.png){ width=100 }
:::
::::::::::::::

- Pakkausten välille on merkitty riippuvuus jos pakkauksen luokat käyttävät toisen pakkauksen luokkia

# Toiminnallisuuden kuvaaminen

- Luokka- ja pakkauskaaviot kuvaavat ohjelman rakennetta
- Ohjelman toiminta ei kuitenkaan tule niistä ilmi millään tavalla

. . .

- Esim. Ohpen Unicafe-tehtävä
  ![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-15.png){ width=400 }
- Vaikka kaavioon on nyt merkitty metodien nimet, ei ohjelman toimintalogiikka selviä kaaviosta
- Esim. mitä tapahtuu, kun maksukortilla jolla on rahaa 3 euroa, ostataan edullinen lounas?

# Sekvenssikaavio

. . .

- Kehitetty alunperin kuvaamaan verkossa olevien ohjelmien keskinäisen kommunikoinnin etenemistä
- Sopivat jossain määrin kuvaamaan, miten ohjelman oliot kutsuvat toistensa metodeja suorituksen aikana

# Sekvenssikaavio

Mitä tapahtuu, kun maksukortilla jolla on rahaa 3 euroa, ostataan edullinen lounas?

```java
public boolean syoEdullisesti(Maksukortti kortti) {
    if (kortti.saldo() < EDULLISEN_HINTA) {
        return false;
    }

    kortti.otaRahaa(EDULLISEN_HINTA);
    this.edulliset++;
    return true;
}
```

# Onnistunut ostos sekvenssikaaviona

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-16.png){ width=300 }

- Oliot ovat laatikoita joista lähtee alas "elämänlanka"
- Aika etenee ylhäältä alas
- Metodikutsut ovat nuolia, jotka yhdistävää kutsuvan ja kutsutun olion elämänlangat
- Paluuarvo merkitään katkoviivalla

# Epäonnistunut ostos sekvenssikaaviona

Mitä tapahtuu, jos maksukortin saldo on 2 euroa, eli vähemmän kuin lounaan hinta:

![](https://raw.githubusercontent.com/mluukkai/ohjelmistotekniikka-syksy-2020/main/web/images/l-17.png){ width=300 }

. . .

- Sekvenssikaaviot kuvaavat siis yksittäistä tapahtumasarjaa
- Toiminnallisuuden kuvaamiseen tarvitaankin yleensä useampi sekvenssikaavio

#

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HARJOITUSTYÖ

# Yleistä

- Kurssin pääpainon muodostaa viikolla 2 aloitettava harjoitustyö
- Harjoitustyössä toteutetaan itsenäisesti ohjelmisto omavalintaisesta aiheesta

- Harjoitustyötä tehdään itsenäisesti, mutta tarjolla on pajaohjausta 

# Työn eteneminen

- Edetään viikottaisten tavoitteiden mukaan
- Työ on saatava valmiiksi kurssin aikana ja sitä on toteutettava tasaisesti, muuten kurssi katsotaan keskeytetyksi

. . .

- Samaa ohjelmaa ei voi jatkaa seuraavalla kurssilla (eli keväällä 2021), vaan työ on aloitettava uudella aiheella alusta

. . .

- Koko kurssin arvostelu perustuu pääasiassa harjoitustyöstä saataviin pisteisiin
- Osa pisteistä kertyy viikoittaisten välitavoitteiden kautta, osa taas perustuu työn lopulliseen palautukseen

# Kieli

- Harjoitustyön ohjelmointikieli on Java
- Ohjelmakoodin muuttujat, luokat ja metodit **kirjoitetaan englanniksi**
- Dokumentaatio voidaan kirjoittaa joko suomeksi tai englanniksi

. . .

- Web-sovelluksia kurssilla ei sallita
  - Sovelluksessa voi toki olla webissä toimivia komponentteja, mutta sovelluksen käyttöliittymän tulee olla ns. desktop-sovellus

. . .

- Uutuus: Python-versio
  - omalla vastuulla
  - Käytetään olio-ohjelmointia, Python Ohpe **ei riitä** esitiedoksi

# Ohjelman toteutus

- Toteutus etenee "iteratiivisesti ja inkrementaalisesti"
  - Heti ensimmäisellä viikolla toteutetaan pieni käyttökelpoinen osa toiminnallisuudesta
  - ohjelman ydin pidetään koko ajan toimivana, uutta toiminnallisuutta lisäten, kunnes tavoiteltu laajuus on saavutettu

. . .

- Iteratiiviseen tapaan tehdä ohjelma liittyy kiinteästi automatisoitu testaus
- Uutta toiminnallisuutta lisättäessä ja vanhaa muokatessa täytyy varmistua, että kaikki vanhat ominaisuudet toimivat edelleen
- Jotta ohjelmaa pystyisi testaamaan, on tärkeää että sovelluslogiikkaa ei kirjoiteta käyttöliittymän sekaan

. . .

- Graafiseen käyttöliittymään suositellaan JavaFX:ää
- Tiedon talletus joko tiedostoon tai tietokantaan suositeltavaa

# Ohjelman toteutus

- Tavoitteena on tuottaa ohjelma, joka voitaisiin antaa toiselle opiskelijalle ylläpidettäväksi ja täydennettäväksi
  - koodin on siis oltava ymmärrettävää ja jatkokehitityksen mahdollistavaa

. . .

- Lopullisessa palautuksessa on oltava lähdekoodin lisäksi dokumentaatio ja automaattiset testit sekä jar-tiedosto

. . .

- Toivottava dokumentaation taso käy ilmi referenssisovelluksesta https://github.com/mluukkai/OtmTodoApp

# Hyvän aiheen ominaisuudet

- **Itseäsi kiinnostava aihe**
- Riittävän mutta ei liian laaja
  - Vältä eeppisiä aiheita, aloita riittävän pienestä
  - Valitse aihe, jonka perustoiminnallisuuden saa toteutettua nopeasti, mutta jota saa myös laajennettua helposti
  - Hyvässä aiheessa on muutamia logiikkaluokkia, tiedostojen tai tietokannan käsittelyä ja sovelluslogiikasta eriytetty käyttöliittymä

. . .

- Kurssilla pääpaino on
  - Toimivuus ja varautuminen virhetilanteisiin
  - Luokkien vastuut
  - Ohjelman selkeä rakenne
  - Laajennettavuus ja ylläpidettävyys

. . .

- **Tällä kurssilla ei ole tärkeää:**
  - Tekoäly
  - Grafiikka
  - Tietoturva
  - Tehokkuus

# Huonon aiheen ominaisuuksia

- Kannattaa yrittää välttää aiheita, joissa pääpaino on tiedon säilömisessä tai liian monimutkaisessa käyttöliittymässä
- Paljon tietoa säilövät, esim. yli 3 tietokantataulua tarvitsevat sovellukset sopivat yleensä paremmin kurssille Tietokantasovellus
- Käyttöliittymäkeskeisissä aiheissa voi olla vaikea keksiä sovelluslogiikkaa, joka on enemmän tämän kurssin painopiste

# Esimerkkejä aiheista

- Hyötyohjelmat
  - Aritmetiikan harjoittelua
  - Tehtävägeneraattori, joka antaa käyttäjälle tehtävän sekä mallivastauksen (esim. matematiikkaa, fysiikkaa, kemiaa, ...)
  - Code Snippet Manageri
  - Laskin, funktiolaskin, graafinen laskin
  - Budjetointisovellus
  - Opintojen seurantasovellus
  - HTML WYSIWYG-editor (What you see is what you get)

# Esimerkkejä aiheista

- Reaaliaikaiset pelit
  - Tetris
  - Pong
  - Pacman
  - Tower Defence
  - Asteroids
  - Space Invaders
  - Yksinkertainen tasohyppypeli, esimerkiksi The Impossible Game

# Esimerkkejä aiheista

- Vuoropohjaiset pelit
  - Tammi
  - Yatzy
  - Miinaharava
  - Laivanupotus
  - Yksinkertainen roolipeli tai luolastoseikkailu
  - Sudoku
  - Muistipeli
  - Ristinolla (mielivaltaisen kokoisella ruudukolla?)

# Esimerkkejä aiheista

- Korttipelit
  - En Garde
  - Pasianssi
  - UNO
  - Texas Hold'em
- Omaan tieteenalaan, sivuaineeseen tai harrastukseen liittyvät hyötyohjelmat
  - Yksinkertainen fysiikkasimulaattori
  - DNA-ketjujen tutkija
  - Keräilykorttien hallintajärjestelmä
  - Fraktaaligeneraattori

# Arvosteluperusteet tarkemmin

- Kurssin maksimi on 60 pistettä
- Ennen loppupalautusta jaossa 19 pistettä
  - Viikkodeadlinet 17p
  - Koodikatselmointi 2p

. . .

- Loppupalautus ratkaise 41 pisteen kohtalon
  - Dokumentaatio 12p
  - Testaus 5p
  - Lopullinen ohjelma 24p
    - Laajuus, ominaisuudet ja koodin laatu

. . .

- Arvosanaan 1 riittää 30 pistettä, arvosanaan 5 tarvitaan noin 55 pistettä
- Läpipääsyyn vaatimuksena on lisäksi vähintään 10 pistettä lopullisesta ohjelmasta

# Harjoitustyön vaikutus kurssipisteisiin

Ohjelman pisteet jakautuvat seuraavasti

- käyttöliittymä 4p
  - 0p yksinkertainen tekstikäyttöliittymä
  - 1-2p monimutkainen tekstikäyttöliittymä
  - 2-3p yksinkertainen graafinen käyttöliittymä
  - 4p laaja graafinen käyttöliittymä

. . .

- tiedon pysyväistalletus 4p
  - 0p ei pysyväistalletusta
  - 1-2p tiedosto
  - 3-4p tietokanta
  - 3-4p internet

. . .

- sovelluslogiikan kompleksisuus 3p
- ohjelman lajuus 5p

. . .

- ulkoisten kirjastojen hyödyntäminen 1p
- suorituskelpoinen jar-tiedosto 1p
- koodin laatu 6p

# Harjoitustyön toimivuus

- Koneiden konfiguraatioissa on eroja, ja tällä kurssilla _ei riitä_ että hajoitustyössä tekemäsi sovellus toimii vain omalla koneellasi

. . .

- Harjoitustyösi pitää pystyä joka viikko suorittamaan, kääntämään ja testaamaan komentoriviltä käsin laitoksen linux-koneilla (tai uusimmat päivitykset sisältävällä cubbli-linuxilla)
  - muussa tapauksessa työtä ei tarkasteta ja menetät viikon/loppupalautuksen pisteet
- Varminta käyttää Javan versiota 11

. . .

- Pääset testaamaan ohjelmaasi laitoksen koneella myös kotoa käsin käyttämällä etätyöpöytää

# Koodin laatuvaatimukset

- Kurssin tavoitteena on, että tuotoksesi voisi ottaa kuka tahansa kaverisi tai muu opiskelija ylläpidettäväksi ja laajennettavaksi
- Lopullisessa palautuksessa tavoitteena on _Clean code_ eli selkeä, ylläpidettävä ja toimivaksi testattu koodi
