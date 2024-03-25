date: 2024.02.26

## Linearis algebrai egyenletrendszerek (l.a.e.r) megoldasa

### 1. Direkt modszerek
Pontosan szamolva veges sok lepesben a pontos megoldasokat adjak.
*peladul*:
- Cramer-szabaly
  nagyon muveletigenyes
- Gauss-eliminacio

### 2. Iteracio modszerek
Egy, a pontos megoldashoz tarto vektorsorozatot generalnak.



### Gauss eliminacio
Megoldando: $Ax = b, \quad A \in \mathbb{R}^{m \times m}, \quad \det A \neq 0 \implies \exists! \text{m.o.}, \quad b \in \mathbb{R}^{m}$.
Azaz:
$$
\begin{array}
aa_{11}x_{1} + a_{12}x_{2} + \dots + a_{1m}x_{m} & = b_{1} \\
\vdots \\
a_{m 1}x_{1} + a_{m 2}x_{2} + \dots + a_{m m}x_{m} & = b_{m}
\end{array}
$$

I. alakban: Atalakitjuk az e.r.-t felso haromszog matrixuva. A foatloban legyenek egyesek
1. lepes: Tfh $a_{11} \neq 0$ ekkor (1)
$$x_{1} + \frac{a_{12}}{a_{11}}x_{2} + \frac{a_{13}}{a_{11}}x_{3} + \frac{a_{1m}}{a_{11}}x_{m} = \frac{b_{1}}{a_{11}} = y_{1}$$
2. lepes: (1)' segitsegevel a (2) - (m) egyenletekbol eliminaljuk $x_{1}$-et, kivonva beloluk az (1)'-nek az $a_{i 1}$-szereset.
$$
\begin{array}
xx_{1} & + \frac{a_{12}}{a_{11}}x_{2} & + \frac{a_{13}}{a_{11}}x_{3} & + \frac{a_{1m}}{a_{11}}x_{m} & = & \frac{b_{1}}{a_{11}} = y_{1} \\ \\
    & a_{22}^{(1)}x_{2} & + \dots &  & = & y_{2}\\
    & & & &\vdots &\\
 & a_{m 2}^{(1)}x_{2} & +  \dots &+ a_{m m}^{(1)}x_{m} & = & b_{m}
\end{array}
$$
3. lepes: nem irom le mert mindenki tud Gauss-eliminalni...

### Mikor hajthato vegre a Gauss-elim?
I. szakaszban $Ax = b \implies Ux = y$

Q.: Mi a kapcsolat $y$ es $b$ kozott?
$b_{1} = a_{11}y_{1}$
$b_{2} = a_{21}y_{1} + a_{22}^{(1)}y_{2}$
...
es igy tovabb
$b_{j} = l_{j 1}y_{1} + l_{j 2}y_{2} + \dots + l_{j j }y_{j}, \quad j = 1, \dots, m, \text{ ahol } l_{jj} = a_{jj}^{(j-1)}$

$$
\begin{bmatrix}
a_{11} & 0 & \dots & 0 \\
a_{21} & a_{22}^{(1)} & \dots & 0 \\
& & \dots & a_{mm}^{(m-1)}
\end{bmatrix}
\cdot
\begin{bmatrix}
y_{1} \\
y_{2} \\
\vdots \\
y_{m}
\end{bmatrix}

\leq

\begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{m}
\end{bmatrix}
$$

Ha a Gauss-elim elvegezheto akkor a fenti matrix invertalhato, azaz a foatloban nincs $0$, tehat $\exists L^{-1}$, ahol $L$ a fenti also haromszog matrix.

Tehat $Ly = b \implies y = L^{-1}b \implies Ux = L^{-1}b \implies LU x = b$

Ebbol adodik egy uj modszer
1. Felirjuk az $A$-t $A = LU$ alakban, ahol $L$ invertalhato also haromszog matrix es $U$ olyan felso haromszog matrix melynek a foatlojaban csak egyesek vannak.
2. Megoldjuk az $Ly = b$ egyenletrendszert $\implies y$
3. Megoldjuk az $Ux = y$ egyenletrendszert $\implies x$

Elnevezes: LU-felbontas modszere
Belathato, hogy 1. - 2. ekvivalens a Gauss-elim elso szakaszaval es 3. ekvivalens a Gauss-elim masodik szakaszaval. Tehat ez a modszer a Gauss-elim modositott algoritmusa.

Tehat a kerdesunk mashogy: Mikor letezik az LU-felbontas? Pontosan ekkor hajthato vegre a Gauss-eliminacio.

Legyen
$$
\Delta_{1} := a_{11}, \quad, \Delta_{2} := \det \begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
,
\dots,

\Delta_{m} := \det A
$$

***All***.: Ha $\Delta_{j} \neq 0$, $j = 1, \dots, m$, akkor $\exists$ LU-felbontassa $A$-nak, es az egyertelmu.
***Biz***.:
1. Letezes
Itt csak az $A \in \mathbb{R}^{2 \times 2}$ esetre mutatjuk meg
$$
A = L \cdot U = 
\begin{bmatrix}
l_{11} & 0 \\
l_{21} & l_{22}
\end{bmatrix}
\cdot
\begin{bmatrix}
1 & u_{12} \\
0 & 1
\end{bmatrix}
\text{ felbontas letezik} \iff
\text{letezik } l_{11}, l_{21}, l_{22}, u_{12} \text{ ismeretlenekre nezve megoldasa a kovetkezo e.r.-nek}
$$

$$
l_{11} = a_{11}
$$
$$
l_{11} u_{12} = a_{12}
$$
$$
l_{21} = a_{21}
$$
$$
l_{21} u_{12} + l_{22} = a_{22}
$$
es a kovetkezo $L$ matrixnak letezzen inverze
$$
L = \begin{bmatrix}
l_{11} & 0 \\
l_{21} & l_{22}
\end{bmatrix}
$$
tehat $l_{11} \neq 0, l_{22} \neq 0$.

Ha $a_{11} \neq 0$, akkor lathato, hogy ennek az egyenletrendszernek $\exists!$ megoldasa:
$$
l_{11} = a_{11}, \quad u_{12} = \frac{a_{12}}{a_{11}}, \quad l_{21} = a_{21}, \quad l_{22} = a_{22} - a_{21} \frac{a_{12}}{a_{11}}
$$
Tovabba $l_{11} \neq 0$, mert $a_{11} \neq 0$ es $l_{22} \neq 0$, mert $l_{22} = \frac{\det A}{a_{11}}$ $\implies \exists L^{-1}$

Megjegyzes: $m > 2$-re teljes indukcioval kovetkezik az allitas.

2. Egyertelmuseg
tfh $A = L_{1}U_{1} = L_{2}U_{2}$
$$
L_{2}^{-1}L_{1}U_{1} = U_{2}
$$
$$
L_{2}^{-1}L_{1} = U_{2}U_{1}^{-1}
$$
Mivel az alsoharomszog matrixok es a felso haromszog matrixok is egy-egy csoportot alkotnak, ezert a fenti csak akkor igaz, ha $L_{2}^{-1}L_{1}$ es $U_{2}U_{1}^{-1}$ is diagonalis. Tovabba $U_{1, 2}$-nek a foatlojaban egyesek vannak, tehat $U_{2}U_{1}^{-1}$-nek is a foatlojaban egyesek vannak. Tehat mindket oldalon az egyseg matrix van.
$$
\implies L_{2}^{-1}L_{1} = I = U_{2}U_{1}^{-1} \implies L_{1} = L_{2}, \quad U_{1} = U_{2}
$$

Megmutathato, hogy ha $\Delta_{j} \neq 0$ valamely $j$-re, akkor $\exists$  LU-felbontasa $A$-nak.
$2 \times 2$ esetben jol latszik:
$$
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
=
\begin{bmatrix}
0 & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
$$
$$
\begin{bmatrix}
0 & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}
=
\begin{bmatrix}
l_{11} & 0 \\
l_{21} & l_{22}
\end{bmatrix}
\cdot
\begin{bmatrix}
1 & u_{12} \\
0 & 1
\end{bmatrix}
\implies l_{11} = 0 \implies \text{ekkor } L \text{ nem invertalhato}
$$


***Kov***.: A Gauss-eliminacio pontosan akkor hajthato vegre, ha $A$ osszes bal felso sarokdeterminansa nem $0$.