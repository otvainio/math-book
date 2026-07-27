# Luku 12: Integraali

Derivaatta syntyi kysymyksestä "kuinka nopeasti?". Integraali syntyy kysymyksestä "**kuinka paljon yhteensä?**" — pinta-ala käyrän alla, kuljettu matka nopeudesta, kertynyt määrä muutosnopeudesta. Nämä kaksi kysymystä näyttävät täysin erillisiltä. Luvun huipennus, **analyysin peruslause**, paljastaa, että ne ovat toistensa käänteisoperaatiot. Se on yksi ihmiskunnan syvimmistä oivalluksista — ja sinä olet käyttänyt sitä jo, kun integroit kiihtyvyyden nopeudeksi fysiikassa.

---

## 12.1 Pinta-alan ongelma

Kuinka lasketaan pinta-ala käyrän $y = f(x)$ alla välillä $[a, b]$? Suorakulmion ala on helppo, mutta käyrän alla oleva alue ei ole suorakulmio. **Idea:** approksimoidaan aluetta ohuilla suorakulmioilla, ja hienonnetaan.

Jaetaan väli $[a, b]$ $n$:ään osaan, kukin leveyttä $\Delta x = \frac{b-a}{n}$. Kussakin osassa piirretään suorakulmio, jonka korkeus on $f$:n arvo jossakin osan pisteessä $x_k^*$. Näiden pinta-alojen summa on **Riemannin summa**:

$$R_n = \sum_{k=1}^{n} f(x_k^*)\,\Delta x.$$

Kun palojen määrä $n$ kasvaa, suorakulmiot seuraavat käyrää yhä tarkemmin, ja summa lähestyy todellista pinta-alaa.

!!! note "Määritelmä (määrätty integraali)"
    Funktio $f$ on **integroituva** välillä $[a, b]$, jos Riemannin summat suppenevat samaan raja-arvoon riippumatta siitä, miten välit ja pisteet $x_k^*$ valitaan, kun $\Delta x \to 0$. Tätä raja-arvoa merkitään
    $$\int_a^b f(x)\,dx = \lim_{n\to\infty} \sum_{k=1}^{n} f(x_k^*)\,\Delta x.$$

Merkki $\int$ on venytetty S (summa), ja $dx$ muistuttaa leveydestä $\Delta x$, joka on kutistunut nollaan. Integraali *on* ääretön summa äärettömän ohuita suorakulmioita — ja huomaa yhteys sarjoihin: sekin oli osasummien raja-arvo.

!!! abstract "Lause 12.1"
    Jokainen suljetulla välillä $[a, b]$ jatkuva funktio on integroituva.

Tämä on syvä tulos (todistus vaatii tasaisen jatkuvuuden käsitteen), joten esitämme sen ilman todistusta. Käytännön viesti: **kaikki funktiot, joita todennäköisesti integroit, ovat integroituvia.** Jatkuvuus riittää.

---

## 12.2 Integraalin perusominaisuudet

Määritelmästä (Riemannin summien raja-arvona) seuraa suoraan:

- **Lineaarisuus:** $\displaystyle\int_a^b \big(\alpha f + \beta g\big)\,dx = \alpha\int_a^b f\,dx + \beta\int_a^b g\,dx.$
- **Additiivisuus:** $\displaystyle\int_a^b f\,dx + \int_b^c f\,dx = \int_a^c f\,dx.$
- **Monotonisuus:** jos $f(x) \leq g(x)$, niin $\int_a^b f\,dx \leq \int_a^b g\,dx.$

Nämä ovat intuitiivisia (pinta-alat lasketaan yhteen, isompi funktio antaa isomman alan), mutta ne periytyvät täsmällisesti summien vastaavista ominaisuuksista.

---

## 12.3 Analyysin peruslause

Nyt luvun — ja koko calculuksen — sydän. Määritellään uusi funktio integroimalla $f$:ää muuttuvaan ylärajaan asti:

$$F(x) = \int_a^x f(t)\,dt.$$

$F(x)$ on "kertynyt pinta-ala pisteeseen $x$ asti". Kysymys: kuinka nopeasti tämä kertymä kasvaa? Vastaus on hämmästyttävä.

!!! abstract "Lause 12.2 (analyysin peruslause, osa I)"
    Olkoon $f$ jatkuva, ja $F(x) = \displaystyle\int_a^x f(t)\,dt$. Silloin $F$ on derivoituva ja
    $$F'(x) = f(x).$$
    Toisin sanoen: **kertymän muutosnopeus on itse funktio.** Integrointi ja derivointi ovat käänteisoperaatioita.

**Todistus.** Lasketaan $F$:n erotusosamäärä. Osoittaja on ala pisteestä $x$ pisteeseen $x+h$:
$$F(x+h) - F(x) = \int_x^{x+h} f(t)\,dt.$$
Tämä on ohut viipale leveyttä $h$. Koska $f$ on jatkuva, se ei ehdi muuttua paljon välillä $[x, x+h]$, joten viipaleen ala on suunnilleen $f(x)\cdot h$. Täsmällisesti: ääriarvolauseen nojalla $f$ saavuttaa viipaleella pienimmän arvon $m_h$ ja suurimman $M_h$, ja
$$m_h \cdot h \leq \int_x^{x+h} f(t)\,dt \leq M_h \cdot h.$$
Jaetaan $h$:lla:
$$m_h \leq \frac{F(x+h)-F(x)}{h} \leq M_h.$$
Kun $h \to 0$, jatkuvuuden nojalla sekä $m_h \to f(x)$ että $M_h \to f(x)$. Puristusperiaate (luku 8) antaa
$$F'(x) = \lim_{h\to 0}\frac{F(x+h)-F(x)}{h} = f(x). \qquad \blacksquare$$

Toinen osa muuttaa tämän *laskusäännöksi* — tavaksi laskea integraaleja etsimällä "vastaderivaatta".

!!! abstract "Lause 12.3 (analyysin peruslause, osa II)"
    Jos $G$ on mikä tahansa $f$:n **integraalifunktio** (eli $G' = f$), niin
    $$\int_a^b f(x)\,dx = G(b) - G(a).$$

**Todistus.** Osan I mukaan $F(x) = \int_a^x f(t)\,dt$ toteuttaa $F' = f$. Myös $G' = f$, joten $(F - G)' = 0$ koko välillä. Luvun 11 nojalla (derivaatta nolla $\Rightarrow$ vakio) on $F - G = C$ jollakin vakiolla $C$. Nyt
$$\int_a^b f\,dx = F(b) = F(b) - F(a) \quad(\text{koska } F(a) = 0)$$
ja korvaamalla $F = G + C$: $\;F(b) - F(a) = (G(b)+C) - (G(a)+C) = G(b) - G(a)$. $\blacksquare$

Huomaa, kuinka **luvun 11 väliarvolause-seuraus** ("derivaatta nolla ⟹ vakio") oli juuri se palanen, joka teki tämän todistuksen mahdolliseksi. Analyysin luvut nojaavat toisiinsa kuin holvikaari.

---

## 12.4 Mitä peruslause tarkoittaa

Peruslause muuttaa mahdottoman helpoksi. Pinta-alan laskeminen suoraan Riemannin summien raja-arvona on työlästä. Mutta osa II sanoo: **etsi vain funktio, jonka derivaatta on $f$, ja sijoita rajat.** Esimerkki:

$$\int_0^2 x^2\,dx = \left[\frac{x^3}{3}\right]_0^2 = \frac{8}{3} - 0 = \frac{8}{3},$$

koska $\frac{x^3}{3}$:n derivaatta on $x^2$. Ala, joka vaatisi äärettömän summan, saadaan kolmella symbolilla.

!!! quote "Sinä käytit tätä jo — fysiikassa"
    Muistatko *Leibnizin ja Newtonin tavoin* -artikkelisi? Integroit kiihtyvyyden nopeudeksi ja nopeuden paikaksi. Se **on** analyysin peruslause: jos $v'(t) = a(t)$, niin
    $$\int_{t_1}^{t_2} a(t)\,dt = v(t_2) - v(t_1) = \text{nopeuden muutos}.$$
    Kertynyt kiihtyvyys on nopeuden muutos, kertynyt nopeus on matka. Fysiikan integrointisi oli peruslause käytännössä — ja sinä käytit sitä oikein ennen kuin näit sen todistettuna.

Ja *ympyrän ala* -työsi: kun johdit $\pi r^2$:n renkaita summaamalla, teit Riemannin integroinnin käsin. Peruslause on syy, miksi $\int_0^r 2\pi\rho\,d\rho = \pi r^2$ toimii.

---

## 12.5 Yhteenveto

- **Määrätty integraali** $\int_a^b f\,dx$ on Riemannin summien raja-arvo — pinta-ala äärettömän ohuina suorakulmioina.
- Jatkuva funktio on aina integroituva.
- **Analyysin peruslause osa I:** $\frac{d}{dx}\int_a^x f(t)\,dt = f(x)$ — kertymän muutos on itse funktio.
- **Osa II:** $\int_a^b f\,dx = G(b) - G(a)$, missä $G' = f$ — integrointi = vastaderivaatan etsintä.
- Derivointi ja integrointi ovat **käänteisoperaatioita**. Fysiikan liike ($a \to v \to s$) on tämä lause käytännössä.

---

## Harjoitukset

**12.1 (★)** Laske $\displaystyle\int_1^3 (2x + 1)\,dx$ analyysin peruslauseella.

??? success "Vastaus"
    Integraalifunktio: $x^2 + x$ (koska sen derivaatta on $2x+1$). Sijoitetaan rajat:
    $$\int_1^3 (2x+1)\,dx = \Big[x^2 + x\Big]_1^3 = (9 + 3) - (1 + 1) = 12 - 2 = 10. \qquad \blacksquare$$

---

**12.2 (★)** Laske $\displaystyle\frac{d}{dx}\int_0^x \cos(t^2)\,dt$.

??? success "Vastaus"
    Analyysin peruslauseen osan I nojalla, suoraan:
    $$\frac{d}{dx}\int_0^x \cos(t^2)\,dt = \cos(x^2).$$
    Huomaa: integraalifunktiota $\int \cos(t^2)\,dt$ ei voi kirjoittaa alkeisfunktiona, mutta *derivaatan* saa silti heti — se on koko peruslauseen voima. $\blacksquare$

---

**12.3 (★★)** Laske käyrän $y = x^2$ ja $x$-akselin väliin jäävä pinta-ala välillä $[0, 3]$, ja vertaa kolmion, jonka kärjet ovat $(0,0), (3,0), (3,9)$, alaan. Kumpi on suurempi ja miksi?

??? success "Vastaus"
    Paraabelin alle jäävä ala:
    $$\int_0^3 x^2\,dx = \left[\frac{x^3}{3}\right]_0^3 = \frac{27}{3} = 9.$$
    Kolmion ala on $\frac12 \cdot 3 \cdot 9 = 13{,}5$. Kolmio on suurempi. Syy: paraabeli $y = x^2$ kaartuu sekantin (kolmion hypotenuusan) *alapuolelle* välillä $[0,3]$, joten sen alle jää vähemmän alaa kuin suoran alle. $\blacksquare$

---

**12.4 (★★)** Osoita, että $\displaystyle\int_{-a}^{a} f(x)\,dx = 0$ jokaiselle **parittomalle** funktiolle ($f(-x) = -f(x)$).

??? tip "Vihje"
    Jaa integraali kahtia pisteessä $0$ ja tee toiseen osaan sijoitus $x \to -x$, tai vetoa symmetriaan.

??? success "Vastaus"
    Jaetaan additiivisuudella:
    $$\int_{-a}^{a} f\,dx = \int_{-a}^{0} f\,dx + \int_{0}^{a} f\,dx.$$
    Ensimmäisessä integraalissa tehdään sijoitus $x = -u$ ($dx = -du$; rajat $x: -a\to 0$ vastaavat $u: a \to 0$):
    $$\int_{-a}^{0} f(x)\,dx = \int_{a}^{0} f(-u)(-du) = \int_{0}^{a} f(-u)\,du = \int_0^a -f(u)\,du = -\int_0^a f\,du.$$
    Käytimme parittomuutta $f(-u) = -f(u)$. Siis
    $$\int_{-a}^a f\,dx = -\int_0^a f\,du + \int_0^a f\,dx = 0. \qquad \blacksquare$$

    *(Geometrisesti: parittoman funktion negatiivisen puolen "ala" kumoaa positiivisen puolen. Esim. $\int_{-\pi}^\pi \sin x\,dx = 0$.)*

---

**12.5 (★★★)** Todista **integraalin väliarvolause**: jos $f$ on jatkuva välillä $[a,b]$, niin on olemassa $c \in [a,b]$, jolle
$$\int_a^b f(x)\,dx = f(c)\,(b - a).$$
*(Eli: integraali on jonkin funktion arvon ja välin pituuden tulo — "keskimääräinen korkeus kertaa leveys".)*

??? tip "Vihje"
    Käytä ääriarvolausetta rajaamaan integraali pienimmän ja suurimman arvon väliin, ja sitten väliarvolausetta (jatkuvuudelle) löytääksesi pisteen, jossa keskiarvo saavutetaan.

??? success "Vastaus"
    Ääriarvolauseen (luku 10) nojalla $f$ saavuttaa välillä $[a,b]$ pienimmän arvon $m$ ja suurimman $M$. Integraalin monotonisuudesta:
    $$m(b-a) \leq \int_a^b f(x)\,dx \leq M(b-a).$$
    Jaetaan $(b-a)$:lla:
    $$m \leq \frac{1}{b-a}\int_a^b f(x)\,dx \leq M.$$
    Keskimmäinen luku (kutsutaan sitä $\mu$:ksi) on siis $f$:n pienimmän ja suurimman arvon välissä. Koska $f$ on jatkuva, se saavuttaa väliarvolauseen (luku 10) nojalla jokaisen arvon näiden välillä — erityisesti arvon $\mu$. Siis on $c$, jolle $f(c) = \mu$, eli
    $$\int_a^b f(x)\,dx = f(c)\,(b-a). \qquad \blacksquare$$

    *(Tämä $\mu = \frac{1}{b-a}\int_a^b f$ on funktion **keskiarvo** välillä — ja lause sanoo, että jatkuva funktio saavuttaa keskiarvonsa jossain pisteessä. Se oli myös piilossa analyysin peruslauseen osan I todistuksessa.)*

---

*Seuraava luku: Taylorin sarjat — miten funktio muuttuu (ääretön) polynomiksi, kuinka tarkasti, ja milloin sarja todella tavoittaa funktion.*
