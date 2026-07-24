# Luku 8: Jonot ja raja-arvot

Tästä alkaa **analyysi** — matematiikan haara, joka käsittelee äärettömyyttä täsmällisesti. Olet käyttänyt raja-arvoja koko ajan: "termit menevät nollaan", "sarja lähestyy arvoa", "kun $n$ kasvaa rajatta". Nämä ovat intuitioita. Tässä luvussa annamme niille **aukottoman määritelmän** — sen kuuluisan $\varepsilon$:n ja $N$:n — ja huomaat, että intuitiosi oli oikea, mutta nyt sen takana on kalliota.

---

## 8.1 Jono

!!! note "Määritelmä"
    **Lukujono** on funktio luonnollisilta luvuilta reaaliluvuille: jokaiseen indeksiin $n$ liittyy termi $a_n$. Jono merkitään $(a_n)$ tai luettelemalla $a_1, a_2, a_3, \ldots$

Esimerkkejä:

$$a_n = \frac1n : \quad 1, \tfrac12, \tfrac13, \tfrac14, \ldots \qquad\qquad b_n = (-1)^n : \quad -1, 1, -1, 1, \ldots$$

Ensimmäinen "asettuu" kohti nollaa. Toinen ei asetu mihinkään — se hyppii ikuisesti. Haluamme tehdä täsmälliseksi, mitä "asettuu kohti" tarkoittaa.

---

## 8.2 Raja-arvon määritelmä

Intuitio: $a_n \to L$ tarkoittaa, että $a_n$ tulee **mielivaltaisen lähelle** lukua $L$, kunhan mennään tarpeeksi pitkälle jonossa. Ongelma on sana "mielivaltaisen lähelle". Kuinka lähelle? *Niin lähelle kuin kuka tahansa vaatii.* Juuri tämä muuttuu $\varepsilon$:ksi.

!!! note "Määritelmä (raja-arvo)"
    Jono $(a_n)$ **suppenee** kohti raja-arvoa $L$, merkitään $\displaystyle\lim_{n\to\infty} a_n = L$, jos:

    > jokaista $\varepsilon > 0$ kohti on olemassa luku $N$ siten, että kaikilla $n > N$ pätee $|a_n - L| < \varepsilon$.

Lue tämä hitaasti, koska se on koko analyysin ydinlause. Se on kuin peli kahdelle:

- **Vastustaja** valitsee tarkkuuden $\varepsilon > 0$ — kuinka lähellä lukua $L$ vaaditaan olemaan ("alle millintuhannesosan!").
- **Sinä** vastaat luvulla $N$ — lupauksella: "tuosta indeksistä eteenpäin jokainen termi on sitä lähempänä."

Jos voitat *jokaisella* vastustajan valitsemalla $\varepsilon$:lla, olipa se kuinka pieni tahansa, niin $L$ on raja-arvo. $|a_n - L| < \varepsilon$ tarkoittaa "termin $a_n$ etäisyys luvusta $L$ on alle $\varepsilon$".

Todistetaan ensimmäinen raja-arvo täsmällisesti. Huomaa, että käytämme luvun 5 **Arkhimedeen ominaisuutta** — analyysi lepää täydellisyyden varassa.

!!! abstract "Lause 8.1"
    $\displaystyle\lim_{n\to\infty} \frac1n = 0.$

**Todistus.** Olkoon $\varepsilon > 0$ mielivaltainen (vastustajan valinta). Arkhimedeen ominaisuuden nojalla on olemassa luonnollinen luku $N$, jolle $\frac1N < \varepsilon$. Nyt kaikilla $n > N$:

$$\left| \frac1n - 0 \right| = \frac1n < \frac1N < \varepsilon.$$

Löysimme vaaditun $N$:n jokaiselle $\varepsilon$:lle, joten $\frac1n \to 0$. $\blacksquare$

Tämä on se raja-arvo, jonka "tiesit" jo — mutta nyt se on todistettu, ei uskottu. Ja huomaa: **koko todistus nojaa siihen, ettei ole äärettömän pieniä reaalilukuja** (Arkhimedes). Ilman täydellisyyttä $\frac1n$ ei välttämättä lähestyisi nollaa.

---

## 8.3 Raja-arvo on yksikäsitteinen

!!! abstract "Lause 8.2"
    Jonolla voi olla korkeintaan yksi raja-arvo.

**Todistus.** Oletetaan, että $a_n \to L$ ja $a_n \to L'$, ja $L \neq L'$. Merkitään etäisyys $d = |L - L'| > 0$. Valitaan $\varepsilon = \frac{d}{2}$.

Koska $a_n \to L$, on olemassa $N_1$, jonka jälkeen $|a_n - L| < \frac{d}{2}$. Koska $a_n \to L'$, on olemassa $N_2$, jonka jälkeen $|a_n - L'| < \frac{d}{2}$. Kun $n$ on suurempi kuin molemmat, kolmioepäyhtälöllä:

$$d = |L - L'| = |L - a_n + a_n - L'| \leq |a_n - L| + |a_n - L'| < \frac{d}{2} + \frac{d}{2} = d.$$

Saimme $d < d$ — ristiriita. Siis $L = L'$. $\blacksquare$

Tämä on ensimmäinen kunnollinen $\varepsilon$-todistuksesi lukea. Huomaa temppu $\varepsilon = \frac{d}{2}$: valitaan tarkkuus niin tiukaksi, että kahden eri raja-arvon "vaikutusalueet" eivät mahdu päällekkäin. Tällaiset valinnat ovat analyysin käsityötä.

---

## 8.4 Raja-arvon laskusäännöt

Onneksi jokaista raja-arvoa ei tarvitse todistaa $\varepsilon$:lla. Kun perusrakennuspalikat on todistettu, raja-arvot yhdistyvät siististi.

!!! abstract "Lause 8.3 (raja-arvon laskusäännöt)"
    Jos $a_n \to A$ ja $b_n \to B$, niin
    $$a_n + b_n \to A + B, \qquad a_n b_n \to AB, \qquad \frac{a_n}{b_n} \to \frac{A}{B} \;\;(\text{kun } B \neq 0).$$

Näiden todistukset ovat $\varepsilon$-harjoituksia (summan tapaus on harjoitus 8.4). Käytännössä ne tekevät raja-arvojen laskemisesta algebraa. Esimerkki:

$$\lim_{n\to\infty} \frac{3n^2 + 1}{n^2 + n} = \lim_{n\to\infty} \frac{3 + \frac{1}{n^2}}{1 + \frac1n} = \frac{3 + 0}{1 + 0} = 3,$$

missä jaoimme ensin $n^2$:lla ja käytimme sitten sääntöä $\frac1n \to 0$ (Lause 8.1) ja laskusääntöjä.

---

## 8.5 Monotoniset jonot ja täydellisyys

Nyt tulee luvun tärkein työkalu — ja se paljastaa, *miksi* rakensimme reaaliluvut täydellisiksi luvussa 5.

!!! note "Määritelmä"
    Jono on **kasvava**, jos $a_1 \leq a_2 \leq a_3 \leq \cdots$, ja **ylhäältä rajoitettu**, jos on olemassa luku $M$, jolle $a_n \leq M$ kaikilla $n$.

!!! abstract "Lause 8.4 (monotonisen suppenemisen lause)"
    Kasvava, ylhäältä rajoitettu jono suppenee. (Raja-arvo on jonon arvojen supremum.)

**Todistus.** Olkoon $(a_n)$ kasvava ja ylhäältä rajoitettu. Joukolla $S = \{a_1, a_2, \ldots\}$ on **täydellisyysaksiooman nojalla** (luku 5) supremum; merkitään $L = \sup S$. Osoitetaan, että $a_n \to L$.

Olkoon $\varepsilon > 0$. Koska $L$ on *pienin* yläraja, luku $L - \varepsilon$ ei ole yläraja, joten jokin jonon jäsen ylittää sen: on olemassa $N$, jolle $a_N > L - \varepsilon$ (tämä on täsmälleen harjoitus 5.4). Koska jono on kasvava, kaikilla $n > N$ pätee $a_n \geq a_N > L - \varepsilon$. Toisaalta $a_n \leq L$ (yläraja). Siis

$$L - \varepsilon < a_n \leq L \implies |a_n - L| < \varepsilon.$$

Näin $a_n \to L$. $\blacksquare$

Tämä on kaunista: **kasvavan rajoitetun jonon ei tarvitse "tietää" raja-arvoaan etukäteen** — täydellisyys takaa, että se on olemassa. Juuri tässä näet, miksi $\mathbb{Q}$ ei riittänyt: rationaalilukujono voi kasvaa ja pysyä rajoitettuna, mutta karata kohti reikää (kohti $\sqrt2$:ta), jota $\mathbb{Q}$:ssa ei ole. $\mathbb{R}$:ssä reikää ei ole, joten raja on aina olemassa.

### Luku $e$ raja-arvona

Klassinen sovellus, joka sitoo yhteen paljon työtäsi:

!!! abstract "Lause 8.5"
    Jono $a_n = \left(1 + \dfrac1n\right)^n$ on kasvava ja ylhäältä rajoitettu, joten se suppenee. Sen raja-arvo on luku $e$:
    $$e = \lim_{n\to\infty}\left(1 + \frac1n\right)^n.$$

Voidaan osoittaa (binomikaavalla), että jono on kasvava ja että jokainen termi on alle $3$. Monotonisen suppenemisen lause takaa siis raja-arvon olemassaolon, ja *määrittelemme* luvun $e$ tuoksi raja-arvoksi. Tämä on toinen tapa tavata $e$ — sarjan $\sum \frac1{n!}$ rinnalla, jonka johdit päiväkirjassasi. (Että nämä kaksi antavat saman luvun, on oma kaunis harjoituksensa.)

---

## 8.6 Puristusperiaate

!!! abstract "Lause 8.6 (puristusperiaate)"
    Jos $a_n \leq b_n \leq c_n$ kaikilla $n$ (jostain indeksistä alkaen), ja $a_n \to L$ sekä $c_n \to L$, niin myös $b_n \to L$.

Jos jonoa puristetaan kahden puolelta samaan raja-arvoon, sen on pakko mennä sinne. Esimerkki: koska $-\frac1n \leq \frac{\sin n}{n} \leq \frac1n$ ja molemmat reunat menevät nollaan, myös $\frac{\sin n}{n} \to 0$ — vaikka $\sin n$ hyppii villisti. Puristus on yksi käytännöllisimmistä työkaluista.

---

## 8.7 Yhteenveto

- **Raja-arvo** $a_n \to L$: jokaista $\varepsilon > 0$ kohti on $N$, jonka jälkeen $|a_n - L| < \varepsilon$. ($\varepsilon$–$N$-peli.)
- $\frac1n \to 0$ nojaa **Arkhimedeen ominaisuuteen**; raja-arvo on **yksikäsitteinen**.
- **Laskusäännöt** tekevät raja-arvoista algebraa.
- **Monotonisen suppenemisen lause:** kasvava rajoitettu jono suppenee — tämä on missä **täydellisyys** lunastetaan. Luku $e$ syntyy näin.
- **Puristusperiaate:** kahden puolelta samaan rajaan puristettu jono menee sinne.

---

## Harjoitukset

**8.1 (★)** Määritä seuraavien jonojen raja-arvot: (a) $\frac{2n+1}{n}$, (b) $\frac{n^2}{2n^2 - 3}$, (c) $\frac{(-1)^n}{n}$.

??? success "Vastaus"
    - (a) $\frac{2n+1}{n} = 2 + \frac1n \to 2 + 0 = 2$.
    - (b) $\frac{n^2}{2n^2-3} = \frac{1}{2 - 3/n^2} \to \frac{1}{2-0} = \frac12$.
    - (c) $\left|\frac{(-1)^n}{n}\right| = \frac1n \to 0$, joten $\frac{(-1)^n}{n} \to 0$ (merkin vaihtelu ei estä, koska itseisarvo menee nollaan). $\blacksquare$

---

**8.2 (★)** Suppeneeko jono $a_n = (-1)^n$? Perustele.

??? success "Vastaus"
    Ei suppene. Jono on $-1, 1, -1, 1, \ldots$ Jos raja-arvo $L$ olisi olemassa, valitsemalla $\varepsilon = 1$ pitäisi jostain indeksistä eteenpäin *kaikkien* termien olla etäisyydellä $< 1$ luvusta $L$. Mutta peräkkäiset termit $-1$ ja $1$ ovat etäisyydellä $2$ toisistaan, joten ne eivät molemmat voi olla alle $1$ etäisyydellä samasta $L$:stä. Ristiriita. $\blacksquare$

---

**8.3 (★★)** Käytä $\varepsilon$–$N$-määritelmää: todista, että $\displaystyle\lim_{n\to\infty}\frac{1}{n^2} = 0$.

??? tip "Vihje"
    Annetulle $\varepsilon$: haluat $\frac{1}{n^2} < \varepsilon$, eli $n > \frac{1}{\sqrt\varepsilon}$. Valitse $N$ Arkhimedeen avulla suuremmaksi kuin tämä.

??? success "Vastaus"
    Olkoon $\varepsilon > 0$. Arkhimedeen ominaisuuden nojalla on $N$, jolle $N > \frac{1}{\sqrt\varepsilon}$, eli $\frac{1}{N^2} < \varepsilon$. Silloin kaikilla $n > N$:
    $$\left|\frac{1}{n^2} - 0\right| = \frac{1}{n^2} < \frac{1}{N^2} < \varepsilon.$$
    Siis $\frac{1}{n^2} \to 0$. $\blacksquare$

---

**8.4 (★★)** Todista summan laskusääntö: jos $a_n \to A$ ja $b_n \to B$, niin $a_n + b_n \to A + B$.

??? tip "Vihje"
    Annetulle $\varepsilon$ käytä *puolikasta*: tee $|a_n - A| < \frac\varepsilon2$ ja $|b_n - B| < \frac\varepsilon2$, ja yhdistä kolmioepäyhtälöllä.

??? success "Vastaus"
    Olkoon $\varepsilon > 0$. Koska $a_n \to A$, on $N_1$, jonka jälkeen $|a_n - A| < \frac\varepsilon2$. Koska $b_n \to B$, on $N_2$, jonka jälkeen $|b_n - B| < \frac\varepsilon2$. Olkoon $N = \max(N_1, N_2)$. Kaikilla $n > N$ kolmioepäyhtälöllä:
    $$|(a_n + b_n) - (A + B)| = |(a_n - A) + (b_n - B)| \leq |a_n - A| + |b_n - B| < \frac\varepsilon2 + \frac\varepsilon2 = \varepsilon.$$
    Siis $a_n + b_n \to A + B$. $\blacksquare$

    *(Temppu "jaa $\varepsilon$ kahtia" on analyysin yleisin yksittäinen kikka. Näet sen sata kertaa.)*

---

**8.5 (★★★)** Jono määritellään rekursiivisesti: $a_1 = 2$ ja $a_{n+1} = \frac12\left(a_n + \frac{2}{a_n}\right)$. Osoita, että jono on vähenevä ja alhaalta rajoitettu (alaraja $\sqrt2$), joten se suppenee. Mihin? *(Tämä on babylonialainen neliöjuurialgoritmi.)*

??? tip "Vihje"
    Rajoitus: näytä $a_n \geq \sqrt2$ käyttämällä epäyhtälöä $\frac{x + 2/x}{2} \geq \sqrt2$ (aritmeettis-geometrinen). Vähenevyys: näytä $a_{n+1} \leq a_n$. Raja-arvolle $L$: ota raja-arvo yhtälöstä $a_{n+1} = \frac12(a_n + 2/a_n)$.

??? success "Vastaus"
    *Alaraja.* Aritmeettis-geometrisen epäyhtälön nojalla kaikilla $x > 0$ pätee $\frac12\left(x + \frac2x\right) \geq \sqrt{x \cdot \frac2x} = \sqrt2$. Siis $a_{n+1} \geq \sqrt2$ kaikilla $n$, joten jono on alhaalta rajoitettu luvulla $\sqrt2$.

    *Vähenevyys.* Koska $a_n \geq \sqrt2$, on $a_n^2 \geq 2$, joten $\frac{2}{a_n} \leq a_n$, ja
    $$a_{n+1} = \frac12\left(a_n + \frac{2}{a_n}\right) \leq \frac12(a_n + a_n) = a_n.$$
    Jono on vähenevä ja alhaalta rajoitettu, joten (monotonisen suppenemisen lauseen vastine alaspäin) se suppenee. Merkitään $L = \lim a_n$.

    *Raja-arvo.* Otetaan raja-arvo rekursiokaavasta: koska $a_{n+1} \to L$ ja $a_n \to L$,
    $$L = \frac12\left(L + \frac2L\right) \implies 2L = L + \frac2L \implies L = \frac2L \implies L^2 = 2.$$
    Koska $L \geq \sqrt2 > 0$, on $L = \sqrt2$. $\blacksquare$

    *(Tämä jono suppenee kohti $\sqrt2$:ta hämmästyttävän nopeasti — se tuplaa tarkat desimaalit joka askeleella. Sama menetelmä, jota tietokoneet käyttävät neliöjuuriin.)*

---

*Seuraava luku: Sarjat ja suppeneminen — äärettömät summat täsmällisesti, ja vihdoin todistus sille, miksi sarjasi suppenevat.*
