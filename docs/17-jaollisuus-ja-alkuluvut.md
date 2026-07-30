# Luku 17: Jaollisuus ja alkuluvut

Lukuteoria on "kokonaislukujen aritmetiikan syvä puoli" — ja se on vanhinta matematiikkaa, jota yhä tutkitaan aktiivisesti. Sen peruskysymys on yksinkertainen: *miten kokonaisluvut jakautuvat toisillaan, ja mitkä luvut ovat rakennuspalikoita?* Vastaus rakennuspalikoihin on **alkuluvut**, ja tämän luvun huipennus on lause, joka sanoo, että jokainen luku rakentuu niistä täsmälleen yhdellä tavalla. Kaikki nojaa yhteen työkaluun, jonka jo tapasit luvussa 15: **Bézout'n identiteettiin.**

---

## 17.1 Jaollisuus

!!! note "Määritelmä"
    Kokonaisluku $a$ **jakaa** luvun $b$, merkitään $a \mid b$, jos on olemassa kokonaisluku $k$, jolle $b = ak$. Sanotaan myös, että $b$ on $a$:n monikerta.

Esimerkiksi $3 \mid 12$ (koska $12 = 3\cdot4$), mutta $3 \nmid 7$. Perusominaisuudet seuraavat suoraan määritelmästä: jos $a \mid b$ ja $a \mid c$, niin $a \mid (b + c)$ ja yleisemmin $a \mid (bx + cy)$ kaikilla kokonaisluvuilla $x, y$. (Todistus: kirjoita $b = ak$, $c = am$, jolloin $bx + cy = a(kx + my)$.)

Kun jako ei mene tasan, jää jäännös:

!!! abstract "Lause 17.1 (jakoalgoritmi)"
    Jos $a$ ja $b > 0$ ovat kokonaislukuja, niin on olemassa yksikäsitteiset kokonaisluvut $q$ (osamäärä) ja $r$ (jäännös), joille
    $$a = bq + r, \qquad 0 \leq r < b.$$

Tämä on sama kuin polynomien jakoalgoritmi (luku 16), mutta kokonaisluvuille. Se on koko lukuteorian moottori — jäännös $r$ on aina pienempi kuin jakaja, ja tästä "pienenemisestä" seuraa kaikki.

---

## 17.2 Suurin yhteinen tekijä ja Eukleideen algoritmi

!!! note "Määritelmä"
    Lukujen $a$ ja $b$ **suurin yhteinen tekijä** $\gcd(a,b)$ on suurin kokonaisluku, joka jakaa molemmat. Jos $\gcd(a,b) = 1$, luvut ovat **suhteellisia alkulukuja** (keskenään jaottomia).

Suurin yhteinen tekijä lasketaan **Eukleideen algoritmilla** — vanhimmalla yhä käytössä olevalla algoritmilla (n. 300 eaa.). Se perustuu havaintoon, että yhteiset tekijät säilyvät jakojäännöksessä:

$$\gcd(a, b) = \gcd(b, r), \qquad \text{missä } a = bq + r.$$

Toistetaan tätä, kunnes jäännös on nolla — viimeinen nollasta eroava jäännös on $\gcd$. Esimerkki, $\gcd(48, 18)$:

$$48 = 2\cdot18 + 12, \quad 18 = 1\cdot12 + 6, \quad 12 = 2\cdot6 + 0 \implies \gcd(48,18) = 6.$$

Algoritmi päättyy aina, koska jäännökset pienenevät — ja luonnollisten lukujen laskeva jono ei voi jatkua ikuisesti (hyvinjärjestysperiaate, luku 3). Lukuteoria ja luvun 3 äärettömyystyökalut kohtaavat.

---

## 17.3 Bézout'n identiteetti

Nyt luvun ratkaiseva työkalu — jonka jo käytit todistaessasi, että $\mathbb{Z}_p$ on kunta (luku 15). Todistetaan se nyt kunnolla.

!!! abstract "Lause 17.2 (Bézout)"
    Lukujen $a$ ja $b$ suurin yhteinen tekijä voidaan kirjoittaa niiden **lineaarikombinaationa**: on olemassa kokonaisluvut $x, y$, joille
    $$\gcd(a, b) = ax + by.$$

**Todistus (hyvinjärjestys).** Tarkastellaan joukkoa
$$S = \{\, ax + by \mid x, y \in \mathbb{Z},\; ax + by > 0 \,\}$$
kaikista positiivisista luvuista, jotka voidaan kirjoittaa muodossa $ax + by$. Joukko on epätyhjä, joten hyvinjärjestysperiaatteen (luku 3) nojalla sillä on pienin alkio $d = ax_0 + by_0$.

Väitetään, että $d = \gcd(a,b)$. Ensin: $d$ jakaa luvun $a$. Jakoalgoritmilla $a = dq + r$, missä $0 \leq r < d$. Silloin
$$r = a - dq = a - (ax_0 + by_0)q = a(1 - x_0 q) + b(-y_0 q),$$
joka on myös muotoa $a\cdot(\ldots) + b\cdot(\ldots)$. Jos $r > 0$, se olisi joukon $S$ alkio ja pienempi kuin $d$ — ristiriita. Siis $r = 0$, eli $d \mid a$. Vastaavasti $d \mid b$. Siis $d$ on yhteinen tekijä.

Lopuksi $d$ on **suurin** yhteinen tekijä: jos $c \mid a$ ja $c \mid b$, niin $c \mid (ax_0 + by_0) = d$, joten $c \leq d$. $\blacksquare$

Seuraus, jota tarvitaan heti: jos $\gcd(a,n) = 1$, niin $ax + ny = 1$ jollakin $x, y$ — ja tämä $x$ on $a$:n käänteisalkio modulo $n$. Juuri tämä teki luvusta $\mathbb{Z}_p$ kunnan.

---

## 17.4 Alkuluvut ja Eukleideen lemma

!!! note "Määritelmä"
    Ykköstä suurempi kokonaisluku $p$ on **alkuluku**, jos sen ainoat positiiviset tekijät ovat $1$ ja $p$ itse. Muut ($> 1$) ovat **yhdistettyjä lukuja**.

Alkuluvut ovat kertolaskun "atomit" — jakamattomat rakennuspalikat. Niiden ratkaiseva ominaisuus on:

!!! abstract "Lause 17.3 (Eukleideen lemma)"
    Jos $p$ on alkuluku ja $p \mid ab$, niin $p \mid a$ tai $p \mid b$.

**Todistus.** Oletetaan $p \mid ab$ mutta $p \nmid a$. Koska $p$ on alkuluku eikä jaa $a$:ta, on $\gcd(p, a) = 1$. Bézout'n nojalla $px + ay = 1$ joillakin $x, y$. Kerrotaan luvulla $b$:
$$pbx + aby = b.$$
Ensimmäinen termi on jaollinen $p$:llä, ja toinen termi $aby$ on jaollinen $p$:llä, koska $p \mid ab$. Siis $p \mid b$. $\blacksquare$

Tämä on hienovaraisempi kuin miltä näyttää — se **ei päde yhdistetyille luvuille!** Esimerkiksi $6 \mid (4 \cdot 9) = 36$, mutta $6 \nmid 4$ ja $6 \nmid 9$. Vain alkuluvuilla on tämä "jakamattomuus". Ja juuri se tekee alkuluvuista rakennuspalikoita.

---

## 17.5 Aritmetiikan peruslause

Luvun huipennus. Luvussa 3 osoitit vahvalla induktiolla, että jokainen luku *voidaan* hajottaa alkulukutuloksi. Nyt lisäämme, että hajotelma on **yksikäsitteinen**.

!!! abstract "Lause 17.4 (aritmetiikan peruslause)"
    Jokainen ykköstä suurempi kokonaisluku voidaan kirjoittaa alkulukujen tulona, ja tämä esitys on **yksikäsitteinen** tekijöiden järjestystä lukuun ottamatta.

**Todistus (yksikäsitteisyys).** Olemassaolo todistettiin luvussa 3. Yksikäsitteisyys: oletetaan, että luvulla on kaksi alkulukuesitystä
$$p_1 p_2 \cdots p_k = q_1 q_2 \cdots q_m.$$
Alkuluku $p_1$ jakaa vasemman puolen, joten se jakaa oikean puolen $q_1 \cdots q_m$. Eukleideen lemman (toistetusti) nojalla $p_1$ jakaa jonkin tekijän $q_j$ — ja koska $q_j$ on alkuluku, on $p_1 = q_j$. Supistetaan tämä pari pois molemmilta puolilta ja jatketaan. Lopulta kaikki tekijät pariutuvat, joten esitykset ovat samat. $\blacksquare$

!!! quote "Miksi yksikäsitteisyys ei ole itsestäänselvää"
    Että $12 = 2\cdot2\cdot3$ eikä mitenkään muuten tunuu ilmeiseltä — mutta se on syvä tosiasia, joka nojaa Eukleideen lemmaan ja siten Bézout'hon. On olemassa lukujärjestelmiä (esim. tietyt "algebralliset kokonaisluvut"), joissa **yksikäsitteinen tekijöihinjako pettää** — siellä luku voi hajota alkutekijöikseen kahdella eri tavalla. Juuri tämän epäonnistumisen huomaaminen johti 1800-luvulla modernin algebran syntyyn. Kokonaisluvuilla meillä on onni: hajotelma on aina yksikäsitteinen.

---

## 17.6 Alkulukuja on äärettömästi

Lopetetaan Eukleideen klassikkoon, jonka näit jo luvussa 1 — nyt osana lukuteorian kokonaisuutta.

!!! abstract "Lause 17.5 (Eukleides)"
    Alkulukuja on äärettömän monta.

**Todistus.** Oletetaan, että niitä on vain äärellinen määrä: $p_1, \ldots, p_k$. Muodostetaan $N = p_1 p_2 \cdots p_k + 1$. Aritmetiikan peruslauseen nojalla $N$:llä on alkulukutekijä $p$. Mutta mikään $p_i$ ei jaa lukua $N$ (jokainen jättää jäännöksen $1$), joten $p$ ei ole listalla — ristiriita. $\blacksquare$

Huomaa, kuinka aritmetiikan peruslause ("jokaisella luvulla on alkulukutekijä") teki tästä aukottoman. Luvut nojaavat toisiinsa.

---

## 17.7 Yhteenveto

- **Jakoalgoritmi:** $a = bq + r$, $0 \leq r < b$ — lukuteorian moottori.
- **Eukleideen algoritmi** laskee $\gcd$:n toistetuilla jakojäännöksillä.
- **Bézout:** $\gcd(a,b) = ax + by$ — todistetaan hyvinjärjestyksellä; antaa käänteisalkiot modulossa.
- **Eukleideen lemma:** alkuluku $p$, $p \mid ab \Rightarrow p \mid a$ tai $p \mid b$ — vain alkuluvuilla.
- **Aritmetiikan peruslause:** yksikäsitteinen alkulukuhajotelma. Alkuluvut ovat kertolaskun atomit.
- **Alkulukuja on äärettömästi** (Eukleides).

---

## Harjoitukset

**17.1 (★)** Laske $\gcd(84, 60)$ Eukleideen algoritmilla.

??? success "Vastaus"
    $$84 = 1\cdot60 + 24, \quad 60 = 2\cdot24 + 12, \quad 24 = 2\cdot12 + 0.$$
    Viimeinen nollasta eroava jäännös on $12$, joten $\gcd(84,60) = 12$. $\blacksquare$

---

**17.2 (★)** Kirjoita luvut $60$ ja $84$ alkulukuhajotelmina ja tarkista niiden avulla, että $\gcd = 12$.

??? success "Vastaus"
    $60 = 2^2 \cdot 3 \cdot 5$ ja $84 = 2^2 \cdot 3 \cdot 7$. Yhteiset tekijät pienimmillä potensseilla: $2^2 \cdot 3 = 12$. Täsmää tehtävän 17.1 kanssa. $\blacksquare$

---

**17.3 (★★)** Etsi Bézout'n kertoimet $x, y$, joille $84x + 60y = \gcd(84,60) = 12$. *(Vinkki: pura Eukleideen algoritmi takaperin.)*

??? tip "Vihje"
    Aloita rivistä $12 = 60 - 2\cdot24$ ja korvaa $24 = 84 - 60$, sitten kokoa $84$:n ja $60$:n kertoimet.

??? success "Vastaus"
    Eukleideen algoritmista: $12 = 60 - 2\cdot24$ ja $24 = 84 - 1\cdot60$. Sijoitetaan:
    $$12 = 60 - 2(84 - 60) = 60 - 2\cdot84 + 2\cdot60 = 3\cdot60 - 2\cdot84.$$
    Siis $x = -2$, $y = 3$: tarkistus $84\cdot(-2) + 60\cdot3 = -168 + 180 = 12$. ✓ $\blacksquare$

---

**17.4 (★★)** Todista, että jos $\gcd(a, b) = 1$ ja $a \mid bc$, niin $a \mid c$. *(Tämä on Eukleideen lemman yleistys.)*

??? tip "Vihje"
    Käytä Bézout'ta: $ax + by = 1$. Kerro luvulla $c$.

??? success "Vastaus"
    Koska $\gcd(a,b) = 1$, Bézout'n nojalla $ax + by = 1$ joillakin $x, y$. Kerrotaan luvulla $c$:
    $$acx + bcy = c.$$
    Ensimmäinen termi on jaollinen $a$:lla, ja toinen termi $bcy$ on jaollinen $a$:lla, koska $a \mid bc$. Siis $a \mid c$. $\blacksquare$

---

**17.5 (★★★)** Todista, että alkulukuja muotoa $4k + 3$ on äärettömän monta. *(Vinkki: mukaile Eukleideen todistusta, mutta muodosta $N = 4p_1 p_2 \cdots p_k - 1$ ja mieti sen alkutekijöiden jäännöksiä modulo $4$.)*

??? tip "Vihje"
    Jokainen pariton luku on muotoa $4k+1$ tai $4k+3$. Osoita, että kahden luvun $4k+1$ tulo on taas muotoa $4k+1$ — joten luvulla, joka on muotoa $4k+3$, täytyy olla ainakin yksi alkulukutekijä muotoa $4k+3$.

??? success "Vastaus"
    Havainto: kahden luvun muotoa $4k+1$ tulo on taas muotoa $4k+1$ (koska $(4a+1)(4b+1) = 16ab + 4a + 4b + 1 = 4(\ldots) + 1$). Siis jos luku on muotoa $4k+3$, sillä ei voi olla pelkkiä $4k+1$-muotoisia parittomia alkulukutekijöitä — ainakin yhden on oltava muotoa $4k+3$.

    Oletetaan nyt vastakohta: muotoa $4k+3$ olevia alkulukuja on vain äärellinen määrä $p_1, \ldots, p_k$ (jätetään $3$ pois listalta tai pidetään mukana; toimii kummin päin). Muodostetaan
    $$N = 4 p_1 p_2 \cdots p_k - 1.$$
    Tämä on muotoa $4k + 3$ (koska $-1 \equiv 3 \pmod 4$) ja pariton. Edellisen havainnon nojalla sillä on alkulukutekijä $p$ muotoa $4k+3$. Mutta mikään $p_i$ ei jaa lukua $N$: jos $p_i \mid N$, niin $p_i \mid (4p_1\cdots p_k - N) = 1$, mahdotonta. Siis $p$ on uusi $4k+3$-alkuluku — ristiriita. Niitä on äärettömän monta. $\blacksquare$

    *(Tämä on esimerkki Dirichlet'n lauseesta: jokaisessa jonossa $a, a+d, a+2d, \ldots$, jossa $\gcd(a,d)=1$, on äärettömän monta alkulukua. Yleinen todistus on paljon syvempi ja käyttää — yllättäen — analyysiä ja $\zeta$-tyylisiä funktioita, kuten näet luvussa 19.)*

---

*Seuraava luku: Kongruenssit — kellon aritmetiikka työkaluna, joka tekee jaollisuudesta laskettavaa.*
