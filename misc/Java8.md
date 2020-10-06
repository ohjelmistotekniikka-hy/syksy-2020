## TMCbeans ja Java 8 

Jos käytät TMCbeansia (eli TMC:n ja Netbeansin yhdistelmää), koneellasi on oltava Java 8, ja maven tulee olla konfiguroitu oikealla tavalla, jotta ohjelmien käynnistäminen/testaaminen/ym onnistuu myös komentoriviltä.

Tarkasta koneesi maven käyttämä Java-versio kirjoittamalla terminaaliin käsky:

`mvn -v`

Jos koneellasi on jokin muu versio vaihda se alla olevan ohjeen mukaisesti:

`export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64/`

Komennon onnistumisen varmistamiseksi mvn -v rupeaa näyttämään oikeaa versiota. 

Eli java 11 sijaan mvn -v sanoo java8.

Tuon aiemmassa komennossa olevan polun löytää helposti ainakin cubblilla komennolla:

`update-alternatives --list java`

-- 

Jotta kurssin esimerkkisovelluksen https://github.com/mluukkai/OtmTodoApp saa toimimaan laitoksen koneilla vaihda se alla olevalla terminaalikäskyllä