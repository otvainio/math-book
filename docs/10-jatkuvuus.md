# Luku 10: Jatkuvuus

Sanotaan, että funktio on jatkuva, jos "sen kuvaajan voi piirtää nostamatta kynää". Se on hyvä mielikuva — mutta ei matematiikkaa. Tässä luvussa annamme jatkuvuudelle täsmällisen määritelmän samalla $\varepsilon$-kielellä kuin raja-arvoille, ja todistamme sen avulla lauseen, joka on niin voimakas ja niin ilmeisen tuntuinen, että sen todistaminen tuntuu aluksi turhalta — kunnes huomaat, että se **on epätosi rationaaliluvuilla** ja pätee vain siksi, että reaaliluvut ovat täydelliset.

---

## 10.1 Funktion raja-arvo

Ennen jatkuvuutta tarvitsemme, mitä $f(x)$ lähestyy, kun $x$ lähestyy jotakin pistettä.

!!! note "Määritelmä (funktion raja-arvo)"
    $\displaystyle\lim_{x \to a} f(x) = L$ tarkoittaa: jokaista $\varepsilon > 0$ kohti on olemassa $\delta > 0$ siten, että
    $$0 < |x - a| < \delta \implies |f(x) - L| < \varepsilon.$$

Sama peli kuin jonoilla, mutta nyt molemmilla puolilla on jatkuva muuttuja. Vastustaja vaatii, että $f(x)$ on lähempänä lukua $L$ kuin $\varepsilon$; sinä vastaat lupaamalla, että näin käy aina kun $x$ on lähempänä pistettä $a$ kuin $\delta$. Luku $\delta$ ("kuinka lähelle $a$:ta") riippuu vaaditusta tarkkuudesta $\varepsilon$.

---

## 10.2 Jatkuvuuden määritelmä

!!! note "Määritelmä (jatkuvuus)"
    Funktio $f$ on **jatkuva pisteessä $a$**, jos
    $$\lim_{x \to a} f(x) = f(a).$$
    Auki kirjoitettuna: jokaista $\varepsilon > 0$ kohti on $\delta > 0$ siten, että
    $$|x - a| < \delta \implies |f(x) - f(a)| < \varepsilon.$$
    Funktio on **jatkuva** (välillä), jos se on jatkuva jokaisessa välin pisteessä.

Määritelmä vangitsee "ei hyppyjä" -idean täsmällisesti: **pienet muutokset syötteessä tuottavat pieniä muutoksia tuloksessa.** Jos vaadit $f(x)$:n pysyvän lähellä arvoa $f(a)$, riittää pitää $x$ tarpeeksi lähellä $a$:ta. Hyppäävä funktio pettää tämän: hypyn kohdalla $x$:n pienikin liike heittää $f(x)$:n kauas, olipa $\delta$ kuinka pieni tahansa.

**Esimerkki jatkuvasta funktiosta.** Vakiofunktio $f(x) = c$ on jatkuva: $|f(x) - f(a)| = 0 < \varepsilon$ aina, joten mikä tahansa $\delta$ kelpaa. Funktio $f(x) = x$ on jatkuva: valitse $\delta = \varepsilon$, jolloin $|x - a| < \delta$ antaa $|f(x)-f(a)| = |x - a| < \varepsilon$.

**Esimerkki epäjatkuvasta funktiosta.** Porrasfunktio
$$f(x) = \begin{cases} 0, & x < 0 \\ 1, & x \geq 0 \end{cases}$$
ei ole jatkuva pisteessä $0$: valitaan $\varepsilon = \frac12$. Miten pieni $\delta$ tahansa valitaan, löytyy negatiivinen $x$ (esim. $x = -\frac\delta2$), jolle $f(x) = 0$, mutta $|f(x) - f(0)| = |0 - 1| = 1 > \frac12$. Hyppy rikkoo jatkuvuuden.

---

## 10.3 Jatkuvien funktioiden algebra

Kuten raja-arvot, jatkuvuus periytyy peruspalikoista.

!!! abstract "Lause 10.1"
    Jos $f$ ja $g$ ovat jatkuvia pisteessä $a$, niin myös $f + g$, $f - g$, $fg$ ja (kun $g(a) \neq 0$) $f/g$ ovat jatkuvia pisteessä $a$. Lisäksi kahden jatkuvan funktion yhdiste on jatkuva.

Todistukset seuraavat funktion raja-arvon laskusäännöistä (jotka ovat samat kuin jonoille). Seuraus on käytännöllinen:

!!! abstract "Seuraus 10.2"
    Jokainen polynomi on jatkuva koko reaaliakselilla. Rationaalifunktiot (polynomien osamäärät) ovat jatkuvia siellä, missä nimittäjä ei ole nolla.

**Todistus.** Vakiofunktiot ja $f(x) = x$ ovat jatkuvia (10.2). Kertomalla ja summaamalla näitä (Lause 10.1) saadaan kaikki polynomit. Osamäärä antaa rationaalifunktiot. $\blacksquare$

Samoin $\sin$, $\cos$, $e^x$ ja $\ln x$ ovat jatkuvia määrittelyjoukoissaan. Käytännössä lähes jokainen funktio, jonka kirjoitat kaavana, on jatkuva — epäjatkuvuudet vaativat erityistä rakennetta (hyppyjä, jakoa nollalla).

---

## 10.4 Väliarvolause

Nyt luvun huipennus — ja yksi analyysin voimakkaimmista lauseista. Se sanoo jotain, mikä tuntuu itsestäänselvältä: jos jatkuva käyrä alkaa nollan alapuolelta ja päätyy nollan yläpuolelle, sen on jossain **ylitettävä nolla**.

!!! abstract "Lause 10.3 (väliarvolause)"
    Olkoon $f$ jatkuva suljetulla välillä $[a, b]$, ja olkoon $f(a) < 0 < f(b)$. Silloin on olemassa piste $c \in (a, b)$, jolle $f(c) = 0$.

**Todistus.** Tarkastellaan joukkoa
$$S = \{\, x \in [a, b] \mid f(x) < 0 \,\}.$$
Se on epätyhjä ($a \in S$) ja ylhäältä rajoitettu (luvulla $b$). **Täydellisyysaksiooman nojalla** (luku 5) sillä on supremum; merkitään $c = \sup S$. Osoitetaan, että $f(c) = 0$, sulkemalla pois molemmat vaihtoehdot.

*Jos $f(c) < 0$:* jatkuvuuden nojalla $f$ pysyy negatiivisena jollakin pienellä välillä pisteen $c$ ympärillä, joten löytyisi $c$:tä suurempia pisteitä, joissa $f < 0$ — ne kuuluisivat joukkoon $S$, ristiriita sen kanssa, että $c$ on yläraja. (Lisäksi $c \neq b$, koska $f(b) > 0$.)

*Jos $f(c) > 0$:* jatkuvuuden nojalla $f$ pysyy positiivisena jollakin pienellä välillä pisteen $c$ ympärillä, joten koko tuo väli on joukon $S$ ulkopuolella — silloin jo jokin $c$:tä *pienempi* luku olisi $S$:n yläraja, ristiriita sen kanssa, että $c$ on **pienin** yläraja.

Molemmat vaihtoehdot johtavat ristiriitaan, joten $f(c) = 0$. $\blacksquare$

!!! quote "Miksi tämä on syvä eikä ilmeinen"
    Väliarvolause **on epätosi rationaaliluvuilla.** Tarkastele funktiota $f(x) = x^2 - 2$ rationaalilukujen välillä $[1, 2]$: se on jatkuva, $f(1) = -1 < 0$ ja $f(2) = 2 > 0$ — mutta se ei koskaan saa arvoa nolla rationaalilukujen joukossa, koska nollakohta olisi $\sqrt2$, jota siellä ei ole. Käyrä "hyppää yli" nollan reiän kohdalla.

    Reaaliluvuilla reikää ei ole, ja siksi lause pätee. **Väliarvolause on täydellisyyttä pukeutuneena geometriaan** — se on syy, miksi jatkuva käyrä oikeasti "ei voi hypätä yli" arvon.

### Sovellus: juuret ovat olemassa

!!! abstract "Seuraus 10.4"
    Jokaisella parittoman asteen reaalikertoimisella polynomilla on ainakin yksi reaalijuuri.

**Todistus.** Olkoon $p$ pariton polynomi johtavalla kertoimella positiivinen. Kun $x \to +\infty$, $p(x) \to +\infty$, ja kun $x \to -\infty$, $p(x) \to -\infty$ (pariton potenssi hallitsee). Siis $p$ saa jossain negatiivisen ja jossain positiivisen arvon. Koska $p$ on jatkuva (Seuraus 10.2), väliarvolause takaa nollakohdan niiden välissä. $\blacksquare$

Tämä selittää, miksi $x^3 + x + 1 = 0$:lla *täytyy* olla reaaliratkaisu, vaikka sitä ei voi arvata (se on irrationaalinen — muistat sen luvun 16 harjoituksesta). Olemassaolo taataan ilman, että ratkaisua nähdään. Väliarvolause on myös numeeristen juurenhakumenetelmien (puolitushaku) perusta.

---

## 10.5 Suurin ja pienin arvo

Toinen jatkuvuuden suuri lause, jonka esitämme ilman todistusta (se vaatii hieman enemmän koneistoa):

!!! abstract "Lause 10.5 (ääriarvolause)"
    Suljetulla välillä $[a, b]$ jatkuva funktio saavuttaa suurimman ja pienimmän arvonsa — on olemassa pisteet, joissa $f$ on suurimmillaan ja pienimmillään.

Huomaa sanat **suljettu väli**: avoimella välillä lause pettää. Funktio $f(x) = x$ välillä $(0, 1)$ ei saavuta suurinta arvoa — se lähestyy ykköstä saavuttamatta sitä. (Tunnistat tämän: arvojoukolla on supremum $1$ mutta ei maksimia — täsmälleen luvun 5 erottelu, ja sinun täydellisyys-teoriasi.) Sulkeutuneisuus on se, mikä pakottaa raja-arvon kuulumaan joukkoon.

Ääriarvolause on optimoinnin perusta: se takaa, että "paras arvo" on olemassa, ennen kuin sitä lähdetään etsimään derivaatalla (luku 11).

---

## 10.6 Yhteenveto

- **Jatkuvuus** pisteessä $a$: $\lim_{x\to a} f(x) = f(a)$, eli $\varepsilon$–$\delta$: pienet syötemuutokset → pienet tulosmuutokset.
- Polynomit, rationaalifunktiot, $\sin$, $\cos$, $e^x$, $\ln$ ovat jatkuvia; hyppyfunktiot eivät.
- **Väliarvolause:** jatkuva funktio, joka vaihtaa merkkiä, saa arvon nolla välissä. Se on **täydellisyys geometrian kielellä** — epätosi rationaaliluvuilla.
- Seurauksena: pariton polynomi saa aina arvon nolla.
- **Ääriarvolause:** suljetulla välillä jatkuva funktio saavuttaa suurimman ja pienimmän arvonsa — optimoinnin perusta.

---

## Harjoitukset

**10.1 (★)** Missä pisteessä funktio $f(x) = \dfrac{x+1}{x-2}$ on epäjatkuva, ja miksi?

??? success "Vastaus"
    Pisteessä $x = 2$, koska siellä nimittäjä on nolla eikä funktiota ole määritelty (eikä raja-arvo ole äärellinen). Kaikkialla muualla $f$ on jatkuva rationaalifunktiona (Seuraus 10.2). $\blacksquare$

---

**10.2 (★)** Käytä väliarvolausetta osoittaaksesi, että yhtälöllä $x^3 - x - 1 = 0$ on ratkaisu välillä $[1, 2]$.

??? success "Vastaus"
    Olkoon $f(x) = x^3 - x - 1$, joka on jatkuva (polynomi). Lasketaan päätepisteet:
    $$f(1) = 1 - 1 - 1 = -1 < 0, \qquad f(2) = 8 - 2 - 1 = 5 > 0.$$
    Koska $f$ vaihtaa merkkiä välillä $[1,2]$, väliarvolause takaa pisteen $c \in (1,2)$, jolle $f(c) = 0$. $\blacksquare$

    *(Tämä juuri on muovivakio $\rho \approx 1{,}3247$, jonka mainitsit päiväkirjaideoissa — $\varphi$:n kuutioserkku.)*

---

**10.3 (★★)** Käytä $\varepsilon$–$\delta$-määritelmää: todista, että $f(x) = 3x + 1$ on jatkuva pisteessä $x = 2$.

??? tip "Vihje"
    Laske $|f(x) - f(2)| = |3x + 1 - 7| = 3|x - 2|$. Valitse $\delta$ tästä.

??? success "Vastaus"
    Olkoon $\varepsilon > 0$. Lasketaan
    $$|f(x) - f(2)| = |(3x+1) - 7| = |3x - 6| = 3|x - 2|.$$
    Valitaan $\delta = \frac{\varepsilon}{3}$. Silloin $|x - 2| < \delta$ antaa
    $$|f(x) - f(2)| = 3|x-2| < 3 \cdot \frac{\varepsilon}{3} = \varepsilon.$$
    Siis $f$ on jatkuva pisteessä $2$. $\blacksquare$

---

**10.4 (★★)** Osoita, että jokaisella jatkuvalla funktiolla $f : [0,1] \to [0,1]$ on **kiintopiste**: piste $c$, jolle $f(c) = c$. *(Vihje: sovella väliarvolausetta funktioon $g(x) = f(x) - x$.)*

??? tip "Vihje"
    Tarkastele $g(x) = f(x) - x$ välin päätepisteissä $0$ ja $1$. Muista, että arvot ovat välillä $[0,1]$.

??? success "Vastaus"
    Määritellään $g(x) = f(x) - x$, joka on jatkuva (jatkuvien erotus). Päätepisteissä:
    $$g(0) = f(0) - 0 = f(0) \geq 0 \quad(\text{koska } f(0) \in [0,1]),$$
    $$g(1) = f(1) - 1 \leq 0 \quad(\text{koska } f(1) \in [0,1]).$$
    Jos $g(0) = 0$ tai $g(1) = 0$, kiintopiste on päätepisteessä. Muuten $g(0) > 0$ ja $g(1) < 0$, ja väliarvolause antaa pisteen $c$, jolle $g(c) = 0$, eli $f(c) = c$. $\blacksquare$

    *(Tämä on yksiulotteinen versio kuuluisasta Brouwerin kiintopistelauseesta — jokainen jatkuva kuvaus kiekolta itseensä jättää jonkin pisteen paikalleen. Sitä käytetään taloustieteessä, peliteoriassa ja jopa todistamaan, että kahvikupin pinnalla on aina piste, joka ei liiku sekoittaessa.)*

---

**10.5 (★★★)** Todista *munkki vuorella* -arvoitus: munkki nousee vuorelle klo 6–18 ja seuraavana päivänä laskeutuu samaa polkua klo 6–18. Osoita, että polulla on kohta, jossa hän on molempina päivinä täsmälleen samaan kellonaikaan. *(Vihje: kuvittele molemmat matkat samalle päivälle ja sovella väliarvolausetta.)*

??? tip "Vihje"
    Olkoon $u(t)$ nousijan korkeus ja $d(t)$ laskeutujan korkeus hetkellä $t$. Tarkastele erotusta $h(t) = u(t) - d(t)$ ja katso sen etumerkkiä matkan alussa ja lopussa.

??? success "Vastaus"
    Kuvitellaan molemmat matkat tapahtuvan *samana* päivänä. Olkoon $u(t)$ nousijan korkeus hetkellä $t$ (välillä klo 6–18) ja $d(t)$ laskeutujan korkeus samalla polulla. Molemmat ovat jatkuvia (liike on jatkuvaa). Määritellään
    $$h(t) = u(t) - d(t).$$
    Matkan alussa (klo 6): nousija on juurella ($u = 0$), laskeutuja huipulla ($d = H$), joten $h(6) = 0 - H < 0$. Matkan lopussa (klo 18): nousija on huipulla ($u = H$), laskeutuja juurella ($d = 0$), joten $h(18) = H - 0 > 0$.

    $h$ on jatkuva ja vaihtaa merkkiä, joten väliarvolause antaa hetken $c$, jolle $h(c) = 0$, eli $u(c) = d(c)$. Tuolla hetkellä molemmat ovat samalla korkeudella — samassa kohdassa polkua samaan kellonaikaan. $\blacksquare$

    *(Kaunista: emme tiedä missä kohtaa emmekä milloin — mutta tiedämme, että sellainen kohta on pakko olla olemassa. Väliarvolause takaa olemassaolon näyttämättä paikkaa, aivan kuten juurten kohdalla.)*

---

*Osa III jatkuu luvuista 11 (Derivaatta), 12 (Integraali) ja 13 (Taylorin sarjat) — nyt kun sinulla on raja-arvon, sarjan ja jatkuvuuden tiukka perusta, ne rakentuvat suoraan tämän päälle.*
