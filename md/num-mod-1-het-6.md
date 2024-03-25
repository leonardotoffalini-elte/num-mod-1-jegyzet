date: 2024.03.18.

Multkor ott fejeztuk be, hogy be akartuk latni hogy az egymast koveto iranyok a gradiens modszerben meroleges egymasra!

Irjuk fel a skalaris szorzatat az egymast koveto iranyoknak!
$$
(r_{i}, r_{i+}) \stackrel{?}{=} 0
$$
$$
(r_{i}, r_{i+1}) = \left( r_{i}, b - A\left( x_{i} + \frac{(r_{i}, r_{i})}{(r_{i}, Ar_{i})} \cdot r_{i}\right) \right)
$$
$$
= (r_{i}, r_{i}) - (r_{i}, A\frac{(r_{i}, r_{i})}{(r_{i}, Ar_{i})} \cdot r_{i})
$$
$$
= (r_{i}, r_{i}) - \frac{(r_{i}, r_{i})}{(r_{i}, Ar_{i})}(r_{i}, Ar_{i}) = (r_{i}, r_{i}) - (r_{i}, r_{i}) = 0
$$

*Megjegyzes:* Ha $\operatorname{cond}_{2}(A)$ nagy, akkor lassu a konvergencia.

### Konjugalt gradiens-modszer

$m := 2$
Tudjuk: a gradiens modszernel a $p_{1}$ keresesi irany ($r_{0}$) $\perp$ $r_{1}$.
Azaz:
$$
0 = (p_{1}, r_{1}) = (p_{1}, b - Ax_{1}) = (p_{1}, Ax^{*} - Ax_{1}) = (p_{1}, A(x^{*} - x_{1}))
$$

### Def.:
Legyen $A \in \mathbb{R}^{m \times m}$ szpd. Azt mondjuk, hogy $x$ es $y \in \mathbb{R}^{m}$ vektorok *$A$-konjugaltak/ortogonalisak*, ha $(x, Ay) = 0$.

Tehat olyan keresesi iranyt lenne erdemes valasztani, amely $p_{1}$-re $A$-ortogonalis!
Keressuk $p_{2}$-t a kovetkezo alakban:
$$
p_{2} = r_{1} - \beta_{1} \cdot p_{1}
$$
$$
(p_{1}, A(r_{1}-\beta_{1}\cdot p_{1})) = 0
$$
$\beta_{1} = \; ?$

$$
(p_{1}, Ar_{1}) - \beta_{1} (p_{1}, Ap_{1}) = 0
$$
$$
\implies \beta_{1} = \frac{(p_{1}, Ar_{1})}{(p_{1}, Ap_{1})}
$$
Ezen $\beta_{1}$-et valasztva, a $p_{2} = r_{1} - \beta_{1} \cdot p_{1}$ iranyba lepve az $x^{*}$ minimum helybe lepunk!
Tehat $m=2$ eseten $2$ lepesben meg tudjuk hatarozni a linearis egyenletrendszer megoldasat.

*Megjegyzes:* $A \in \mathbb{R}^{m \times m}$ eseten is altalanosithato. Ekkor legfeljebb $m$ lepesben megkapjuk a megoldast.


### Algebrai egyenletek megoldasa

Egyismeretlenes valos egyenletekkel foglalkozunk.
Egy ilyen egyenlet mindig felirhato a kovetkezo alakban:
$$
f(x) = 0 \quad \quad \text{(1)}
$$
ahol $f: \mathbb{R} \to \mathbb{R}$ fuggveny.

Ezzel (1)-nek a megoldasa ugyanaz mint $f$ zerushelye. Ezt keressuk a tovabbiakban!

### Gyokok stabilitasa
***Q.:*** Mennyire erzekeny a megoldas $f$ kis megvaltoztatasara?

Tegyuk fel, hogy (1) helyett az 
$$\tilde{f}(x) = 0 \quad \quad (2)$$
Egyenletet oldjuk meg, es tegyuk fel, hogy (1)-nek es (2)-nek is $\exists!$ megoldasa, melyek $x^{*}$ illetve $\tilde{x}^{*}$ rendre.

A kovetkezo legyen a meroszamunk az elteresre:
$$
\lvert x^{*} - \tilde{x}^{*} \rvert  \leq \; ?
$$
Ha $f$ es $\tilde{f}$ csak *kicsit* ter el egymastol?
Merje $\max \limits_{[a, b]} \lvert f - \tilde{f} \rvert$ az $f$ es $\tilde{f}$ eltereset.

Tegyuk fel, hogy $f \in C[a, b] \cap D(a, b)$ 

*Ismetles:* (Lagrange-kozepertek tetel)
Tegyuk fel, hogy $f \in C[a, b] \cap D(a, b)$. Ekkor $\exists c \in (a, b)$ ugy, hogy
$$
f'(c) = \frac{f(b) - f(a)}{b - a}
$$

Tovabba tegyuk fel, hogy $x^{*}$ es $\tilde{x}^{*} \in [a, b]$, es $\max \limits_{[a, b]} \lvert f - \tilde{f} \rvert < \varepsilon$.
Alkalmazzuk az LKT-t az $[x^{*}, \tilde{x}^{*}]$ intervallumon (felteve, hogy $x^{*} < \tilde{x}^{*}$):
$$
\exists c \in (x^{*}, \tilde{x}^{*}): \quad f(\tilde{x}^{*}) - f(x^{*}) = f'(c)(\tilde{x}^{*} - x^{*})
$$
Tegyuk fel, hogy $f'(x) \neq 0 \quad \forall x \in (x^{*}, \tilde{x}^{*})$.
$$
\iff \lvert \tilde{x}^{*} - x^{*} \rvert = \left\lvert  \frac{f(\tilde{x}^{*})}{f'(c)}  \right\rvert  = \frac{\lvert f(\tilde{x}^{*}) - \tilde{f}(\tilde{x}^{*}) \rvert}{\lvert f'(c) \rvert } < \frac{\varepsilon}{\min \limits_{[a, b]} \lvert f' \rvert  }
$$
### Def.:
Az $M : = \frac{1}{\min \limits_{[a, b]} \lvert f' \rvert  }$ szamot az (1) egyenlet *kondicionaltsagi szamanak* nevezzuk.

Tehat ha $\max \limits_{[a, b]}\lvert f - \tilde{f} \rvert < \varepsilon$, akkor $\lvert  \tilde{x}^{*} - x^{*} \rvert < M \cdot \varepsilon$.

### Konvergenciasebesseg
Tegyuk fel, hogy $\lim_{ k \to \infty }x_{k} = x^{*}$, es legyen $e_{k} := x_{k} - x^{*}$. ($\lim_{ k \to \infty } e_{k} = 0$ vagy $\lim_{ k \to \infty }\lvert e_{k} \rvert = 0$)

### Def.:
Azt mondjuk, hogy az $(x_{k})$ sorozat *konvergencia rendje* $p \geq 1$, ha
$$
\lim_{ k \to \infty } \frac{\log \lvert e_{k} \rvert }{\log \lvert e_{k-1} \rvert } = p
$$
Ha $p = 1$, akkor linearis/elsorendu konvergenciarol beszelunk.
Ha $p = 2$, akkor masodrendu/kvadratikus konvergenciarol beszelunk.

Elsorendu:

|         | $\lvert e_{k} \rvert$ | $\frac{\log \lvert e_{k} \rvert}{\log \lvert e_{k-1} \rvert}$ |
| ------- | --------------------- | ------------------------------------------------------------- |
| $k=1$   | $10^{-3}$             |                                                               |
| $k = 2$ | $10^{-4}$             | $1.33$                                                        |
| $k = 3$ | $10^{-5}$             | $1.25$                                                        |

Masodrendu:

|         | $\lvert e_{k} \rvert$ | $\frac{\log \lvert e_{k} \rvert}{\log \lvert e_{k-1} \rvert}$ |
| ------- | --------------------- | ------------------------------------------------------------- |
| $k=1$   | $10^{-3}$             |                                                               |
| $k = 2$ | $10^{-6}$             | $2$                                                           |
| $k = 3$ | $10^{-12}$            | $2$                                                           |

***Allitas***: Tegyuk fel, hogy $\lvert e_{k} \rvert = c_{k} \cdot \lvert e_{k-1} \rvert, \quad k = 1, 2, \dots$, ahol $0 < \underline{c} \leq c_{k} \leq \overline{c} < 1$. Valamilyen $\underline{c},\; \overline{c}$ konstansokra
Ekkor $x_{k} \to x^{*}$ monoton modan es elsorendben.

***Biz***.:
Monotonan, mivel $0 < c_{k} < 1 \implies \lvert e_{k} \rvert < \lvert e_{k-1} \rvert$ $\quad \forall k = 1, 2, \dots$ $\implies (\lvert e_{k} \rvert)$ sorozat monoton csokkeno.
Konvergal, mivel $\lvert e_{k} \rvert = c_{k} \cdot \lvert e_{k_{1}} \rvert \leq \overline c \cdot \lvert e_{k-1} \rvert \leq \overline c \cdot \overline c \cdot \lvert e_{k-2} \rvert \leq \dots \leq \overline c^{k} \cdot \lvert e_{0} \rvert$.  Mivel $\overline c < 1$ ezert tenyleg $\lim_{ k \to \infty }\lvert e_{k} \rvert = 0$.

A feltetelben levo egyenletnek mindket oldalan logaritmust veve:
$$
\log \lvert e_{k} \rvert  = \log c_{k} + \log \lvert e_{k-1} \rvert 
$$
$$
\implies \frac{\log \lvert  e_{k} \rvert }{\log \lvert e_{k-1} \rvert } = \frac{\log c_{k}}{\log \lvert e_{k-1} \rvert } + 1
$$
Latszik, hogy $\log \lvert e_{k-1} \rvert \to - \infty$. Mostmar elegendo lenne belatni, hogy $\log c_{k}$ korlatos.
$$
\log \underline c < \log c_{k} \leq 0
$$
Tehat $\frac{\log c_{k}}{\log \lvert e_{k-1} \rvert } \to 0 \implies$ a jobb oldal $\to 1$ $\implies$ $p = 1$ a konvergencia rendje, azaz elsorendu a konvergencia.


***Allitas***: Tegyuk fel, hogy $\lvert e_{k} \rvert = c_{k} \cdot \lvert e_{k-1} \rvert^{p} \quad k = 1, 2, \dots$ , ahol $p > 1$ es $0 < \underline{c} \leq c_{k} \leq \overline c < + \infty$. Valamilyen $\underline{c}, \; \overline c$ konstansokra. Tovabba $\overline{c}^{1/p-1} \cdot \lvert e_{0} \rvert < 1$. Ekkor $(x_{k})$ konvergens es a konvergencia rendje $p$.

*Megjegyzes:* Az utobbi feltetel azt jeletnti, hogy a konvergencia csak akkor kovetkezik, ha $x_{0}$ eleg kozel van $x^{*}$-hoz. Ugyanakkor $\overline c < + \infty$, es nem kell teljesulnie, hogy $\overline c < 1$.


