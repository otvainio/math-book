# Luku 1: Todistuksen taito

Matematiikka eroaa kaikista muista tieteistä yhdessä asiassa: sen totuudet eivät ole havaintoja vaan **todistuksia**. Fysiikka voi mitata, että kappale putoaa kiihtyvyydellä $9{,}81 \text{ m/s}^2$ — mutta mittaus voi aina osoittautua epätarkaksi. Kun matematiikassa on kerran todistettu, että $\sqrt{2}$ on irrationaalinen, se on totta ikuisesti. Eukleideen todistukset ovat yhtä päteviä tänään kuin 2300 vuotta sitten.

Tässä luvussa opit todistamisen viisi perustekniikkaa. Ne ovat työkalupakki, jota koko loppukirja käyttää.

---

## 1.1 Mitä todistus on

**Todistus** on aukoton päättelyketju, joka johtaa oletuksista väitteeseen. Jokainen askel on joko:

- oletus (jokin, minkä totuus hyväksytään lähtökohdaksi),
- aiemmin todistettu tulos, tai
- looginen seuraus edellisistä askelista.

Todistus ei ole "vahva perustelu" eikä "paljon esimerkkejä". Tämä ero on tärkein yksittäinen asia koko kirjassa, joten tehdään se heti kipeän selväksi.

**Varoittava esimerkki.** Tutki polynomia $p(n) = n^2 + n + 41$. Laske:

$$p(1) = 43, \quad p(2) = 47, \quad p(3) = 53, \quad p(4) = 61, \quad \ldots$$

Jokainen näistä on alkuluku. Voit jatkaa: $p(5), p(6), \ldots, p(39)$ — **kaikki alkulukuja**. Neljäkymmentä peräkkäistä onnistumista! Uskaltaisitko jo väittää, että $p(n)$ on aina alkuluku?

Älä. Kohdassa $n = 40$:

$$p(40) = 1600 + 40 + 41 = 1681 = 41^2$$

Ei alkuluku. Neljäkymmentä esimerkkiä ei todistanut mitään — ja tämä on lempeä tapaus. On olemassa väitteitä, jotka pätevät ensimmäiselle $10^{18}$ luvulle ja pettävät sitten.[^1]

[^1]: Kuuluisin esimerkki on ns. Pólyan konjektuuri (1919), joka väitti jotakin kaikista luvuista ja piti paikkansa miljardeille — kunnes vuonna 1958 löydettiin vastaesimerkki suuruusluokassa $10^{361}$ ja myöhemmin pienempi, $906\,150\,257$.

Esimerkit voivat siis **ehdottaa** totuutta, mutta vain todistus **takaa** sen. Käydään nyt läpi tekniikat, joilla takuu hankitaan.

---

## 1.2 Suora todistus

Yksinkertaisin rakenne: oletetaan lähtötilanne, ja päätellään väite suoraan siitä, askel askeleelta.

Ennen ensimmäistä esimerkkiä kaksi määritelmää, joita käytämme jatkuvasti:

!!! note "Määritelmä"
    Kokonaisluku $n$ on **parillinen**, jos $n = 2k$ jollakin kokonaisluvulla $k$, ja **pariton**, jos $n = 2k + 1$ jollakin kokonaisluvulla $k$.

Huomaa, mitä määritelmä tekee: se muuttaa arkikielen sanan ("parillinen") **yhtälöksi**, jolla voi laskea. Tämä on määritelmien koko tehtävä matematiikassa.

!!! abstract "Lause 1.1"
    Jos $n$ on pariton, niin $n^2$ on pariton.

**Todistus.** Oletetaan, että $n$ on pariton. Määritelmän nojalla $n = 2k + 1$ jollakin kokonaisluvulla $k$. Silloin

$$n^2 = (2k+1)^2 = 4k^2 + 4k + 1 = 2(2k^2 + 2k) + 1.$$

Koska $2k^2 + 2k$ on kokonaisluku, luku $n^2$ on muotoa $2m + 1$, eli pariton. $\blacksquare$

Siinä kaikki. Huomaa rakenne: *määritelmä sisään → algebraa → määritelmä ulos*. Suurin osa suorista todistuksista on juuri tätä.

Toinen esimerkki, jossa sama tekniikka tuottaa vähemmän ilmeisen tuloksen:

!!! abstract "Lause 1.2"
    Kahden peräkkäisen kokonaisluvun neliöiden erotus on aina pariton.

**Todistus.** Peräkkäiset kokonaisluvut ovat $n$ ja $n+1$. Niiden neliöiden erotus on

$$(n+1)^2 - n^2 = n^2 + 2n + 1 - n^2 = 2n + 1,$$

joka on määritelmän mukaan pariton. $\blacksquare$

Sivutuotteena saatiin enemmän kuin luvattiin: erotus ei ole vain pariton, vaan *täsmälleen* $2n+1$ — eli jokainen pariton luku on kahden peräkkäisen neliön erotus. Hyvä todistus kertoo usein enemmän kuin väite vaati.

---

## 1.3 Kontrapositio

Väite "jos $A$, niin $B$" on loogisesti täsmälleen sama kuin "jos ei $B$, niin ei $A$". Jälkimmäistä kutsutaan **kontrapositioksi**, ja joskus se on paljon helpompi todistaa.

!!! abstract "Lause 1.3"
    Jos $n^2$ on parillinen, niin $n$ on parillinen.

Yritä hetki suoraan: "oletetaan että $n^2 = 2k$…" — ja huomaat olevasi jumissa, koska $n$:ää on vaikea kaivaa esiin $n^2$:n sisältä (tarvittaisiin neliöjuuri, joka ei pysy kokonaisluvuissa).

Käännetään väite kontrapositioon: *jos $n$ on pariton, niin $n^2$ on pariton.* Mutta tämä on täsmälleen Lause 1.1, jonka jo todistimme! $\blacksquare$

Kontrapositio ei ole temppu vaan näkökulman vaihto: sama väite, luettuna peilistä. Kun suora suunta tökkii, kokeile peiliä.

!!! warning "Varo käänteisväitettä"
    Kontrapositio ("ei $B$ ⟹ ei $A$") on sama väite kuin alkuperäinen. Sen sijaan **käänteisväite** ("jos $B$, niin $A$") on *eri väite*, joka voi olla epätosi vaikka alkuperäinen on tosi. "Jos sataa, katu kastuu" ei tarkoita, että "jos katu on märkä, sataa" — joku on voinut pestä katua.

---

## 1.4 Ristiriitatodistus

Tämä on tekniikoista dramaattisin. Haluamme todistaa väitteen $P$. Teemme näin:

1. Oletetaan **vastakohta**: $P$ ei ole totta.
2. Päätellään tästä oletuksesta jotakin mahdotonta — ristiriita.
3. Koska looginen päättely ei voi tuottaa mahdotonta todesta oletuksesta, oletuksen on oltava väärä. Siis $P$ on totta. $\blacksquare$

Matemaatikko G. H. Hardy kutsui tätä "matemaatikon hienoimmaksi aseeksi": *"Se on hienompi gambiitti kuin mikään shakissa: shakinpelaaja voi uhrata sotilaan tai upseerin, mutta matemaatikko uhraa koko pelin."*

Klassikko ensin — todistus, jonka jokainen matemaatikko kantaa mukanaan:

!!! abstract "Lause 1.4"
    $\sqrt{2}$ on irrationaalinen.

**Todistus.** Oletetaan vastakohta: $\sqrt{2}$ on rationaalinen, eli $\sqrt{2} = \frac{a}{b}$, missä $a$ ja $b$ ovat kokonaislukuja, $b \neq 0$, ja murtoluku on supistetussa muodossa: $\operatorname{syt}(a,b) = 1$.

Korotetaan toiseen ja järjestetään:

$$2 = \frac{a^2}{b^2} \quad\Longrightarrow\quad a^2 = 2b^2.$$

Oikea puoli on parillinen, joten $a^2$ on parillinen — ja Lauseen 1.3 nojalla $a$ on parillinen. Kirjoitetaan $a = 2k$:

$$(2k)^2 = 2b^2 \quad\Longrightarrow\quad 4k^2 = 2b^2 \quad\Longrightarrow\quad b^2 = 2k^2.$$

Siis myös $b^2$ on parillinen, joten $b$ on parillinen.

Mutta nyt sekä $a$ että $b$ ovat parillisia — molemmat jaollisia kahdella — mikä on ristiriidassa oletuksen $\operatorname{syt}(a,b) = 1$ kanssa. Oletus kaatui, joten $\sqrt{2}$ on irrationaalinen. $\blacksquare$

Huomaa, miten Lause 1.3 (kontrapositiolla todistettu) toimi tässä rakennuspalikkana. Todistukset kasautuvat toistensa päälle — siksi järjestyksellä on väliä.

Toinen klassikko, vielä vanhempi:

!!! abstract "Lause 1.5 (Eukleides, n. 300 eaa.)"
    Alkulukuja on äärettömän monta.

**Todistus.** Oletetaan vastakohta: alkulukuja on vain äärellinen määrä, ja ne ovat $p_1, p_2, \ldots, p_k$ — *kaikki* olemassa olevat alkuluvut. Muodostetaan luku

$$N = p_1 \cdot p_2 \cdots p_k + 1.$$

Jaetaanpa $N$ millä tahansa listan alkuluvulla $p_i$, jakojäännökseksi jää aina $1$. Siis **mikään listan alkuluku ei jaa lukua $N$**.

Mutta jokaisella ykköstä suuremmalla kokonaisluvulla on ainakin yksi alkulukutekijä.[^2] Luvun $N$ alkulukutekijä ei siis ole listalla — vaikka listan piti sisältää kaikki alkuluvut. Ristiriita. Alkulukuja on äärettömän monta. $\blacksquare$

[^2]: Tämä "ilmeinen" apuväite todistetaan induktiolla — tekniikalla, jonka opit seuraavassa osiossa. Kirjan luvussa 17 se tehdään huolellisesti.

!!! warning "Yleinen väärinkäsitys"
    Todistus **ei** väitä, että $N$ itse olisi alkuluku! Esimerkiksi $2 \cdot 3 \cdot 5 \cdot 7 \cdot 11 \cdot 13 + 1 = 30\,031 = 59 \cdot 509$ ei ole alkuluku — mutta sen tekijät $59$ ja $509$ ovat uusia alkulukuja, jotka eivät olleet listalla. Ristiriita syntyy joka tapauksessa.

---

## 1.5 Induktio

Edelliset tekniikat todistavat yksittäisiä väitteitä. **Induktio** todistaa väitteen *äärettömän monelle luvulle kerralla* — se on ensimmäinen kosketuksesi hallittuun äärettömyyteen.

Idea on dominopalikkarivi. Jos

1. ensimmäinen palikka kaatuu, ja
2. jokainen kaatuva palikka kaataa seuraavan,

niin **kaikki** palikat kaatuvat — vaikka niitä olisi äärettömän monta.

!!! note "Induktioperiaate"
    Väite $P(n)$ pätee kaikilla kokonaisluvuilla $n \geq 1$, jos:

    1. **Perusaskel:** $P(1)$ on tosi.
    2. **Induktioaskel:** jos $P(n)$ on tosi (tätä kutsutaan **induktio-oletukseksi**), niin $P(n+1)$ on tosi.

!!! abstract "Lause 1.6"
    Kaikilla $n \geq 1$:
    $$1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2}$$

**Todistus.**

*Perusaskel.* Kun $n = 1$: vasen puoli on $1$, oikea puoli on $\frac{1 \cdot 2}{2} = 1$. Täsmää.

*Induktioaskel.* Oletetaan, että väite pätee luvulla $n$, eli

$$1 + 2 + \cdots + n = \frac{n(n+1)}{2} \qquad \text{(induktio-oletus)}$$

Todistetaan, että se pätee luvulla $n+1$. Lähdetään summasta lukuun $n+1$ asti ja käytetään induktio-oletusta:

$$\underbrace{1 + 2 + \cdots + n}_{=\,\frac{n(n+1)}{2}} + (n+1) = \frac{n(n+1)}{2} + (n+1)$$

Otetaan $(n+1)$ yhteiseksi tekijäksi:

$$= (n+1)\left(\frac{n}{2} + 1\right) = \frac{(n+1)(n+2)}{2}.$$

Tämä on täsmälleen kaava sijoituksella $n \to n+1$. Induktioaskel on valmis, ja väite pätee kaikilla $n \geq 1$. $\blacksquare$

Toinen esimerkki, jossa todistetaan epäyhtälö:

!!! abstract "Lause 1.7"
    Kaikilla $n \geq 5$ pätee $2^n > n^2$.

Huomaa ensin, että väite **ei** päde pienillä luvuilla: $2^2 = 4 = 2^2$ ja $2^4 = 16 = 4^2$ (yhtäsuuruus, ei suurempi kuin), ja $2^3 = 8 < 9 = 3^2$. Induktion perusaskel voi alkaa mistä tahansa — tässä luvusta 5.

**Todistus.**

*Perusaskel.* $n = 5$: $2^5 = 32 > 25 = 5^2$. ✓

*Induktioaskel.* Oletetaan $2^n > n^2$ jollakin $n \geq 5$. Silloin

$$2^{n+1} = 2 \cdot 2^n > 2n^2.$$

Riittää siis osoittaa, että $2n^2 \geq (n+1)^2$ kun $n \geq 5$. Tämä on yhtäpitävää sen kanssa, että

$$2n^2 - (n+1)^2 = n^2 - 2n - 1 \geq 0,$$

ja kun $n \geq 5$: $n^2 - 2n - 1 = n(n-2) - 1 \geq 5 \cdot 3 - 1 = 14 > 0$. ✓

Siis $2^{n+1} > 2n^2 \geq (n+1)^2$, ja induktio on valmis. $\blacksquare$

!!! tip "Missä induktion voima on"
    Induktio-oletus ei ole huijausta ("oletetaan mitä todistetaan") — todistat vain *siirtymän*: **jos** kone toimii vaiheessa $n$, se toimii vaiheessa $n+1$. Perusaskel käynnistää koneen, siirtymä pitää sen käynnissä ikuisesti.

---

## 1.6 Vastaesimerkki

Kaikki tähänastiset tekniikat todistavat väitteitä *todeksi*. Mutta entä jos väite on **epätosi**? Silloin riittää yksi ainoa **vastaesimerkki** — ja tämä on ainoa tilanne, jossa yksi esimerkki ratkaisee mitään.

!!! abstract "Väite (Fermat, 1640) — epätosi!"
    Kaikki luvut muotoa $F_n = 2^{2^n} + 1$ ovat alkulukuja.

Fermat tarkisti: $F_0 = 3$, $F_1 = 5$, $F_2 = 17$, $F_3 = 257$, $F_4 = 65\,537$ — kaikki alkulukuja — ja esitti väitteen, että näin jatkuu. Sata vuotta myöhemmin Euler laski:

$$F_5 = 2^{32} + 1 = 4\,294\,967\,297 = 641 \times 6\,700\,417.$$

Yksi vastaesimerkki, ja väite oli kuollut. (Kukaan ei ole tähän päivään mennessä löytänyt yhtään uutta Fermat'n alkulukua luvun $F_4$ jälkeen — tilanne on siis kääntynyt täysin päälaelleen.)

Vastaesimerkin etsiminen ja todistuksen yrittäminen ovat saman prosessin kaksi kättä: kun kohtaat tuntemattoman väitteen, yritä *vuorotellen* todistaa sitä ja kaataa sitä. Kumpi tahansa onnistuu ensin, olet valmis.

---

## 1.7 Yhteenveto

| Tekniikka | Milloin | Rakenne |
|---|---|---|
| Suora todistus | oletuksesta pääsee etenemään | $A \Rightarrow \cdots \Rightarrow B$ |
| Kontrapositio | "$B$:stä taaksepäin" on helpompi | todista: ei $B$ ⟹ ei $A$ |
| Ristiriita | väitteen kieltäminen antaa käsiin jotain konkreettista | oleta ei-$P$, johda mahdottomuus |
| Induktio | väite koskee kaikkia lukuja $n$ | perusaskel + siirtymä $n \to n+1$ |
| Vastaesimerkki | väite on epätosi | yksi esimerkki riittää |

---

## Harjoitukset

**1.1 (★)** Todista suoraan: kahden parittoman luvun summa on parillinen.

**1.2 (★)** Todista suoraan: jos $n$ on parillinen, niin $n^2$ on jaollinen neljällä.

**1.3 (★★)** Todista kontrapositiolla: jos $n^2$ on jaollinen kolmella, niin $n$ on jaollinen kolmella. *(Muista: jos $n$ ei ole jaollinen kolmella, se on muotoa $3k+1$ tai $3k+2$.)*

**1.4 (★★)** Todista ristiriidalla: $\sqrt{3}$ on irrationaalinen. *(Käytä tehtävää 1.3 samassa roolissa kuin Lause 1.3 oli $\sqrt2$:n todistuksessa.)*

**1.5 (★★)** Todista induktiolla: $1^2 + 2^2 + \cdots + n^2 = \dfrac{n(n+1)(2n+1)}{6}$ kaikilla $n \geq 1$.

**1.6 (★★)** Todista induktiolla: $n! > 2^n$ kaikilla $n \geq 4$.

**1.7 (★★)** Kaada väite vastaesimerkillä: "jos $n$ on alkuluku, niin $2^n - 1$ on alkuluku."

**1.8 (★★★)** Todista ristiriidalla: ei ole olemassa suurinta rationaalilukua, joka on pienempi kuin $\sqrt{2}$. *(Oleta, että $q$ on sellainen, ja rakenna rationaaliluku, joka on aidosti lukujen $q$ ja $\sqrt2$ välissä.)*

**1.9 (★★★)** Todista induktiolla **Bernoullin epäyhtälö**: $(1+x)^n \geq 1 + nx$ kaikilla $n \geq 1$, kun $x \geq -1$. *(Missä kohtaa tarvitset oletusta $x \geq -1$? Ilman sitä todistus kaatuu — löydä se askel.)*

---

## Vihjeet

**1.1** Kirjoita luvut muodossa $2k+1$ ja $2m+1$ — huomaa, että tarvitset *eri* kirjaimet.

**1.3** Laske $(3k+1)^2$ ja $(3k+2)^2$ ja katso jakojäännös kolmella.

**1.5** Induktioaskeleessa: lisää $(n+1)^2$ ja ota $(n+1)$ yhteiseksi tekijäksi.

**1.6** Perusaskel on $n=4$. Induktioaskeleessa: $(n+1)! = (n+1) \cdot n!$, ja $n+1 > 2$.

**1.7** Kokeile alkulukuja järjestyksessä. Viides yrittämäsi kaataa väitteen.

**1.8** Lukujen $q$ ja $\sqrt2$ keskiarvo on suurempi kuin $q$ ja pienempi kuin $\sqrt2$ — mutta onko se rationaalinen? Jos ei suoraan, mikä muu luku kelpaisi?

**1.9** Induktioaskeleessa kerrot puolittain luvulla $(1+x)$. Epäyhtälön suunta säilyy vain, jos kerroin ei ole negatiivinen.

---

## Vastauksia

**1.1** $(2k+1) + (2m+1) = 2(k+m+1)$, parillinen. $\blacksquare$

**1.3** $(3k+1)^2 = 3(3k^2+2k)+1$ ja $(3k+2)^2 = 3(3k^2+4k+1)+1$ — kumpikaan ei ole jaollinen kolmella. Siis jos $3 \nmid n$, niin $3 \nmid n^2$; kontrapositiona väite. $\blacksquare$

**1.7** $n = 11$: $2^{11} - 1 = 2047 = 23 \times 89$. (Luvut $2^2-1=3$, $2^3-1=7$, $2^5-1=31$ ja $2^7-1=127$ ovat kaikki alkulukuja — ansa oli viritetty hyvin.)

Muiden tehtävien ratkaisut käydään läpi yhdessä, kun olet yrittänyt niitä.

---

*Seuraava luku: Joukot ja funktiot — kieli, jolla koko moderni matematiikka on kirjoitettu.*
