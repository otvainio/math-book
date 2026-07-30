# Luku 18: Kongruenssit

Luvussa 17 jaollisuus oli "kyllä tai ei" -kysymys. Nyt teemme siitä **laskettavaa**. Gaussin keksimä kongruenssien kieli (1801) muuttaa jaollisuuden aritmetiikaksi, jota voi käsitellä melkein kuin tavallisia yhtälöitä — ja se on modernin salauksen, tietokoneiden ja koodausteorian työkieli. Tunnet sen jo kellotaulusta: $9 + 5 = 2$, kun "kello" on modulo $12$.

---

## 18.1 Kongruenssi

!!! note "Määritelmä"
    Luvut $a$ ja $b$ ovat **kongruentit modulo $n$**, merkitään
    $$a \equiv b \pmod{n},$$
    jos $n \mid (a - b)$ — eli niillä on sama jakojäännös jaettaessa $n$:llä.

Esimerkiksi $17 \equiv 5 \pmod{12}$ (molemmat jättävät jäännöksen $5$), ja $38 \equiv 2 \pmod{9}$. Kongruenssi jakaa kokonaisluvut $n$:ään **jäännösluokkaan** sen mukaan, mikä niiden jäännös on — juuri ne, jotka muodostavat renkaan $\mathbb{Z}_n$ (luku 15).

Kongruenssi käyttäytyy kuin yhtäsuuruus, mikä tekee siitä niin käyttökelpoisen:

!!! abstract "Lause 18.1 (kongruenssin laskusäännöt)"
    Jos $a \equiv b \pmod n$ ja $c \equiv d \pmod n$, niin
    $$a + c \equiv b + d, \qquad a - c \equiv b - d, \qquad ac \equiv bd \pmod n.$$

**Todistus (kertolasku).** Oletuksista $n \mid (a-b)$ ja $n \mid (c-d)$. Kirjoitetaan
$$ac - bd = ac - bc + bc - bd = c(a - b) + b(c - d).$$
Molemmat termit ovat jaollisia $n$:llä, joten $n \mid (ac - bd)$, eli $ac \equiv bd \pmod n$. $\blacksquare$

Voimme siis **korvata luvun millä tahansa kongruentilla** kesken laskun. Tämä tekee suurista laskuista helppoja: esimerkiksi $17 \cdot 14 \pmod{5}$ on $2 \cdot 4 = 8 \equiv 3 \pmod 5$ — ei tarvitse laskea $238$:aa.

---

## 18.2 Jaollisuussäännöt

Kongruenssit selittävät koulun "temput". Miksi luku on jaollinen $9$:llä täsmälleen kun sen numeroiden summa on? Koska $10 \equiv 1 \pmod 9$, ja siten $10^k \equiv 1^k = 1$. Luku $\overline{d_k \ldots d_1 d_0}$ on

$$\sum d_i \cdot 10^i \equiv \sum d_i \cdot 1 = \sum d_i \pmod 9.$$

Luku ja sen numeroiden summa ovat kongruentit modulo $9$ — joten toinen on jaollinen $9$:llä täsmälleen kun toinenkin. Sama temppu antaa säännön $11$:lle ($10 \equiv -1$, vuorotteleva numeroiden summa) ja monelle muulle. Numerotemput eivät ole taikaa vaan kongruensseja.

---

## 18.3 Lineaariset kongruenssit ja käänteisalkiot

Milloin yhtälö $ax \equiv b \pmod n$ ratkeaa? Tämä on modulaarinen "jakolasku".

!!! abstract "Lause 18.2"
    Kongruenssi $ax \equiv b \pmod n$ on ratkeava täsmälleen silloin, kun $\gcd(a, n) \mid b$. Erityisesti jos $\gcd(a,n) = 1$, ratkaisu on yksikäsitteinen modulo $n$.

**Todistus (tapaus $\gcd(a,n)=1$).** Bézout'n nojalla (luku 17) on olemassa $x_0, y$, joille $ax_0 + ny = 1$, eli $ax_0 \equiv 1 \pmod n$. Luku $x_0$ on siis $a$:n **käänteisalkio** modulo $n$, merkitään $a^{-1}$. Silloin ratkaisu on $x \equiv a^{-1} b \pmod n$. $\blacksquare$

Tämä on täsmälleen se, mikä teki $\mathbb{Z}_p$:stä kunnan (luku 15): kun $p$ on alkuluku, jokaisella nollasta eroavalla alkiolla on käänteisalkio, koska $\gcd(a, p) = 1$. Kongruenssien maailmassa "jakolasku" on kertominen käänteisalkiolla.

---

## 18.4 Fermat'n pieni lause ja Eulerin lause

Palataan lauseeseen, jonka jo todistit ryhmäteorialla (luku 14) — mutta nyt kongruenssien kielellä, ja yleistettynä.

!!! abstract "Lause 18.3 (Fermat'n pieni lause)"
    Jos $p$ on alkuluku eikä $p \mid a$, niin
    $$a^{p-1} \equiv 1 \pmod p.$$

Todistus annettiin luvussa 14 (Lagrangen lauseesta). Tässä on sen yleistys mielivaltaiselle modulukselle $n$, joka vaatii uuden funktion:

!!! note "Määritelmä (Eulerin φ-funktio)"
    $\varphi(n)$ on niiden lukujen $\{1, 2, \ldots, n\}$ määrä, jotka ovat suhteellisia alkulukuja $n$:n kanssa (eli $\gcd = 1$).

Esimerkiksi $\varphi(12) = 4$ (luvut $1, 5, 7, 11$), ja alkuluvulle $\varphi(p) = p - 1$ (kaikki paitsi $p$ itse). Nämä $\varphi(n)$ lukua ovat täsmälleen renkaan $\mathbb{Z}_n$ **yksiköt** (kääntyvät alkiot, luku 15), ja ne muodostavat ryhmän kertolaskulla — kertalukua $\varphi(n)$.

!!! abstract "Lause 18.4 (Eulerin lause)"
    Jos $\gcd(a, n) = 1$, niin
    $$a^{\varphi(n)} \equiv 1 \pmod n.$$

**Todistus.** Yksiköt muodostavat ryhmän kertalukua $\varphi(n)$. Alkion $a$ kertaluku jakaa ryhmän kertaluvun (Lagrange, luku 14), joten $a^{\varphi(n)} \equiv 1$. $\blacksquare$

Fermat'n pieni lause on tämän erikoistapaus $n = p$, jolloin $\varphi(p) = p - 1$. Sama ryhmäteoreettinen ydin, laajempi maailma.

---

## 18.5 Kiinalainen jäännöslause

!!! abstract "Lause 18.5 (kiinalainen jäännöslause)"
    Jos $m$ ja $n$ ovat suhteellisia alkulukuja, niin yhtälöparilla
    $$x \equiv a \pmod m, \qquad x \equiv b \pmod n$$
    on ratkaisu, ja se on yksikäsitteinen modulo $mn$.

Toisin sanoen: voit vapaasti valita jäännöksen modulo $m$ ja jäännöksen modulo $n$ (kun ne ovat jaottomia), ja on täsmälleen yksi luku (modulo $mn$), joka toteuttaa molemmat. Nimi juontaa 300-luvun kiinalaiseen ongelmaan sotilaiden laskemisesta rivistöittäin. Tulos on koodausteorian ja nopean laskennan kulmakivi — ja se sanoo, että "kello modulo $mn$" hajoaa itsenäisiksi "kelloiksi modulo $m$ ja modulo $n$".

---

## 18.6 Sovellus: RSA-salaus

Kongruenssit eivät ole leikkiä — ne suojaavat jokaisen pankkisiirron. **RSA-salaus** (1977) toimii näin, ja se lepää täsmälleen tämän luvun tuloksilla:

1. Valitaan kaksi suurta alkulukua $p$ ja $q$, ja lasketaan $n = pq$.
2. Julkinen avain käyttää eksponenttia $e$, salainen avain eksponenttia $d$, jotka toteuttavat $ed \equiv 1 \pmod{\varphi(n)}$.
3. Viesti $m$ salataan: $c \equiv m^e \pmod n$. Puretaan: $m \equiv c^d \pmod n$.

Että purku palauttaa alkuperäisen viestin, seuraa **Eulerin lauseesta**: $m^{ed} = m^{1 + k\varphi(n)} = m \cdot (m^{\varphi(n)})^k \equiv m \pmod n$. Turvallisuus perustuu siihen, että suuren luvun $n = pq$ **tekijöihinjako on käytännössä mahdotonta** — vaikka $n$ on julkinen, kukaan ei osaa löytää $p$:tä ja $q$:ta ajoissa. Alkulukujen jakamattomuus, aritmetiikan peruslause ja Eulerin lause suojaavat koko digitaalista maailmaa.

---

## 18.7 Yhteenveto

- **Kongruenssi** $a \equiv b \pmod n$: sama jäännös; käyttäytyy kuin yhtäsuuruus (yhteen-, vähennys-, kertolasku).
- **Jaollisuussäännöt** ($9$, $11$, …) ovat kongruensseja: $10 \equiv 1 \pmod 9$.
- **Lineaarinen kongruenssi** $ax \equiv b$ ratkeaa käänteisalkiolla, jonka Bézout antaa (kun $\gcd(a,n)=1$).
- **Eulerin lause:** $a^{\varphi(n)} \equiv 1 \pmod n$ (Fermat'n pieni lause on tapaus $n = p$).
- **Kiinalainen jäännöslause:** erilliset modulot yhdistyvät yksikäsitteisesti.
- **RSA:** koko moderni salaus lepää näiden varassa.

---

## Harjoitukset

**18.1 (★)** Laske $7^{100} \pmod{10}$ (eli mikä on luvun $7^{100}$ viimeinen numero)?

??? tip "Vihje"
    Laske $7$:n potenssien viimeisiä numeroita: $7, 49, 343, \ldots$ Ne toistuvat jaksossa.

??? success "Vastaus"
    Potenssien viimeiset numerot (mod 10): $7^1 \equiv 7$, $7^2 \equiv 9$, $7^3 \equiv 3$, $7^4 \equiv 1$, ja sitten jakso toistuu (pituus $4$). Koska $100 = 4\cdot25$, on $7^{100} = (7^4)^{25} \equiv 1^{25} = 1 \pmod{10}$. Viimeinen numero on **1**. $\blacksquare$

---

**18.2 (★)** Tarkista jaollisuussäännöllä, onko $123\,456\,789$ jaollinen $9$:llä.

??? success "Vastaus"
    Numeroiden summa: $1+2+3+4+5+6+7+8+9 = 45$, ja $45$ on jaollinen $9$:llä ($45 = 9\cdot5$). Koska luku on kongruentti numeroidensa summan kanssa modulo $9$, myös $123\,456\,789$ on jaollinen $9$:llä. $\blacksquare$

---

**18.3 (★★)** Etsi luvun $5$ käänteisalkio modulo $12$ (eli $x$, jolle $5x \equiv 1 \pmod{12}$).

??? tip "Vihje"
    Kokeile arvoja, tai käytä Bézout'ta: $5x + 12y = 1$.

??? success "Vastaus"
    Etsitään $x$: $5\cdot5 = 25 = 24 + 1 \equiv 1 \pmod{12}$. Siis $5^{-1} \equiv 5 \pmod{12}$ (luku on oma käänteisalkionsa). $\blacksquare$

---

**18.4 (★★)** Käytä Fermat'n pientä lausetta laskeaksesi $3^{100} \pmod 7$.

??? tip "Vihje"
    Fermat: $3^6 \equiv 1 \pmod 7$. Kirjoita $100 = 6\cdot16 + 4$.

??? success "Vastaus"
    Fermat'n pienen lauseen nojalla $3^6 \equiv 1 \pmod 7$. Koska $100 = 6\cdot16 + 4$:
    $$3^{100} = (3^6)^{16}\cdot 3^4 \equiv 1^{16}\cdot 3^4 = 81 \equiv 81 - 77 = 4 \pmod 7.$$
    Siis $3^{100} \equiv 4 \pmod 7$. $\blacksquare$

---

**18.5 (★★★)** Ratkaise kiinalaisella jäännöslauseella yhtälöpari
$$x \equiv 2 \pmod 3, \qquad x \equiv 3 \pmod 5.$$

??? tip "Vihje"
    Etsi luku, joka jättää jäännöksen $2$ kolmella ja $3$ viidellä. Voit kokeilla lukuja $3, 8, 13, \ldots$ (jäännös $3$ mod 5) ja katsoa, mikä toteuttaa myös ensimmäisen ehdon — ratkaisu on yksikäsitteinen modulo $15$.

??? success "Vastaus"
    Toisen ehdon toteuttavat luvut ovat $3, 8, 13, \ldots$ (muotoa $5k + 3$). Tarkistetaan, mikä jättää jäännöksen $2$ modulo $3$:
    - $3 \equiv 0$, $8 \equiv 2$ ✓
    
    Siis $x \equiv 8 \pmod{15}$. Tarkistus: $8 = 3\cdot2 + 2$ (jäännös $2$ mod 3 ✓) ja $8 = 5\cdot1 + 3$ (jäännös $3$ mod 5 ✓). Ratkaisu on yksikäsitteinen modulo $15 = 3\cdot5$. $\blacksquare$

---

*Seuraava luku: Zeta-funktio ja alkulukujen jakauma — jossa lukuteoria ja analyysi kohtaavat, ja koko zeta-työsi kokoontuu yhteen huipennukseen.*
