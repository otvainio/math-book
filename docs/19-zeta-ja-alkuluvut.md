# Luku 19: Zeta-funktio ja alkulukujen jakauma

Tämä luku on koko kirjan — ja koko kesäsi — huipennus. Se on paikka, jossa **lukuteoria ja analyysi kohtaavat**: jossa alkuluvut, jotka näyttävät hajautuvan kaoottisesti, paljastuvat noudattavan syvää lakia, ja jossa sama $\zeta$-funktio, jonka arvon $\zeta(2) = \frac{\pi^2}{6}$ laskit päiväkirjassa, osoittautuu alkulukujen salaisuuden avaimeksi. Matka päättyy matematiikan suurimman ratkaisemattoman ongelman porteille — jonka reunalla itse asiassa jo kävelit.

---

## 19.1 Kuinka alkuluvut jakautuvat

Alkuluvut alkavat tiheästi ja harvenevat: $2, 3, 5, 7, 11, 13, \ldots$ mutta suurten lukujen seassa niitä on yhä vähemmän. Merkitään

$$\pi(x) = \text{alkulukujen määrä, jotka ovat} \leq x.$$

(Tämä $\pi$ ei liity ympyrävakioon — sama kirjain, eri merkitys.) Esimerkiksi $\pi(10) = 4$ (luvut $2,3,5,7$) ja $\pi(100) = 25$. Kysymys, joka kiehtoi matemaatikkoja vuosisatoja: **onko alkulukujen harvenemisessa laki?**

Gauss arvasi 15-vuotiaana (sinun ikäisenäsi) tutkimalla taulukoita, että alkulukujen "tiheys" luvun $x$ lähellä on noin $\frac{1}{\ln x}$. Tämä johtaa arvioon $\pi(x) \approx \frac{x}{\ln x}$, ja se osoittautui todeksi:

!!! abstract "Alkulukulause (Hadamard & de la Vallée Poussin, 1896)"
    $$\pi(x) \sim \frac{x}{\ln x}, \qquad \text{eli} \qquad \lim_{x\to\infty}\frac{\pi(x)}{x/\ln x} = 1.$$

Alkuluvut, jotka näyttävät ilmestyvän satunnaisesti, noudattavat tarkkaa keskimääräistä lakia. Todennäköisyys, että luku $n$:n lähellä on alkuluku, on suunnilleen $\frac{1}{\ln n}$ — mitä suurempi luku, sitä harvinaisempi alkuluku, mutta täsmälleen ennustettavalla nopeudella. Alkulukulauseen todistus on syvä ja käyttää — yllättäen — **kompleksianalyysiä** ja $\zeta$-funktiota. Miksi? Sen paljastaa Eulerin löytö.

---

## 19.2 Alkulukujen käänteislukujen summa

Ensin osoitetaan, että alkulukuja on "tarpeeksi tiheässä" — tavalla, joka on vahvempi kuin pelkkä äärettömyys.

!!! abstract "Lause 19.1 (Euler, 1737)"
    Alkulukujen käänteislukujen summa hajaantuu:
    $$\sum_{p \text{ alkuluku}} \frac{1}{p} = \frac12 + \frac13 + \frac15 + \frac17 + \frac{1}{11} + \cdots = \infty.$$

Vertaa tätä lukuun 9: harmoninen sarja $\sum \frac1n$ hajaantuu, mutta neliöiden sarja $\sum \frac{1}{n^2}$ suppenee. Alkuluvut asettuvat *tähän väliin* — niitä on niin paljon, että niiden käänteislukujen summa hajaantuu (toisin kuin neliöillä), mutta vain hädin tuskin (summa kasvaa kuin $\ln\ln x$, uskomattoman hitaasti). Tämä on paljon vahvempi tulos kuin Eukleideen "äärettömän monta" — se mittaa *kuinka* monta.

Todistuksen idea vie suoraan seuraavaan lauseeseen, joka on koko luvun sydän.

---

## 19.3 Eulerin tulo: silta alkulukuihin

Nyt paljastuu, miksi $\zeta$-funktio — puhtaan analyyttinen olio — tietää kaiken alkuluvuista. Muistetaan

$$\zeta(s) = \sum_{n=1}^{\infty}\frac{1}{n^s} = 1 + \frac{1}{2^s} + \frac{1}{3^s} + \cdots \qquad (s > 1).$$

!!! abstract "Lause 19.2 (Eulerin tulo, 1737)"
    Kun $s > 1$,
    $$\zeta(s) = \prod_{p \text{ alkuluku}} \frac{1}{1 - p^{-s}}.$$
    **Summa yli kaikkien lukujen $=$ tulo yli kaikkien alkulukujen.**

**Todistus.** Kirjoitetaan jokainen tekijä geometrisena sarjana (luku 9), koska $p^{-s} < 1$:
$$\frac{1}{1 - p^{-s}} = 1 + \frac{1}{p^s} + \frac{1}{p^{2s}} + \frac{1}{p^{3s}} + \cdots$$
Kerrotaan nämä sarjat yhteen kaikkien alkulukujen yli. Tulon jokainen termi syntyy valitsemalla kustakin tekijästä yksi pala $p^{-a_p s}$, ja niiden tulo on
$$\frac{1}{(p_1^{a_1} p_2^{a_2} \cdots)^s} = \frac{1}{n^s}, \qquad \text{missä } n = p_1^{a_1}p_2^{a_2}\cdots.$$
**Aritmetiikan peruslauseen (luku 17) nojalla** jokainen luku $n$ syntyy täsmälleen yhdellä alkulukupotenssien valinnalla — joten jokainen $\frac{1}{n^s}$ esiintyy tulossa täsmälleen kerran. Siis tulo on $\sum_n \frac{1}{n^s} = \zeta(s)$. $\blacksquare$

!!! quote "Miksi tämä on hämmästyttävää"
    Vasemmalla puolella on summa **kaikista** kokonaisluvuista. Oikealla tulo **pelkistä alkuluvuista**. Se, että nämä ovat yhtä suuret, on aritmetiikan peruslause pukeutuneena analyysiin — ja se on ovi, jonka kautta $\zeta$-funktio "näkee" alkuluvut.

    Tästä seuraa alkulukujen äärettömyys **uudella tavalla**: jos alkulukuja olisi vain äärellinen määrä, oikea puoli olisi äärellinen tulo, siis äärellinen luku. Mutta kun $s \to 1$, vasen puoli $\zeta(s) \to \infty$ (harmoninen sarja hajaantuu). Ristiriita — joten alkulukuja on äärettömästi. Sama argumentti tarkennettuna antaa Lauseen 19.1 ($\sum \frac1p = \infty$). Analyysi todistaa lukuteorian väitteen.

Ja huomaa, mitä tämä tekee sinun työllesi: sijoittamalla $s = 2$ saat
$$\frac{\pi^2}{6} = \zeta(2) = \prod_p \frac{1}{1 - p^{-2}} = \prod_p \frac{p^2}{p^2 - 1}.$$
Sinun Basel-tuloksesi **on** tulo alkulukujen yli. $\pi$ ja alkuluvut, samassa yhtälössä.

---

## 19.4 Zeta koko kompleksitasossa

Tähän asti $\zeta(s)$ oli määritelty vain kun $s > 1$ (muuten sarja hajaantuu). Mutta Riemann teki 1859 rohkean askeleen: hän **jatkoi** funktion koko kompleksitasoon **analyyttisen jatkon** avulla (luku 25). Tuloksena $\zeta(s)$ saa arvon melkein jokaisessa kompleksipisteessä $s$ — ja nämä arvot kätkevät alkulukujen salaisuudet.

Tämän jatketun funktion arvoja sinä jo lasket päiväkirjassa:
$$\zeta(2) = \frac{\pi^2}{6}, \qquad \zeta(-1) = -\frac{1}{12}, \qquad \zeta\!\left(\tfrac12\right) \approx -1{,}4603.$$

Arvo $\zeta(-1) = -\frac{1}{12}$ — "$1 + 2 + 3 + \cdots$" — on juuri analyyttisen jatkon tuote: se ei ole hajaantuvan sarjan summa, vaan jatketun funktion arvo kohdassa, jossa alkuperäinen sarja ei enää toimi. Sinä johdit sen eta-funktion ja Grandin sarjan avulla; se on sama luku.

Jatkettu funktio saa arvon nolla tietyissä pisteissä — sen **nollakohdissa** — ja juuri ne hallitsevat alkulukuja.

- **Triviaalit nollakohdat:** $s = -2, -4, -6, \ldots$ (parilliset negatiiviset luvut).
- **Epätriviaalit nollakohdat:** kaikki muut, ja ne sijaitsevat "kriittisessä nauhassa" $0 < \operatorname{Re}(s) < 1$.

---

## 19.5 Riemannin hypoteesi

Tässä on koko matkasi päätepiste — matematiikan kuuluisin ratkaisematon ongelma.

!!! abstract "Riemannin hypoteesi (1859, avoin)"
    Kaikki $\zeta$-funktion epätriviaalit nollakohdat sijaitsevat suoralla
    $$\operatorname{Re}(s) = \frac{1}{2}.$$

Miksi tämä on tärkeä? Koska **$\zeta$-funktion nollakohdat hallitsevat alkulukujen jakaumaa.** Alkulukulause (§19.1) antaa alkulukujen keskimääräisen tiheyden, mutta todelliset alkuluvut poikkeavat tästä keskiarvosta — ja poikkeaman suuruuden määräävät täsmälleen nollakohtien paikat. Riemannin hypoteesi sanoo, että poikkeama on **niin pieni kuin se voi olla** — että alkuluvut ovat "niin säännöllisiä kuin satunnaiselta näyttävä jono voi olla". Jos hypoteesi on tosi, tiedämme alkulukujen jakaumasta täsmällisimmän mahdollisen tuloksen.

Hypoteesi on ollut avoin **yli 160 vuotta.** Sen ratkaisusta on luvattu miljoona dollaria (yksi Clay-instituutin vuosituhannen ongelmista). Ensimmäiset kymmenet triljoonat nollakohdat on tarkistettu tietokoneella — kaikki suoralla $\operatorname{Re}(s) = \frac12$ — mutta yksikään ei ole todistus.

!!! quote "Sinä kävelit kriittisellä suoralla"
    Muistatko päiväkirjasarjasi
    $$1 - \frac{1}{\sqrt2} + \frac{1}{\sqrt3} - \cdots = (1 - \sqrt2)\,\zeta\!\left(\tfrac12\right)?$$
    Se luku $s = \frac12$ **on kriittinen suora.** Sijoittaessasi $\zeta$:aan arvon $\frac12$ olit kirjaimellisesti sillä suoralla, jonka ympärille koko Riemannin hypoteesi rakentuu — sillä suoralla, jolla kaikkien epätriviaalien nollakohtien uskotaan makaavan. Et tiennyt sitä silloin, mutta laskusi kosketti matematiikan syvintä avointa arvoitusta.

---

## 19.6 Yhteenveto — ja matkan pää

- **Alkulukulause:** $\pi(x) \sim \dfrac{x}{\ln x}$ — alkuluvut harvenevat täsmällisellä lailla.
- $\sum \frac1p = \infty$ — alkulukuja on "tarpeeksi", mutta hädin tuskin.
- **Eulerin tulo:** $\zeta(s) = \prod_p \frac{1}{1-p^{-s}}$ — summa kaikista luvuista = tulo alkuluvuista, aritmetiikan peruslauseen nojalla. Sinun $\zeta(2)=\frac{\pi^2}{6}$ on tulo alkulukujen yli.
- **Analyyttinen jatko** antaa $\zeta$:lle arvot koko tasossa: $\zeta(-1) = -\frac{1}{12}$, $\zeta(\frac12) \approx -1{,}46$.
- **Riemannin hypoteesi:** epätriviaalit nollakohdat suoralla $\operatorname{Re}(s) = \frac12$ — matematiikan suurin avoin ongelma, jota sinä koskettelit laskuissasi.

!!! success "Loppusanat"
    Tässä kohtaavat kaikki kirjan langat: **luvut** (Osa II), joista alkuluvut ovat atomit; **äärettömyys ja analyysi** (Osa III), jonka sarjat ja raja-arvot antoivat $\zeta$-funktiolle merkityksen; **algebra** (Osa IV), jonka aritmetiikan peruslause teki Eulerin tulon mahdolliseksi; ja **lukuteoria** (Osa V), joka kysyi alkulukujen salaisuuden.

    Ja niiden keskellä on funktio, jonka arvon $\frac{\pi^2}{6}$ sinä laskit omin käsin ennen kuin tiesit, että se on avain koko kokonaislukujen rakenteeseen. Matematiikka on yhtä kudosta — ja sinä olet kutonut sitä koko kesän, aavistamatta kuinka syvälle langat ulottuvat.

---

## Harjoitukset

**19.1 (★)** Laske $\pi(20)$ (alkulukujen määrä $\leq 20$) ja vertaa arvioon $\dfrac{20}{\ln 20}$.

??? success "Vastaus"
    Alkuluvut $\leq 20$: $2, 3, 5, 7, 11, 13, 17, 19$ — yhteensä $\pi(20) = 8$.
    Arvio: $\dfrac{20}{\ln 20} = \dfrac{20}{2{,}996} \approx 6{,}7$. Arvio on oikeaa suuruusluokkaa mutta vielä epätarkka — alkulukulause on *asymptoottinen* ja tarkentuu suurilla $x$. $\blacksquare$

---

**19.2 (★★)** Kirjoita Eulerin tulon ensimmäiset kolme tekijää ($p = 2, 3, 5$) tapaukselle $s = 2$, ja tarkista, että niiden tulo lähestyy arvoa $\zeta(2) = \frac{\pi^2}{6} \approx 1{,}6449$.

??? tip "Vihje"
    Tekijä on $\frac{1}{1 - p^{-2}} = \frac{p^2}{p^2 - 1}$. Laske $p = 2, 3, 5$ ja kerro.

??? success "Vastaus"
    Tekijät $\frac{p^2}{p^2-1}$:
    $$p=2:\ \frac{4}{3} \approx 1{,}333, \qquad p=3:\ \frac{9}{8} = 1{,}125, \qquad p=5:\ \frac{25}{24} \approx 1{,}042.$$
    Tulo: $1{,}333 \cdot 1{,}125 \cdot 1{,}042 \approx 1{,}563$. Se lähestyy arvoa $1{,}6449$ alhaaltapäin; lisää tekijöitä (alkulukuja $7, 11, \ldots$) tuo tuloksen yhä lähemmäs. $\blacksquare$

---

**19.3 (★★)** Osoita Eulerin tulon avulla, että jos alkulukuja olisi vain äärellinen määrä, niin $\zeta(1) = \sum \frac1n$ olisi äärellinen — ja päättele ristiriita.

??? tip "Vihje"
    Jos alkulukuja on äärellisesti, Eulerin tulo on äärellinen tulo äärellisiä lukuja, siis äärellinen. Mutta mitä tiedät harmonisesta sarjasta $\zeta(1)$?

??? success "Vastaus"
    Jos alkulukuja olisi vain äärellinen määrä $p_1, \ldots, p_k$, niin (kun $s \to 1$) Eulerin tulo olisi äärellinen tulo
    $$\prod_{i=1}^{k}\frac{1}{1 - p_i^{-1}},$$
    joka on äärellinen luku. Mutta Eulerin tulon mukaan tämä on yhtä kuin $\zeta(1) = \sum_{n}\frac1n$, joka on **harmoninen sarja** — ja se **hajaantuu** (luku 9). Äärellinen luku ei voi olla yhtä kuin ääretön. Ristiriita, joten alkulukuja on äärettömästi. $\blacksquare$

    *(Tämä on Eulerin analyyttinen todistus Eukleideen lauseelle — täysin eri kuin luvun 17 alkeellinen versio, ja se paljastaa syvemmän totuuden: alkulukuja on niin monta, että ne "aiheuttavat" harmonisen sarjan hajaantumisen.)*

---

**19.4 (★★★)** Riemannin hypoteesi voidaan ilmaista myös näin: jokaiselle $\varepsilon > 0$ pätee $|\pi(x) - \operatorname{Li}(x)| < C x^{1/2 + \varepsilon}$ jollakin vakiolla, missä $\operatorname{Li}(x) = \int_2^x \frac{dt}{\ln t}$. Mitä eksponentti $\frac12$ tässä muodossa liittyy §19.5:n suoraan $\operatorname{Re}(s) = \frac12$? Pohdi sanallisesti (ei laskua).

??? success "Vastaus"
    Eksponentti $\frac12$ virheen rajassa on **suora seuraus** siitä, että nollakohdat ovat suoralla $\operatorname{Re}(s) = \frac12$. Alkulukujen jakauman virhetermi (poikkeama sileästä arviosta $\operatorname{Li}(x)$) rakentuu summana $\zeta$:n nollakohtien yli, ja kunkin nollakohdan $s = \sigma + it$ vaikutus kasvaa kuin $x^{\sigma}$. Jos kaikki nollakohdat ovat suoralla $\sigma = \frac12$, jokainen vaikutus on korkeintaan luokkaa $x^{1/2}$ — ja virhe pysyy niin pienenä kuin mahdollista.

    Toisin sanoen: **nollakohtien reaaliosa $= $ virheen eksponentti.** Riemannin hypoteesi ($\sigma = \frac12$ kaikille) on täsmälleen väite, että alkuluvut ovat mahdollisimman säännöllisesti jakautuneet. Jos jokin nollakohta olisi suoran ulkopuolella, esim. $\sigma = 0{,}7$, virhe kasvaisi kuin $x^{0{,}7}$ — alkuluvut olisivat "epäsäännöllisempiä". Suora ja eksponentti ovat sama asia kahdesta suunnasta. $\blacksquare$

---

*Osa V (Lukuteoria) on nyt valmis. Se kokosi yhteen algebrasi, analyysisi ja koko zeta-työsi — ja vei sinut matematiikan syvimmän avoimen ongelman äärelle.*
