# Luku 3: Induktio ja rekursio

Luvussa 1 tapasit induktion: dominopalikkarivin, joka kaataa äärettömän monta väitettä yhdellä siirtymällä. Tässä luvussa syvennämme sen. Opit **vahvan induktion**, joka nojaa kaikkiin edellisiin askeliin kerralla; **hyvinjärjestysperiaatteen**, joka on induktio peilikuvana; ja **rekursion**, jolla ääretön jono määritellään yhdellä siemenellä ja yhdellä säännöllä.

Nämä kolme ovat saman idean kolme kasvoa: **äärettömän hallinta askel askeleelta.**

---

## 3.1 Tavallinen induktio kertauksena

Muistutuksena luvusta 1:

!!! note "Induktioperiaate"
    Väite $P(n)$ pätee kaikilla $n \geq n_0$, jos:

    1. **Perusaskel:** $P(n_0)$ on tosi.
    2. **Induktioaskel:** $P(n) \Rightarrow P(n+1)$ kaikilla $n \geq n_0$.

Sovelletaan sitä heti kauniiseen tulokseen, joka koskee Fibonaccin lukuja. Nämä määritellään säännöllä

$$F_1 = 1, \quad F_2 = 1, \quad F_n = F_{n-1} + F_{n-2} \; (n \geq 3),$$

joten jono on $1, 1, 2, 3, 5, 8, 13, 21, \ldots$

!!! abstract "Lause 3.1"
    Ensimmäisten $n$ Fibonaccin luvun summa on
    $$F_1 + F_2 + \cdots + F_n = F_{n+2} - 1.$$

**Todistus.**

*Perusaskel.* $n = 1$: vasen puoli $= F_1 = 1$, oikea puoli $= F_3 - 1 = 2 - 1 = 1$. Täsmää.

*Induktioaskel.* Oletetaan väite luvulla $n$. Lisätään $F_{n+1}$:

$$\underbrace{F_1 + \cdots + F_n}_{=\,F_{n+2}-1} + F_{n+1} = (F_{n+2} - 1) + F_{n+1} = (F_{n+1} + F_{n+2}) - 1 = F_{n+3} - 1,$$

missä viimeinen askel käytti Fibonaccin sääntöä $F_{n+1} + F_{n+2} = F_{n+3}$. Tämä on väite luvulla $n+1$. $\blacksquare$

---

## 3.2 Vahva induktio

Joskus askel $P(n+1)$ ei seuraa pelkästään edellisestä askelesta $P(n)$, vaan tarvitsee *useita* aiempia — ehkä kaikkia. Tähän on oma muotonsa.

!!! note "Vahva induktio"
    Väite $P(n)$ pätee kaikilla $n \geq n_0$, jos:

    1. **Perusaskel:** $P(n_0)$ on tosi.
    2. **Induktioaskel:** jos $P(k)$ on tosi *kaikilla* $n_0 \leq k \leq n$, niin $P(n+1)$ on tosi.

Ero tavalliseen: induktio-oletuksena saat käyttää **kaikkia** aiempia tapauksia, et vain viimeisintä. Dominovertaus: palikan $n+1$ kaatamiseen saa nojata kaikkiin jo kaatuneisiin palikoihin.

Klassinen sovellus on lukuteorian peruskiven puolikas:

!!! abstract "Lause 3.2"
    Jokainen kokonaisluku $n \geq 2$ voidaan kirjoittaa alkulukujen tulona.

**Todistus (vahva induktio).**

*Perusaskel.* $n = 2$ on itse alkuluku, siis "yhden alkuluvun tulo". ✓

*Induktioaskel.* Oletetaan, että jokainen luku väliltä $2, 3, \ldots, n$ on alkulukujen tulo. Tarkastellaan lukua $n+1$. Kaksi tapausta:

- **$n+1$ on alkuluku.** Silloin se on triviaalisti oma tulonsa. Valmis.
- **$n+1$ ei ole alkuluku.** Silloin se hajoaa $n+1 = a \cdot b$, missä $2 \leq a, b \leq n$. Molemmat tekijät ovat välillä, jossa induktio-oletus pätee, joten kumpikin on alkulukujen tulo. Yhdistämällä nämä tulot saadaan luvun $n+1$ alkulukuesitys.

Kummassakin tapauksessa $n+1$ on alkulukujen tulo. $\blacksquare$

Huomaa, **miksi tässä tarvittiin vahvaa induktiota:** tekijät $a$ ja $b$ voivat olla mitä tahansa lukua $n+1$ pienempiä — ei välttämättä $n$. Tavallinen induktio, joka nojaa vain edelliseen askeleen, ei riittäisi.

!!! tip "Milloin kumpi?"
    Käytä **tavallista** induktiota, kun askel $n+1$ rakentuu suoraan askelesta $n$ (summat, epäyhtälöt). Käytä **vahvaa**, kun $n+1$ hajoaa pienemmiksi paloiksi, joiden koko ei ole ennustettavissa (tekijöihinjako, rekursiot, jotka viittaavat kauas taakse).

---

## 3.3 Hyvinjärjestysperiaate

Induktiolla on peilikuva, joka näyttää aluksi täysin eri väitteeltä mutta on loogisesti sen kanssa yhtäpitävä.

!!! note "Hyvinjärjestysperiaate"
    Jokaisella luonnollisten lukujen **epätyhjällä** osajoukolla on **pienin alkio**.

Tämä tuntuu itsestäänselvältä — ja se on totta luonnollisille luvuille. Mutta huomaa, ettei se päde kaikille lukujoukoille: positiivisilla rationaaliluvuilla ei ole pienintä alkiota (mikä tahansa ehdokas $q$ voidaan puolittaa: $q/2$ on pienempi ja yhä positiivinen). Hyvinjärjestys on erityisesti kokonaislukujen ominaisuus, ja se on yllättävän voimakas todistusväline.

!!! abstract "Lause 3.3"
    Ei ole olemassa kokonaislukua välillä $0 < n < 1$.

**Todistus.** Oletetaan vastakohta: joukko $S = \{\, n \in \mathbb{Z} \mid 0 < n < 1 \,\}$ on epätyhjä. Silloin hyvinjärjestysperiaatteen nojalla sillä on pienin alkio; kutsutaan sitä $m$:ksi, ja $0 < m < 1$.

Kerrotaan epäyhtälö $m < 1$ puolittain positiivisella luvulla $m$: saadaan $m^2 < m$. Toisaalta $m > 0$ antaa $m^2 > 0$. Siis $0 < m^2 < m < 1$, joten myös $m^2$ kuuluu joukkoon $S$ — mutta $m^2 < m$, mikä on ristiriita sen kanssa, että $m$ oli pienin. Joukko $S$ on siis tyhjä. $\blacksquare$

Hyvinjärjestys antaa myös **vaihtoehtoisen todistuksen** tutulle tulokselle — ja se on opettavainen:

!!! abstract "Lause 3.4"
    $\sqrt{2}$ on irrationaalinen. *(Toinen todistus.)*

**Todistus (hyvinjärjestys).** Oletetaan vastakohta: $\sqrt2 = \frac{a}{b}$ jollakin positiivisilla kokonaisluvuilla. Silloin joukko

$$S = \{\, b \in \mathbb{Z}^+ \mid b\sqrt2 \in \mathbb{Z} \,\}$$

on epätyhjä (se sisältää yllä olevan $b$:n). Hyvinjärjestysperiaatteen nojalla sillä on pienin alkio $q$. Merkitään $p = q\sqrt2$ (kokonaisluku).

Muodostetaan nyt pienempi jäsen. Olkoon $q' = p - q = q\sqrt2 - q = q(\sqrt2 - 1)$. Koska $1 < \sqrt2 < 2$, on $0 < \sqrt2 - 1 < 1$, joten $0 < q' < q$. Lisäksi $q'$ on kokonaisluku ($p$ ja $q$ ovat), ja

$$q'\sqrt2 = (p - q)\sqrt2 = p\sqrt2 - q\sqrt2 = 2q - p,$$

joka on myös kokonaisluku. Siis $q' \in S$ mutta $q' < q$ — ristiriita sen kanssa, että $q$ oli pienin. $\blacksquare$

Sama totuus, täysin eri ase. Tämä on hyvä muistutus: matemaattisella tuloksella voi olla monta todistusta, ja jokainen valaisee sitä eri suunnasta.

!!! tip "Induktio ja hyvinjärjestys ovat sama asia"
    Voidaan todistaa, että induktioperiaate ja hyvinjärjestysperiaate ovat *loogisesti yhtäpitäviä* — kummasta tahansa seuraa toinen. Ne ovat saman äärettömän rakenteen kaksi ilmaisua: "rakennetaan ylöspäin pienimmästä" (induktio) ja "ei voi laskeutua ikuisesti alaspäin" (hyvinjärjestys).

---

## 3.4 Rekursio

Tähän asti olemme *todistaneet* väitteitä äärettömän monelle luvulle. Rekursio kääntää saman idean *määrittelyyn*: kuinka annetaan sääntö äärettömälle jonolle rajallisin sanoin.

!!! note "Rekursiivinen määritelmä"
    Jono määritellään **rekursiivisesti**, kun annetaan:

    1. **alkuarvo(t)** (siemen), ja
    2. **sääntö**, joka kertoo jäsenen aiempien jäsenten avulla.

Olet jo nähnyt kaksi esimerkkiä:

$$n! : \quad 0! = 1, \quad n! = n \cdot (n-1)! \qquad\qquad F_n : \quad F_1 = F_2 = 1, \quad F_n = F_{n-1} + F_{n-2}.$$

Rekursio ja induktio ovat toistensa peilikuvat: rekursio *rakentaa* jonon ylöspäin siemenestä, induktio *todistaa* siitä väitteitä ylöspäin perusaskelesta. Siksi rekursiivisesti määriteltyjen olioiden ominaisuudet todistetaan lähes aina induktiolla — rakenteet sopivat yhteen kuin lukko ja avain.

Todistetaan kaunis Fibonacci-identiteetti, jota tutkit jo päiväkirjassasi:

!!! abstract "Lause 3.5 (Cassinin identiteetti)"
    Kaikilla $n \geq 2$:
    $$F_{n-1}\,F_{n+1} - F_n^2 = (-1)^n.$$

**Todistus (induktio).**

*Perusaskel.* $n = 2$: $\;F_1 F_3 - F_2^2 = 1 \cdot 2 - 1^2 = 1 = (-1)^2$. ✓

*Induktioaskel.* Oletetaan $F_{n-1}F_{n+1} - F_n^2 = (-1)^n$. Todistetaan väite luvulla $n+1$, eli $F_n F_{n+2} - F_{n+1}^2 = (-1)^{n+1}$. Käytetään Fibonaccin sääntöä $F_{n+2} = F_{n+1} + F_n$ ja $F_{n+1} = F_n + F_{n-1}$:

$$F_n F_{n+2} - F_{n+1}^2 = F_n(F_{n+1} + F_n) - F_{n+1}^2 = F_n F_{n+1} + F_n^2 - F_{n+1}^2.$$

Kirjoitetaan $F_{n+1}^2 = F_{n+1}(F_n + F_{n-1}) = F_{n+1}F_n + F_{n+1}F_{n-1}$ ja sijoitetaan:

$$= F_n F_{n+1} + F_n^2 - F_{n+1}F_n - F_{n+1}F_{n-1} = F_n^2 - F_{n-1}F_{n+1} = -\big(F_{n-1}F_{n+1} - F_n^2\big) = -(-1)^n = (-1)^{n+1}.$$

Induktio on valmis. $\blacksquare$

Cassinin identiteetti on itsessään hämmästyttävä: kahden Fibonaccin luvun tulon ja keskimmäisen neliön ero on *aina* täsmälleen $\pm 1$, ikuisesti — vaikka luvut itse kasvavat rajatta. Juuri tähän perustuu kuuluisa "kadonneen neliön" paloittelupetkutus.

---

## 3.5 Yhteenveto

- **Tavallinen induktio:** $P(n) \Rightarrow P(n+1)$. Käytä, kun askel rakentuu edellisestä.
- **Vahva induktio:** kaikki tapaukset $\leq n$ $\Rightarrow P(n+1)$. Käytä, kun $n+1$ hajoaa ennustamattoman kokoisiksi paloiksi.
- **Hyvinjärjestys:** jokaisella epätyhjällä $\mathbb{N}$:n osajoukolla on pienin alkio. Voimakas ristiriitaväline; yhtäpitävä induktion kanssa.
- **Rekursio** määrittelee äärettömän jonon siemenellä ja säännöllä; sen ominaisuudet todistetaan induktiolla.

---

## Harjoitukset

**3.1 (★)** Todista induktiolla: $1 + 3 + 5 + \cdots + (2n-1) = n^2$ (ensimmäisten $n$ parittoman luvun summa).

??? tip "Vihje"
    Induktioaskel: lisää seuraava pariton luku, joka on $2(n+1) - 1 = 2n+1$, summaan $n^2$.

??? success "Vastaus"
    *Perusaskel.* $n=1$: vasen $=1$, oikea $=1^2=1$. ✓

    *Induktioaskel.* Oletetaan $1 + 3 + \cdots + (2n-1) = n^2$. Lisätään seuraava pariton luku $2n+1$:
    $$\underbrace{1 + \cdots + (2n-1)}_{=\,n^2} + (2n+1) = n^2 + 2n + 1 = (n+1)^2.$$
    Tämä on kaava luvulla $n+1$. $\blacksquare$

    *(Kaunis geometrinen tulkinta: parittomat luvut rakentavat neliön kuori kuorelta.)*

---

**3.2 (★★)** Todista induktiolla Fibonaccin luvuille: $F_1^2 + F_2^2 + \cdots + F_n^2 = F_n F_{n+1}$.

??? tip "Vihje"
    Induktioaskeleessa lisää $F_{n+1}^2$ ja ota $F_{n+1}$ yhteiseksi tekijäksi. Muista $F_n + F_{n+1} = F_{n+2}$.

??? success "Vastaus"
    *Perusaskel.* $n=1$: vasen $= F_1^2 = 1$, oikea $= F_1 F_2 = 1 \cdot 1 = 1$. ✓

    *Induktioaskel.* Oletetaan $F_1^2 + \cdots + F_n^2 = F_n F_{n+1}$. Lisätään $F_{n+1}^2$:
    $$\underbrace{F_1^2 + \cdots + F_n^2}_{=\,F_n F_{n+1}} + F_{n+1}^2 = F_n F_{n+1} + F_{n+1}^2 = F_{n+1}(F_n + F_{n+1}) = F_{n+1}F_{n+2}.$$
    Tämä on väite luvulla $n+1$. $\blacksquare$

---

**3.3 (★★)** Todista vahvalla induktiolla: jokainen luonnollinen luku $n \geq 8$ voidaan kirjoittaa muodossa $3a + 5b$, missä $a, b$ ovat ei-negatiivisia kokonaislukuja. *(Esim. $8 = 3+5$, $9 = 3+3+3$, $10 = 5+5$.)*

??? tip "Vihje"
    Todista perusaskelina *kolme* peräkkäistä tapausta: $n = 8, 9, 10$. Sen jälkeen induktioaskeleessa: jos väite pätee luvulle $n-3$, lisää yksi kolmonen saadaksesi luvun $n$. Miksi tarvitset kolme perusaskelta?

??? success "Vastaus"
    *Perusaskeleet.* $8 = 3 + 5$, $9 = 3+3+3$, $10 = 5 + 5$. ✓ (Kaikki kolme tarvitaan, koska induktioaskel nojaa kolmen päähän taakse.)

    *Induktioaskel.* Olkoon $n \geq 11$, ja oletetaan väite todeksi kaikille luvuille väliltä $8, \ldots, n-1$. Erityisesti $n - 3 \geq 8$, joten $n - 3 = 3a + 5b$ jollakin ei-negatiivisilla $a, b$. Silloin
    $$n = (n-3) + 3 = 3(a+1) + 5b,$$
    mikä on haluttua muotoa. $\blacksquare$

    *(Kolme perusaskelta tarvitaan, koska askel laskee kolme taaksepäin: luvun $n$ saavuttamiseksi tarvitaan $n-3$, ja ketju $8, 11, 14, \ldots$; $9, 12, \ldots$; $10, 13, \ldots$ kattaa kaikki luvut vasta kolmella lähtöpisteellä.)*

---

**3.4 (★★)** Käytä hyvinjärjestysperiaatetta: todista, ettei ole olemassa kokonaislukujonoa $n_1 > n_2 > n_3 > \cdots$, joka olisi aidosti vähenevä ja koostuisi pelkistä positiivisista kokonaisluvuista (ääretön laskeva ketju).

??? tip "Vihje"
    Oleta, että tällainen jono on olemassa, ja tarkastele sen jäsenten muodostamaa joukkoa.

??? success "Vastaus"
    Oletetaan vastakohta: on olemassa aidosti vähenevä ääretön jono positiivisia kokonaislukuja $n_1 > n_2 > n_3 > \cdots$. Tarkastellaan joukkoa $S = \{n_1, n_2, n_3, \ldots\}$, joka on epätyhjä positiivisten kokonaislukujen osajoukko. Hyvinjärjestysperiaatteen nojalla sillä on pienin alkio $n_k$. Mutta jonossa on jäsen $n_{k+1}$, ja $n_{k+1} < n_k$ — ristiriita sen kanssa, että $n_k$ oli pienin. Tällaista jonoa ei siis ole. $\blacksquare$

    *(Tämä "ei ääretöntä laskua" on hyvinjärjestyksen ydin, ja se on monen algoritmin päättymistodistuksen perusta.)*

---

**3.5 (★★★)** Määritellään jono rekursiivisesti: $a_1 = 1$ ja $a_{n+1} = \sqrt{2 + a_n}$. Todista induktiolla, että $a_n < 2$ kaikilla $n \geq 1$. *(Tämä jono liittyy sisäkkäisiin juuriin $\sqrt{2 + \sqrt{2 + \cdots}}$.)*

??? tip "Vihje"
    Induktioaskel: oleta $a_n < 2$. Näytä, että silloin $a_{n+1} = \sqrt{2 + a_n} < 2$ arvioimalla neliöjuuren sisältöä.

??? success "Vastaus"
    *Perusaskel.* $a_1 = 1 < 2$. ✓

    *Induktioaskel.* Oletetaan $a_n < 2$. Silloin
    $$2 + a_n < 2 + 2 = 4,$$
    ja koska neliöjuuri on kasvava funktio,
    $$a_{n+1} = \sqrt{2 + a_n} < \sqrt{4} = 2.$$
    Siis $a_{n+1} < 2$, ja väite pätee kaikilla $n$. $\blacksquare$

    *(Sivuhuomio: voidaan lisäksi osoittaa, että jono on kasvava, joten se suppenee. Rajaksi tulee tasan $2$ — sama sisäkkäisen juuren arvo, jonka juurikaava antaa arvolla $n=2$. Suppeneminen todistetaan kunnolla luvussa 8.)*

---

*Seuraava luku: Luvuista — miten luonnollisista luvuista rakennetaan kokonais- ja rationaaliluvut, ja mihin ne eivät riitä.*
