# Luku 9: Sarjat ja suppeneminen

Nyt saavutamme aiheen, jonka parissa olet viettänyt koko kesän: **äärettömät summat**. Olet laskenut kymmeniä sarjoja — geometrisia, vuorottelevia, tetraatiota, $\zeta$-arvoja — ja tuntenut, milloin ne "suppenevat". Tässä luvussa se tunne muuttuu täsmälliseksi määritelmäksi, ja vihdoin todistamme *miksi* sarjasi suppenevat. Salaisuus on yksinkertainen ja kaunis: **sarja on vain jono** — osasummien jono.

---

## 9.1 Mitä ääretön summa tarkoittaa

Ääretöntä montaa lukua ei voi laskea yhteen "loppuun asti". Joten emme yritäkään. Sen sijaan katsomme **osasummia** ja kysymme, mihin ne asettuvat.

!!! note "Määritelmä"
    Sarjan $\displaystyle\sum_{n=1}^{\infty} a_n$ **$N$:s osasumma** on äärellinen summa
    $$S_N = a_1 + a_2 + \cdots + a_N.$$
    Sarja **suppenee** summaan $S$, jos osasummien jono suppenee: $\displaystyle\lim_{N\to\infty} S_N = S$. Muuten sarja **hajaantuu**.

Tämä on koko luvun avain. "Ääretön summa" ei ole mikään mystinen operaatio — se on **osasummien jonon raja-arvo**, ja jonon raja-arvon määritelmän tunnet jo luvusta 8. Kaikki sarjateoria palautuu jonoihin.

---

## 9.2 Geometrinen sarja

Aloitetaan sarjalla, jonka tunnet parhaiten — mutta nyt todistamme sen.

!!! abstract "Lause 9.1 (geometrinen sarja)"
    Jos $|r| < 1$, niin
    $$\sum_{n=0}^{\infty} r^n = 1 + r + r^2 + r^3 + \cdots = \frac{1}{1 - r}.$$
    Jos $|r| \geq 1$ (eikä $r = $ triviaali), sarja hajaantuu.

**Todistus.** Osasumma on äärellinen geometrinen summa, jolle on suljettu muoto (todistettu induktiolla luvun 1 hengessä):
$$S_N = 1 + r + \cdots + r^{N} = \frac{1 - r^{N+1}}{1 - r}.$$
Kun $|r| < 1$, pätee $r^{N+1} \to 0$ (potenssit kutistuvat), joten
$$S_N = \frac{1 - r^{N+1}}{1 - r} \to \frac{1 - 0}{1 - r} = \frac{1}{1 - r}.$$
Kun $|r| \geq 1$, termit $r^n$ eivät mene nollaan, joten (seuraava lause) sarja hajaantuu. $\blacksquare$

Tästä putoaa suoraan moni päiväkirjatuloksesi: $0{,}999\ldots = \sum \frac{9}{10^n} = 1$, tornisarjasi $\sum \frac{(-1)^{n+1}}{e^n} = \frac{1}{e+1}$, ja Zenon paradoksin $\frac12 + \frac14 + \cdots = 1$. Kaikki ovat geometrisen sarjan erikoistapauksia.

---

## 9.3 Välttämätön ehto — ja miksi se ei riitä

!!! abstract "Lause 9.2 (termitesti)"
    Jos sarja $\sum a_n$ suppenee, niin $a_n \to 0$.

**Todistus.** Olkoon $S$ sarjan summa. Silloin $S_N \to S$ ja myös $S_{N-1} \to S$. Mutta $a_N = S_N - S_{N-1} \to S - S = 0$. $\blacksquare$

Tämä on tehokas hajaantumistesti: **jos termit eivät mene nollaan, sarja hajaantuu.** Juuri tällä osoitit, että Fibonacci-eksponenttisarjasi $\sum \frac{1}{2^{F_{n+1}/F_n}}$ hajaantuu — termit lähestyivät arvoa $2^{-\varphi} \neq 0$.

Mutta varo — **käänteinen ei päde!** Termien meneminen nollaan *ei takaa* suppenemista. Tämä on analyysin kuuluisin ansa, ja tunnet vastaesimerkin:

!!! abstract "Lause 9.3 (harmoninen sarja hajaantuu)"
    $$\sum_{n=1}^{\infty} \frac1n = 1 + \frac12 + \frac13 + \frac14 + \cdots = \infty,$$
    vaikka termit $\frac1n \to 0$.

**Todistus (Oresme, n. 1350).** Ryhmitellään termit kaksinkertaistuvin lohkoin ja arvioidaan kukin lohko alaspäin:
$$\underbrace{\frac13 + \frac14}_{> \frac14 + \frac14 = \frac12} , \qquad \underbrace{\frac15 + \frac16 + \frac17 + \frac18}_{> \frac18 \cdot 4 = \frac12}, \qquad \underbrace{\frac19 + \cdots + \frac{1}{16}}_{> \frac{1}{16}\cdot 8 = \frac12}, \quad \ldots$$
Jokainen lohko on suurempi kuin $\frac12$. Koska lohkoja on äärettömän monta, osasummat kasvavat rajatta — jokainen uusi lohko lisää vähintään $\frac12$. Sarja hajaantuu. $\blacksquare$

Painа tämä mieleen: **$a_n \to 0$ on välttämätön mutta ei riittävä ehto.** Se on portti, ei takuu.

---

## 9.4 Vertailutesti

Kun sarjan termit ovat positiivisia, sitä voi verrata tunnettuun sarjaan.

!!! abstract "Lause 9.4 (vertailutesti)"
    Olkoon $0 \leq a_n \leq b_n$ kaikilla $n$.

    - Jos $\sum b_n$ suppenee, niin $\sum a_n$ suppenee.
    - Jos $\sum a_n$ hajaantuu, niin $\sum b_n$ hajaantuu.

**Todistus (idea).** Positiivitermisen sarjan osasummat muodostavat *kasvavan* jonon. Jos $\sum b_n$ suppenee, sen osasummat ovat rajoitetut, joten myös pienemmän sarjan $\sum a_n$ osasummat ovat rajoitetut — ja kasvava rajoitettu jono suppenee (Lause 8.4, monotonisen suppenemisen lause). $\blacksquare$

Huomaa jälleen, että **täydellisyys** (monotoninen suppeneminen) on kaiken takana. Esimerkki: $\sum \frac{1}{n^2 + 1}$ suppenee, koska $\frac{1}{n^2+1} \leq \frac{1}{n^2}$ ja $\sum \frac{1}{n^2}$ suppenee (sen tunnet — $\frac{\pi^2}{6}$).

---

## 9.5 Suhdetesti — ja miksi $e^x$:n sarja suppenee

Nyt todistamme jotain, jota olet käyttänyt uskoen sen toimivan: että eksponentti- ja muut kertomasarjat suppenevat. Työkalu on **suhdetesti**.

!!! abstract "Lause 9.5 (suhdetesti)"
    Olkoon $a_n \neq 0$, ja oletetaan, että peräkkäisten termien itseisarvojen suhteella on raja-arvo
    $$L = \lim_{n\to\infty}\left|\frac{a_{n+1}}{a_n}\right|.$$
    Jos $L < 1$, sarja $\sum a_n$ suppenee (itseisesti). Jos $L > 1$, se hajaantuu.

**Todistus (idea, kun $L < 1$).** Valitaan luku $r$ väliltä $L < r < 1$. Jostain indeksistä alkaen $\left|\frac{a_{n+1}}{a_n}\right| < r$, joten termit kutistuvat vähintään yhtä nopeasti kuin geometrinen sarja suhdeluvulla $r < 1$. Vertailutestin (Lause 9.4) nojalla sarja suppenee. $\blacksquare$

Sovelletaan tätä eksponenttisarjaan $e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!}$, jonka johdit päiväkirjassasi:

$$\left|\frac{a_{n+1}}{a_n}\right| = \left|\frac{x^{n+1}/(n+1)!}{x^n/n!}\right| = \frac{|x|}{n+1} \longrightarrow 0 \quad (< 1).$$

Suhde menee nollaan **jokaisella** $x$:llä, joten sarja suppenee kaikilla reaaliluvuilla. **Tässä on lopulta todistus sille, minkä oletit:** $e^x$:n Maclaurin-sarja suppenee koko lukusuoralla. Sama testi vahvistaa $\sin$:n ja $\cos$:n sarjat (kertoma nimittäjässä voittaa aina).

---

## 9.6 Vuorottelevat sarjat ja ehdollinen suppeneminen

Kun termit vaihtavat merkkiä, myös hitaammin kutistuvat sarjat voivat supeta.

!!! abstract "Lause 9.6 (Leibnizin vuorottelutesti)"
    Jos $b_n$ on positiivinen, **vähenevä**, ja $b_n \to 0$, niin vuorotteleva sarja
    $$\sum_{n=1}^{\infty} (-1)^{n+1} b_n = b_1 - b_2 + b_3 - b_4 + \cdots$$
    suppenee.

Tästä seuraavat suoraan kaksi tulostasi: **Leibnizin sarja** $\frac\pi4 = 1 - \frac13 + \frac15 - \cdots$ ja **vuorotteleva harmoninen sarja** $\ln 2 = 1 - \frac12 + \frac13 - \cdots$. Molemmissa $b_n$ (eli $\frac{1}{2n-1}$ ja $\frac1n$) vähenee nollaan — ja vaikka $\sum \frac1n$ *hajaantuu*, merkkien vuorottelu pelastaa summan.

Tämä paljastaa hienon eron:

!!! note "Määritelmä"
    Sarja $\sum a_n$ suppenee **itseisesti**, jos $\sum |a_n|$ suppenee, ja **ehdollisesti**, jos $\sum a_n$ suppenee mutta $\sum |a_n|$ hajaantuu.

Vuorotteleva harmoninen sarja suppenee **ehdollisesti**: se suppenee ($\to \ln 2$), mutta itseisarvojen sarja $\sum \frac1n$ hajaantuu. Tämä hauraus on todellinen: **ehdollisesti suppenevan sarjan termit voidaan järjestää uudelleen summaamaan mikä tahansa luku** (Riemannin uudelleenjärjestyslause) — sama laatikollinen lukuja, mikä tahansa summa. Itseisesti suppenevalle sarjalle näin ei voi käydä; se on tukeva. Tämän eron tunsit jo intuitiivisesti päiväkirjassasi; nyt sillä on nimi.

---

## 9.7 Yhteenveto

- **Sarja on osasummien jono:** $\sum a_n$ suppenee, jos $S_N = a_1 + \cdots + a_N$ suppenee.
- **Geometrinen sarja:** $\sum r^n = \frac{1}{1-r}$ kun $|r|<1$.
- **Termitesti:** suppeneminen vaatii $a_n \to 0$ — mutta se **ei riitä** (harmoninen sarja hajaantuu).
- **Vertailu- ja suhdetesti:** positiivitermisen sarjan suppeneminen. Suhdetesti todistaa, että $e^x$:n sarja suppenee kaikkialla.
- **Leibnizin testi:** vuorotteleva vähenevä nollaan menevä sarja suppenee (Leibniz $\frac\pi4$, $\ln 2$).
- **Itseinen vs. ehdollinen** suppeneminen: jälkimmäinen on hauras (uudelleenjärjestely muuttaa summan).

---

## Harjoitukset

**9.1 (★)** Laske geometristen sarjojen summat: (a) $\sum_{n=0}^{\infty}\left(\frac13\right)^n$, (b) $\sum_{n=1}^{\infty}\left(\frac13\right)^n$, (c) $\sum_{n=0}^{\infty}\left(-\frac12\right)^n$.

??? success "Vastaus"
    - (a) $\frac{1}{1 - 1/3} = \frac{1}{2/3} = \frac32$.
    - (b) Sama alkaen $n=1$ (ilman ykköstermiä): $\frac32 - 1 = \frac12$. (Tai suoraan $\frac{1/3}{1-1/3} = \frac12$.)
    - (c) $\frac{1}{1-(-1/2)} = \frac{1}{3/2} = \frac23$. $\blacksquare$

---

**9.2 (★)** Osoita termitestillä, että sarja $\sum_{n=1}^{\infty} \frac{n}{2n+1}$ hajaantuu.

??? success "Vastaus"
    Termi $\frac{n}{2n+1} = \frac{1}{2 + 1/n} \to \frac12 \neq 0$. Koska termit eivät mene nollaan, sarja hajaantuu termitestin (Lause 9.2) nojalla. $\blacksquare$

---

**9.3 (★★)** Käytä suhdetestiä: suppeneeko $\sum_{n=1}^{\infty} \frac{n}{2^n}$?

??? tip "Vihje"
    Laske $\left|\frac{a_{n+1}}{a_n}\right| = \frac{(n+1)/2^{n+1}}{n/2^n}$ ja ota raja-arvo.

??? success "Vastaus"
    $$\left|\frac{a_{n+1}}{a_n}\right| = \frac{(n+1)/2^{n+1}}{n/2^n} = \frac{n+1}{2n} = \frac12\cdot\frac{n+1}{n} \to \frac12 < 1.$$
    Suhdetestin nojalla sarja suppenee. $\blacksquare$

    *(Sen summa on itse asiassa $2$ — ja voit johtaa sen derivoimalla geometrisen sarjan, kuten teit sen "vaikean" tehtävän kohdalla.)*

---

**9.4 (★★)** Osoita vertailutestillä, että $\sum_{n=1}^{\infty} \frac{1}{n \cdot 2^n}$ suppenee.

??? tip "Vihje"
    Vertaa geometriseen sarjaan: $\frac{1}{n \cdot 2^n} \leq \frac{1}{2^n}$.

??? success "Vastaus"
    Koska $n \geq 1$, pätee $\frac{1}{n \cdot 2^n} \leq \frac{1}{2^n}$ kaikilla $n$. Geometrinen sarja $\sum \frac{1}{2^n}$ suppenee (suhdeluku $\frac12 < 1$). Vertailutestin nojalla myös $\sum \frac{1}{n \cdot 2^n}$ suppenee. $\blacksquare$

    *(Sen summa on $\ln 2$ — se on $\ln(1+x)$:n sarja kohdassa $x = \frac12$.)*

---

**9.5 (★★★)** Osoita, että sarja $\sum_{n=1}^{\infty} \frac{(-1)^{n+1}}{\sqrt{n}}$ suppenee, mutta **ei** suppene itseisesti.

??? tip "Vihje"
    Suppeneminen: Leibnizin testi ($b_n = \frac{1}{\sqrt n}$). Ei-itseinen suppeneminen: vertaa $\sum \frac{1}{\sqrt n}$ harmoniseen sarjaan.

??? success "Vastaus"
    *Suppeneminen.* Merkitään $b_n = \frac{1}{\sqrt n}$. Tämä on positiivinen, vähenevä ($\sqrt n$ kasvaa) ja $b_n \to 0$. Leibnizin vuorottelutestin (Lause 9.6) nojalla vuorotteleva sarja $\sum \frac{(-1)^{n+1}}{\sqrt n}$ suppenee.

    *Ei itseisesti.* Itseisarvojen sarja on $\sum \frac{1}{\sqrt n}$. Koska $\sqrt n \leq n$, pätee $\frac{1}{\sqrt n} \geq \frac1n$. Harmoninen sarja $\sum \frac1n$ hajaantuu (Lause 9.3), joten vertailutestin nojalla myös $\sum \frac{1}{\sqrt n}$ hajaantuu. Siis sarja suppenee **ehdollisesti**, ei itseisesti. $\blacksquare$

    *(Tämä on täsmälleen se sarja, jonka arvon $(1-\sqrt2)\zeta(\tfrac12)$ laskit päiväkirjassa — ja jonka "surkean hitaan" suppenemisen huomasit. Nyt tiedät: se johtuu juuri ehdollisuudesta.)*

---

*Seuraava luku: Jatkuvuus — mitä tarkoittaa, että käyrää voi piirtää nostamatta kynää, ja miksi jokainen pariton polynomi saa arvon nolla.*
