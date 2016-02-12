Ohjelman yleisrakenne
=====================

* Ohjelman toiminnan kannalta tärkein luokka on game.Board. Se on vastuussa pelilaudan päivittämisestä ja liikkeiden asettamisesta laudalle. Board sisältää kaksiulotteisen Player -taulukon, missä Player enum kertoo minkä värinen nappula kussakin laudan koordinaatissa on. 
* board.game.AI luokka sisältää tekoälyn kaikki ominaisuudet. Tekoäly päättää kullakin vuorolla liikkeensä siihen liitetyn Board-olion mukaan, käyttäen 8:n syvyistä alfa-beta-pruunausta. Tekoälyn ensimmäiset 2 siirtoa (kullekin pelaajalle) ovat satunnaisia, jotta vältyttäisiin joka pelissä samoilta lopputuloksilta.
* utilities-hakemisto sisältää ohjelman käyttämät tietorakenteet ja staattiset metodit, kuten ArrayListien järjestäminen. Javan vastaavien luokkien mukaan nimetyt luokat tekevät täsmälleen mitä niiltä odottaakin.  ZobristHash taas kykenee tuottamaan Player 2d-taulukolle uniikin 64 bittisen BigInteger-avaimen, jota käytän testauksessa. ZobristHashin antamat hashit sopisivat myös hyvin transpositiotaulun avaimeksi, mihin se on tarkoitettukin, mutta transpositiotauluja en saanut ajanpuutteessa toteutettua.
* App-luokan ainoa tehtävä on käynnistää ohjelma.
* MoveTransmitter ja TextUI välittävät yhdessä tekoälyn ja pelaajan siirtoja Board-oliolle. Luokat ovat toiminnaltaan hyvin yksinkertaisia ja lähinnä placeholdereita, joten niitä ei olla testattu.

Aika- ja tilavaativuudet
========================
* Aikavaativuus on tekoälyllä sama kuin alfa-beta-pruunauksella yleensä, eli suurinpiirtein O(b^(d/2)), missä b on keskimääräinen lasten määrä per solmu ja d on on haun syvyys. Omassa algoritmissani d on siis rekursiopuun syvyys, ja b on keskimääräinen olemassa olevien liikkeiden määrä kullakin vuorolla.
* Positioiden arvon laskeminen on melko triviaali operaatio joka ei vaikuta tekoälyn tehokkuuteen ratkaisevasti.
* Tilavaativuus on tekoälylle O(d*a), missä d on rekursiopuun syvyys, ja a on ArrayListiin keskimäärin talletettujen siirtojen lukumäärä.
* Tietorakenteiden perusoperaatioiden vaativuudet vastaavat näkemäkseni teoreettisia.
* ArrayListien järjestämiseen on käytetty mergesorttia, aikavaativuus O(n + nlogn) = O(nlogn).


Lähteet
=======
* http://chessprogramming.wikispaces.com/
* http://en.wikipedia.org/wiki/Computer_Othello
* http://radagast.se/othello/howto.html
