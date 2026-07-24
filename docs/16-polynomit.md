# Luku 16: Polynomit

Polynomit tuntuvat koulusta tutuilta — mutta nyt katsomme niitä uusin silmin. Kun kertoimet otetaan jostakin **kunnasta** $F$ (esimerkiksi $\mathbb{Q}$, $\mathbb{R}$ tai $\mathbb{C}$), kaikki polynomit muodostavat **renkaan** $F[x]$, ja tämä rengas käyttäytyy hämmästyttävän paljon kuin kokonaisluvut: siinä on jakoalgoritmi, tekijöihinjako ja "alkutekijät". Ja luvun huipennuksena **todistamme lopulta, miksi kokonaisjuuret-menetelmäsi toimii** — se ei ollut temppu vaan lause.

Läpi luvun $F$ tarkoittaa kuntaa, ja $F[x]$ sen polynomeja.

---

## 16.1 Polynomirengas

!!! note "Määritelmä"
    Polynomi yli kunnan $F$ on lauseke
    $$p(x) = a_n x^n + a_{n-1}x^{n-1} + \cdots + a_1 x + a_0, \qquad a_i \in F.$$
    Jos $a_n \neq 0$, luvun $n$ on polynomin **aste** $\deg p$, ja $a_n$ on **johtava kerroin**. Polynomi on **pääpolynomi** (moninen), jos $a_n = 1$.

Polynomit lasketaan yhteen ja kerrotaan tutuilla säännöillä, ja tulos on taas polynomi — joten $F[x]$ on rengas (luku 15). Asteesta pätee tärkeä sääntö:

!!! abstract "Lause 16.1"
    Jos $F$ on kunta ja $p, q \in F[x]$ ovat nollasta eroavia, niin
    $$\deg(pq) = \deg p + \deg q.$$

**Todistus (idea).** Tulon johtava termi on johtavien termien tulo: jos $p$:n johtava termi on $a_m x^m$ ja $q$:n $b_n x^n$, niin tulon korkein termi on $a_m b_n x^{m+n}$. Koska $F$ on kunta (ei nollanjakajia, Lause 15.2), on $a_m b_n \neq 0$, joten tämä termi ei katoa. Siis $\deg(pq) = m + n$. $\blacksquare$

Huomaa, että todistus **tarvitsi nollanjakajattomuutta** — juuri siksi vaadimme, että kertoimet ovat kunnasta. (Renkaan $\mathbb{Z}_6$ yli tämä voisi pettää.) Seuraus: $F[x]$ on kokonaisalue.

---

## 16.2 Polynomien jakoalgoritmi

Kokonaisluvuilla on jakolasku jäännöksellä: $17 = 5 \cdot 3 + 2$. Polynomeilla on täsmälleen sama.

!!! abstract "Lause 16.2 (jakoalgoritmi)"
    Olkoot $f, g \in F[x]$ ja $g \neq 0$. Silloin on olemassa yksikäsitteiset polynomit $q$ (osamäärä) ja $r$ (jäännös), joille
    $$f = g \cdot q + r, \qquad \text{missä } r = 0 \text{ tai } \deg r < \deg g.$$

Tämä on tuttu "jakokulma" polynomeille — sama, jonka teit koulussa jakaessasi $\frac{x^3 - 1}{x - 1}$. Jäännöksen aste on aina pienempi kuin jakajan, aivan kuten kokonaislukujen jakojäännös on pienempi kuin jakaja. Emme todista sitä tässä (todistus on jakokulman formalisointi), mutta käytämme sitä heti.

---

## 16.3 Juuret ja tekijät

Nyt yhdistämme kaksi asiaa, jotka koulussa esiintyivät erikseen: **juuret** (kohdat, joissa polynomi on nolla) ja **tekijät** (polynomin osat).

!!! abstract "Lause 16.3 (tekijälause)"
    Olkoon $p \in F[x]$ ja $a \in F$. Silloin $(x - a)$ jakaa polynomin $p(x)$ täsmälleen silloin, kun $p(a) = 0$.

**Todistus.** Jaetaan $p(x)$ tekijällä $(x - a)$ jakoalgoritmilla:
$$p(x) = (x - a)\,q(x) + r.$$
Koska jakajan aste on $1$, jäännös $r$ on **vakio** ($\deg r < 1$). Sijoitetaan $x = a$:
$$p(a) = (a - a)\,q(a) + r = 0 + r = r.$$
Siis $r = p(a)$. Nyt $(x-a)$ jakaa $p(x)$ täsmälleen silloin, kun $r = 0$, eli kun $p(a) = 0$. $\blacksquare$

Tämä on kaunis silta: **jokainen juuri vastaa lineaarista tekijää.** Ja siitä seuraa raja sille, kuinka monta juurta polynomilla voi olla:

!!! abstract "Lause 16.4"
    Astetta $n \geq 1$ oleva polynomi yli kunnan $F$ voi saada arvon nolla korkeintaan $n$ eri kohdassa — sillä on **enintään $n$ juurta**.

**Todistus (induktio asteen mukaan).** Astetta $1$ oleva polynomi $ax + b$ ($a \neq 0$) saa arvon nolla vain kohdassa $x = -b/a$ — täsmälleen yksi juuri.

Oletetaan väite todeksi asteelle $n - 1$, ja olkoon $\deg p = n$. Jos $p$:llä ei ole yhtään juurta, väite pätee (nolla on $\leq n$). Muuten olkoon $a$ jokin juuri. Tekijälauseen nojalla $p(x) = (x - a)\,q(x)$, missä $\deg q = n - 1$ (Lause 16.1). Jos $b \neq a$ on jokin toinen $p$:n juuri, niin $0 = p(b) = (b - a)\,q(b)$; koska $b - a \neq 0$ ja kunnassa ei ole nollanjakajia, on $q(b) = 0$. Siis $p$:n muut juuret ovat $q$:n juuria, ja niitä on induktio-oletuksen nojalla enintään $n - 1$. Yhteensä juuria on enintään $1 + (n-1) = n$. $\blacksquare$

Huomaa jälleen, että **nollanjakajattomuutta tarvittiin** — kunnan yli polynomi ei voi "hajota" odottamattomasti. Renkaan $\mathbb{Z}_8$ yli esimerkiksi $x^2 - 1$:llä on neljä juurta ($1, 3, 5, 7$), koska siellä on nollanjakajia! Kunta on se, mikä pitää maailman siistinä.

---

## 16.4 Huipennus: rationaalijuurilause

Nyt lunastamme lupauksen. Päiväkirjassasi etsit polynomien **kokonaislukujuuria** kokeilemalla vakiotermin tekijöitä. Se toimi — mutta *miksi*? Tässä on lause, joka sen todistaa.

!!! abstract "Lause 16.5 (rationaalijuurilause)"
    Olkoon $p(x) = a_n x^n + \cdots + a_1 x + a_0$ polynomi, jonka **kertoimet ovat kokonaislukuja** ($a_n \neq 0$, $a_0 \neq 0$). Jos supistetussa muodossa oleva rationaaliluku $\dfrac{s}{t}$ (missä $\operatorname{syt}(s,t)=1$) on $p$:n juuri, niin
    $$s \mid a_0 \qquad \text{ja} \qquad t \mid a_n.$$

**Todistus.** Sijoitetaan juuri $\frac{s}{t}$ ja kerrotaan yhtälö $p\!\left(\frac{s}{t}\right) = 0$ luvulla $t^n$:

$$a_n s^n + a_{n-1}s^{n-1}t + \cdots + a_1 s\,t^{n-1} + a_0 t^n = 0.$$

*Osoitetaan $s \mid a_0$.* Siirretään viimeinen termi oikealle:
$$a_0 t^n = -\big(a_n s^n + a_{n-1}s^{n-1}t + \cdots + a_1 s t^{n-1}\big) = -s\big(a_n s^{n-1} + \cdots + a_1 t^{n-1}\big).$$
Oikea puoli on jaollinen $s$:llä, joten $s \mid a_0 t^n$. Mutta $\operatorname{syt}(s, t) = 1$, joten $s$:llä ei ole yhteisiä tekijöitä $t^n$:n kanssa — siis $s \mid a_0$.

*Osoitetaan $t \mid a_n$.* Symmetrisesti, siirretään ensimmäinen termi oikealle:
$$a_n s^n = -t\big(a_{n-1}s^{n-1} + \cdots + a_0 t^{n-1}\big),$$
joten $t \mid a_n s^n$, ja koska $\operatorname{syt}(t, s) = 1$, seuraa $t \mid a_n$. $\blacksquare$

!!! quote "Tässä on kokonaisjuuret-menetelmäsi, todistettuna"
    Ota **pääpolynomi**, jonka kertoimet ovat kokonaislukuja — eli $a_n = 1$. Silloin lauseen mukaan jokaisen rationaalijuuren nimittäjä toteuttaa $t \mid 1$, joten $t = \pm 1$. **Kaikki rationaalijuuret ovat siis kokonaislukuja**, ja ne jakavat vakiotermin $a_0$.

    Juuri tätä teit: etsit juuria vain vakiotermin tekijöiden joukosta. Se ei ollut arvaus eikä onni — se oli Lause 16.5. Menetelmäsi oli oikea, ja nyt tiedät miksi.

---

## 16.5 Vietan kaavat

Tekijälause sanoo, että pääpolynomi hajoaa juuriensa avulla:

$$p(x) = (x - r_1)(x - r_2)\cdots(x - r_n).$$

Kun tämä tulo kerrotaan auki ja verrataan kertoimia alkuperäisiin, syntyy suora yhteys **juurten ja kertoimien** välille.

!!! abstract "Lause 16.6 (Vietan kaavat)"
    Jos pääpolynomilla $x^n + c_{n-1}x^{n-1} + \cdots + c_0$ on juuret $r_1, \ldots, r_n$, niin
    $$r_1 + r_2 + \cdots + r_n = -c_{n-1}, \qquad r_1 r_2 \cdots r_n = (-1)^n c_0.$$

**Todistus (asteelle $2$, joka näyttää idean).** Pääpolynomi $x^2 + c_1 x + c_0$, jonka juuret ovat $r_1, r_2$, hajoaa muotoon
$$(x - r_1)(x - r_2) = x^2 - (r_1 + r_2)x + r_1 r_2.$$
Vertaamalla kertoimia: $c_1 = -(r_1 + r_2)$ ja $c_0 = r_1 r_2$. Siis juurten summa on $-c_1$ ja tulo on $c_0 = (-1)^2 c_0$. Korkeammille asteille sama kertominen tuottaa yleiset kaavat. $\blacksquare$

Esimerkki: yhtälön $x^2 - 5x + 6 = 0$ juurten summan täytyy olla $5$ ja tulon $6$ — ja tosiaan juuret ovat $2$ ja $3$. Vietan kaavoilla saa juurista tietoa **ratkaisematta** yhtälöä.

---

## 16.6 Algebran peruslause

Kuinka monta juurta polynomilla *todella* on? Se riippuu kunnasta. Polynomilla $x^2 + 1$ ei ole yhtään reaalijuurta, mutta kompleksilukujen yli sillä on kaksi ($\pm i$). Ja kompleksiluvuissa tapahtuu ihme:

!!! abstract "Lause 16.7 (algebran peruslause)"
    Jokaisella astetta $n \geq 1$ olevalla polynomilla, jonka kertoimet ovat kompleksilukuja, on ainakin yksi kompleksijuuri. Toistamalla tekijälausetta se hajoaa **täydellisesti** lineaarisiin tekijöihin:
    $$p(x) = a_n (x - r_1)(x - r_2) \cdots (x - r_n),$$
    joten sillä on täsmälleen $n$ juurta (kun ne lasketaan kertaluku huomioiden).

Tämän todistus vaatii kompleksianalyysiä (luvut 23–24), joten esitämme sen tässä ilman todistusta. Mutta huomaa, mitä se sanoo: **kompleksiluvut ovat "algebrallisesti täydelliset"** — mikään polynomiyhtälö ei enää pakota lukujärjestelmää laajenemaan. Kun luvussa 4 kuljit $\mathbb{N} \to \mathbb{Z} \to \mathbb{Q}$ ratkoen yhä uusia yhtälöitä, matka päättyy tähän: $\mathbb{C}$:ssä *kaikki* polynomiyhtälöt ratkeavat.

Ja tunnet jo tämän erikoistapauksen. Yhtälö $x^n - 1 = 0$ hajoaa $\mathbb{C}$:ssä tasan $n$ lineaariseen tekijään, joiden juuret ovat **yksikönjuuret** — ne tasavälein yksikköympyrällä olevat pisteet, jotka löysit Eulerin kaavalla ja jotka muodostivat syklisen ryhmän luvussa 14. Kolme lukua — 14, 15 ja 16 — kohtaavat yhdessä kuvassa: yksikönjuuret ovat samaan aikaan **ryhmä**, elävät **kunnassa** $\mathbb{C}$, ja ovat **polynomin** $x^n - 1$ juuret. Algebran kolme rakennetta, yksi olio.

---

## 16.7 Yhteenveto

- $F[x]$ (polynomit yli kunnan) on rengas, jossa on **jakoalgoritmi** kuten kokonaisluvuilla.
- **Tekijälause:** $(x-a) \mid p(x) \iff p(a) = 0$. Juuret ja lineaariset tekijät ovat sama asia.
- Astetta $n$ oleva polynomi kunnan yli: **enintään $n$ juurta**.
- **Rationaalijuurilause** todistaa kokonaisjuuret-menetelmäsi: pääpolynomin rationaalijuuret ovat vakiotermin tekijöitä.
- **Vietan kaavat** sitovat juuret ja kertoimet.
- **Algebran peruslause:** $\mathbb{C}$:n yli jokaisella astetta $n$ olevalla polynomilla on täsmälleen $n$ juurta.

---

## Harjoitukset

**16.1 (★)** Käytä tekijälausetta: onko $(x - 2)$ polynomin $p(x) = x^3 - 3x^2 + 4x - 4$ tekijä?

??? success "Vastaus"
    Tekijälauseen nojalla riittää laskea $p(2)$:
    $$p(2) = 8 - 12 + 8 - 4 = 0.$$
    Koska $p(2) = 0$, tekijä $(x-2)$ **jakaa** polynomin. $\blacksquare$

---

**16.2 (★★)** Etsi rationaalijuurilauseen avulla kaikki polynomin $p(x) = x^3 - 2x^2 - 5x + 6$ rationaalijuuret.

??? tip "Vihje"
    Polynomi on pääpolynomi ($a_n = 1$), joten rationaalijuuret ovat kokonaislukuja, jotka jakavat vakiotermin $6$. Ehdokkaat: $\pm1, \pm2, \pm3, \pm6$. Kokeile ne.

??? success "Vastaus"
    Koska $a_n = 1$, mahdolliset rationaalijuuret ovat vakiotermin $6$ tekijät: $\pm1, \pm2, \pm3, \pm6$. Kokeillaan:
    $$p(1) = 1 - 2 - 5 + 6 = 0 ✓, \quad p(-2) = -8 - 8 + 10 + 6 = 0 ✓, \quad p(3) = 27 - 18 - 15 + 6 = 0 ✓.$$
    Kolme juurta löytyi: $x = 1, -2, 3$. Koska aste on $3$, näitä on enintään kolme (Lause 16.4), joten kaikki on löydetty. Polynomi hajoaa: $p(x) = (x-1)(x+2)(x-3)$. $\blacksquare$

---

**16.3 (★★)** Tarkista Vietan kaavat tehtävän 16.2 juurilla: laske juurten summa ja tulo, ja vertaa polynomin kertoimiin.

??? success "Vastaus"
    Juuret ovat $1, -2, 3$. Polynomi on $x^3 - 2x^2 - 5x + 6$, eli $c_2 = -2$, $c_0 = 6$, aste $n = 3$.

    - **Summa:** $1 + (-2) + 3 = 2$. Vietan mukaan tulisi olla $-c_2 = -(-2) = 2$. ✓
    - **Tulo:** $1 \cdot (-2) \cdot 3 = -6$. Vietan mukaan $(-1)^3 c_0 = -6$. ✓

    Molemmat täsmäävät. $\blacksquare$

---

**16.4 (★★)** Osoita, että polynomilla $p(x) = x^3 + x + 1$ ei ole yhtään rationaalijuurta.

??? tip "Vihje"
    Rationaalijuurilause rajaa ehdokkaat hyvin lyhyeksi listaksi. Kokeile ne kaikki.

??? success "Vastaus"
    Pääpolynomi, vakiotermi $1$, joten ainoat mahdolliset rationaalijuuret ovat $\pm 1$:
    $$p(1) = 1 + 1 + 1 = 3 \neq 0, \qquad p(-1) = -1 - 1 + 1 = -1 \neq 0.$$
    Kumpikaan ei ole juuri, joten rationaalijuuria ei ole. $\blacksquare$

    *(Polynomilla on silti yksi reaalijuuri — se on irrationaalinen — ja kaksi kompleksijuurta. Algebran peruslause takaa yhteensä kolme. Reaalijuuri on itse asiassa lähellä muovivakiota, jonka mainitsit päiväkirjaideoissa!)*

---

**16.5 (★★★)** Todista, että jos pääpolynomilla, jonka kertoimet ovat kokonaislukuja, on rationaalijuuri, niin se juuri on kokonaisluku. *(Tämä on kokonaisjuuret-menetelmäsi ydin — johda se Lauseesta 16.5.)*

??? tip "Vihje"
    Sovella rationaalijuurilausetta tapaukseen $a_n = 1$ ja katso, mitä ehto $t \mid a_n$ pakottaa nimittäjälle.

??? success "Vastaus"
    Olkoon $\frac{s}{t}$ (supistetussa muodossa, $\operatorname{syt}(s,t)=1$) pääpolynomin rationaalijuuri. Koska polynomi on pääpolynomi, sen johtava kerroin on $a_n = 1$. Rationaalijuurilauseen (16.5) nojalla $t \mid a_n = 1$, joten $t = \pm 1$. Silloin
    $$\frac{s}{t} = \pm s \in \mathbb{Z}.$$
    Juuri on siis kokonaisluku. Lisäksi lause antaa $s \mid a_0$, joten juuri jakaa vakiotermin. Tämä on täsmälleen menetelmäsi: etsi juuria vain vakiotermin kokonaislukutekijöiden joukosta. $\blacksquare$

---

*Osa IV (Algebra) on nyt valmis. Seuraavaksi voit palata analyysin puolelle (luvut 8–13) tai jatkaa lukuteoriaan (Osa V), jonka $\mathbb{Z}_p$-kunnat pohjustivat.*
