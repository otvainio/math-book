# Luku 11: Derivaatta

Olet derivoinut satoja funktioita. Nyt kysymme: *mikä derivaatta oikeasti on?* Vastaus on yksi raja-arvo — sama $\varepsilon$-raja-arvo, jonka opit luvussa 8 — ja siitä seuraa kaikki: tutut derivointisäännöt (jotka nyt **todistetaan**, et vain käytä), sekä väliarvolause, joka on koko differentiaalilaskennan piilotettu moottori.

---

## 11.1 Derivaatan määritelmä

Derivaatta mittaa **hetkellistä muutosnopeutta**. Kuinka nopeasti $f$ muuttuu pisteessä $a$? Otetaan lähipiste $a + h$, lasketaan keskimääräinen muutosnopeus välillä, ja annetaan $h$:n mennä nollaan.

!!! note "Määritelmä"
    Funktio $f$ on **derivoituva** pisteessä $a$, jos raja-arvo
    $$f'(a) = \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$$
    on olemassa. Tätä lukua kutsutaan $f$:n **derivaataksi** pisteessä $a$.

Osamäärä $\frac{f(a+h)-f(a)}{h}$ on **erotusosamäärä** — sekantin (kahden pisteen kautta kulkevan suoran) kulmakerroin. Kun $h \to 0$, sekantti kääntyy **tangentiksi**, ja sen kulmakerroin on $f'(a)$. Siksi derivaatta on "tangentin kulmakerroin" — huomaa, että tämä on nyt *määritelmä ja lause*, ei vain kuva.

**Esimerkki.** Lasketaan $f(x) = x^2$:n derivaatta määritelmästä:
$$f'(a) = \lim_{h\to 0}\frac{(a+h)^2 - a^2}{h} = \lim_{h\to 0}\frac{2ah + h^2}{h} = \lim_{h\to 0}(2a + h) = 2a.$$
Siis $\frac{d}{dx}x^2 = 2x$ — ei potenssisääntönä uskottuna, vaan raja-arvona todistettuna. Samalla tavalla saadaan yleinen $\frac{d}{dx}x^n = nx^{n-1}$.

---

## 11.2 Derivoituvuus ja jatkuvuus

!!! abstract "Lause 11.1"
    Jos $f$ on derivoituva pisteessä $a$, niin $f$ on jatkuva pisteessä $a$.

**Todistus.** Kirjoitetaan erotus tulona ja käytetään raja-arvon laskusääntöjä:
$$\lim_{h\to 0}\big(f(a+h) - f(a)\big) = \lim_{h\to 0}\underbrace{\frac{f(a+h)-f(a)}{h}}_{\to f'(a)} \cdot \underbrace{h}_{\to 0} = f'(a)\cdot 0 = 0.$$
Siis $f(a+h) \to f(a)$, mikä on jatkuvuus pisteessä $a$. $\blacksquare$

**Käänteinen ei päde:** jatkuva funktio ei aina ole derivoituva. Klassinen esimerkki on $f(x) = |x|$ pisteessä $0$: se on jatkuva, mutta sen kuvaajassa on *kärki* — vasemmalta tuleva erotusosamäärä lähestyy $-1$, oikealta $+1$, joten raja-arvoa ei ole. Derivoituvuus on siis aidosti vahvempi ehto kuin jatkuvuus: se vaatii sileyttä, ei vain aukottomuutta. (Muistat päiväkirjasta Weierstrassin hirviön — funktion, joka on kaikkialla jatkuva mutta *ei missään* derivoituva. Se on tämän ilmiön äärimmäinen muoto.)

---

## 11.3 Derivointisäännöt — todistettuina

Nyt todistamme säännöt, joita olet käyttänyt luottaen niiden toimivan.

!!! abstract "Lause 11.2 (tulon sääntö)"
    $(fg)'(a) = f'(a)g(a) + f(a)g'(a)$.

**Todistus.** Kirjoitetaan erotusosamäärä ja lisätään ja vähennetään sama termi (analyysin klassinen kikka):
$$\frac{f(a+h)g(a+h) - f(a)g(a)}{h} = \frac{f(a+h)g(a+h) - f(a+h)g(a) + f(a+h)g(a) - f(a)g(a)}{h}$$
$$= f(a+h)\cdot\frac{g(a+h)-g(a)}{h} + g(a)\cdot\frac{f(a+h)-f(a)}{h}.$$
Kun $h \to 0$: ensimmäisessä termissä $f(a+h) \to f(a)$ (jatkuvuus, Lause 11.1) ja jälkimmäinen osamäärä $\to g'(a)$; toisessa termissä osamäärä $\to f'(a)$. Saadaan $f(a)g'(a) + g(a)f'(a)$. $\blacksquare$

Se "lisää ja vähennä $f(a+h)g(a)$" -temppu on nerokas: se hajottaa yhden muutoksen kahdeksi, joista kumpikin koskee vain yhtä tekijää kerrallaan.

!!! abstract "Lause 11.3 (ketjusääntö)"
    Jos $g$ on derivoituva pisteessä $a$ ja $f$ pisteessä $g(a)$, niin yhdistetyn funktion derivaatta on
    $$(f \circ g)'(a) = f'(g(a)) \cdot g'(a).$$

**Todistus (idea).** Erotusosamäärä yhdistetylle funktiolle voidaan kirjoittaa ketjuna:
$$\frac{f(g(a+h)) - f(g(a))}{h} = \underbrace{\frac{f(g(a+h)) - f(g(a))}{g(a+h)-g(a)}}_{\to\, f'(g(a))} \cdot \underbrace{\frac{g(a+h)-g(a)}{h}}_{\to\, g'(a)}.$$
Sisäfunktion muutos $g(a+h) - g(a)$ toimii "uutena $h$:na" ulkofunktiolle. Kun $h \to 0$, molemmat tekijät suppenevat, ja tulo on $f'(g(a))\,g'(a)$. $\blacksquare$

Tämä on täsmälleen se sääntö, jolla johdit $\sqrt{\sin(e^{x^2+1})}$:n päiväkirjassa — neljä sisäkkäistä funktiota, ketju kerroksittain. Nyt tiedät, *miksi* se toimii: yhdistetyn funktion erotusosamäärä hajoaa tekijöiden osamäärien tuloksi.

Vastaavasti todistetaan **osamäärän sääntö** (harjoitus 11.3). Näillä kolmella — tulo, ketju, osamäärä — johdat minkä tahansa alkeisfunktion derivaatan.

---

## 11.4 Väliarvolause

Nyt differentiaalilaskennan piilotettu moottori. Aloitetaan sen erikoistapauksesta.

!!! abstract "Lause 11.4 (Rollen lause)"
    Olkoon $f$ jatkuva välillä $[a,b]$, derivoituva välillä $(a,b)$, ja $f(a) = f(b)$. Silloin on olemassa piste $c \in (a,b)$, jolle $f'(c) = 0$.

**Todistus.** Ääriarvolauseen (luku 10) nojalla $f$ saavuttaa suurimman ja pienimmän arvonsa välillä $[a,b]$. Jos molemmat saavutetaan päätepisteissä, niin (koska $f(a) = f(b)$) funktio on vakio, ja $f' = 0$ kaikkialla. Muuten ääriarvo saavutetaan jossain sisäpisteessä $c$. Sisäpisteessä olevassa huipussa tai laaksossa tangentti on **vaakasuora**: erotusosamäärä on ei-positiivinen toiselta puolelta ja ei-negatiivinen toiselta, joten raja-arvon on oltava $f'(c) = 0$. $\blacksquare$

!!! abstract "Lause 11.5 (väliarvolause)"
    Olkoon $f$ jatkuva välillä $[a,b]$ ja derivoituva välillä $(a,b)$. Silloin on olemassa $c \in (a,b)$, jolle
    $$f'(c) = \frac{f(b) - f(a)}{b - a}.$$

**Todistus.** Oikea puoli on päätepisteet yhdistävän sekantin kulmakerroin. "Kallistetaan" funktio niin, että sekantti muuttuu vaakasuoraksi: määritellään
$$g(x) = f(x) - \frac{f(b)-f(a)}{b-a}(x - a).$$
Tämä $g$ on jatkuva ja derivoituva, ja suoralla laskulla $g(a) = g(b) = f(a)$. Rollen lause antaa pisteen $c$, jolle $g'(c) = 0$, eli
$$f'(c) - \frac{f(b)-f(a)}{b-a} = 0. \qquad \blacksquare$$

Väliarvolause sanoo: **jossain kohtaa hetkellinen muutosnopeus on täsmälleen keskimääräinen muutosnopeus.** Jos ajat 100 km kahdessa tunnissa (keskinopeus 50 km/h), niin jollain hetkellä mittarisi näytti tasan 50. Se tuntuu ilmeiseltä — mutta kuten väliarvolause luvussa 10, se on totta vain täydellisyyden ansiosta (Rolle nojaa ääriarvolauseeseen, joka nojaa täydellisyyteen).

---

## 11.5 Mihin väliarvolausetta tarvitaan

Se on silta derivaatan (paikallinen tieto) ja funktion käytöksen (globaali tieto) välillä. Kaikki tuttu "derivaatta kertoo kulun" seuraa siitä.

!!! abstract "Lause 11.6"
    Jos $f'(x) > 0$ koko välillä, niin $f$ on **aidosti kasvava** siellä. Jos $f'(x) = 0$ koko välillä, niin $f$ on **vakio**.

**Todistus.** Otetaan $x_1 < x_2$ välillä. Väliarvolause antaa $c$:n, jolle
$$f(x_2) - f(x_1) = f'(c)(x_2 - x_1).$$
Jos $f'(c) > 0$, oikea puoli on positiivinen, joten $f(x_2) > f(x_1)$ — kasvava. Jos $f'(c) = 0$, oikea puoli on nolla, joten $f(x_2) = f(x_1)$ — vakio. $\blacksquare$

Toinen puoli on "vakion derivaatta on nolla" käännettynä: **jos derivaatta on nolla kaikkialla, funktio on vakio.** Tämä on hienovaraisempi kuin miltä näyttää — se on syy, miksi kahdella funktiolla, joilla on sama derivaatta, on vain vakioero. Ja *juuri tätä* tarvitaan seuraavassa luvussa, kun integraali ja derivaatta sidotaan yhteen. Ääriarvojen etsintä (derivaatan nollakohdat) nojaa myös tähän — se on optimoinnin perusta, jonka ääriarvolause (luku 10) takasi olevan mielekäs.

---

## 11.6 Yhteenveto

- **Derivaatta** $f'(a) = \lim_{h\to 0}\frac{f(a+h)-f(a)}{h}$ — erotusosamäärän raja-arvo, tangentin kulmakerroin.
- Derivoituvuus $\Rightarrow$ jatkuvuus (mutta ei kääntäen: $|x|$).
- **Tulo-, ketju- ja osamääräsäännöt** todistetaan erotusosamäärästä — niitä ei tarvitse uskoa.
- **Väliarvolause:** hetkellinen muutos = keskimääräinen muutos jossain pisteessä. Rolle + täydellisyys.
- Väliarvolauseesta seuraa "derivaatta kertoo kulun": $f' > 0 \Rightarrow$ kasvava, $f' = 0 \Rightarrow$ vakio.

---

## Harjoitukset

**11.1 (★)** Laske määritelmästä (erotusosamäärän raja-arvona) funktion $f(x) = x^2 + 3x$ derivaatta pisteessä $x = a$.

??? success "Vastaus"
    $$f'(a) = \lim_{h\to 0}\frac{(a+h)^2 + 3(a+h) - (a^2 + 3a)}{h} = \lim_{h\to 0}\frac{2ah + h^2 + 3h}{h} = \lim_{h\to 0}(2a + h + 3) = 2a + 3.$$
    Siis $f'(x) = 2x + 3$. $\blacksquare$

---

**11.2 (★)** Osoita, että $f(x) = |x|$ ei ole derivoituva pisteessä $0$.

??? success "Vastaus"
    Erotusosamäärä pisteessä $0$ on $\frac{|0+h| - |0|}{h} = \frac{|h|}{h}$. Kun $h > 0$, tämä on $+1$; kun $h < 0$, se on $-1$. Vasemman- ja oikeanpuoleiset raja-arvot ovat eri ($-1 \neq +1$), joten raja-arvoa ei ole, eikä $f$ ole derivoituva pisteessä $0$. $\blacksquare$

---

**11.3 (★★)** Todista osamäärän sääntö: $\left(\dfrac{f}{g}\right)'(a) = \dfrac{f'(a)g(a) - f(a)g'(a)}{g(a)^2}$ (kun $g(a) \neq 0$).

??? tip "Vihje"
    Kirjoita erotusosamäärä $\frac{1}{h}\left(\frac{f(a+h)}{g(a+h)} - \frac{f(a)}{g(a)}\right)$, tuo yhteinen nimittäjä, ja käytä samaa "lisää ja vähennä" -temppua kuin tulon säännössä.

??? success "Vastaus"
    Erotusosamäärä yhteisellä nimittäjällä:
    $$\frac{1}{h}\cdot\frac{f(a+h)g(a) - f(a)g(a+h)}{g(a+h)g(a)}.$$
    Osoittajaan lisätään ja vähennetään $f(a)g(a)$:
    $$f(a+h)g(a) - f(a)g(a+h) = g(a)\big(f(a+h)-f(a)\big) - f(a)\big(g(a+h)-g(a)\big).$$
    Jaetaan $h$:lla ja otetaan raja-arvo $h \to 0$ (käyttäen $g(a+h) \to g(a)$ jatkuvuudella):
    $$\frac{g(a)f'(a) - f(a)g'(a)}{g(a)g(a)} = \frac{f'(a)g(a) - f(a)g'(a)}{g(a)^2}. \qquad \blacksquare$$

---

**11.4 (★★)** Käytä väliarvolausetta osoittaaksesi, että $|\sin x - \sin y| \leq |x - y|$ kaikilla $x, y$.

??? tip "Vihje"
    Sovella väliarvolausetta funktioon $\sin$ välillä $[y, x]$. Muista, että $|\cos| \leq 1$.

??? success "Vastaus"
    Oletetaan $x \neq y$ (muuten väite on triviaali). Väliarvolauseen nojalla on $c$ lukujen $x$ ja $y$ välissä, jolle
    $$\sin x - \sin y = \cos(c)\,(x - y).$$
    Otetaan itseisarvot ja käytetään $|\cos c| \leq 1$:
    $$|\sin x - \sin y| = |\cos c|\,|x - y| \leq |x - y|. \qquad \blacksquare$$

    *(Tämä sanoo, että sini ei koskaan "kiihdytä" enempää kuin identiteettifunktio — sen kulmakerroin on aina korkeintaan $1$. Tällaisia funktioita kutsutaan Lipschitz-jatkuviksi.)*

---

**11.5 (★★★)** Todista, että yhtälöllä $x^3 - 3x + 1 = 0$ on täsmälleen kolme reaalijuurta. *(Vihje: yhdistä derivaatan merkki, ääriarvot ja väliarvolause.)*

??? tip "Vihje"
    Laske $f'(x)$ ja löydä funktion ääriarvokohdat. Tutki funktion arvoja niissä ja äärettömyyksissä, ja käytä väliarvolausetta kolmen etumerkinvaihdon löytämiseen.

??? success "Vastaus"
    Olkoon $f(x) = x^3 - 3x + 1$. Derivaatta $f'(x) = 3x^2 - 3 = 3(x-1)(x+1)$ on nolla pisteissä $x = -1$ ja $x = 1$. Merkkikaaviosta: $f$ kasvaa välillä $(-\infty, -1)$, vähenee välillä $(-1, 1)$, ja kasvaa välillä $(1, \infty)$. Lasketaan ääriarvot:
    $$f(-1) = -1 + 3 + 1 = 3 > 0 \quad(\text{paikallinen maksimi}),$$
    $$f(1) = 1 - 3 + 1 = -1 < 0 \quad(\text{paikallinen minimi}).$$
    Nyt:
    - $f(-\infty) = -\infty$ ja $f(-1) = 3 > 0$: väliarvolause antaa juuren välille $(-\infty, -1)$.
    - $f(-1) = 3 > 0$ ja $f(1) = -1 < 0$: juuri välille $(-1, 1)$.
    - $f(1) = -1 < 0$ ja $f(+\infty) = +\infty$: juuri välille $(1, \infty)$.

    Kolme etumerkinvaihtoa antaa kolme juurta, ja koska aste on $3$, niitä on enintään kolme (luku 16). Siis täsmälleen kolme reaalijuurta. $\blacksquare$

---

*Seuraava luku: Integraali — pinta-alan täsmällinen määritelmä, ja analyysin peruslause, joka sitoo integraalin ja derivaatan yhteen.*
