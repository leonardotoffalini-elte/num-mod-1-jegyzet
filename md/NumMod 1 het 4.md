date: 2024.03.04

*Megjegyzesek*: 
1. A $\Delta_{j} \neq 0, \quad \forall j = 1, \dots, m$ teljesul, ha $A$ *szimmetrikus pozitiv definit* matrix (szpd).
2. A $\Delta_{j} \neq 0, \quad \forall j = 1, \dots, m$ teljesul, ha $A$ *szigoruan dominans foatloju*, tehat $\forall i = 1, \dots, n$ -re $2\lvert a_{ii} \rvert > \sum_{j = 1}^{m} \lvert a_{ij} \rvert$.
3. Ha $\det A \neq 0$, akkor mindig $\exists P \in \mathbb{R}^{n\times m}$ permutalo matrix, hogy $PA$-nak $\exists$ LU-felbontasa.
4. Ha $A$ szimmetrikus pozitiv definit matrix, akkor $\exists$ egy masik felbontasa is: $A = G \cdot G^{T}$, ahol $G$ also haromszog matrix, pozitiv foatloval. (Cholesky-felbontas)

### Foelem-kivalasztas (pivoting)
Gauss elim $j$-edik lepese:
$$
\begin{bmatrix}
1 & \dots & \dots \\
\vdots & \vdots & \vdots \\
0 & a_{jj}^{(j)}  & \dots \\
\vdots & \vdots & \vdots \\
0  & 0 & 1
\end{bmatrix}
$$
A $a_{jj}^{(j)}$ szammal elosztjuk a $j$-edik sort.
Nem elonyos, ha $\lvert a_{jj}^{(j)} \rvert$ nagyon kicsi, mert akkor a kerekitesi hiba nagy lesz.
1. *Reszleges foelem kivalasztas*: Sorcserevel a foatloba hozzuk az $a_{jj}^{(j)}$ alatti legnagyobb absz erteku elemet.
2. *Teljes foelem kivalasztas*: Sorcserevel es oszlop cserevel az $A[j:n, j:n]$ jobb also reszmatrix legnagyobb absz erteku elemet visszuk a foatloba. (Itt figyelni kell arra, hogy oszlop cserenel az $x$ elemeit is csereljuk.)

### Iteracios modszerek
#### 1. Klasszikus iteracios modszerek
Emlek:
***Def***.: Amh. az $x^{*} \in \mathbb{R}^{n}$ az $f:\mathbb{R}^{n}\to \mathbb{R}^{n}$ *fixpontja*, ha $f(x^{*}) = x^{*}$.
***Def***.: Amh. az $f:\mathbb{R}^{m}\to \mathbb{R}^{m}$ fuggveny *kontrakci* az $\lvert\lvert \cdot \rvert\rvert$ $\mathbb{R}^{n}$-beli normaban, ha $\exists q \in [0,1]$-melyre:
$$
\lvert\lvert f(x)-f(y) \rvert\rvert \leq q\cdot \lvert\lvert x-y \rvert\rvert \quad \forall x,y \in D(f)
$$
***Tetel***: Ha $f:\mathbb{R}^{n}\to \mathbb{R}^{n}$ az egesz $\mathbb{R}^{n}$-en ertelmezett kontrakcio ($q$-val), akkor:
1. $f$-nek $\exists! x^{*}$ fixpontja.
2. Tetszoleges $x^{0} \in \mathbb{R}^{n}$ vektorbol inditva $x^{n+1} = f(x^{n})$ rekurzioval felepitett $(x)_{n}$ sorozat konvergens, es $x_{n} \to x^{*}$.
3. $\lvert\lvert x^{n} - x^{*} \rvert\rvert \leq \frac{q^{n}}{1-q} \lvert\lvert x^{1} - x^{0} \rvert\rvert$

***Q***.: Hogyan alkalmazhatjuk ezt a tetel lin.a.e.r. megoldasara?

(1) $Ax = b, \quad A\in\mathbb{R}^{m\times m}, \quad \det A \neq 0, \quad b \in \mathbb{R}^{m}$
Tfh (1) atirhato a kovetkezo  alakra
(2) $x = Qx + r$, ahol $Q \in \mathbb{R}^{m\times m}, \quad r \in \mathbb{R}^{m}$
Ekkor az $f(x) := Qx + r$ jelolessel a feladat megoldasa az $f:\mathbb{R}^{m}\to \mathbb{R}^{m}$ fuggveny fixpontja. Ezt a fixpontot keressuk.

 ***Q***.: Mikor lesz $f$ kontrakcio?
 $$
x, y \in \mathbb{R}^{m}, \quad f(x) - f(y) = Qx + r - Qy - r = Q(x -y)
$$
$$
\lvert\lvert f(x) - f(y) \rvert\rvert _{\mathbb{R}^{m}} = \lvert\lvert Q(x-y) \rvert\rvert _{\mathbb{R}^{m}} \leq \lvert\lvert Q \rvert\rvert \cdot \lvert\lvert x-y \rvert\rvert _{\mathbb{R}^{m}} 
$$
Tehat be kell latni, hogy $\lvert\lvert Q \rvert\rvert < 1$, akkor $f$ kontrakcio es $q = \lvert\lvert Q \rvert\rvert$.
Tetel $\implies$ ekkor az $x^{n+1} = Qx^{n} + r$ rekurzioval definialt sorozat konverges (barmelyik $\mathbb{R}^{m}$-beli vektornormaban), es $x_{n}\to x^{*}$, mely (1)-nek a megoldasa.

***Q***.:
1. Hogyan irjuk at (1)-et (2) alakura?
2. Mikor fog teljesulni, hogy $\lvert\lvert Q \rvert\rvert < 1$ valamelyik indukalt matrix norma szerint?

### Jacobi-iteracio
$$
Ax = b
$$
$$
A = L + D + U
$$
$$
(L + D + U)x = b
$$
$$
Dx = -(L+U)x + b
$$
$$
x = D^{-1}(b - (L+U)x) = -D^{-1}(L+U)x + D^{-1}b
$$
$$
Q_{J} = -D^{-1}(L+U) \quad r_{J} = D^{-1}b
$$
Fixpont iteracio:
$x^{0} \in \mathbb{R}^{m}$-t rogzitjuk
$x^{n+1} = -D^{-1}(L+U)x^{n} + D^{-1}b$

***All***.: $\lvert\lvert Q_{j} \rvert\rvert_{\infty} < 1 \iff A \text{ szigoruan dominans foatloju}$.

***Kov***.: Ha $A$ szigoruan dominans foatloju, akkor a Jacobi-iteracio konvergens.

### Gauss-Seidel-iteracio
$$
Ax = b
$$
$$
A = L + D + U
$$
$$
(L+D+U)x = b
$$
$$
(L+D)x = -Ux + b
$$
$$
x = -(L+D)^{-1}Ux + (L+D)^{-1}b
$$
$$
Q_{GS} = -(L+D)^{-1}U, \quad r_{GS} = (L+D)^{-1}b
$$

### Stacionarius-iteracio
Eszrevetel: A Jacobi-iteracio atirhato:
$$
x^{n+1} = -D^{-1}(L+U)x^{n} + D^{-1}b
$$
$$
Dx^{n+1} = - (L+U)x^{n} + b
$$
$$
Dx^{n+1} = -(A - D)x^{n} + b
$$
$$
D(x^{n+1} - x^{n}) + Ax^{n} = b
$$
(Jacobi-iteracio kanonikus alakja)

Gauss-Seidel-iteracio atirva:
$$
(D+L)(x^{n+1}-x^{n})+Ax^{n}=b \quad \quad (\text{SI})
$$
(Gauss-Seidel kanonikus alakja)

***Def***.: Legyen $B \in \mathbb{R}^{m\times m}$, es $\tau > 0$ szam. A
$$
B \cdot \frac{x^{n+1}-x^{n}}{\tau} + Ax^{n} = b
$$
iteraciot *stacionarius-iteracionak* nevezzuk.

*Megj*.: 
Jacobi: $B = D, \quad \tau = 1$
Gauss-Seidel: $B = D + L, \quad \tau = 1$
(Meg altalanosabb: $B \leftrightarrow B_{n}, \quad \tau \leftrightarrow \tau_{n}$)

Egy fontos stacionarius iteracio (Tulrelaxacios modeszer / Successive overrelaxation method - SOR-modszer):
$$
B = D + \omega L, \quad \tau = \omega, \quad \text{ ahol } \omega > 0 \text{ adott parameter}
$$
$$
(D + \omega L)\cdot \frac{x^{n+1}-x^{n}}{\omega} + Ax^{n} = b
$$
Megfigyeles: $\omega = 1$-re visszakapjuk a Gauss-Seidel-iteraciot.


