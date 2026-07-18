# Luku 4: Luvuista

Olet käyttänyt lukuja koko elämäsi. Mutta *mitä luvut ovat*? Tässä luvussa rakennamme lukujärjestelmät perustuksista: luonnollisista luvuista kokonaislukuihin ja edelleen rationaalilukuihin. Jokainen laajennus syntyy samasta tarpeesta — **ratkaista yhtälö, jota edellinen järjestelmä ei osannut.** Ja luvun lopussa törmäämme ensimmäistä kertaa seinään, jota edes rationaaliluvut eivät ylitä. Se seinä on seuraavan luvun aihe.

---

## 4.1 Luonnolliset luvut

Kaikki alkaa laskemisesta: $0, 1, 2, 3, \ldots$ Nämä ovat **luonnolliset luvut** $\mathbb{N}$. Giuseppe Peano osoitti 1889, että koko niiden rakenne seuraa muutamasta yksinkertaisesta perusoletuksesta.

!!! note "Peanon aksioomat (epämuodollisesti)"
    1. $0$ on luonnollinen luku.
    2. Jokaisella luonnollisella luvulla $n$ on **seuraaja** $S(n)$ (ajattele: $n+1$).
    3. $0$ ei ole minkään luvun seuraaja.
    4. Eri luvuilla on eri seuraajat.
    5. **Induktioperiaate:** jos joukko sisältää $0$:n ja jokaisen jäsenensä seuraajan, se sisältää kaikki luonnolliset luvut.

Huomaa viides aksiooma: **induktio ei ole temppu vaan luonnollisten lukujen määritelmän osa.** Se, mitä luvussa 3 käytit todistusvälineenä, on itse asiassa se, mikä tekee luvuista luonnollisia. Yhteenlasku ja kertolasku määritellään näistä rekursiivisesti (esim. $n + 0 = n$ ja $n + S(m) = S(n+m)$), ja kaikki tutut laskusäännöt seuraavat induktiolla.

Luonnolliset luvut riittävät laskemiseen ja yhteenlaskuun. Mutta yhtälö

$$x + 3 = 1$$

ei ratkea niissä — vastaus olisi $-2$, jota ei ole. **Tarvitaan lisää lukuja.**

---

## 4.2 Kokonaisluvut

Laajennetaan järjestelmää niin, että vähennyslasku onnistuu aina. Tulos on **kokonaisluvut**

$$\mathbb{Z} = \{\, \ldots, -3, -2, -1, 0, 1, 2, 3, \ldots \,\}.$$

Miten negatiiviset luvut *rakennetaan*, jos käytössä on vain luonnolliset luvut? Nokkela idea: **kokonaisluku on erotus** — pari luonnollisia lukuja $(a, b)$, joka edustaa lukua "$a - b$". Mutta $(3, 1)$, $(4, 2)$ ja $(10, 8)$ edustavat kaikki samaa lukua $2$. Ne on siis samaistettava:

$$(a, b) \sim (c, d) \quad\text{täsmälleen kun}\quad a + d = b + c.$$

(Huomaa: ehto $a + d = b + c$ välttää vähennyslaskun — se käyttää vain yhteenlaskua, joka on jo määritelty.) Kokonaisluku *on* tällaisten samanarvoisten parien luokka. Tämä on ensimmäinen kohtaamisesi **ekvivalenssiluokan** kanssa: rakennetaan uusi olio niputtamalla vanhoja, jotka halutaan samaistaa.

Lopputulos on tuttu: $\mathbb{Z}$ on **rengas** — siinä voi laskea yhteen, vähentää ja kertoa, ja tutut lait (vaihdanta, liitäntä, osittelu) pätevät. Mutta yhtälö

$$3x = 1$$

ei vieläkään ratkea: vastaus olisi $\frac13$, jota ei ole kokonaislukuna. **Tarvitaan taas lisää.**

---

## 4.3 Rationaaliluvut

Nyt halutaan, että jakolasku (nollalla jakamista lukuun ottamatta) onnistuu aina. Sama temppu kuin äsken, mutta erotuksen sijaan **osamäärä**: rationaaliluku on pari $(a, b)$ kokonaislukuja, $b \neq 0$, joka edustaa murtolukua $\frac{a}{b}$ — ja samaistetaan yhtä suuret murtoluvut:

$$\frac{a}{b} \sim \frac{c}{d} \quad\text{täsmälleen kun}\quad ad = bc.$$

Näin syntyy **rationaalilukujen** joukko

$$\mathbb{Q} = \left\{\, \frac{a}{b} \;\middle|\; a, b \in \mathbb{Z},\; b \neq 0 \,\right\}.$$

Rationaaliluvuissa kaikki neljä peruslaskutoimitusta onnistuvat (paitsi nollalla jako). Tällaista rakennetta kutsutaan **kunnaksi**.

!!! note "Kunta"
    **Kunta** on joukko, jossa on yhteen- ja kertolasku, jotka tottelevat tuttuja lakeja, ja jossa jokaisella alkiolla on vasta-alkio (yhteenlaskun käänteinen) ja jokaisella nollasta eroavalla alkiolla käänteisalkio (kertolaskun käänteinen). Lyhyesti: kunnassa voi laskea yhteen, vähentää, kertoa ja jakaa (paitsi nollalla).

$\mathbb{Q}$, $\mathbb{R}$ ja $\mathbb{C}$ ovat kaikkia kuntia; $\mathbb{Z}$ ei ole (siitä puuttuvat käänteisluvut). Kunnat ovat algebran keskeisin rakenne, ja palaamme niihin luvussa 16.

---

## 4.4 Rationaalilukujen tiheys

Rationaaliluvuilla on ominaisuus, jota kokonaisluvuilla ei ole: niitä on "kaikkialla".

!!! abstract "Lause 4.1 (tiheys)"
    Minkä tahansa kahden eri rationaaliluvun välissä on toinen rationaaliluku.

**Todistus.** Olkoot $r < s$ rationaalilukuja. Niiden keskiarvo

$$m = \frac{r + s}{2}$$

on rationaalinen (rationaalilukujen summa ja jako kahdella pysyvät rationaalisina), ja koska $r < s$, pätee $r < m < s$. $\blacksquare$

Seuraus on hämmästyttävä: koska kahden rationaaliluvun välistä löytyy aina uusi, **niiden välissä on itse asiassa äärettömän monta.** Rationaaliluvuilla ei ole "seuraavaa" lukua — toisin kuin kokonaisluvuilla, joilla $5$:n jälkeen tulee $6$. Rationaalilukujen suora vaikuttaa täysin täyteen pakatulta.

!!! warning "Tiheä mutta täynnä reikiä"
    "Tiheä" ei tarkoita "aukoton"! Vaikka rationaalilukuja on joka välissä äärettömän monta, niiden seassa on silti *reikiä* — kohtia, joissa pitäisi olla luku mutta ei ole. Seuraava osio paljastaa ensimmäisen.

---

## 4.5 Seinä: rationaalilukujen reikä

Palataan lukuun, jonka tunnet: $\sqrt2$. Todistit jo (luku 1), että se ei ole rationaalinen. Katsotaan nyt, *mitä* se paljastaa rationaalilukujen rakenteesta.

Tarkastellaan kahta rationaalilukujen joukkoa:

$$A = \{\, x \in \mathbb{Q} \mid x > 0,\; x^2 < 2 \,\}, \qquad B = \{\, x \in \mathbb{Q} \mid x > 0,\; x^2 > 2 \,\}.$$

$A$ sisältää luvut, jotka ovat "liian pieniä ollakseen $\sqrt2$" ($1$, $1{,}4$, $1{,}41$, …), ja $B$ ne, jotka ovat "liian suuria" ($2$, $1{,}5$, $1{,}42$, …). Yhdessä ne kattavat melkein kaikki positiiviset rationaaliluvut — väliin ei jää yhtään rationaalilukua, koska mikään rationaaliluku ei toteuta $x^2 = 2$.

Ja nyt terävä havainto, jonka teit jo harjoituksessa 1.8:

- Joukolla $A$ **ei ole suurinta alkiota.** Mille tahansa $x \in A$ löytyy suurempi rationaaliluku, joka on yhä $A$:ssa (todistit tämän).
- Joukolla $B$ ei ole pienintä alkiota.

Rationaalilukujen maailmassa $A$ vain "kurottaa ylöspäin" saavuttamatta koskaan mitään ylärajaa, ja $B$ kurottaa alaspäin. **Niiden väliin jää reikä** — kohta, jossa luvun $\sqrt2$ pitäisi olla, mutta jossa ei ole rationaalilukua.

!!! tip "Tässä syntyy sinun täydellisyys-teoriasi"
    Huomaatko? Joukko $A$ on täsmälleen se tilanne, jota pohdit: määrä, jolla ei ole maksimia, mutta joka lähestyy jotakin. Rationaaliluvuissa se "jotakin" *puuttuu* — reikä on aito. Seuraava luku täyttää reiän: se rakentaa reaaliluvut niin, että jokaisen tällaisen kurottavan joukon yläpuolella **on** luku (supremum), vaikkei maksimia olisikaan. Sitä täyttämistä kutsutaan **täydellisyydeksi**.

---

## 4.6 Yhteenveto

- $\mathbb{N} \subseteq \mathbb{Z} \subseteq \mathbb{Q}$ — jokainen laajennus ratkaisee yhtälön, jota edellinen ei osannut (vähennys, jako).
- Uudet luvut *rakennetaan* vanhoista ekvivalenssiluokkina (erotukset → $\mathbb{Z}$, osamäärät → $\mathbb{Q}$).
- $\mathbb{Q}$ on **kunta**: yhteen-, vähennys-, kerto- ja jakolasku onnistuvat.
- $\mathbb{Q}$ on **tiheä**: joka välissä äärettömän monta lukua — mutta silti täynnä **reikiä** (esim. $\sqrt2$:n kohdalla).

---

## Harjoitukset

**4.1 (★)** Mitkä seuraavista yhtälöistä ovat ratkeavia joukossa $\mathbb{N}$, mitkä vasta $\mathbb{Z}$:ssa, mitkä vasta $\mathbb{Q}$:ssa? (a) $x + 5 = 9$, (b) $x + 9 = 5$, (c) $4x = 2$, (d) $2x = 8$.

??? success "Vastaus"
    - (a) $x = 4 \in \mathbb{N}$ — ratkeaa jo luonnollisissa luvuissa.
    - (b) $x = -4$ — vaatii $\mathbb{Z}$:n.
    - (c) $x = \frac12$ — vaatii $\mathbb{Q}$:n.
    - (d) $x = 4 \in \mathbb{N}$ — ratkeaa luonnollisissa luvuissa.

    Huomaa, ettei kertolasku aina vaadi $\mathbb{Q}$:ta: se riippuu luvuista.

---

**4.2 (★)** Osoita tiheyden avulla, että lukujen $\frac13$ ja $\frac12$ välissä on rationaaliluku, ja etsi yksi.

??? success "Vastaus"
    Keskiarvo:
    $$m = \frac{\frac13 + \frac12}{2} = \frac{\frac{2}{6} + \frac{3}{6}}{2} = \frac{5/6}{2} = \frac{5}{12}.$$
    Tarkistus: $\frac13 = \frac{4}{12} < \frac{5}{12} < \frac{6}{12} = \frac12$. ✓

---

**4.3 (★★)** Todista, että kahden rationaaliluvun summa on rationaalinen ja tulo on rationaalinen. *(Tämä on osa väitettä "$\mathbb{Q}$ on suljettu yhteen- ja kertolaskun suhteen".)*

??? tip "Vihje"
    Kirjoita luvut muodossa $\frac{a}{b}$ ja $\frac{c}{d}$ ja laske summa ja tulo yhteiseksi murtoluvuksi.

??? success "Vastaus"
    Olkoot luvut $\frac{a}{b}$ ja $\frac{c}{d}$ rationaalisia ($b, d \neq 0$). Silloin
    $$\frac{a}{b} + \frac{c}{d} = \frac{ad + bc}{bd}, \qquad \frac{a}{b} \cdot \frac{c}{d} = \frac{ac}{bd}.$$
    Molemmissa osoittaja ja nimittäjä ovat kokonaislukuja, ja nimittäjä $bd \neq 0$ (kahden nollasta eroavan kokonaisluvun tulo). Siis molemmat ovat rationaalilukuja. $\blacksquare$

---

**4.4 (★★)** Osoita, että jos $r$ on rationaalinen ja $x$ on irrationaalinen, niin $r + x$ on irrationaalinen. *(Vihje: ristiriita.)*

??? tip "Vihje"
    Oleta vastakohta, että $r + x$ olisi rationaalinen, ja ratkaise $x$.

??? success "Vastaus"
    Oletetaan vastakohta: $r + x$ on rationaalinen; merkitään $r + x = q \in \mathbb{Q}$. Silloin
    $$x = q - r.$$
    Mutta $q$ ja $r$ ovat rationaalisia, ja tehtävän 4.3 (sekä vasta-alkion) nojalla niiden erotus $q - r$ on rationaalinen. Siis $x$ olisi rationaalinen — ristiriita oletuksen kanssa, että $x$ on irrationaalinen. Siis $r + x$ on irrationaalinen. $\blacksquare$

    *(Seuraus: esimerkiksi $1 + \sqrt2$, $\frac12 + \sqrt2$ ja $\pi - 3$ ovat kaikki irrationaalisia.)*

---

**4.5 (★★★)** Osoita, että joukolla $A = \{\, x \in \mathbb{Q} \mid x > 0,\; x^2 < 2 \,\}$ ei ole suurinta alkiota. *(Tämä on harjoitus 1.8 uudessa muodossa — voit käyttää samaa konstruktiota.)*

??? tip "Vihje"
    Ota mielivaltainen $x \in A$ ja rakenna suurempi rationaaliluku $x + h$, joka on yhä $A$:ssa, valitsemalla $h$ tarpeeksi pieneksi. Käytä samaa arviota kuin harjoituksessa 1.8.

??? success "Vastaus"
    Olkoon $x \in A$, siis $x > 0$ rationaalinen ja $x^2 < 2$. Merkitään $d = 2 - x^2 > 0$ (rationaalinen). Valitaan rationaaliluku
    $$h = \frac{d}{2(2x+1)} > 0.$$
    Silloin $h < 1$ (koska $d < 2 < 2(2x+1)$), joten $h^2 < h$, ja
    $$(x+h)^2 = x^2 + 2xh + h^2 < x^2 + 2xh + h = x^2 + h(2x+1) = x^2 + \frac{d}{2} < x^2 + d = 2.$$
    Siis $x + h$ on rationaalinen, $x + h > x$, ja $(x+h)^2 < 2$, joten $x + h \in A$. Löysimme suuremman $A$:n alkion, joten $x$ ei voinut olla suurin. Koska $x$ oli mielivaltainen, joukolla $A$ ei ole suurinta alkiota. $\blacksquare$

    *(Juuri tämä "aina löytyy suurempi, mutta yläraja puuttuu $\mathbb{Q}$:sta" on rationaalilukujen reikä — ja seuraavan luvun lähtökohta.)*

---

*Seuraava luku: Reaaliluvut ja täydellisyys — reiän täyttäminen, ja täsmällinen kieli sille, mitä pohdit täydellisyydestä.*
