date: 2024.03.11.


### Stacionarius iteracio konvergenciaja
*emlek:*
$$
B \frac{x^{n+1} - x^{n}}{\tau} + A \cdot x^{n} = b \qquad \text{(SI)}
$$ 
$$
Ax = b \qquad \text{(1)}
$$ 

tfh. $A$ szpd, tehat $A = A^{T}$, $x^{T}Ax > 0, \; \text{ha } x \neq 0$
maskeppen: $\exists \delta > 0: (Ax, x) \geq \delta \cdot \lvert\lvert x \rvert\rvert^{2}$

jelolje $x^{*}$ az (1) egyenelet megoldasat, azaz $Ax^{*} = b$
jelolje $e_{n}:=x^{n}-x^{*}$ (az $n$-edik iteracio hibaja)

***Def***.: Azt mondjuk hogy a stacionarius iteracio (SI) konvergens, ha $\exists \lim x_{n}$ és $x_{n}\to x^{*}$, azaz $\lim_{ n \to \infty }e_{n} = 0$.

***All***.: Tegyuk fol, hogy $A$ szpd. Ha $\exists B^{-1}$, es $\tau > 0$  parameter olyan, hogy $B - 0.5 \tau A$ szpd, akkor a stacionarius iteracio konvergens.
***Biz***.:
$$
x^{n} = e_{n} + x^{*}, \quad x^{n+1} = e_{n+1} + x^{*} \leadsto \text{ (SI)-be beirva}
$$
$$
B \frac{e_{n+1} + x^{*} - e_{n} - x^{*}}{\tau} + Ae_{n} + Ax^{*} = b
$$
$$
B \frac{e_{n+1} - e_{n}}{\tau} + Ae_{n} = 0 \qquad \text{(3) hibaegyenlet}
$$
Fejezzuk ki $e_{n+1}$-el
$$
Be_{n+1} = (B - \tau A)e_{n}
$$
$$
e_{n+1} = (I - \tau B^{-1}A)e_{n}
$$
$$
Ae_{n+1} = (A - \tau AB^{-1}A)e_{n}
$$
$$
\implies (Ae_{n+1}, e_{n+1}) = (Ae_{n} - \tau AB^{-1}Ae_{n}, e_{n} - \tau B^{-1}Ae_{n})
$$
$$
= (Ae_{n}, e_{n}) - \tau(AB^{-1}Ae_{n}, e_{n}) - \tau(Ae_{n}, B^{-1}Ae_{n}) + \tau ^{2}(AB^{-1}Ae_{n}, B^{-1}Ae_{n})
$$
Tudjuk, hogy
$$
(AB^{-1}Ae_{n}, e_{n}) = (B^{-1}Ae_{n}, A^{T}e_{n}) = (B^{-1}Ae_{n}, Ae_{n}) = (Ae_{n}, B^{-1}Ae_{n})
$$
Tehat
$$
(Ae_{n+1},e_{n+1}) = (Ae_{n}, e_{n}) - 2\tau(AB^{-1}Ae_{n}, e_{n}) + \tau ^{2}(AB^{-1}Ae_{n}, B^{-1}Ae_{n})
$$
Jelolje $J_{n} = (Ae_{n}, e_{n})$. Ezzel
$$
J_{n+1} = J_{n} - 2\tau(Ae_{n}, B^{-1}Ae_{n}) + \tau ^{2}(AB^{-1}Ae_{n}, \stackrel{y_{n}}{\overbrace{ B^{-1}Ae_{n}}})
$$
Ezzel $By_{n} = Ae_{n}$
$$
= J_{n} - 2\tau(By_{n}, y_{n}) + \tau ^{2} (Ay_{n}, y_{n}) = J_{n} - 2\tau \left( (By_{n}, y_{n}) - \frac{\tau}{2}(Ay_{n}, y_{n}) \right)
$$
$$
\leadsto J_{n+1} = J_{n} - 2\tau((B - 0.5\tau A)y_{n}, y_{n}) \qquad \text{(4)}
$$
$$
\implies J_{n+1} \leq J_{n}
$$
Mert feltetel szerint $\tau > 0$ es $(B - 0.5 \tau A)$ szpd, tehat pozitiv szor pozitiv tagot vonunk ki, tehat egy pozitiv szamot vonunk ki. Ezert a jobb oldal kisebb mint $J_{n}$.
Igy a $(J_{n})$ sorozat monoton csokkeno, es $J_{n} \geq 0$, (mert $J_{n} = (Ae_{n}, e_{n})$ ), tehat ez a sorozat alulrol korlatos.
Tehat $(J_{n})$ konvergens, jeloles $J^{*} := \lim_{ n \to \infty }J_{n}$

(4)-ben vegyunk limeszt $\leadsto$
$$
J^{*} = J^{*} - 2\tau \lim_{ n \to \infty } ((B - 0.5 \tau A)y_{n}, y_{n})
$$
$$
\implies \lim_{ n \to \infty } ((B - 0.5 \tau A)y_{n}, y_{n}) = 0
$$
Mivel $B - 0.5\tau A$ szpd, ezert $\exists \delta > 0: ((B - 0.5 \tau A)y_{n}, y_{n}) \geq \delta \cdot \lvert\lvert y_{n} \rvert\rvert^{2}$.
Rendorelv:
$$
((B - 0.5 \tau A)y_{n}, y_{n}) \geq \delta \cdot \lvert\lvert y_{n} \rvert\rvert^{2} \geq 0
$$
$$
\lim_{ n \to \infty } ((B - 0.5 \tau A)y_{n}, y_{n}) \geq \lim_{ n \to \infty }  \delta \cdot \lvert\lvert y_{n} \rvert\rvert^{2} \geq 0
$$
$$
\implies 0 \geq \lim_{ n \to \infty } \delta \cdot \lvert\lvert y_{n} \rvert\rvert ^{2} \geq 0 \implies \lim_{ n \to \infty } \delta \cdot \lvert\lvert y_{n} \rvert\rvert ^{2} = 0
$$

Mivel $y_{n} = B^{-1}Ae_{n}$ $\leadsto e_{n} = A^{-1}By_{n}$
$$
0 \leq \lvert\lvert e_{n} \rvert\rvert = \lvert\lvert A^{-1}By_{n} \rvert\rvert \leq \lvert\lvert A^{-1}B \rvert\rvert  \cdot \lvert\lvert y_{n} \rvert\rvert \to 0 \implies \lvert\lvert e_{n} \rvert\rvert \to 0 \implies e_{n} \to 0
$$

### Sor modszer konvergenciaja
Kulcskerdes: $\omega$ megvalasztasa.
Fugg $A$-tol!

Nehany allitas:
1.) Tetszoleges $A \in \mathbb{R}^{n \times m}$ eseten a SOR-modszer konvergenciajahoz szukseges, hogy $\omega \in (0, 2)$.
2.) Ha $A$ szpd, akkor $\omega \in (0, 2)$ elegseges is a konvergenciahoz.
$\implies$ Ha $A$ szpd, akkor a Gauss-Seidel iteracio konvergens, mert a GS-it pont a SOR-modszer $\omega = 1$-el.


### Gradiens alapu modszerek
$$
Ax = b \qquad \text{(1)}
$$
Tegyuk fel, hogy $A$ szpd.

***Def***.: $\phi : \mathbb{R}^{m} \to \mathbb{R}$ fv-t:
$$
\phi(x) := \frac{1}{2}(x, Ax) - (x, b)
$$
ez differencialhato $\mathbb{R}^{m}$-en.
Derivaljuk!
$$
\phi'(x) = \nabla \phi(x) = Ax - b \qquad \text{(szamolassal ellenorizheto)}
$$
$Ax - b$ az $r := b - Ax$ *maradekvektor* $-1$ szerese!

Hol $0$ a gradiens?
$$
\phi'(x) = Ax - b = 0 \leadsto x = A^{-1}b \qquad \text{ ez eppen az (1) megoldasa}
$$
$$
\phi''(x) = A
$$
Mivel feltettuk, hogy $A$ szpd, ezert $\phi''(x)$ potiv definit, tehat ahol a gradiens nulla ott lokalis minimum hely van.
$\implies x^{*}$ az egyetlen lokalis minimum hely / globalis minimum helye $\phi$-nek.

***Q.:*** Hogy nez ki a $\phi$ fuggveny?  Tekintsunk egy ket dimenzios peldat:
$$
\begin{align}
2x_{1} & = 4 \\
8x_{2} & = 8
\end{align}
$$
Megoldas: $x_{1}^{*} = 2, \; x_{2}^{*} = 1$
$$
A = \begin{bmatrix}
2 & 0 \\
0 & 8
\end{bmatrix}, \quad
b = \begin{bmatrix}
4 \\
8
\end{bmatrix}
$$
$$
\phi(x) = \frac{1}{2}(x, Ax) - (x, b)
$$
$$
\phi(x) = \frac{1}{2} \left(\begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}, \begin{bmatrix}
2x_{1} \\
8x_{2}
\end{bmatrix}\right) - \left( \begin{bmatrix}
x_{1} \\
x_{2}
\end{bmatrix}, \begin{bmatrix}
4 \\
8
\end{bmatrix} \right)
= \frac{1}{2}x_{1}2x_{1} + \frac{1}{2}x_{2}8x_{2} - 4x_{1}-8x_{2} = (x_{1}- 2)^{2} + 4(x_{2}-1)^{2}-8
$$
Szintvonalak?
$Ac = 0$-hoz tartozo
$$
(x_{1} - 2)^{2} + 4(x_{2} - 1)^{2} - 8 = 0
$$
$$
\frac{(x_{1} - 2)^{2}}{8} + \frac{(x_{2} - 1)^{2}}{2} = 1
$$
Ez egy $(2, 1)$ kozeppontu ellipszis $\sqrt{ 8 }, \sqrt{ 2 }$ fotengelyekkel. Tehat $(2, 1)$ a megoldas.

Tehat a fuggveny szintvonalai koncentrikus hiperellipszoidok!

Eloszor gondoljuk meg, hogy egy $x \in \mathbb{R}^{m}$ pontot es egy $p \neq 0$ vektort rogzitve $p$ irany menten hol veszi fel a $\phi$ a legkisebb erteket?

Jel.: $g(\alpha) := \phi(x + \alpha p)$
***Q.:*** Mely $\alpha$-ra lesz $g(\alpha)$ fuggveny erteke minimalis?

***All.:*** A $g(\alpha) = \phi(x + \alpha p)$ fuggveny egyertelmu minimumat az
$$
\alpha = \frac{(p, r)}{(p, Ap)}
$$
megvalasztas eseten veszi fol!

***Biz***.: Farago jegyzet 83. oldal


***Q.:*** Hogyan valasszuk meg $p_{1}, p_{2}, \dots$ keresesi iranyokat?

### Gradiens modszer
Tudjuk: A $\nabla \phi$ -vel ellentetes iranyban a legmeredekebb a lejtes.

$x_{i}$ pontban $p_{i+1}$-el jelolve a keresesi iranyt:
$$
p_{i+1} := -\nabla \phi(x_{i})
$$
$$
\nabla \phi(x) = Ax - b = -r
$$
$$
\implies p_{i+1} := - \nabla \phi(x_{i}) = b - Ax_{i} = r_{i}
$$
ami eppen az $x_{i}$ pontbeli maradekvektor.

$$
x_{i} \leadsto x_{i+1} = x_{i} + \alpha \cdot p_{i+1} = x_{i} + \frac{(p_{i+1}, r_{i})}{(p_{i+1}, Ap_{i+1})} \cdot p_{i+1} = x_{i} + \frac{(r_{i}, r_{i})}{(r_{i}, Ar_{i})} \cdot r_{i}
$$
Mi lesz $x_{i+1}$-ben a maradekvektor?
$$
r_{i+1} = b - Ax_{i+1} = b - A \cdot \left(x_{i} + \frac{(r_{i}, r_{i})}{(r_{i}, Ar_{i})} \cdot r_{i}\right)
$$
Vegyuk eszre: $r_{i} \perp r_{i+1}$, mert addig megyunk $p_{i}$ iranyban ameddig nem erintjuk a kovetkezo szintvonalat, amire a kovetkezo gradiens meroleges.





