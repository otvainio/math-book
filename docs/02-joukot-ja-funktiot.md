# Luku 2: Joukot ja funktiot

Edellisessä luvussa opit todistamaan. Tässä luvussa opit **kielen**, jolla melkein kaikki moderni matematiikka on kirjoitettu: joukot ja funktiot. Kun ymmärrät ne kunnolla, huomaat, että "lukusuora", "kuvaaja", "muuttuja" ja "ratkaisujoukko" ovat kaikki saman yksinkertaisen idean puhetapoja.

Joukko-oppi keksittiin yllättävän myöhään — Georg Cantor loi sen vasta 1870-luvulla. Ennen sitä matematiikka toimi ilman täsmällistä käsitystä "kokoelmasta". Tänään se on koko rakennuksen perustus.

---

## 2.1 Joukko

!!! note "Määritelmä"
    **Joukko** on kokoelma erillisiä olioita, joita kutsutaan sen **alkioiksi**. Jos $x$ on joukon $A$ alkio, kirjoitetaan $x \in A$ ("$x$ kuuluu joukkoon $A$"). Jos ei, kirjoitetaan $x \notin A$.

Joukon määrää *täysin* se, mitkä alkiot siihen kuuluvat — ei mikään muu. Kaksi joukkoa ovat samat täsmälleen silloin, kun niillä on samat alkiot.

Joukko voidaan esittää **luettelemalla** alkiot aaltosulkeissa:

$$A = \{1, 2, 3, 4, 5\}, \qquad B = \{\text{punainen}, \text{vihreä}, \text{sininen}\}.$$

Kaksi tärkeää periaatetta luettelussa:

- **Järjestyksellä ei ole väliä:** $\{1, 2, 3\} = \{3, 1, 2\}$.
- **Toistolla ei ole väliä:** $\{1, 2, 2, 3\} = \{1, 2, 3\}$. Alkio joko kuuluu joukkoon tai ei; se ei voi kuulua "kahdesti".

Ääretöntä joukkoa ei voi luetella loppuun, joten käytetään **ehtoa** (rakennemerkintää):

$$P = \{\, n \mid n \text{ on parillinen positiivinen kokonaisluku} \,\} = \{2, 4, 6, 8, \ldots\}.$$

Pystyviiva $\mid$ luetaan "siten että". Vasemmalla on alkion muoto, oikealla ehto, jonka sen on täytettävä.

### Tärkeät lukujoukot

Näille on omat vakiintuneet symbolinsa, joita käytämme läpi kirjan:

| Symboli | Joukko | Alkioita |
|---|---|---|
| $\mathbb{N}$ | luonnolliset luvut | $0, 1, 2, 3, \ldots$ |
| $\mathbb{Z}$ | kokonaisluvut | $\ldots, -2, -1, 0, 1, 2, \ldots$ |
| $\mathbb{Q}$ | rationaaliluvut | murtoluvut $\frac{a}{b}$, $b \neq 0$ |
| $\mathbb{R}$ | reaaliluvut | koko lukusuora |
| $\mathbb{C}$ | kompleksiluvut | $a + bi$ |

!!! note "Tyhjä joukko"
    Joukko, jossa ei ole yhtään alkiota, on **tyhjä joukko**, merkitään $\varnothing$ tai $\{\,\}$. Se on ainutlaatuinen: tyhjiä joukkoja on vain yksi. Huomaa, että $\varnothing \neq \{\varnothing\}$ — jälkimmäisessä on yksi alkio (nimittäin tyhjä joukko itse), joten se ei ole tyhjä.

---

## 2.2 Osajoukot

!!! note "Määritelmä"
    Joukko $A$ on joukon $B$ **osajoukko**, merkitään $A \subseteq B$, jos jokainen $A$:n alkio kuuluu myös $B$:hen. Toisin sanoen: $x \in A \Rightarrow x \in B$.

Esimerkiksi $\mathbb{N} \subseteq \mathbb{Z} \subseteq \mathbb{Q} \subseteq \mathbb{R} \subseteq \mathbb{C}$ — lukujärjestelmät ovat sisäkkäisiä.

Tässä on ensimmäinen tärkeä tekniikka, jota käytät läpi matematiikan: **kuinka todistetaan, että kaksi joukkoa ovat samat.**

!!! abstract "Periaate: joukkojen yhtäsuuruus"
    $A = B$ täsmälleen silloin, kun $A \subseteq B$ **ja** $B \subseteq A$.

    Siis todistaaksesi $A = B$ todistat kaksi asiaa: jokainen $A$:n alkio on $B$:ssä, ja jokainen $B$:n alkio on $A$:ssa.

Tämä "kaksoissisältyminen" on joukkojen maailman vastine yhtälön molemmille puolille.

!!! abstract "Lause 2.1"
    Tyhjä joukko on jokaisen joukon osajoukko: $\varnothing \subseteq A$ kaikilla $A$.

**Todistus.** Väite $\varnothing \subseteq A$ tarkoittaa: *jos $x \in \varnothing$, niin $x \in A$.* Mutta ehto "$x \in \varnothing$" ei ole koskaan tosi — tyhjässä joukossa ei ole alkioita. Väite "jos (epätosi), niin …" on aina tosi (kutsutaan **tyhjästi todeksi**). Siis $\varnothing \subseteq A$. $\blacksquare$

!!! tip "Tyhjästi tosi"
    Lause muotoa "jos $P$, niin $Q$" on tosi aina, kun $P$ on epätosi — riippumatta $Q$:sta. "Jos kuu on juustoa, niin $2+2=5$" on loogisesti tosi lause, koska ehto ei toteudu. Tämä tuntuu aluksi oudolta, mutta se on välttämätöntä, jotta logiikka toimisi johdonmukaisesti.

### Potenssijoukko

!!! note "Määritelmä"
    Joukon $A$ **potenssijoukko** $\mathcal{P}(A)$ on kaikkien $A$:n osajoukkojen joukko.

Esimerkiksi jos $A = \{1, 2\}$, sen osajoukot ovat $\varnothing$, $\{1\}$, $\{2\}$ ja $\{1,2\}$, joten

$$\mathcal{P}(A) = \big\{\, \varnothing,\; \{1\},\; \{2\},\; \{1,2\} \,\big\}.$$

Neljä osajoukkoa. Ei sattumaa:

!!! abstract "Lause 2.2"
    Jos joukossa $A$ on $n$ alkiota, niin sillä on $2^n$ osajoukkoa.

**Todistus.** Muodostaessasi osajoukkoa teet jokaisen alkion kohdalla itsenäisen valinnan: *otanko sen mukaan vai en?* Kaksi vaihtoehtoa per alkio, $n$ alkiota, ja valinnat ovat riippumattomia, joten erilaisia osajoukkoja on

$$\underbrace{2 \cdot 2 \cdots 2}_{n \text{ kertaa}} = 2^n. \qquad \blacksquare$$

Tästä syystä potenssijoukkoa merkitään $2^A$:kin, ja tässä on syy nimeen "potenssijoukko".

---

## 2.3 Joukko-operaatiot

Joukoista voi rakentaa uusia joukkoja kolmella perusoperaatiolla.

!!! note "Määritelmä"
    Olkoot $A$ ja $B$ joukkoja.

    - **Yhdiste** $A \cup B = \{\, x \mid x \in A \text{ tai } x \in B \,\}$ — alkiot, jotka ovat ainakin toisessa.
    - **Leikkaus** $A \cap B = \{\, x \mid x \in A \text{ ja } x \in B \,\}$ — alkiot, jotka ovat molemmissa.
    - **Erotus** $A \setminus B = \{\, x \mid x \in A \text{ ja } x \notin B \,\}$ — $A$:n alkiot, jotka eivät ole $B$:ssä.

Esimerkki: jos $A = \{1,2,3,4\}$ ja $B = \{3,4,5,6\}$, niin

$$A \cup B = \{1,2,3,4,5,6\}, \quad A \cap B = \{3,4\}, \quad A \setminus B = \{1,2\}.$$

Sana "tai" tarkoittaa matematiikassa aina **"ainakin toinen, mahdollisesti molemmat"** — ei "joko–tai". Siksi $3 \in A \cup B$, vaikka $3$ on molemmissa.

Nämä operaatiot tottelevat lakeja, jotka muistuttavat lukujen laskusääntöjä. Todistetaan yksi mallina — huomaa, että käytämme juuri opittua kaksoissisältymistekniikkaa.

!!! abstract "Lause 2.3 (yksi De Morganin laeista)"
    Kaikilla joukoilla $A, B, C$:
    $$C \setminus (A \cup B) = (C \setminus A) \cap (C \setminus B).$$

**Todistus.** Osoitetaan kaksoissisältyminen.

*($\subseteq$)* Olkoon $x \in C \setminus (A \cup B)$. Silloin $x \in C$ mutta $x \notin A \cup B$. Jälkimmäinen tarkoittaa, ettei $x$ ole $A$:ssa eikä $B$:ssä. Siis $x \in C$ ja $x \notin A$ (eli $x \in C \setminus A$), ja samoin $x \in C \setminus B$. Näin $x \in (C \setminus A) \cap (C \setminus B)$.

*($\supseteq$)* Olkoon $x \in (C \setminus A) \cap (C \setminus B)$. Silloin $x \in C \setminus A$ ja $x \in C \setminus B$, joten $x \in C$, $x \notin A$ ja $x \notin B$. Koska $x$ ei ole $A$:ssa eikä $B$:ssä, se ei ole niiden yhdisteessä: $x \notin A \cup B$. Siis $x \in C \setminus (A \cup B)$.

Molemmat sisältymiset pätevät, joten joukot ovat samat. $\blacksquare$

Lue todistus toiseen kertaan ja huomaa: se on itse asiassa *logiikkaa alkioiden tasolla*. "Ei ($A$ tai $B$)" on sama kuin "(ei $A$) ja (ei $B$)" — De Morganin laki logiikassa. Joukko-operaatiot ovat logiikan sanoja pukeutuneina kokoelmiksi.

---

## 2.4 Järjestetyt parit ja tulojoukko

Joukossa järjestyksellä ei ole väliä. Mutta usein järjestys on koko juju: piste $(3, 5)$ tasossa ei ole sama kuin $(5, 3)$. Tätä varten tarvitaan **järjestetty pari**.

!!! note "Määritelmä"
    **Järjestetty pari** $(a, b)$ on olio, jolle $(a,b) = (c,d)$ täsmälleen silloin, kun $a = c$ **ja** $b = d$.

    Joukkojen $A$ ja $B$ **karteesinen tulo** on kaikkien järjestettyjen parien joukko:
    $$A \times B = \{\, (a, b) \mid a \in A,\; b \in B \,\}.$$

Nimi kunnioittaa René Descartesia (latinaksi Cartesius), joka keksi kuvata tason pisteet lukupareina — koko analyyttisen geometrian perustan. Kun kirjoitat $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$, tarkoitat täsmälleen tasoa: jokainen piste on pari $(x, y)$.

Esimerkki: jos $A = \{1, 2\}$ ja $B = \{a, b\}$, niin

$$A \times B = \{\,(1,a),\; (1,b),\; (2,a),\; (2,b)\,\}.$$

Neljä paria $= 2 \times 2$. Yleisesti: jos $A$:ssa on $m$ alkiota ja $B$:ssä $n$, niin $A \times B$:ssä on $mn$ alkiota — siitä tulo­merkki $\times$.

---

## 2.5 Funktio

Nyt pääsemme luvun sydämeen. Olet käyttänyt funktioita koko ajan — $f(x) = x^2$, $\sin x$, $\sqrt x$ — mutta mikä funktio *on*?

!!! note "Määritelmä"
    **Funktio** $f$ joukolta $A$ joukolle $B$, merkitään $f : A \to B$, on sääntö, joka liittää **jokaiseen** $A$:n alkioon **täsmälleen yhden** $B$:n alkion. Alkioon $x$ liitettyä alkiota merkitään $f(x)$.

    - $A$ on funktion **määrittelyjoukko** (lähtöjoukko),
    - $B$ on **maalijoukko**,
    - $\{\, f(x) \mid x \in A \,\}$ on funktion **arvojoukko** (kuva) — ne $B$:n alkiot, jotka todella saavutetaan.

Kaksi sanaa määritelmässä kantavat kaiken painon:

- **"jokaiseen"** — jokaisella lähtöjoukon alkiolla *on* arvo. Ei aukkoja.
- **"täsmälleen yhden"** — arvoja on *vain yksi*. Ei kahta arvoa samalle syötteelle.

Juuri jälkimmäinen selittää havaintosi, jonka teit vaakaparaabelista: käyrä $x = y^2$ **ei ole funktio** muuttujan $x$ funktiona, koska $x = 4$ antaisi kaksi arvoa, $y = 2$ ja $y = -2$. Siksi neliöjuuri $\sqrt{}$ määritellään antamaan vain positiivinen haara — jotta siitä *tulisi* funktio. Määritelmä pakottaa valinnan.

!!! tip "Funktio kolmena eri asiana"
    Sama funktio voidaan kuvata monella tavalla:

    - **kaavana:** $f(x) = x^2$
    - **kuvaajana:** paraabeli tasossa
    - **parijoukkona:** $\{\,(x, x^2) \mid x \in \mathbb{R}\,\}$

    Viimeinen on täsmällisin: funktio *on* pohjimmiltaan joukko järjestettyjä pareja $(x, f(x))$, jossa mikään $x$ ei esiinny kahdesti eri arvon kanssa. Tämä on kuvaaja — funktion ja sen kuvaajan välillä ei ole eroa, kun asia ajatellaan loppuun.

---

## 2.6 Injektio, surjektio, bijektio

Funktioita luokitellaan sen mukaan, *miten* ne kuvaavat lähtöjoukon maalijoukolle. Kolme käsitettä, jotka palaavat läpi koko matematiikan — ja jotka Cantor tarvitsi äärettömyyksien vertailuun (luku 28).

!!! note "Määritelmä"
    Olkoon $f : A \to B$.

    - $f$ on **injektio** (yksi yhteen), jos eri alkiot kuvautuvat eri alkioille: $x_1 \neq x_2 \Rightarrow f(x_1) \neq f(x_2)$.
    - $f$ on **surjektio** (päälle), jos jokainen maalijoukon alkio saavutetaan: jokaisella $y \in B$ on jokin $x \in A$, jolle $f(x) = y$.
    - $f$ on **bijektio**, jos se on sekä injektio että surjektio.

Havainnollisesti: injektio ei "törmää" (kaksi syötettä ei koskaan päädy samaan arvoon), surjektio "peittää" koko maalijoukon, ja bijektio tekee molemmat — se on *täydellinen pariutus* joukkojen $A$ ja $B$ välillä.

**Esimerkkejä** funktiosta $\mathbb{R} \to \mathbb{R}$:

- $f(x) = x^2$ **ei ole injektio** ($f(-2) = f(2) = 4$) eikä surjektio (negatiivisia arvoja ei saavuteta).
- $f(x) = x^3$ **on bijektio** — jokainen reaaliluku saavutetaan täsmälleen kerran.
- $f(x) = e^x$ on injektio mutta ei surjektio (arvot ovat vain positiivisia).

Injektiivisyyden todistamiseen on kätevä tekniikka, joka kannattaa painaa mieleen:

!!! tip "Injektiivisyyden todistaminen"
    Osoittaaksesi, että $f$ on injektio, oleta $f(x_1) = f(x_2)$ ja päättele, että $x_1 = x_2$. (Tämä on kontrapositio määritelmälle — helpompi käyttää.)

!!! abstract "Lause 2.4"
    Funktio $f : \mathbb{R} \to \mathbb{R}$, $f(x) = 3x + 2$, on bijektio.

**Todistus.**

*Injektio.* Oletetaan $f(x_1) = f(x_2)$, eli $3x_1 + 2 = 3x_2 + 2$. Vähennetään $2$ ja jaetaan kolmella: $x_1 = x_2$. Siis $f$ on injektio.

*Surjektio.* Olkoon $y \in \mathbb{R}$ mielivaltainen. Etsitään $x$, jolle $f(x) = y$. Ratkaistaan: $3x + 2 = y \Rightarrow x = \frac{y-2}{3}$. Tämä $x$ on reaaliluku, ja $f\!\left(\frac{y-2}{3}\right) = 3\cdot\frac{y-2}{3} + 2 = y$. Siis jokainen $y$ saavutetaan, ja $f$ on surjektio.

Molemmat ehdot täyttyvät, joten $f$ on bijektio. $\blacksquare$

Huomaa surjektiotodistuksen rakenne: *ratkaisit yhtälön $f(x) = y$ muuttujan $x$ suhteen.* Tämä ei ole sattumaa — se johtaa suoraan seuraavaan käsitteeseen.

---

## 2.7 Yhdistetty funktio ja käänteisfunktio

!!! note "Määritelmä"
    Jos $f : A \to B$ ja $g : B \to C$, niin **yhdistetty funktio** $g \circ f : A \to C$ määritellään
    $$(g \circ f)(x) = g(f(x)).$$
    Ensin $f$, sitten $g$ — luetaan "oikealta vasemmalle".

Tämä on täsmälleen se rakenne, jonka takana **ketjusääntö** piilee: kun derivoit $\sin(x^2)$, käsittelet yhdistettyä funktiota $g \circ f$, missä $f(x) = x^2$ ja $g(u) = \sin u$. Ketjusääntö kertoo, miten yhdistetyn funktion derivaatta rakentuu osiensa derivaatoista.

!!! note "Määritelmä"
    Funktio $f : A \to B$ on **kääntyvä**, jos on olemassa funktio $f^{-1} : B \to A$, jolle
    $$f^{-1}(f(x)) = x \text{ kaikilla } x \in A \qquad\text{ja}\qquad f(f^{-1}(y)) = y \text{ kaikilla } y \in B.$$
    Tällöin $f^{-1}$ on $f$:n **käänteisfunktio**: se "purkaa" sen, minkä $f$ teki.

Milloin funktio on kääntyvä? Täsmälleen silloin, kun se on bijektio — ja tämä yhdistää koko luvun:

!!! abstract "Lause 2.5"
    Funktio $f : A \to B$ on kääntyvä täsmälleen silloin, kun se on bijektio.

**Todistus (idea).** Jotta $f^{-1}(y)$ olisi määritelty jokaisella $y \in B$, tarvitaan että jokaisella $y$:llä *on* alkukuva — eli $f$ on **surjektio**. Jotta $f^{-1}(y)$ olisi yksikäsitteinen (funktio saa antaa vain yhden arvon), tarvitaan että alkukuvia on vain yksi — eli $f$ on **injektio**. Molemmat yhdessä: bijektio. $\blacksquare$

Tässä on nyt täsmällinen versio siitä, mitä pohdit neliöjuuren kohdalla:

- $f(x) = x^2$ koko joukolla $\mathbb{R}$ **ei ole** bijektio, joten sillä ei ole käänteisfunktiota. ("Kaksi $y$-arvoa" tarkoittaa: injektiivisyys pettää.)
- Mutta rajoita $f(x) = x^2$ joukolle $[0, \infty)$ — vain ei-negatiiviset $x$ — ja se **on** bijektio joukolle $[0, \infty)$. Nyt käänteisfunktio on olemassa: se on $\sqrt{}$.

Neliöjuuri on siis $x^2$:n käänteisfunktio *sillä ehdolla*, että rajoitat lähtöjoukon puolikkaaseen, jolla $x^2$ on injektio. Havaintosi vaakaparaabelista oli täsmälleen tämä, ja nyt sinulla on sille täsmällinen kieli.

!!! tip "Käänteisfunktio geometrisesti"
    Käänteisfunktion kuvaaja on alkuperäisen kuvaaja **peilattuna suoran $y = x$ suhteen**. Peilaus vaihtaa $x$:n ja $y$:n roolit — juuri se, mitä käänteisfunktion ottaminen tekee. Siksi $y = \sqrt x$ on $y = x^2$ peilattuna, kuten jo huomasit.

---

## 2.8 Yhteenveto

- **Joukko** on kokoelma erillisiä alkioita; sen määrää täysin jäsenyys.
- $A = B$ todistetaan **kaksoissisältymisellä**: $A \subseteq B$ ja $B \subseteq A$.
- $n$-alkioisella joukolla on $2^n$ osajoukkoa.
- Operaatiot $\cup, \cap, \setminus$ ovat logiikan "tai, ja, ei" pukeutuneina joukoiksi.
- **Funktio** liittää jokaiseen lähtöalkioon täsmälleen yhden arvon.
- **Injektio** ei törmää, **surjektio** peittää, **bijektio** tekee molemmat.
- Funktio on **kääntyvä** täsmälleen silloin, kun se on bijektio — ja käänteisfunktio on kuvaaja peilattuna suoran $y=x$ yli.

---

## Harjoitukset

Yritä jokaista tehtävää itse ennen kuin avaat vihjeen tai vastauksen.

---

**2.1 (★)** Olkoot $A = \{1,2,3,4,5\}$ ja $B = \{2,4,6\}$. Määritä $A \cup B$, $A \cap B$, $A \setminus B$ ja $B \setminus A$.

??? success "Vastaus"
    $$A \cup B = \{1,2,3,4,5,6\}, \quad A \cap B = \{2,4\},$$
    $$A \setminus B = \{1,3,5\}, \quad B \setminus A = \{6\}.$$

    Huomaa, että $A \setminus B \neq B \setminus A$ — erotus ei ole vaihdannainen.

---

**2.2 (★)** Luettele joukon $A = \{a, b, c\}$ kaikki osajoukot. Montako niitä on, ja täsmääkö se Lauseen 2.2 kanssa?

??? success "Vastaus"
    Osajoukot:
    $$\varnothing,\; \{a\},\; \{b\},\; \{c\},\; \{a,b\},\; \{a,c\},\; \{b,c\},\; \{a,b,c\}.$$

    Niitä on $8 = 2^3$, mikä täsmää Lauseen 2.2 kanssa ($n = 3$ alkiota). Muista laskea mukaan sekä $\varnothing$ että koko joukko $A$ itse. $\blacksquare$

---

**2.3 (★★)** Onko funktio $f : \mathbb{R} \to \mathbb{R}$, $f(x) = x^2 + 1$, injektio? Entä surjektio? Perustele molemmat.

??? tip "Vihje"
    Injektiolle: löydätkö kaksi eri $x$:ää, joilla on sama arvo? Surjektiolle: mitkä arvot funktio voi ylipäätään saada?

??? success "Vastaus"
    **Ei injektio:** $f(-1) = 2 = f(1)$, mutta $-1 \neq 1$. Kaksi eri syötettä, sama arvo.

    **Ei surjektio:** koska $x^2 \geq 0$, on $f(x) = x^2 + 1 \geq 1$ kaikilla $x$. Siis esimerkiksi arvoa $y = 0$ ei koskaan saavuteta — maalijoukon $\mathbb{R}$ alkioita jää peittämättä. $\blacksquare$

---

**2.4 (★★)** Todista, että funktio $f : \mathbb{R} \to \mathbb{R}$, $f(x) = 5x - 3$, on bijektio, ja määritä sen käänteisfunktio $f^{-1}$.

??? tip "Vihje"
    Injektio: oleta $f(x_1) = f(x_2)$, päättele $x_1 = x_2$. Surjektio ja käänteisfunktio: ratkaise yhtälö $y = 5x - 3$ muuttujan $x$ suhteen.

??? success "Vastaus"
    *Injektio.* Jos $5x_1 - 3 = 5x_2 - 3$, niin lisäämällä $3$ ja jakamalla viidellä saadaan $x_1 = x_2$.

    *Surjektio ja käänteisfunktio.* Olkoon $y \in \mathbb{R}$. Ratkaistaan $y = 5x - 3$:
    $$x = \frac{y + 3}{5}.$$
    Tämä $x$ on reaaliluku, ja $f\!\left(\frac{y+3}{5}\right) = 5 \cdot \frac{y+3}{5} - 3 = y$, joten jokainen $y$ saavutetaan. Funktio on bijektio, ja

    $$f^{-1}(y) = \frac{y + 3}{5}. \qquad \blacksquare$$

---

**2.5 (★★)** Olkoot $f(x) = x^2$ ja $g(x) = x + 1$ (molemmat $\mathbb{R} \to \mathbb{R}$). Määritä $(g \circ f)(x)$ ja $(f \circ g)(x)$. Ovatko ne samat?

??? success "Vastaus"
    $$(g \circ f)(x) = g(f(x)) = g(x^2) = x^2 + 1,$$
    $$(f \circ g)(x) = f(g(x)) = f(x+1) = (x+1)^2 = x^2 + 2x + 1.$$

    Ne **eivät** ole samat: yhdistäminen ei ole vaihdannainen. Järjestyksellä on väliä — ensin neliöön ja sitten $+1$ on eri asia kuin ensin $+1$ ja sitten neliöön. $\blacksquare$

---

**2.6 (★★)** Todista kaksoissisältymisellä: $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$. *(Tämä on leikkauksen "osittelulaki".)*

??? tip "Vihje"
    Ota mielivaltainen $x$ vasemmasta joukosta, pura määritelmät ("$x \in A$ ja ($x \in B$ tai $x \in C$)"), ja järjestä uudelleen. Tee sitten sama toiseen suuntaan.

??? success "Vastaus"
    *($\subseteq$)* Olkoon $x \in A \cap (B \cup C)$. Silloin $x \in A$ ja $x \in B \cup C$, eli $x \in A$ ja ($x \in B$ tai $x \in C$).

    - Jos $x \in B$: yhdessä $x \in A$:n kanssa saadaan $x \in A \cap B$.
    - Jos $x \in C$: samoin $x \in A \cap C$.

    Kummassakin tapauksessa $x \in (A \cap B) \cup (A \cap C)$.

    *($\supseteq$)* Olkoon $x \in (A \cap B) \cup (A \cap C)$. Silloin $x \in A \cap B$ tai $x \in A \cap C$. Kummassakin tapauksessa $x \in A$, ja lisäksi $x \in B$ tai $x \in C$, eli $x \in B \cup C$. Siis $x \in A \cap (B \cup C)$.

    Molemmat sisältymiset pätevät, joten joukot ovat samat. $\blacksquare$

    *(Tämä on täsmälleen logiikan laki "$P$ ja ($Q$ tai $R$)" $=$ "($P$ ja $Q$) tai ($P$ ja $R$)", puettuna joukoiksi.)*

---

**2.7 (★★★)** Olkoot $f : A \to B$ ja $g : B \to C$ molemmat injektioita. Todista, että yhdistetty funktio $g \circ f : A \to C$ on injektio.

??? tip "Vihje"
    Käytä injektiivisyyden tekniikkaa: oleta $(g \circ f)(x_1) = (g \circ f)(x_2)$ ja pura se auki. Sovella ensin $g$:n injektiivisyyttä, sitten $f$:n.

??? success "Vastaus"
    Oletetaan $(g \circ f)(x_1) = (g \circ f)(x_2)$, eli

    $$g(f(x_1)) = g(f(x_2)).$$

    Koska $g$ on injektio, sama arvo tarkoittaa samaa syötettä:

    $$f(x_1) = f(x_2).$$

    Koska $f$ on injektio, tästä seuraa

    $$x_1 = x_2.$$

    Siis $(g \circ f)(x_1) = (g \circ f)(x_2) \Rightarrow x_1 = x_2$, eli $g \circ f$ on injektio. $\blacksquare$

    *(Sama pätee surjektioille ja siten bijektioille: kahden bijektion yhdiste on bijektio. Tätä Cantor käyttää luvussa 28 osoittaakseen, että "samankokoisuus" on äärettömille joukoille johdonmukainen käsite.)*

---

**2.8 (★★★)** Osoita, että funktio $f : \mathbb{R} \setminus \{1\} \to \mathbb{R} \setminus \{1\}$, määritelty kaavalla $f(x) = \dfrac{x+1}{x-1}$, on oma käänteisfunktionsa, eli $f(f(x)) = x$.

??? tip "Vihje"
    Laske $f(f(x))$ sijoittamalla $f(x)$ kaavaan $f$:n paikalle. Sievennä murtolukujen murtoluku kertomalla osoittaja ja nimittäjä läpi luvulla $(x-1)$.

??? success "Vastaus"
    Sijoitetaan $f(x) = \dfrac{x+1}{x-1}$ funktioon $f$:

    $$f(f(x)) = \frac{f(x) + 1}{f(x) - 1} = \frac{\dfrac{x+1}{x-1} + 1}{\dfrac{x+1}{x-1} - 1}.$$

    Kerrotaan sekä osoittaja että nimittäjä luvulla $(x-1)$:

    $$= \frac{(x+1) + (x-1)}{(x+1) - (x-1)} = \frac{2x}{2} = x.$$

    Siis $f(f(x)) = x$: funktio on oma käänteisfunktionsa. (Tällaista funktiota kutsutaan **involuutioksi** — se palauttaa alkutilan, kun sitä sovelletaan kahdesti. Peilaus ja käännös ovat muita esimerkkejä.) $\blacksquare$

---

*Seuraava luku: Induktio ja rekursio — miten yhdellä siemenellä ja yhdellä säännöllä rakennetaan ääretön.*
