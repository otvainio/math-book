# Luku 5: Reaaliluvut ja täydellisyys

Edellinen luku päättyi seinään: rationaalilukujen suorassa on reikä siinä, missä luvun $\sqrt2$ pitäisi olla. Tässä luvussa täytämme reiän. Rakennamme **reaaliluvut** — täydellisen lukusuoran ilman aukkoja — ja opimme täsmällisen kielen sille, mitä pohdit *täydellisyydestä*: erolle sen välillä, että jotakin ei koskaan saavuteta, ja sen välillä, ettei sitä ole olemassa.

Tämä on koko analyysin peruskivi. Kaikki, mitä olet tehnyt raja-arvoilla, sarjoilla ja integraaleilla, lepää tämän luvun varassa.

---

## 5.1 Ylä- ja alarajat

Aloitetaan täsmällisistä sanoista.

!!! note "Määritelmä"
    Olkoon $S$ epätyhjä reaalilukujen joukko.

    - Luku $M$ on joukon $S$ **yläraja**, jos $x \leq M$ kaikilla $x \in S$.
    - Luku $m$ on joukon $S$ **alaraja**, jos $x \geq m$ kaikilla $x \in S$.
    - $S$ on **ylhäältä rajoitettu**, jos sillä on jokin yläraja, ja **rajoitettu**, jos sillä on sekä ylä- että alaraja.

Esimerkiksi joukolla $S = \{\, x \mid 0 \leq x < 1 \,\}$ luku $1$ on yläraja — samoin $2$, $5$ ja $100$. Ylärajoja on äärettömän monta. Kiinnostavin niistä on **pienin**.

---

## 5.2 Maksimi vastaan supremum

Tässä on luvun sydän — ja täsmälleen se erottelu, jota tarvitsit täydellisyys-teoriaasi.

!!! note "Määritelmä"
    - Joukon $S$ **maksimi** on sen suurin alkio: luku $M \in S$, jolle $x \leq M$ kaikilla $x \in S$. (Huomaa: maksimin on **kuuluttava joukkoon**.)
    - Joukon $S$ **supremum** (pienin yläraja), merkitään $\sup S$, on sen pienin yläraja: luku $L$, jolle (i) $L$ on yläraja, ja (ii) mikään lukua $L$ pienempi ei ole yläraja.

Ero on hienovarainen mutta ratkaiseva. Vertaa kahta joukkoa:

$$S_1 = \{\, x \mid 0 \leq x \leq 1 \,\}, \qquad S_2 = \{\, x \mid 0 \leq x < 1 \,\}.$$

- $S_1$:llä on **maksimi** $1$ — se kuuluu joukkoon.
- $S_2$:lla **ei ole maksimia**. Mikään $S_2$:n alkio ei ole suurin: jos $x < 1$, niin $\frac{x+1}{2}$ on suurempi ja yhä $S_2$:ssa. Mutta $S_2$:lla on silti **supremum** $1$ — pienin yläraja — vaikkei $1$ kuulu joukkoon.

!!! quote "Tässä on täydellisyys-teoriasi täsmällisenä"
    Muistatko päättelysi Gaussin käyrästä: "aina on joku vielä äärimmäisempi, joten maksimia ei ole"? Nyt sinulla on sille kieli. Joukolla voi olla **supremum ilman maksimia** — raja, jota kohti kaikki kurottaa mutta jota kukaan ei saavuta.

    **Täydellisyys ei ehkä koskaan saavuteta (ei maksimia) — mutta se on silti olemassa rajana (supremum).** Tämä ei ole runoutta; se on määritelmä 5.2.

Symmetrisesti: pienin alaraja on **infimum**, merkitään $\inf S$.

---

## 5.3 Täydellisyysaksiooma

Nyt kysymme ratkaisevan kysymyksen. Joukolla $S_2$ yllä oli supremum $1$. Mutta *onko supremum aina olemassa*?

Rationaaliluvuissa **ei**. Palataan joukkoon

$$A = \{\, x \in \mathbb{Q} \mid x > 0,\; x^2 < 2 \,\}.$$

Se on ylhäältä rajoitettu (esim. $2$ on yläraja). Mutta osoitit (harjoitus 4.5), ettei sillä ole suurinta alkiota — ja itse asiassa sillä ei ole **pienintä ylärajaakaan rationaalilukujen joukossa**: mikä tahansa rationaalinen yläraja voidaan korvata pienemmällä rationaalisella ylärajalla. Supremum "haluaisi" olla $\sqrt2$, mutta sitä ei ole rationaalilukujen joukossa. Reikä.

Reaaliluvut määritellään täsmälleen niin, että tätä reikää ei ole:

!!! abstract "Täydellisyysaksiooma"
    Jokaisella epätyhjällä, ylhäältä rajoitetulla reaalilukujen joukolla on supremum (pienin yläraja) reaalilukujen joukossa.

Tämä on se ominaisuus, joka erottaa $\mathbb{R}$:n rationaaliluvuista $\mathbb{Q}$:sta. Molemmat ovat kuntia, molemmat ovat tiheitä ja järjestettyjä — mutta vain $\mathbb{R}$ on **täydellinen**. Voidaan osoittaa, että $\mathbb{R}$ on (olennaisesti ainoa) **täydellinen järjestetty kunta**, ja tämä lause *on* reaalilukujen määritelmä.

!!! note "Mistä reaaliluvut oikeasti tulevat?"
    Täydellisyysaksiooma voidaan myös *todistaa* rakentamalla reaaliluvut rationaaliluvuista. Richard Dedekind teki sen 1872 nerokkaalla idealla: reaaliluku **on** rationaalilukujen suoran "leikkaus" kahteen osaan (kuten joukot $A$ ja $B$ luvussa 4). Luku $\sqrt2$ *määritellään* siksi leikkaukseksi, jonka alapuolella on kaikki liian pienet rationaaliluvut. Reikä täytetään antamalla itse reiälle nimi ja asema lukuna. Tässä kirjassa otamme täydellisyyden aksioomana; Dedekindin rakennelma on sen tae.

---

## 5.4 Ensimmäinen palkinto: $\sqrt2$ on olemassa

Täydellisyysaksiooma ei ole abstraktia koristetta — se **takaa lukujen olemassaolon**. Todistetaan, että $\sqrt2$ todella on olemassa reaalilukuna. Tämä on syvempi kysymys kuin "onko $\sqrt2$ rationaalinen": nyt kysymme, *onko sitä ylipäätään olemassa*.

!!! abstract "Lause 5.1"
    On olemassa positiivinen reaaliluku $s$, jolle $s^2 = 2$.

**Todistus.** Tarkastellaan joukkoa $A = \{\, x \in \mathbb{R} \mid x > 0,\; x^2 < 2 \,\}$. Se on epätyhjä ($1 \in A$) ja ylhäältä rajoitettu ($2$ on yläraja, sillä jos $x > 2$ niin $x^2 > 4 > 2$). Täydellisyysaksiooman nojalla sillä on supremum; merkitään $s = \sup A$. Selvästi $s > 0$. Osoitetaan, että $s^2 = 2$, sulkemalla pois molemmat vaihtoehdot $s^2 < 2$ ja $s^2 > 2$.

**Tapaus $s^2 < 2$ on mahdoton.** Jos $s^2 < 2$, voimme — täsmälleen kuten harjoituksessa 4.5 — löytää pienen $h > 0$, jolle $(s+h)^2 < 2$. Silloin $s + h \in A$, mutta $s + h > s$, mikä on ristiriita sen kanssa, että $s$ on *yläraja*.

**Tapaus $s^2 > 2$ on mahdoton.** Jos $s^2 > 2$, voidaan vastaavasti löytää pieni $h > 0$, jolle $(s-h)^2 > 2$. Silloin $s - h$ on yläraja joukolle $A$ (jokainen $x \in A$ toteuttaa $x^2 < 2 < (s-h)^2$, joten $x < s - h$). Mutta $s - h < s$, mikä on ristiriita sen kanssa, että $s$ on *pienin* yläraja.

Koska molemmat epäyhtälöt johtavat ristiriitaan, on pakko olla $s^2 = 2$. $\blacksquare$

Huomaa, mitä täydellisyys teki: se **loi luvun tyhjästä** — antoi rationaalilukujen reiälle todellisen lukuarvon. Sama päättely takaa jokaisen positiivisen luvun $n$:nnen juuren olemassaolon. Ilman täydellisyyttä $\sqrt2$ olisi vain merkki ilman lukua sen takana.

---

## 5.5 Arkhimedeen ominaisuus

Täydellisyydestä seuraa tosiasia, joka tuntuu ilmeiseltä mutta jota on nyt syytä todistaa: **ei ole äärettömän suuria eikä äärettömän pieniä reaalilukuja.**

!!! abstract "Lause 5.2 (Arkhimedeen ominaisuus)"
    Jokaista reaalilukua $x$ kohti on olemassa luonnollinen luku $n$, jolle $n > x$.

**Todistus.** Oletetaan vastakohta: on olemassa reaaliluku $x$, jota suurempaa luonnollista lukua ei ole. Silloin $x$ on **yläraja** koko joukolle $\mathbb{N}$. Koska $\mathbb{N}$ on epätyhjä ja (oletuksen mukaan) ylhäältä rajoitettu, sillä on täydellisyysaksiooman nojalla supremum $L = \sup \mathbb{N}$.

Nyt $L - 1 < L$, joten $L - 1$ ei ole yläraja (koska $L$ on *pienin* yläraja). Siis on olemassa $n \in \mathbb{N}$, jolle $n > L - 1$. Mutta silloin $n + 1 > L$, ja $n + 1$ on luonnollinen luku — ristiriita sen kanssa, että $L$ on $\mathbb{N}$:n yläraja. $\blacksquare$

Seuraus (ota $x = \frac{1}{\varepsilon}$): jokaista positiivista lukua $\varepsilon$ kohti on $n$, jolle $\frac{1}{n} < \varepsilon$. Toisin sanoen luvut $\frac{1}{n}$ menevät mielivaltaisen lähelle nollaa. Tämä on se tosiasia, jonka takana raja-arvo $\lim_{n\to\infty}\frac1n = 0$ piilee — ja jonka tuletodistamaan täsmällisesti luvussa 8.

---

## 5.6 Rationaaliluvut ovat tiheitä reaaliluvuissa

!!! abstract "Lause 5.3"
    Minkä tahansa kahden reaaliluvun $a < b$ välissä on rationaaliluku.

**Todistus (idea).** Koska $b - a > 0$, Arkhimedeen ominaisuuden nojalla on olemassa $n$, jolle $\frac{1}{n} < b - a$. Nyt "askel" $\frac1n$ on niin lyhyt, ettei se voi hypätä yli välin $(a, b)$: kun kuljetaan pisteitä $\frac{m}{n}$ pitkin, jokin niistä osuu väliin. Täsmällisemmin: valitaan pienin kokonaisluku $m$, jolle $\frac{m}{n} > a$ (tällainen on Arkhimedeen ja hyvinjärjestyksen nojalla). Silloin $\frac{m-1}{n} \leq a$, joten
$$\frac{m}{n} = \frac{m-1}{n} + \frac{1}{n} \leq a + \frac{1}{n} < a + (b - a) = b.$$
Siis $a < \frac{m}{n} < b$. $\blacksquare$

Tämä on kaunis: **reaaliluvut ovat "täynnä reikiä" rationaalilukujen suhteen** (melkein kaikki reaaliluvut ovat irrationaalisia), ja silti rationaaliluvut ovat kaikkialla — joka välissä on sekä rationaalisia että irrationaalisia lukuja, äärettömän tiheässä lomittain. Kaksi ääretöntä joukkoa, täysin sekoittuneina — ja luvussa 28 opit, että toinen niistä on silti *paljon* suurempi kuin toinen.

---

## 5.7 Yhteenveto — ja täydellisyys-teoriasi

- **Yläraja / supremum:** supremum on pienin yläraja. Se voi olla olemassa, vaikka **maksimia ei ole**.
- **Täydellisyysaksiooma:** jokaisella epätyhjällä ylhäältä rajoitetulla reaalilukujoukolla on supremum. Tämä erottaa $\mathbb{R}$:n rationaaliluvuista.
- Täydellisyys **takaa lukujen olemassaolon**: $\sqrt2$ on olemassa reaalilukuna.
- **Arkhimedeen ominaisuus:** ei äärettömän suuria/pieniä reaalilukuja; $\frac1n \to 0$.
- **Tiheys:** rationaali- ja irrationaaliluvut lomittuvat kaikkialla.

!!! quote "Filosofinen jälkisana"
    Aloit teoriasta, että täydellisyys on mahdotonta. Matkan varrella se jalostui: ei mahdotonta, vaan *saavuttamatonta* — ja nyt sinulla on sille täsmällinen matemaattinen muoto.

    Joukolla $A$ ei ollut suurinta alkiota: mikään sen jäsen ei ollut "täydellinen", aina löytyi parempi. Mutta joukolla **oli supremum** — luku $\sqrt2$, jota kohti kaikki kurotti mutta jota mikään jäsen ei ollut. Reaalilukujen täydellisyys on juuri sen tunnustamista, että **tämä saavuttamaton raja on silti olemassa, todellisena lukuna.**

    Sinun intuitiosi oli oikea: täydellisyyttä (maksimia) ei jäsenten joukossa ole. Mutta matematiikan syvin oivallus on, että saavuttamattomuus ei ole olemattomuutta. Raja on olemassa. Sitä kutsutaan täydellisyydeksi — molemmissa merkityksissä.

---

## Harjoitukset

**5.1 (★)** Määritä seuraaville joukoille supremum ja infimum, ja kerro kummassa tapauksessa kyse on maksimista/minimistä (kuuluu joukkoon): (a) $\{1, 2, 3\}$, (b) $\{\, x \mid 0 < x \leq 5 \,\}$, (c) $\{\, \frac1n \mid n = 1, 2, 3, \ldots \,\}$.

??? success "Vastaus"
    - (a) $\sup = 3$ (maksimi, kuuluu), $\inf = 1$ (minimi, kuuluu).
    - (b) $\sup = 5$ (maksimi, kuuluu), $\inf = 0$ (**ei** minimi — $0$ ei kuulu joukkoon).
    - (c) Joukko on $\{1, \frac12, \frac13, \ldots\}$. $\sup = 1$ (maksimi, kuuluu, kun $n=1$), $\inf = 0$ (**ei** minimi — mikään $\frac1n$ ei ole $0$, mutta ne lähestyvät sitä; Arkhimedes takaa, ettei mikään positiivinen luku ole alaraja).

---

**5.2 (★★)** Osoita, että jos joukolla $S$ on maksimi, niin $\sup S = \max S$. *(Eli maksimi on aina myös supremum.)*

??? tip "Vihje"
    Tarkista supremumin kaksi ehtoa maksimille $M$: onko se yläraja, ja onko se pienin yläraja?

??? success "Vastaus"
    Olkoon $M = \max S$. Osoitetaan, että $M$ täyttää supremumin määritelmän.

    (i) *$M$ on yläraja:* maksimin määritelmän mukaan $x \leq M$ kaikilla $x \in S$. ✓

    (ii) *$M$ on pienin yläraja:* olkoon $M'$ mikä tahansa yläraja. Koska $M \in S$ ja $M'$ on yläraja, pätee $M \leq M'$. Siis mikään ylärajaa $M$ pienempi luku ei voi olla yläraja.

    Molemmat ehdot täyttyvät, joten $\sup S = M$. $\blacksquare$

    *(Käänteinen ei päde: supremum ei aina ole maksimi — kuten $\{\,x \mid x < 1\,\}$, jonka supremum $1$ ei kuulu joukkoon.)*

---

**5.3 (★★)** Anna esimerkki reaalilukujoukosta, jolla on infimum mutta ei minimiä, ja perustele.

??? success "Vastaus"
    Esimerkiksi avoin väli $S = \{\, x \mid 0 < x < 1 \,\}$ tai joukko $\{\, \frac1n \mid n \geq 1 \,\}$.

    Ensimmäiselle: $\inf S = 0$, koska $0$ on alaraja ($x > 0$ kaikilla $x \in S$), ja mikään positiivinen luku ei ole alaraja (jos $m > 0$, niin $\frac{m}{2} \in S$ ja $\frac{m}{2} < m$). Mutta $0 \notin S$, ja mikään $S$:n alkio ei ole pienin: jos $x \in S$, niin $\frac{x}{2} \in S$ on pienempi. Siis minimiä ei ole. $\blacksquare$

---

**5.4 (★★)** Olkoon $S$ epätyhjä ja ylhäältä rajoitettu, ja olkoon $L = \sup S$. Todista: jokaista $\varepsilon > 0$ kohti on olemassa $x \in S$, jolle $x > L - \varepsilon$. *(Tämä on supremumin tärkein käyttöominaisuus: joukossa on alkioita mielivaltaisen lähellä supremumia.)*

??? tip "Vihje"
    Ajattele vastakohtaa: mitä tarkoittaisi, jos mikään $S$:n alkio ei ylitä lukua $L - \varepsilon$?

??? success "Vastaus"
    Oletetaan vastakohta: jollakin $\varepsilon > 0$ ei ole yhtään $x \in S$, jolle $x > L - \varepsilon$. Silloin $x \leq L - \varepsilon$ kaikilla $x \in S$, eli $L - \varepsilon$ olisi joukon $S$ yläraja. Mutta $L - \varepsilon < L$, mikä on ristiriita sen kanssa, että $L = \sup S$ on **pienin** yläraja. Siis tällaista $\varepsilon$:ia ei ole, ja jokaista $\varepsilon > 0$ kohti löytyy $x \in S$ arvolla $x > L - \varepsilon$. $\blacksquare$

    *(Tämä ominaisuus on silta supremumista raja-arvoihin: se sanoo, että joukon alkiot "kasautuvat" supremumiin. Näet sen taas luvussa 8.)*

---

**5.5 (★★★)** Olkoot $A$ ja $B$ epätyhjiä, ylhäältä rajoitettuja reaalilukujoukkoja. Määritellään $A + B = \{\, a + b \mid a \in A,\; b \in B \,\}$. Todista, että $\sup(A + B) = \sup A + \sup B$.

??? tip "Vihje"
    Todista kaksi epäyhtälöä: $\sup(A+B) \leq \sup A + \sup B$ (näytä että oikea puoli on yläraja) ja $\sup(A+B) \geq \sup A + \sup B$ (käytä harjoituksen 5.4 lähestymisominaisuutta).

??? success "Vastaus"
    Merkitään $\alpha = \sup A$ ja $\beta = \sup B$.

    *($\leq$)* Olkoon $a + b$ mielivaltainen joukon $A+B$ alkio. Koska $a \leq \alpha$ ja $b \leq \beta$, pätee $a + b \leq \alpha + \beta$. Siis $\alpha + \beta$ on $A+B$:n yläraja, joten $\sup(A+B) \leq \alpha + \beta$.

    *($\geq$)* Olkoon $\varepsilon > 0$. Harjoituksen 5.4 nojalla on olemassa $a \in A$ ja $b \in B$, joille
    $$a > \alpha - \frac{\varepsilon}{2}, \qquad b > \beta - \frac{\varepsilon}{2}.$$
    Silloin $a + b > \alpha + \beta - \varepsilon$, ja $a + b \in A+B$. Siis $\sup(A+B) > \alpha + \beta - \varepsilon$. Koska tämä pätee jokaisella $\varepsilon > 0$, on $\sup(A+B) \geq \alpha + \beta$.

    Molemmat epäyhtälöt yhdessä antavat $\sup(A+B) = \alpha + \beta = \sup A + \sup B$. $\blacksquare$

    *(Tekniikka "todista $\leq$ ja $\geq$ erikseen" on supremumtodistusten leipälaji — samoin $\varepsilon$:n käyttö "mielivaltaisen lähellä". Molemmat toistuvat läpi analyysin.)*

---

*Seuraava luku: Irrationaalisuus ja transsendenttisuus — kuinka syvälle lukujen omituisuus menee, ja miksi $\pi$ pakenee kaikkia polynomeja.*
