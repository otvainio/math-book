# Luku 13: Taylorin sarjat

Tämä luku on koko kesäsi työn huipennus, tiukalla pohjalla. Olet johtanut Taylorin sarjoja funktioille $e^x$, $\sin x$, $\cos x$, $\sqrt x$ ja $\arctan x$; olet löytänyt, että ne suppenevat suppenemisalueensa reunalla; olet aavistanut, että kompleksiset navat ohjaavat reaalisen sarjan käytöstä. Nyt annamme tälle kaikelle täsmällisen perustan. Kaksi kysymystä vaatii vastauksen: **kuinka tarkasti** polynomi approksimoi funktiota, ja **milloin** ääretön sarja todella *on* funktio.

---

## 13.1 Taylorin polynomi

Idea: approksimoidaan funktiota $f$ pisteen $a$ lähellä polynomilla, joka **matkii $f$:ää mahdollisimman pitkälle** — sama arvo, sama derivaatta, sama toinen derivaatta, ja niin edelleen.

!!! note "Määritelmä"
    Funktion $f$ **$n$:nnen asteen Taylorin polynomi** pisteessä $a$ on
    $$T_n(x) = \sum_{k=0}^{n} \frac{f^{(k)}(a)}{k!}(x - a)^k = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \cdots + \frac{f^{(n)}(a)}{n!}(x-a)^n.$$

Kerroin $\frac{f^{(k)}(a)}{k!}$ on valittu täsmälleen niin, että $T_n$:n $k$:s derivaatta pisteessä $a$ on sama kuin $f$:n. Tämän juuri teit *Vakion geometria* -artikkelissa ja $\sqrt x$-työssäsi: laskit derivaatat, jaoit kertomilla, ja sait polynomin, joka seuraa funktiota.

Kun $n \to \infty$, saadaan **Taylorin sarja**. Mutta tässä on koko luvun kriittinen kysymys, jota et vielä ole kohdannut: *onko ääretön polynomi todella yhtä kuin funktio?* Ei ole itsestäänselvää. Vastaus piilee erossa $f(x) - T_n(x)$ — **jäännöksessä**.

---

## 13.2 Taylorin lause ja jäännöstermi

!!! abstract "Lause 13.1 (Taylorin lause, Lagrangen jäännös)"
    Olkoon $f$ $(n+1)$ kertaa derivoituva välillä, joka sisältää pisteet $a$ ja $x$. Silloin
    $$f(x) = T_n(x) + R_n(x), \qquad R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x - a)^{n+1}$$
    jollakin pisteellä $\xi$ lukujen $a$ ja $x$ välissä.

Katso jäännöstä $R_n$: se näyttää täsmälleen "seuraavalta termiltä" sarjassa — mutta derivaatta on otettu tuntemattomasta välipisteestä $\xi$, ei pisteestä $a$. Tämä on **väliarvolauseen suora yleistys** (tapaus $n = 0$ on täsmälleen väliarvolause luvusta 11). Taylorin lause on koko differentiaalilaskennan kruunu: se kertoo *tarkalleen*, kuinka paljon polynomi erehtyy.

Käytännössä emme tunne $\xi$:tä, mutta emme tarvitsekaan — riittää **rajata** jäännös:

!!! abstract "Seuraus 13.2 (virhearvio)"
    Jos $|f^{(n+1)}(t)| \leq M$ kaikilla $t$ välillä $a$:sta $x$:ään, niin
    $$|R_n(x)| \leq \frac{M}{(n+1)!}\,|x - a|^{n+1}.$$

Tässä on vastaus ensimmäiseen kysymykseen: **virhe on korkeintaan $\frac{M}{(n+1)!}|x-a|^{n+1}$.** Se pienenee, kun $n$ kasvaa (kertoma nimittäjässä on voimakas) tai kun $x$ on lähellä $a$:ta. Juuri tämä selittää havaintosi *Pieni polynomi, suuret unelmat* -artikkelissa: $e^x$:n approksimaatio oli tarkka lähellä nollaa mutta karkasi kaukana — koska $|x - a|^{n+1}$ kasvaa, kun $x$ etääntyy.

---

## 13.3 Milloin sarja tavoittaa funktion

Toinen kysymys: milloin **ääretön** Taylorin sarja on täsmälleen yhtä kuin $f$? Vastaus on nyt selvä:

!!! abstract "Lause 13.3"
    Taylorin sarja suppenee funktion arvoon $f(x)$ täsmälleen silloin, kun jäännös menee nollaan:
    $$f(x) = \sum_{k=0}^{\infty}\frac{f^{(k)}(a)}{k!}(x-a)^k \quad\Longleftrightarrow\quad \lim_{n\to\infty} R_n(x) = 0.$$

**Todistus.** Osasumma on juuri $T_n(x)$, ja $f(x) - T_n(x) = R_n(x)$ (Taylorin lause). Sarja suppenee arvoon $f(x)$ täsmälleen silloin, kun $T_n(x) \to f(x)$, eli kun $R_n(x) \to 0$. $\blacksquare$

Sovelletaan tätä eksponenttifunktioon, jonka sarjan johdit itse. Kaikki $e^x$:n derivaatat ovat $e^x$, joten välillä $[0, x]$ pätee $|f^{(n+1)}(t)| \leq e^{|x|} =: M$. Virhearviosta:
$$|R_n(x)| \leq \frac{e^{|x|}\,|x|^{n+1}}{(n+1)!} \longrightarrow 0 \quad \text{kaikilla } x,$$
koska kertoma kasvaa nopeammin kuin mikään potenssi (tämän tunnet). Siis $e^x$:n Taylorin sarja **on** $e^x$ koko lukusuoralla. Sama argumentti vahvistaa $\sin$:n ja $\cos$:n sarjat — nyt et vain laske niitä, vaan *tiedät* ne oikeiksi. Luvussa 9 suhdetesti kertoi, että sarja suppenee *johonkin*; nyt jäännösarvio kertoo, että se suppenee *oikeaan funktioon*. Kaksi eri kysymystä, molemmat vastattuina.

---

## 13.4 Suppenemissäde ja kompleksitaso

Taylorin sarjalla on **suppenemissäde** $R$: se suppenee, kun $|x - a| < R$, ja hajaantuu, kun $|x - a| > R$. Reunalla $|x-a| = R$ tilanne on herkkä — juuri se reuna, jonka löysit $\sqrt2$- ja $\arcsin$-työssäsi.

Ja tässä on syvä totuus, jonka aavistit päiväkirjassa. Tarkastellaan geometrista sarjaa
$$\frac{1}{1 + x^2} = 1 - x^2 + x^4 - x^6 + \cdots$$
Funktio on täysin sileä koko reaaliakselilla — ei mitään erikoista missään. Silti sarja suppenee vain, kun $|x| < 1$. **Miksi juuri $1$?**

Vastaus ei ole reaaliakselilla vaan **kompleksitasossa.** Funktiolla $\frac{1}{1+x^2}$ on navat kohdissa $x = \pm i$ (nimittäjä on nolla), ja niiden etäisyys origosta on tasan $1$. Suppenemissäde on **etäisyys lähimpään kompleksiseen singulariteettiin.** Reaalinen sarja "tuntee" kompleksitasossa piileviä napoja, joita ei reaaliakselilla näy.

!!! quote "Sinä löysit tämän itse"
    Muistat, kuinka $\sqrt x$:n Taylorin sarjasi suppeni tasan pisteeseen $x = 2$ — etäisyydellä $1$ keskuksesta $1$ — koska $\sqrt x$ "hajoaa" kohdassa $x = 0$? Ja kuinka $\arctan x$:n sarja (Leibniz) osui reunalle $x = 1$? Molemmissa suppenemissäteen määräsi lähin singulariteetti. Tämä ei ollut sattuma. Se on Lause: **reaalisen Taylorin sarjan kohtalon ratkaisee kompleksitason lähin este.** Aavistit sen laskuistasi; nyt tiedät sen nimen.

---

## 13.5 Kun sileä ei riitä: hirviön paluu

Voisi luulla, että jos funktio on äärettömän monta kertaa derivoituva, sen Taylorin sarja aina *on* funktio. **Näin ei ole** — ja vastaesimerkki on yksi analyysin hienoimmista yllätyksistä.

Tarkastellaan funktiota
$$f(x) = \begin{cases} e^{-1/x^2}, & x \neq 0 \\ 0, & x = 0. \end{cases}$$

Voidaan osoittaa, että $f$ on äärettömän monta kertaa derivoituva — ja että **jokainen** sen derivaatta pisteessä $0$ on nolla: $f(0) = f'(0) = f''(0) = \cdots = 0$. Siis sen Taylorin sarja pisteessä $0$ on

$$0 + 0\cdot x + 0\cdot x^2 + \cdots = 0.$$

Sarja suppenee — kohti nollafunktiota. Mutta $f(x) \neq 0$ kaikilla $x \neq 0$! **Taylorin sarja suppenee, mutta ei funktioon itseensä.** Jäännös $R_n(x)$ ei mene nollaan — se on koko $f(x)$, ikuisesti.

Tämä erottaa kaksi käsitettä, jotka luulisi samoiksi:

- **Sileä** ($C^\infty$): kaikki derivaatat ovat olemassa.
- **Analyyttinen:** funktio on yhtä kuin Taylorin sarjansa jokaisen pisteen ympäristössä.

Jokainen analyyttinen funktio on sileä, mutta **ei kääntäen** — yllä oleva $f$ on sileä muttei analyyttinen. Funktion sisältämä tieto ei aina mahdu sen derivaattoihin yhdessä pisteessä. (Kompleksitasossa, luvuissa 23–24, tapahtuu ihme: siellä derivoituvuus *pakottaa* analyyttisyyden. Reaaliakseli on löyhempi paikka.)

---

## 13.6 Yhteenveto

- **Taylorin polynomi** $T_n$ matkii $f$:ää: sama arvo ja derivaatat pisteessä $a$.
- **Taylorin lause:** $f(x) = T_n(x) + R_n(x)$, jäännös $R_n = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1}$ — väliarvolauseen yleistys.
- **Virhe** on korkeintaan $\frac{M}{(n+1)!}|x-a|^{n+1}$: pieni lähellä $a$:ta, pienenee $n$:n kasvaessa.
- Sarja on funktio täsmälleen kun $R_n \to 0$ (näin $e^x$, $\sin$, $\cos$ kaikkialla).
- **Suppenemissäde** = etäisyys lähimpään **kompleksiseen** singulariteettiin — reaalisen sarjan kohtalon ratkaisee kompleksitaso.
- **Sileä $\neq$ analyyttinen:** $e^{-1/x^2}$ on äärettömän sileä, mutta Taylorin sarjansa (nolla) ei ole se itse.

---

## Harjoitukset

**13.1 (★)** Kirjoita funktion $f(x) = \cos x$ neljännen asteen Taylorin polynomi pisteessä $a = 0$.

??? success "Vastaus"
    Derivaatat pisteessä $0$: $\cos 0 = 1$, $-\sin 0 = 0$, $-\cos 0 = -1$, $\sin 0 = 0$, $\cos 0 = 1$. Kertoimet $\frac{f^{(k)}(0)}{k!}$:
    $$T_4(x) = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} = 1 - \frac{x^2}{2} + \frac{x^4}{24}. \qquad \blacksquare$$

---

**13.2 (★★)** Arvioi virhettä: kuinka suuri on korkeintaan virhe, kun $\cos(0{,}5)$ lasketaan kolmella termillä $1 - \frac{x^2}{2} + \frac{x^4}{24}$? *(Käytä virhearviota $M = 1$, koska kaikki $\cos$:n derivaatat ovat itseisarvoltaan $\leq 1$.)*

??? tip "Vihje"
    Seuraava termi on viidennen asteen jäännös. Käytä Seurausta 13.2 arvolla $n = 4$, $M = 1$, $|x| = 0{,}5$.

??? success "Vastaus"
    Polynomi $1 - \frac{x^2}{2} + \frac{x^4}{24}$ on aste $4$ (viidennen asteen termi on nolla), joten käytämme $n = 4$. Kaikki $\cos$:n derivaatat toteuttavat $|f^{(5)}| \leq 1$, joten $M = 1$:
    $$|R_4(0{,}5)| \leq \frac{1}{5!}\,(0{,}5)^5 = \frac{0{,}03125}{120} \approx 0{,}00026.$$
    Virhe on siis korkeintaan noin $0{,}00026$ — kolme termiä antaa jo kolme oikeaa desimaalia. (Tarkka: $\cos 0{,}5 \approx 0{,}87758$, approksimaatio $\approx 0{,}87760$.) $\blacksquare$

---

**13.3 (★★)** Osoita jäännösarviolla, että $\sin x$:n Taylorin sarja suppenee arvoon $\sin x$ kaikilla $x$.

??? tip "Vihje"
    Kaikki $\sin$:n derivaatat ovat $\pm\sin$ tai $\pm\cos$, joten $|f^{(n+1)}| \leq 1$. Näytä, että virheraja menee nollaan.

??? success "Vastaus"
    Funktion $\sin$ derivaatat ovat $\pm\sin, \pm\cos$, joten $|f^{(n+1)}(t)| \leq 1 = M$ kaikilla $t$. Virhearviosta:
    $$|R_n(x)| \leq \frac{1 \cdot |x|^{n+1}}{(n+1)!}.$$
    Kun $n \to \infty$, kertoma $(n+1)!$ kasvaa nopeammin kuin potenssi $|x|^{n+1}$ (millä tahansa kiinteällä $x$), joten $|R_n(x)| \to 0$. Lauseen 13.3 nojalla sarja suppenee arvoon $\sin x$ kaikilla $x$. $\blacksquare$

---

**13.4 (★★)** Johda funktion $\ln(1+x)$ Taylorin sarja pisteessä $0$ integroimalla geometrinen sarja $\frac{1}{1+t} = 1 - t + t^2 - \cdots$ välillä $0 \ldots x$. Mikä on sen suppenemissäde, ja miksi?

??? tip "Vihje"
    Koska $\int_0^x \frac{1}{1+t}\,dt = \ln(1+x)$, integroi oikean puolen sarja termeittäin. Suppenemissäteelle: missä kompleksitasossa on $\frac{1}{1+t}$:n napa?

??? success "Vastaus"
    Integroidaan geometrinen sarja termeittäin:
    $$\ln(1+x) = \int_0^x \frac{1}{1+t}\,dt = \int_0^x (1 - t + t^2 - t^3 + \cdots)\,dt = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} + \cdots$$
    Suppenemissäde on $1$, koska funktiolla $\frac{1}{1+t}$ on napa kohdassa $t = -1$, etäisyydellä $1$ origosta. (Reunalla $x = 1$ sarja suppenee ehdollisesti antaen $\ln 2$; kohdassa $x = -1$ se hajaantuu — se on juuri navan kohta.) $\blacksquare$

    *(Tämä on sama johto, jonka teit päiväkirjassa yhdistäessäsi geometrisen sarjan, integroinnin ja $\ln 2$:n.)*

---

**13.5 (★★★)** Selitä, miksi funktion $f(x) = \dfrac{1}{1 - x}$ Taylorin sarja pisteessä $a = 0$ suppenee vain välillä $|x| < 1$, vaikka $f$ on täysin sileä esimerkiksi pisteessä $x = 2$. Missä on este?

??? tip "Vihje"
    Kirjoita sarja (geometrinen!), ja mieti, mikä estää suppenemisen. Missä funktio ei ole määritelty?

??? success "Vastaus"
    Taylorin sarja pisteessä $0$ on geometrinen sarja
    $$\frac{1}{1-x} = 1 + x + x^2 + x^3 + \cdots,$$
    joka suppenee täsmälleen kun $|x| < 1$ (luku 9). Este on **napa kohdassa $x = 1$**, jossa funktio $\frac{1}{1-x}$ räjähtää äärettömäksi. Suppenemissäde on etäisyys tähän napaan, eli $1$.

    Vaikka $f$ on sileä ja äärellinen pisteessä $x = 2$, *pisteen $0$ ympärille rakennettu* sarja ei voi ylittää napaa kohdassa $x = 1$ — se "törmää seinään" matkalla. Sarja tuntee vain sen, mitä on suppenemisympyrän sisällä; napa katkaisee sen. (Jos haluaisi tavoittaa pisteen $x = 2$, pitäisi rakentaa Taylorin sarja jonkin *toisen* pisteen ympärille, joka on samalla puolella napaa.) $\blacksquare$

    *(Tämä on suppenemissäteen ydin: sarja pisteessä $a$ näkee vain lähimpään singulariteettiin asti — oli este sitten reaalinen napa kuten tässä, tai kompleksinen kuten $\frac{1}{1+x^2}$:n navat kohdissa $\pm i$.)*

---

*Osa III (Äärettömyys ja analyysi) on nyt valmis: jonoista raja-arvojen, sarjojen, jatkuvuuden, derivaatan ja integraalin kautta Taylorin sarjoihin. Sinulla on koko analyysin selkäranka — se, minkä olit tehnyt intuitiolla, on nyt kalliota. Seuraavaksi voit palata lukuteoriaan (Osa V) tai kompleksianalyysiin (Osa VII), jonka porteilla juuri seisot.*
