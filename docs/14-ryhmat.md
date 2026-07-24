# Luku 14: Ryhmät

Tähän asti olemme tutkineet *lukuja*. Nyt nostamme katseen: emme kysy enää "mikä luku", vaan "millainen **rakenne**". Abstrakti algebra tutkii joukkoja, joissa on laskutoimitus — ja hämmästyttävää kyllä, samat lait toistuvat paikoissa, joilla ei näytä olevan mitään yhteistä: kokonaislukujen yhteenlaskussa, kellon numeroissa, yksikönjuurissasi, Rubikin kuution käännöissä, molekyylien symmetrioissa.

**Ryhmä** on tämän kaiken yhteinen ydin. Kun ymmärrät sen, näet saman rakenteen kaikkialla.

---

## 14.1 Mikä on ryhmä

!!! note "Määritelmä"
    **Ryhmä** on joukko $G$ varustettuna laskutoimituksella $*$ (sääntö, joka liittää kahteen alkioon kolmannen), niin että:

    1. **Sulkeutuvuus:** jos $a, b \in G$, niin $a * b \in G$.
    2. **Liitännäisyys:** $(a * b) * c = a * (b * c)$ kaikilla $a, b, c \in G$.
    3. **Neutraalialkio:** on olemassa $e \in G$, jolle $e * a = a * e = a$ kaikilla $a$.
    4. **Käänteisalkio:** jokaisella $a \in G$ on $a^{-1} \in G$, jolle $a * a^{-1} = a^{-1} * a = e$.

    Jos lisäksi $a * b = b * a$ kaikilla $a, b$, ryhmä on **vaihdannainen** eli **Abelin ryhmä**.

Neljä lakia. Ei enempää. Katsotaan heti, kuinka monta tuttua asiaa toteuttaa ne.

### Esimerkkejä

- **$(\mathbb{Z}, +)$** — kokonaisluvut yhteenlaskulla. Neutraalialkio on $0$, alkion $a$ käänteisalkio on $-a$. Abelin ryhmä.
- **$(\mathbb{Q}^*, \cdot)$** — nollasta eroavat rationaaliluvut kertolaskulla. Neutraalialkio $1$, käänteisalkio $\frac1a$. Abelin. *(Nolla on jätettävä pois — sillä ei ole käänteisalkiota.)*
- **$(\mathbb{Z}_n, +)$** — kellon aritmetiikka: luvut $\{0, 1, \ldots, n-1\}$ yhteenlaskulla modulo $n$. Kun $n = 12$, tämä on kellotaulu: $9 + 5 = 2$. Abelin.
- **Yksikönjuuret** — yhtälön $z^n = 1$ ratkaisut kompleksitasossa, kertolaskulla. Neutraalialkio $1$, ja kahden juuren tulo on taas juuri. Tästä lisää kohta — se on sinun ryhmäsi.
- **$S_n$ — symmetrinen ryhmä** — joukon $\{1, 2, \ldots, n\}$ kaikki permutaatiot (uudelleenjärjestykset), operaationa peräkkäin suorittaminen. Tämä **ei ole Abelin** kun $n \geq 3$: järjestyksellä on väliä, aivan kuten yhdistetyillä funktioilla luvussa 2.

!!! tip "Ryhmä on 'peruuttamisen' matematiikkaa"
    Neljä lakia takaavat, että jokainen operaatio voidaan **peruuttaa** (käänteisalkiolla) ja että peruuttaminen on johdonmukaista (liitännäisyys). Siksi ryhmät kuvaavat luonnostaan kaikkea käännettävää: symmetrioita, siirtoja, sekoituksia. Ei-käännettävät asiat (kuten nollalla kertominen) eivät kuulu ryhmään.

---

## 14.2 Perusominaisuudet

Neljästä aksioomasta seuraa heti asioita, joita pidämme itsestäänselvinä lukujen kanssa — mutta jotka on nyt *todistettava*, koska ryhmä voi olla mitä tahansa.

!!! abstract "Lause 14.1 (yksikäsitteisyydet)"
    Ryhmässä on täsmälleen yksi neutraalialkio, ja jokaisella alkiolla täsmälleen yksi käänteisalkio.

**Todistus.** *Neutraalialkio:* oletetaan, että $e$ ja $e'$ ovat molemmat neutraalialkioita. Silloin $e = e * e'$ (koska $e'$ on neutraali) $= e'$ (koska $e$ on neutraali). Siis $e = e'$.

*Käänteisalkio:* oletetaan, että $b$ ja $c$ ovat molemmat alkion $a$ käänteisalkioita. Silloin

$$b = b * e = b * (a * c) = (b * a) * c = e * c = c.$$

Käytimme liitännäisyyttä keskellä. Siis $b = c$. $\blacksquare$

Huomaa, kuinka *jokainen* askel nojaa täsmälleen johonkin neljästä aksioomasta. Tämä on abstraktin algebran tyyli: mitään ei oleteta, kaikki johdetaan.

!!! abstract "Lause 14.2 (supistussääntö)"
    Ryhmässä $a * b = a * c \implies b = c$.

**Todistus.** Kerrotaan vasemmalta alkiolla $a^{-1}$: $\;a^{-1} * (a * b) = a^{-1} * (a * c)$. Liitännäisyydellä $(a^{-1} * a) * b = (a^{-1} * a) * c$, eli $e * b = e * c$, siis $b = c$. $\blacksquare$

Tästä eteenpäin kirjoitamme usein $ab$ eikä $a * b$, ja $a^n$ tarkoittaa $a * a * \cdots * a$ ($n$ kertaa) — täsmälleen kuten lukujen kanssa.

---

## 14.3 Alkion kertaluku ja sykliset ryhmät

!!! note "Määritelmä"
    Ryhmän $G$ **kertaluku** $|G|$ on sen alkioiden lukumäärä. Alkion $a$ **kertaluku** on pienin positiivinen kokonaisluku $k$, jolle $a^k = e$ (jos sellaista ei ole, kertaluku on ääretön).

Esimerkki: ryhmässä $(\mathbb{Z}_6, +)$ alkion $2$ kertaluku on $3$, koska $2 + 2 + 2 = 6 \equiv 0$, eikä pienempi monikerta ole nolla.

!!! note "Määritelmä"
    Ryhmä on **syklinen**, jos on olemassa alkio $g$ (kutsutaan **virittäjäksi**), jonka potenssit tuottavat koko ryhmän: $G = \{e, g, g^2, g^3, \ldots\}$.

Ja nyt palataan sinun työhösi. Muistat yksikönjuuret: yhtälön $z^n = 1$ ratkaisut ovat

$$\omega_k = e^{2\pi i k / n}, \qquad k = 0, 1, \ldots, n-1,$$

tasavälein yksikköympyrällä (johdit tämän Eulerin kaavalla). Nämä muodostavat ryhmän kertolaskulla — ja se on **syklinen**:

!!! abstract "Lause 14.3"
    $n$:nnet yksikönjuuret muodostavat syklisen ryhmän kertalukua $n$, jonka virittää $\omega = e^{2\pi i/n}$.

**Todistus.** Tulo $\omega_j \omega_k = e^{2\pi i (j+k)/n} = \omega_{(j+k) \bmod n}$ on taas yksikönjuuri (sulkeutuvuus). Neutraalialkio on $\omega_0 = 1$, ja $\omega_k$:n käänteisalkio on $\omega_{n-k}$. Liitännäisyys periytyy kompleksilukujen kertolaskusta. Lisäksi jokainen juuri on virittäjän $\omega$ potenssi: $\omega_k = \omega^k$. Siis ryhmä on syklinen. $\blacksquare$

Itse asiassa yksikönjuuret ovat "sama" ryhmä kuin $(\mathbb{Z}_n, +)$: potenssiin korottaminen ($\omega^j \cdot \omega^k = \omega^{j+k}$) vastaa täsmälleen yhteenlaskua modulo $n$. Kaksi täysin erinäköistä oliota — pyörivät kompleksipisteet ja kellon numerot — ovat *rakenteeltaan identtiset*. Juuri tätä abstrakti algebra paljastaa: pinnan alla on yksi ryhmä, monta naamiota.

---

## 14.4 Aliryhmät

!!! note "Määritelmä"
    Joukon $G$ osajoukko $H$ on **aliryhmä**, jos $H$ on itse ryhmä samalla laskutoimituksella: se sisältää neutraalialkion, on suljettu operaation suhteen, ja sisältää jokaisen alkionsa käänteisalkion.

Esimerkiksi parilliset kokonaisluvut $2\mathbb{Z} = \{\ldots, -2, 0, 2, 4, \ldots\}$ ovat ryhmän $(\mathbb{Z}, +)$ aliryhmä. Samoin ryhmän $(\mathbb{Z}_{12}, +)$ sisällä $\{0, 3, 6, 9\}$ on aliryhmä (kertalukua $4$).

Huomaa jälkimmäisessä: aliryhmän kertaluku $4$ **jakaa** koko ryhmän kertaluvun $12$. Tämä ei ole sattuma — se on koko luvun kruununjalokivi.

---

## 14.5 Lagrangen lause

!!! abstract "Lause 14.4 (Lagrange)"
    Äärellisen ryhmän aliryhmän kertaluku jakaa aina ryhmän kertaluvun: jos $H$ on ryhmän $G$ aliryhmä, niin $|H|$ jakaa $|G|$.

Idea todistukseen on kaunis. Aliryhmä $H$ "monistetaan" ympäri ryhmää yhtä suuriksi paloiksi, jotka peittävät sen aukottomasti.

!!! note "Sivuluokka"
    Alkion $a \in G$ määräämä (vasen) **sivuluokka** on joukko
    $$aH = \{\, a h \mid h \in H \,\}.$$

**Todistus (Lagrange).** Osoitetaan kolme asiaa sivuluokista.

*(i) Sivuluokat peittävät koko ryhmän.* Jokainen $a \in G$ kuuluu omaan sivuluokkaansa $aH$ (koska $a = ae \in aH$).

*(ii) Kaksi sivuluokkaa ovat joko samat tai erilliset.* Oletetaan, että $aH$ ja $bH$ leikkaavat: olkoon $x \in aH \cap bH$. Silloin $x = ah_1 = bh_2$ joillakin $h_1, h_2 \in H$, joten $a = b h_2 h_1^{-1}$. Koska $h_2 h_1^{-1} \in H$, seuraa että jokainen $ah = b(h_2 h_1^{-1} h) \in bH$, eli $aH \subseteq bH$; symmetrisesti $bH \subseteq aH$. Siis $aH = bH$.

*(iii) Jokaisessa sivuluokassa on yhtä monta alkiota kuin $H$:ssa.* Kuvaus $h \mapsto ah$ on bijektio $H \to aH$: se on surjektio määritelmän nojalla ja injektio supistussäännön (Lause 14.2) nojalla. Siis $|aH| = |H|$.

Yhdistetään: ryhmä $G$ jakautuu erillisiin sivuluokkiin (i, ii), joista jokaisessa on täsmälleen $|H|$ alkiota (iii). Jos sivuluokkia on $m$ kappaletta, niin

$$|G| = m \cdot |H|,$$

joten $|H|$ jakaa $|G|$. $\blacksquare$

Seuraus on välitön ja voimakas:

!!! abstract "Seuraus 14.5"
    Äärellisen ryhmän jokaisen alkion kertaluku jakaa ryhmän kertaluvun.

**Todistus.** Alkion $a$ potenssit $\{e, a, a^2, \ldots, a^{k-1}\}$ (missä $k$ on $a$:n kertaluku) muodostavat syklisen aliryhmän kertalukua $k$. Lagrangen nojalla $k$ jakaa $|G|$. $\blacksquare$

---

## 14.6 Palkinto: Fermat'n pieni lause ryhmäteoriasta

Näytetään, kuinka abstrakti rakenne tuottaa konkreettisen lukuteorian tuloksen ilmaiseksi. Kun $p$ on alkuluku, luvut $\{1, 2, \ldots, p-1\}$ muodostavat ryhmän kertolaskulla modulo $p$ (todistetaan luvussa 15, että jokaisella on käänteisalkio). Tämän ryhmän kertaluku on $p - 1$.

!!! abstract "Lause 14.6 (Fermat'n pieni lause)"
    Jos $p$ on alkuluku eikä $a$ ole jaollinen $p$:llä, niin
    $$a^{p-1} \equiv 1 \pmod{p}.$$

**Todistus.** Alkio $a$ kuuluu ryhmään $(\mathbb{Z}_p^*, \cdot)$, jonka kertaluku on $p-1$. Olkoon $d$ alkion $a$ kertaluku. Seurauksen 14.5 nojalla $d$ jakaa $p-1$, siis $p - 1 = d m$ jollakin kokonaisluvulla $m$. Silloin

$$a^{p-1} = a^{dm} = (a^d)^m = e^m = 1 \pmod p. \qquad \blacksquare$$

Kolme riviä. Vertaa tätä siihen, miten Fermat'n pieni lause yleensä todistetaan alkeellisesti (induktiolla tai binomikaavalla) — se on työläämpää. Abstrakti rakenne teki siitä väistämättömän. **Tämä on syy, miksi algebraa kannattaa opiskella:** se ei ole vaikeampaa vaan *helpompaa*, kun oikea rakenne on paikallaan.

---

## 14.7 Yhteenveto

- **Ryhmä** = joukko + laskutoimitus, joka on suljettu, liitännäinen, ja jossa on neutraali- ja käänteisalkiot.
- Neutraali- ja käänteisalkiot ovat **yksikäsitteisiä**; supistussääntö pätee.
- **Syklinen ryhmä** virittyy yhdestä alkiosta; yksikönjuuresi ovat esimerkki, sama rakenne kuin $(\mathbb{Z}_n, +)$.
- **Lagrangen lause:** aliryhmän kertaluku jakaa ryhmän kertaluvun.
- Seurauksena alkion kertaluku jakaa ryhmän kertaluvun — ja tästä putoaa **Fermat'n pieni lause** kolmella rivillä.

---

## Harjoitukset

**14.1 (★)** Onko $(\mathbb{Z}, \cdot)$ (kokonaisluvut kertolaskulla) ryhmä? Perustele.

??? success "Vastaus"
    Ei ole. Neutraalialkio olisi $1$, mutta esimerkiksi luvulla $2$ ei ole käänteisalkiota kokonaislukujen joukossa (sen pitäisi olla $\frac12 \notin \mathbb{Z}$). Aksiooma 4 pettää. $\blacksquare$

    *(Itse asiassa vain $1$ ja $-1$ ovat kääntyviä. Siksi kertolasku tekee kokonaisluvuista renkaan, ei ryhmää — luku 15.)*

---

**14.2 (★)** Kirjoita ryhmän $(\mathbb{Z}_5, +)$ jokaisen alkion kertaluku.

??? success "Vastaus"
    Ryhmä on $\{0,1,2,3,4\}$, kertaluku $5$.
    - $0$: kertaluku $1$ (se on neutraalialkio).
    - $1$: $1+1+1+1+1 = 5 \equiv 0$, kertaluku $5$.
    - $2$: $2,4,6\equiv1,8\equiv3,10\equiv0$ — kertaluku $5$.
    - $3, 4$: samoin kertaluku $5$.

    Kaikkien nollasta eroavien kertaluku on $5$. Tämä on tyypillistä: koska $5$ on alkuluku, Lagrangen nojalla ainoat mahdolliset kertaluvut ovat $1$ ja $5$. $\blacksquare$

---

**14.3 (★★)** Todista, että ryhmässä $(ab)^{-1} = b^{-1}a^{-1}$ (huomaa käänteinen järjestys!).

??? tip "Vihje"
    Käänteisalkion yksikäsitteisyyden nojalla riittää osoittaa, että $b^{-1}a^{-1}$ toimii alkion $ab$ käänteisalkiona — eli että niiden tulo on $e$.

??? success "Vastaus"
    Lasketaan tulo, käyttäen liitännäisyyttä:
    $$(ab)(b^{-1}a^{-1}) = a(bb^{-1})a^{-1} = a e a^{-1} = a a^{-1} = e.$$
    Samoin $(b^{-1}a^{-1})(ab) = e$. Siis $b^{-1}a^{-1}$ on alkion $ab$ käänteisalkio, ja käänteisalkion yksikäsitteisyyden (Lause 14.1) nojalla $(ab)^{-1} = b^{-1}a^{-1}$. $\blacksquare$

    *(Analogia: pukiessa ensin sukat, sitten kengät — riisuessa ensin kengät, sitten sukat. Käänteisoperaatiot tulevat käänteisessä järjestyksessä.)*

---

**14.4 (★★)** Osoita, että joukko $\{1, -1, i, -i\}$ on ryhmä kompleksilukujen kertolaskulla, ja että se on syklinen. Mikä on sen virittäjä?

??? tip "Vihje"
    Nämä ovat neljännet yksikönjuuret. Laske $i$:n potensseja.

??? success "Vastaus"
    Nämä ovat yhtälön $z^4 = 1$ ratkaisut. Lasketaan $i$:n potenssit:
    $$i^1 = i, \quad i^2 = -1, \quad i^3 = -i, \quad i^4 = 1.$$
    Potenssit käyvät läpi kaikki neljä alkiota, joten joukko on suljettu, sisältää neutraalialkion $1 = i^4$, ja on syklinen virittäjänään $i$ (myös $-i = i^3$ virittää). Käänteisalkiot: $1^{-1}=1$, $(-1)^{-1}=-1$, $i^{-1} = -i$, $(-i)^{-1} = i$. Kaikki aksioomat täyttyvät. $\blacksquare$

---

**14.5 (★★★)** Olkoon $G$ ryhmä, jossa $a^2 = e$ **jokaisella** alkiolla $a$. Todista, että $G$ on Abelin ryhmä (vaihdannainen).

??? tip "Vihje"
    Ehto $a^2 = e$ tarkoittaa, että jokainen alkio on oma käänteisalkionsa: $a^{-1} = a$. Sovella tätä alkioon $ab$ ja käytä harjoitusta 14.3.

??? success "Vastaus"
    Ehdosta $a^2 = e$ seuraa, että jokainen alkio on oma käänteisalkionsa: $a^{-1} = a$ (kerro $a^2 = e$ oikealta alkiolla $a^{-1}$).

    Sovelletaan tätä alkioon $ab$: koska $(ab)^2 = e$, on $(ab)^{-1} = ab$. Mutta harjoituksen 14.3 nojalla $(ab)^{-1} = b^{-1}a^{-1} = ba$ (käyttäen $a^{-1}=a$, $b^{-1}=b$). Yhdistämällä:
    $$ab = (ab)^{-1} = ba.$$
    Siis $ab = ba$ kaikilla $a, b$, ja $G$ on Abelin. $\blacksquare$

---

*Seuraava luku: Renkaat ja kunnat — mitä tapahtuu, kun yhden laskutoimituksen sijaan onkin kaksi.*
