# Luku 15: Renkaat ja kunnat

Ryhmässä oli yksi laskutoimitus. Mutta luvut, joita tunnet, kantavat **kahta**: yhteenlaskua *ja* kertolaskua, sidottuina toisiinsa osittelulailla $a(b+c) = ab + ac$. Rakennetta, jolla on nämä molemmat, kutsutaan **renkaaksi**, ja sen erityisen sivistynyttä muotoa **kunnaksi**. Kunnat ovat se maaperä, jolla polynomit, yhtälöt ja koko koulualgebra elävät — ja tässä luvussa näet *miksi* alkuluvut ratkaisevat, milloin jako onnistuu.

---

## 15.1 Rengas

!!! note "Määritelmä"
    **Rengas** on joukko $R$ varustettuna kahdella laskutoimituksella, yhteenlaskulla $+$ ja kertolaskulla $\cdot$, niin että:

    1. $(R, +)$ on Abelin ryhmä (neutraalialkio $0$, vasta-alkiot $-a$).
    2. Kertolasku on liitännäinen: $(ab)c = a(bc)$.
    3. **Osittelulait** sitovat operaatiot: $a(b+c) = ab + ac$ ja $(a+b)c = ac + bc$.

    Rengas on **vaihdannainen**, jos $ab = ba$, ja siinä on **ykkösalkio**, jos on olemassa $1 \neq 0$, jolle $1 \cdot a = a \cdot 1 = a$.

Tässä kirjassa "rengas" tarkoittaa jatkossa **vaihdannaista rengasta, jossa on ykkösalkio** — se riittää kaikkeen, mitä tarvitsemme.

### Esimerkkejä

- **$\mathbb{Z}$** — kokonaisluvut. Perusesimerkki: yhteen-, vähennys- ja kertolasku onnistuvat, mutta jako ei aina.
- **$\mathbb{Q}, \mathbb{R}, \mathbb{C}$** — nämä ovat renkaita ja vieläpä kuntia (kohta).
- **$\mathbb{Z}_n$** — kellon aritmetiikka modulo $n$, nyt *molemmilla* laskutoimituksilla. Esim. $\mathbb{Z}_{12}$:ssä $5 \cdot 5 = 25 \equiv 1$.
- **Polynomit $R[x]$** — kaikki polynomit, joiden kertoimet ovat renkaassa $R$. Näistä luku 16.

Ryhmässä oli neljä lakia; renkaassa on enemmän, koska kaksi operaatiota on saatava toimimaan yhdessä. Mutta idea on sama: **luetellaan pelisäännöt, ja tutkitaan kaikkea, mikä niitä tottelee.**

---

## 15.2 Nollan omituisuudet

Yksi asia, jonka lukujen kanssa opimme pitämään itsestäänselvänä, ei päde kaikissa renkaissa — ja juuri se ero on kiinnostava.

!!! abstract "Lause 15.1"
    Jokaisessa renkaassa $0 \cdot a = 0$.

**Todistus.** $0 \cdot a = (0 + 0) \cdot a = 0 \cdot a + 0 \cdot a$ (osittelulaki). Vähennetään $0 \cdot a$ molemmilta puolilta (mahdollista, koska $(R,+)$ on ryhmä): $0 = 0 \cdot a$. $\blacksquare$

Reaaliluvuilla pätee myös käänteinen tuttu tosiasia: *jos $ab = 0$, niin $a = 0$ tai $b = 0$.* Mutta tämä **ei päde kaikissa renkaissa!**

!!! note "Määritelmä"
    Renkaan nollasta eroava alkio $a$ on **nollanjakaja**, jos on olemassa nollasta eroava $b$, jolle $ab = 0$.

Esimerkki: renkaassa $\mathbb{Z}_6$ pätee $2 \cdot 3 = 6 \equiv 0$, vaikka $2 \neq 0$ ja $3 \neq 0$. Luvut $2$ ja $3$ ovat nollanjakajia. Kaksi "positiivista" asiaa kertoutuu tyhjäksi — mahdotonta kokonaisluvuilla, arkipäivää kellon aritmetiikassa.

!!! note "Määritelmä"
    Rengas, jossa **ei ole nollanjakajia**, on **kokonaisalue**.

$\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$ ja $\mathbb{C}$ ovat kokonaisalueita. $\mathbb{Z}_6$ ei ole. Kokonaisalueissa "tulo on nolla vain jos tekijä on nolla" — ja siksi niissä yhtälöt käyttäytyvät kuten koulussa opit.

---

## 15.3 Yksiköt ja kunnat

Renkaassa voi aina laskea yhteen, vähentää ja kertoa. Milloin voi myös **jakaa**? Jakaminen on kertominen käänteisluvulla — joten kysymme, milloin käänteisluvut ovat olemassa.

!!! note "Määritelmä"
    Renkaan alkio $a$ on **yksikkö** (kääntyvä), jos sillä on kertolaskun käänteisalkio: on olemassa $a^{-1}$, jolle $a a^{-1} = 1$.

Kokonaisluvuissa $\mathbb{Z}$ vain $1$ ja $-1$ ovat yksiköitä (harjoitus 14.1). Rationaaliluvuissa $\mathbb{Q}$ **jokainen** nollasta eroava luku on yksikkö. Juuri tämä ero antaa aiheen tärkeimmälle määritelmälle koko algebrassa:

!!! note "Määritelmä"
    **Kunta** on vaihdannainen rengas, jossa $1 \neq 0$ ja jossa **jokainen nollasta eroava alkio on yksikkö** — eli jokaisella nollasta eroavalla alkiolla on käänteisluku.

Kunnassa onnistuvat kaikki neljä laskutoimitusta (paitsi nollalla jako). $\mathbb{Q}$, $\mathbb{R}$ ja $\mathbb{C}$ ovat kuntia; $\mathbb{Z}$ ei ole. Kunta on algebran "täydellinen" laskuympäristö — ja huomaa yhteys lukuun 4, jossa tapasit tämän käsitteen ensi kertaa.

!!! abstract "Lause 15.2"
    Jokainen kunta on kokonaisalue (ei nollanjakajia).

**Todistus.** Oletetaan $ab = 0$ kunnassa, ja että $a \neq 0$. Koska $a$ on yksikkö, kerrotaan vasemmalta alkiolla $a^{-1}$:
$$a^{-1}(ab) = a^{-1} \cdot 0 \implies (a^{-1}a)b = 0 \implies b = 0.$$
Siis jos $a \neq 0$, niin $b = 0$ — nollanjakajia ei ole. $\blacksquare$

---

## 15.4 Milloin $\mathbb{Z}_n$ on kunta?

Nyt saavutamme luvun huipennuksen — ja se sitoo yhteen alkuluvut, ryhmät ja jaon.

Kellon aritmetiikka $\mathbb{Z}_n$ on aina rengas. Mutta koska se voi sisältää nollanjakajia (kuten $\mathbb{Z}_6$), se ei aina ole kunta. Milloin on?

!!! abstract "Lause 15.3"
    $\mathbb{Z}_n$ on kunta täsmälleen silloin, kun $n$ on alkuluku.

**Todistus.**

*(Jos $n$ ei ole alkuluku, $\mathbb{Z}_n$ ei ole kunta.)* Jos $n = ab$, missä $1 < a, b < n$, niin $\mathbb{Z}_n$:ssä $a \cdot b = n \equiv 0$, vaikka $a, b \neq 0$. Siis $a$ on nollanjakaja, ja Lauseen 15.2 nojalla $\mathbb{Z}_n$ ei voi olla kunta.

*(Jos $n = p$ on alkuluku, $\mathbb{Z}_p$ on kunta.)* Riittää osoittaa, että jokaisella nollasta eroavalla $a \in \{1, \ldots, p-1\}$ on käänteisalkio. Koska $p$ on alkuluku eikä $a$ ole sen monikerta, on $\operatorname{syt}(a, p) = 1$. **Bézout'n identiteetin** nojalla on olemassa kokonaisluvut $x, y$, joille

$$ax + py = 1.$$

Otetaan tästä jäännös modulo $p$: koska $py \equiv 0$, saadaan $ax \equiv 1 \pmod p$. Siis $x \bmod p$ on alkion $a$ käänteisalkio. Jokaisella nollasta eroavalla alkiolla on käänteisalkio, joten $\mathbb{Z}_p$ on kunta. $\blacksquare$

Tässä on syvä kauneus: **alkuluvun jakamattomuus lukuteoriassa** on *sama asia* kuin **jakolaskun onnistuminen algebrassa**. Nämä äärelliset kunnat $\mathbb{Z}_p$ ovat modernin salauksen (RSA, elliptiset käyrät) ja koodausteorian perusta — koko digitaalinen maailma lepää tämän lauseen varassa.

Ja huomaa, mikä lupaus nyt lunastui: luvussa 14 oletimme, että $(\mathbb{Z}_p^*, \cdot)$ on ryhmä (jotta Fermat'n pieni lause toimisi). Juuri todistimme sen: koska $\mathbb{Z}_p$ on kunta, jokaisella nollasta eroavalla alkiolla on käänteisalkio, joten ne muodostavat ryhmän kertolaskulla. Palaset loksahtavat.

---

## 15.5 Yhteenveto

- **Rengas** = joukko, jossa on yhteen- ja kertolasku osittelulakeineen (esim. $\mathbb{Z}$, $\mathbb{Z}_n$, polynomit).
- **Nollanjakaja:** nollasta eroava alkio, jonka tulo toisen kanssa on nolla (esim. $2$ ja $3$ renkaassa $\mathbb{Z}_6$). **Kokonaisalue** = rengas ilman niitä.
- **Kunta** = rengas, jossa jokaisella nollasta eroavalla alkiolla on käänteisalkio; kaikki neljä laskutoimitusta onnistuvat.
- **$\mathbb{Z}_n$ on kunta täsmälleen kun $n$ on alkuluku** — alkulukujen jakamattomuus = jakolaskun onnistuminen.

---

## Harjoitukset

**15.1 (★)** Etsi renkaasta $\mathbb{Z}_{10}$ kaikki nollanjakajat. *(Etsi nollasta eroavat $a$, joille on olemassa nollasta eroava $b$ tulolla $ab \equiv 0$.)*

??? success "Vastaus"
    Nollanjakajat ovat luvut, joilla on yhteinen tekijä $10 = 2 \cdot 5$:n kanssa: $2, 4, 5, 6, 8$.
    Esimerkiksi $2 \cdot 5 = 10 \equiv 0$, $4 \cdot 5 = 20 \equiv 0$, $6 \cdot 5 = 30 \equiv 0$, $8 \cdot 5 = 40 \equiv 0$, $5 \cdot 2 = 0$.
    Luvut $1, 3, 7, 9$ (jotka ovat suhteellisia alkulukuja $10$:n kanssa) *eivät* ole nollanjakajia — ne ovat yksiköitä. $\blacksquare$

---

**15.2 (★)** Onko $\mathbb{Z}_7$ kunta? Entä $\mathbb{Z}_8$? Perustele Lauseella 15.3.

??? success "Vastaus"
    $\mathbb{Z}_7$ **on** kunta, koska $7$ on alkuluku. $\mathbb{Z}_8$ **ei ole** kunta, koska $8 = 2^3$ ei ole alkuluku (esim. $2 \cdot 4 = 8 \equiv 0$, joten $2$ on nollanjakaja). $\blacksquare$

---

**15.3 (★★)** Etsi luvun $3$ käänteisalkio kunnassa $\mathbb{Z}_7$. *(Eli luku $x$, jolle $3x \equiv 1 \pmod 7$.)*

??? tip "Vihje"
    Kokeile arvoja $x = 1, 2, \ldots, 6$, tai käytä Bézout'ta: etsi $x, y$ joille $3x + 7y = 1$.

??? success "Vastaus"
    Etsitään $x$, jolle $3x \equiv 1 \pmod 7$. Kokeilemalla: $3 \cdot 5 = 15 = 14 + 1 \equiv 1 \pmod 7$. Siis $3^{-1} = 5$ kunnassa $\mathbb{Z}_7$. $\blacksquare$

    *(Tarkistus Bézout'lla: $3 \cdot 5 - 7 \cdot 2 = 15 - 14 = 1$. ✓)*

---

**15.4 (★★)** Todista, että kokonaisalueessa pätee supistussääntö: jos $a \neq 0$ ja $ab = ac$, niin $b = c$. *(Huomaa: tämä ei vaadi käänteisalkiota — siksi se pätee jo kokonaisalueessa, ei vain kunnassa.)*

??? tip "Vihje"
    Siirrä kaikki samalle puolelle ja ota yhteinen tekijä. Käytä nollanjakajattomuutta.

??? success "Vastaus"
    Oletuksesta $ab = ac$ seuraa $ab - ac = 0$, eli osittelulailla
    $$a(b - c) = 0.$$
    Koska kyseessä on kokonaisalue eikä $a = 0$, ei $a$ voi olla nollanjakaja, joten toisen tekijän on oltava nolla: $b - c = 0$, eli $b = c$. $\blacksquare$

    *(Huomaa, ettei tämä päde nollanjakajallisessa renkaassa: $\mathbb{Z}_6$:ssa $2 \cdot 1 = 2 \cdot 4$ mutta $1 \neq 4$.)*

---

**15.5 (★★★)** Olkoon $R$ äärellinen kokonaisalue. Todista, että $R$ on kunta. *(Eli: äärellisessä maailmassa nollanjakajattomuus riittää jo takaamaan käänteisalkiot.)*

??? tip "Vihje"
    Ota nollasta eroava $a \in R$ ja tarkastele kuvausta $x \mapsto ax$. Osoita supistussäännön (harjoitus 15.4) avulla, että se on injektio, ja päättele äärellisyydestä, että se on surjektio — joten jokin $x$ kuvautuu ykköseksi.

??? success "Vastaus"
    Olkoon $a \in R$, $a \neq 0$. Tarkastellaan kuvausta $f : R \to R$, $f(x) = ax$.

    *$f$ on injektio:* jos $ax_1 = ax_2$, niin harjoituksen 15.4 supistussäännön (pätee kokonaisalueessa) nojalla $x_1 = x_2$.

    *$f$ on surjektio:* injektiivinen kuvaus äärellisestä joukosta itseensä on aina myös surjektio (se ei voi "hukata" alkioita, koska niitä on äärellinen määrä eikä kaksi kuvaudu samaan). 

    Koska $f$ on surjektio, jokin $x \in R$ kuvautuu ykköseksi: $ax = 1$. Siis $a$:lla on käänteisalkio. Koska $a$ oli mielivaltainen nollasta eroava alkio, $R$ on kunta. $\blacksquare$

    *(Tämä on kaunis äärellisyyden voima: ääretön kokonaisalue $\mathbb{Z}$ ei ole kunta, mutta jokainen äärellinen on. Tästä seuraa, että äärelliset kunnat ovat täsmälleen $\mathbb{Z}_p$ ja niiden laajennukset — mutta se on jo pidemmän tarinan aihe.)*

---

*Seuraava luku: Polynomit — renkaan konkreettisin ja hyödyllisin esimerkki, ja kotisi, jossa kokonaisjuuret-menetelmäsi vihdoin todistetaan.*
