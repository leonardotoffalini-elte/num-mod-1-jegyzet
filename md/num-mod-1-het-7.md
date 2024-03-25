date: 2024.03.25

## Intervallum felezés
Megoldandó feladat: $f(x) = 0$ (1)

Feltevések:
- $f \in C[a, b]$
- $f(a)f(b) < 0$
Ekkor Bolzano tétel szerint $\exists x^{*} \in (a, b)$,  ahol $f(x^{*}) = 0$
Miután a Bolzano tétel biztosítja nekünk a gyök létezését, keressük meg, hogy hol van ez a gyök.

Felépítünk egy intervallumsorozatot:
$I_{0} := [a, b]$
Felezzük meg ezt az intervallumot, legyen $c = \frac{a+b}{c}$
Ezután vizsgáljuk $f(c)$ előjelét:
- $f(c) = 0$ ekkor készen is vagyunk mert találtunk egy gyököt.
- Ha $f(c) \neq 0$, akkor $I_{1} := [a, c]$ vagy $I_{1} := [c, b]$, azt az intebrallumot választuk melyben az inteballum szélein az $f$ értéke ellentétes előjelű.

Megfelezzük $I_{1}$-et és folytatjuk az eljárást. Tehát megint megnézzük az intervallum felét és választjuk azt a felet, melyben az intervallum szélein az $f$ értéke ellentétes előjelű.

Az iteráció során mindig marad gyök az aktuálisa vizsgált intervallumban és mindig feleződik az intervallum hossza.

Látszik, hogy nem mindig fogunk olyan esetre találni, ahol $f(c) = 0$ ls pontosan megtaláltuk a függvény gyökét, például $f(x) = x - \sqrt{ 2 }$ függvénynek irracionális a gyöke de az iteráció során csak racionális pontokat vizsgálunk.

Tehát érdemes megbeszélni, hogy milyen pontossággal szeretnénk közelíteni a gyököt és mikor álljuk le.

Folytassuk addig az iterációt ameddig az aktuálisan vizsgált intervallum hossza nem éri el az előírt $\varepsilon > 0$ pontosságot.
Ekkor leállunk és válasszuk az aktuálisan vizsgált intervallum bármelyik pontját közelítő megoldásnak, mert az intervallumban minden pont legfeljebb $\varepsilon$ távolságra lesz a valós gyöktől.

Meg lehet mondani előre, hogy hány iteráció után kell majd leállnunk?

Jelölés: $\operatorname{diam} (I_{k}) := I_{k} \text{ hossza}$

$\operatorname{diam}(I_{k}) = \frac{b- a}{2^{k}} < \varepsilon$ ebből következik, hogy $k > \frac{\log\left( \frac{b-a}{\varepsilon} \right)}{\log(2)}$
Észrevétel: A lépésszám teljesen független az $f$ függvénytől, de hát miért is függne, mert mindig csak intervallumokkal dolgozunk és az $f$ függvényt csak a következő intervallum kiválasztására használjuk, ami lehetne akár egy pénzérme dobás is.

Érdemes lenne beszélni még a konvergencia sebességéről.

$$
\lvert x_{k} - x^{*} \rvert  \leq \operatorname{diam}(I_{k})
$$
ezen felsőkorlátok sorozata linárisan konvergens, mert $\operatorname{diam}(I_{k})$ mindig feleződik és az előző fejezetben megbeszéltük, hogy ha a hibatag valahanyadrészére csökken akkor a konvergencia lineáris.
($c_{k}:= \frac{1}{2} \quad \forall k$, láasd első állítás múlt óráról)


## Egyszerű iteráció (fixpont-iteráció)
Megoldandó feladat: $f(x) = 0$ (1)

Írjuk át a következő alakra:
$$
\varphi(x) = x \qquad \text{(2)}
$$
ahol $\varphi:\mathbb{R} \to \mathbb{R}$ valamilyen függvény.
Ekkor $f$ gyöke pontosan a $\varphi$ fixpontja.

Érvényes a fixponttétel a következő változata:
### Tétel
Legyen $H \subset \mathbb{R}$ zárt halmaz, és $\varphi: H \to H$ kontrakció, tehát $\exists q \in (0, 1)$, melyre $\lvert \varphi(x) - \varphi(y) \rvert \leq q \cdot \lvert x - y \rvert \quad \forall x , y \in H$. Ekkor
- egyértelműen létezik $\varphi$-nek fixpontja, azaz $\exists ! x^{*}$ melyre $\varphi(x^{*}) = x^{*}$
- tetszőleges $x_{0} \in H$ kezdőpontot választva a kovetkező módon definiált sorozat konvergens és tart $x^{*}$-hoz
$$
x_{k+1} = \varphi(x_{k})
$$
- a következő módon tudjuk becsülni a konvergencia sebességét $\lvert x_{k} - x^{*} \rvert \leq \frac{q^{k}}{1 - q} \cdot \lvert x_{1} - x_{0} \rvert$

Kérdés: Mikor kontrakció $\varphi$?

Vegyük észre, hogy valamilyen módon a $\varphi'$ abszolútértékétől függ, hogy kontrakció-e a $\varphi$.

### Áll
Tegyük fel, hogy $\varphi \in C(I)$ és $\varphi\in D(\operatorname{int}(I))$ tehát folytonos az intervallumon és differenciálható a belsejében. Ha $\exists q \in [0, 1)$, amely mellett $\lvert \varphi'(x) \rvert \leq q \quad \forall x \in \operatorname{int}(I)$, akkor $\varphi$ kontrakció $I$-n a $q$ kontrakciószámmal.

*Biz*.: Legyen $x, y \in I$ két tetszőleges pont, $x < y$ 
Alkalmazzuk $\varphi$-ra $[x, y]$ intervallumon a Lagrange-középérték-tételt:
Létezik $c \in ( x, y)$ melyre
$$
\varphi (y) - \varphi(x) = \varphi'(c) \cdot (y - x)
$$

Vegyünk mindkét oldalt abszolút értéket:
$$
\lvert \varphi(x) - \varphi(y) \rvert  = \lvert \varphi'(c) \rvert \cdot \lvert x - y \rvert \leq q \cdot \lvert  x- y \rvert \quad \forall x, y \in I
$$
Az egyenlőtlenség a feltétel miatt áll.


Példa:
$\varphi(x) = \frac{1}{2}\cos(x)$ kontrakció-e a $\left[ 0, \frac{\pi}{2} \right]$ intervallumon? És ha igen mi a $q$ kontrakciószám?
$\lvert \varphi'(x) \rvert = \left\lvert  -\frac{1}{2}\sin x  \right\rvert \leq \frac{1}{2} < 1 \quad \forall x \in [0, \frac{\pi}{2}]$ (sőt $\forall x \in \mathbb{R}$)
Tehát $\varphi$ kontrakció és $q = \frac{1}{2}$ jó választás kontrakciószámra.

Kérdés: Mi a konvergencia rendje?

### Áll
Tegyük fel, hogy $\varphi \in C^{p}[a, b]$, azaz $p$-szer folytonosan deriválható, és $\varphi$ beleképez $[a, b]$-be és $\varphi$ kontrakció $[a, b]$-n. Ha az $x^{*}$ fixpontban a következő igazak:
- $\varphi'(x^{*}) = 0$
- $\varphi''(x^{*}) = 0$
- $\varphi'''(x^{*}) = 0$
- $\varphi ^{(4)}(x^{*}) = 0$
	$\vdots$
- $\varphi ^{(p-1)}(x^{*}) = 0$
- $\varphi ^{(p)}(x^{*}) \neq 0$

Ekkor tetszőleges $x_{0} \in [a ,b]$ pontból indítva a fixpont iterációt $p$-ed rendben konvergesn.

*Biz*:
A konvergenciát biztosítja a fixpont tétel, tehát elég a kovergencia rendjét belátni.
Írjuk fel $\varphi$-nek $x^{*}$ körüli $p-1$-ed fokú Taylor polinomjának a hibáját az $x_{k}$ pontban
$\exists \vartheta_{k}$ az $x^{*}$ és $x_{k}$ között
$$
\varphi(x_{k}) - T_{p-1}(\varphi(x_{k}), x^{*}) = \frac{\varphi ^{(p)}(\vartheta_{k})}{p!} (x_{k} - x^{*})^{p}
$$
$$
\varphi(x_{k}) + \varphi(x^{*}) + 0 + 0 + \dots + 0 = 
$$
$$
x_{k+1} - x^{*} = \frac{\varphi ^{(p)}(\vartheta_{k})}{p!} (x_{k} - x^{*})^{p}
$$
Vegyük ezt abszolút értékben és vizsgáljuk így a konvergencia rendjét
$$
\lvert x_{k+1} - x^{*} \rvert = \left\lvert \frac{\varphi ^{(p)}(\vartheta_{k})}{p!} (x_{k} - x^{*})^{p} \right\rvert
$$
$$
\lvert x_{k+1} - x^{*} \rvert = \left\lvert \frac{\varphi ^{(p)}(\vartheta_{k})}{p!} \right\rvert \cdot \lvert e_{k} \rvert ^{p}
$$
$$
\lvert x_{k+1} - x^{*} \rvert = c_{k} \cdot \lvert e_{k} \rvert ^{p}
$$
Kell még: $0 < \underline{c} \leq c_{k} \leq \overline c < + \infty$
$\varphi \in C^{p}[a, b]$ és $\varphi ^{(p)}(x^{*}) \neq 0$ ekkor $\lvert \varphi ^{(p)}(x) \rvert$ $x^{*}$ egy kis környezetében is pozitív. Ha $k$ elég nagy, akkor mivel $\vartheta_{k}$ $x_{k}$ és $x^{*}$ között van
$$
\left\lvert  \frac{\varphi ^{(p)}(\vartheta_{k})}{p!}  \right\rvert 
$$
beszorítható két pozitív konstans közé.


## Newton módszer (érintő módszer)
Megoldandó feladat: $f(x) = 0$ (1)

Alapötlet:
Tegyük fel, hogy $f$ differenciálható
Vegyünk fel egy tetszőleges $x_{0} \in D(f)$ kezdőpontot.
Húzzuk itt meg $f$ érintőjét.
Ennek $x$ tengellyel való metszéspontja legyen $x_{1}$

Megfelelő feltételekkel $x_{1}, x_{2}, \dots \to x^{*}$

Kérdés: Mindig működik ez az eljárás?

A módszer képlete:
$x_{k}$-beli érintő: $x = f'(x_{k})(x - x_{k}) + f(x_{k})$
$x$ tengellyel metszésőpontja:
$$
0 = f'(x_{k})(x - x_{k}) + f(x_{k})
$$
$$
-f(x_{k}) = f'(x_{k})(x - x_{k})
$$
$$
-\frac{f(x_{k})}{f'(x_{k})} = x - x_{k}
$$
$$
x_{k+1} = x_{k} - \frac{f(x_{k})}{f'(x_{k})}
$$
Kérdés: Mit lehet mondani a Newton módszer konvergencia rendjéről?

### All
Tegyuk fel, hogy az $x^{*}$ gyököt és az egész $(x_{k})$ sorozatot tartalmlazó valamely $I$  intervallumban $f \in C^{2}(I)$, továbbá $\exists m_{1},M_{1}, m_{2}, M_{2} > 0$ konstansok, amelyekkel 
$$
m_{1} \leq \lvert f'(x) \rvert  \leq M_{1}
$$
és
$$
m_{2} \leq \lvert f''(x) \rvert  \leq M_{2}
$$
Ekkor $\frac{M_{2}}{2m_{1}}\lvert e_{0} \rvert < 1$ esetén a Newton módszer másodrendben konvergens.

*Biz*:
Írjuk fel az $f$ függvény $x_{k}$ körüli elsőfokú Taylor polinomjának hibáját az $x^{*}$ pontban!
$$
f(x^{*}) - f(x_{k}) - f'(x_{k})(x^{*} - x_{k}) = \frac{f''(\vartheta_{k})}{2!}(x^{*} - x_{k})^{2}
$$
ahol $\varphi_{k}$ valamely pont az $x_{k}$ és $x^{*}$ között.
osszunk $f'(x_{k})$-val mindkét oldalt
$$
0 - \frac{f(x_{k})}{f'(x_{k})} - (x^{*} - x_{k}) = \frac{f''(\vartheta_{k})}{2f'(x_{k})}(x^{*} - x_{k})^{2}
$$
$$
x_{k+1} - x^{*} = \frac{f''(\vartheta_{k})}{2f'(x_{k})}(x^{*} - x_{k})^{2}
$$
$$
\lvert e_{k+1} \rvert = \left\lvert  \frac{f''(\vartheta_{k})}{2f'(x_{k})}  \right\rvert \cdot \lvert e_{k} \rvert ^{2}
$$
$$
\lvert e_{k+1} \rvert = c_{k} \cdot \lvert e_{k} \rvert ^{2}
$$
Kell még, hogy $0 < \underline{c} \leq c_{k} \leq \overline c < + \infty$
De pont a feltétel szerint
$$
0 < \frac{m_{2}}{2M_{1}} \leq c_{k} \leq \frac{M_{2}}{2m_{1}} < + \infty
$$
$$
\frac{M_{2}^{1/2-1}}{2m_{1}} \cdot \lvert e_{0} \rvert  = \frac{M_{2}}{2m_{1}} < 1
$$
esetén másodrendű a konvergencia.


