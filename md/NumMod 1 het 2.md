date: 2024.02.19
### Emlek:
$|a - \tilde{a}| \leq \Delta a$
what if $a- \tilde{a}$-en nem ertelmezett egy norma

motivation: kene egy tavolsag fuggveny hogy ertelmezzuk $|a-\tilde{a}|$ erteket

Tekintsuk a $| \cdot|:\mathbb{R} \to \mathbb{R}$   fuggvenyt tulajdonsagait:
1. $|x| \geq 0 \forall x \in \mathbb{R}$ es $|x| = 0 \iff x = 0$
2. $|\lambda x| = |\lambda|\cdot|x|$
3. $|x + y| \leq |x| + |y|$ $\forall x,y \in \mathbb{R}$

-> altalanositas:

***Def***.: Legyen $X$ tetszoleges vektorter, es $\lvert \lvert \cdot \rvert \rvert:X \to \mathbb{R}$ egy fv a kov tulajdonsagokkal:
1. $\lvert \lvert x \rvert \rvert \geq 0$ $\forall x \in X$ es $\lvert \lvert x \rvert \rvert = 0 \iff x = 0_{X}$ ($X$ nullvektora)
2. $\lvert \lvert \lambda x \rvert \rvert = \lvert \lambda \rvert \cdot \lvert \lvert x \rvert \rvert$ $\forall x \in X, \forall \lambda \in \mathbb{R}$
3. $\lvert \lvert x + y \rvert \rvert \leq \lvert \lvert x \rvert \rvert + \lvert \lvert y \rvert \rvert$ $\forall x, y \in X$
Ekkor ezen $\lvert \lvert \cdot \rvert \rvert$ normanak nevezzuk es a normalt ter (N.T.) a kovetkezo rendezett par: $(X, \lvert \lvert \cdot \rvert \rvert)$.


***Def***.: Ha $(X, \lvert \lvert \cdot \rvert \rvert)$ NT, akkor $x, y \in X$ elemek tavolsagan az $\lvert \lvert x-y \rvert \rvert$ szamot ertjuk.

*peldak*:
1. $X = \mathbb{R}$ es $\lvert \lvert \cdot \rvert \rvert = \lvert \cdot \rvert$ 
2. $X = \mathbb{R}^{n}$ a kovetkezo normakkal:
	1.  $\lvert \lvert x \rvert\rvert_{1} :=   \sum \lvert x_{j} \rvert$
	2. $\lvert \lvert x \rvert \rvert_{2} := \sqrt{ \sum \lvert x_{j} \rvert^{2} }$
	3. $\lvert \lvert x \rvert \rvert_{\infty} := \max \{ \lvert x_{j} \rvert \}$
	4. $\lvert \lvert x \rvert \rvert_{p} := \left( \sum \lvert x_{j} \rvert^{p} \right)^{1 / p}$
		Ha $p \to \infty \implies \lvert \lvert x \rvert \rvert_{p} \to \lvert \lvert x \rvert \rvert_{\infty}$ $\forall x \in X$
3.  $X = C[a, b]$ a kovetkezo normakkal:
	1. $\lvert \lvert f \rvert \rvert_{\infty} := \max_{x \in[a, b]} \lvert f(x) \rvert$ 
	2. $\lvert \lvert f \rvert \rvert_{\int} := \int _{a}^{b} \lvert f(x) \rvert \, dx$

### Fontos fogalmak normalt terekben

#### 1. Hibafogalmak
Legyen $(X, \lvert \lvert \cdot \rvert \rvert)$ egy tetszoleges NT, $a, \tilde{a} \in X$
- $\tilde{a}$ abszolut hibaja: $a - \tilde{a} \in X$ 
- $\tilde{a}$ abszolut hibakorlatja: $\Delta_{a}$ szam, melyre $\lvert \lvert a- \tilde{a} \rvert \rvert \leq \Delta_{a}$ 
- $\tilde{a}$ relativ hibaja: $\frac{a - \tilde{a}}{ \lvert \lvert \tilde{a} \rvert \rvert} \in X$
- $\tilde{a}$ relativ hibakorlatja: $\frac{\lvert \lvert a- \tilde{a} \rvert \rvert}{ \lvert \lvert \tilde{a} \rvert \rvert} \leq \delta_{a}\in\mathbb{R}$

#### 2. Konvergencia

***Def***.: Amh az $(X_{n}) \subset X$ sorozat *konvergens*, ha $\exists x \in X$: $\lvert \lvert x_{n}- x \rvert \rvert \to 0$.


### Matrixnormak

Tudjuk: az $\mathbb{R}^{n \times n}$-es matrixok a rajta ertelmezett $+$ es $\lambda$-val valo szorzas muveletekkel vektorteret alkotnak.

**Q**.: Hogyan definialhato rajta norma?

***Def***.: Legyen $\lvert \lvert \cdot \rvert \rvert _\mathbb{R^{n}}$ egy $\mathbb{R}^{n}$ -beli vektornorma. Ekkor az $A \in \mathbb{R}^{n \times n}$ matrix ezen vektornorma altal indukalt matrixnormajanak a kovetkezo szamot ertjuk: 
$$
\lvert \lvert A \rvert  \rvert := \sup_{x \in \mathbb{R}^{n}, x \neq 0} \frac{\lvert \lvert Ax \rvert  \rvert _{\mathbb{R}^{n}}}{\lvert \lvert x \rvert  \rvert _{\mathbb{R}^{n}}}
$$

Jelentesek:
- $\lvert \lvert Ax \rvert \rvert_{\mathbb{R}^{n}}$ az $Ax$ vektor "hossza"
- $\frac{\lvert \lvert Ax \rvert  \rvert _{\mathbb{R}^{n}}}{\lvert \lvert x \rvert  \rvert _{\mathbb{R}^{n}}}$ : hanyszorosara nyujtotta $A$ matrix az $x$ vektort
- $\sup_{x \in \mathbb{R}^{n}, x \neq 0} \frac{\lvert \lvert Ax \rvert  \rvert _{\mathbb{R}^{n}}}{\lvert \lvert x \rvert  \rvert _{\mathbb{R}^{n}}}$ : lehetseges legnagyobb megnyujtasnak az erteke

*peldak*:
$$
\lvert \lvert I \rvert \rvert = \sup_{x \in \mathbb{R}^{n}, x \neq 0} \frac{\lvert \lvert Ix \rvert  \rvert _{\mathbb{R}^{n}}}{\lvert \lvert x \rvert  \rvert _{\mathbb{R}^{n}}} = \sup_{x \in \mathbb{R}^{n}, x \neq 0} \frac{\lvert \lvert x \rvert  \rvert }{\lvert \lvert x \rvert  \rvert } = \sup 1 = 1$$
Tehat barmelyik $\lvert \lvert \cdot \rvert \rvert_{\mathbb{R}^{n}}$ norma altal indukalt matrixnormaban $\lvert \lvert I \rvert \rvert = 1$.

A sup-norma kiszamitasa a tanult vektornormak eseten:
1. Ha $\lvert \lvert \cdot \rvert \rvert_{\mathbb{R}^{n}} = \lvert \lvert \cdot \rvert \rvert_{1}$ , akkor:
$$
\lvert \lvert A \rvert  \rvert  = \lvert \lvert A \rvert  \rvert _{1} = \max_{j \in \{ 1, \dots, n \}} \sum_{i = 1} ^{n} \lvert a_{ij} \rvert 
$$
max oszloposszeg!
peldaul:
$$
\begin{bmatrix}
-2 && 1 \\
0 && 3
\end{bmatrix}

\implies \lvert \lvert A \rvert  \rvert_{1} =  \max \{ \lvert -2 \rvert + \lvert 0 \rvert, \lvert 1 \rvert + \lvert 3 \rvert  \} = 3
$$

2. Ha $\lvert \lvert \cdot \rvert \rvert = \lvert \lvert \cdot \rvert \rvert_{2}$, akkor:
$$
\lvert \lvert A \rvert \rvert = \lvert \lvert A \rvert \rvert_{2} = \sqrt{ \lambda_{\max} (A^{T}A) }
$$
ahol $\lambda_{\max}$ a legnagyobb sajaterteket jeloli.
Neve: "spektralnorma", mert a sajatertekek halmazat "spektral"-nak nevezik.

2.  Ha $\lvert \lvert \cdot \rvert \rvert = \lvert \lvert \cdot \rvert \rvert_{\infty}$, akkor:
$$
\lvert \lvert A \rvert \rvert = \lvert \lvert A \rvert \rvert_{\infty} = \max_{i \in \{ 1, \dots, n \}} \sum_{j=1}^{n} \lvert a_{ij} \rvert 
$$

max sorosszeg!

peldaul:
$$
\begin{bmatrix}
-2 & 1 \\
0 & 3
\end{bmatrix}
\implies \lvert \lvert A \rvert  \rvert _{\infty} = \max \{ \lvert -2 \rvert + \lvert 1 \rvert , \lvert 0 \rvert + \lvert 3 \rvert  \} = 3
$$


***All***.: Az indukalt matrix normakra igazak:
1. $\lvert \lvert Ax \rvert \rvert \leq \lvert \lvert A \rvert \rvert \cdot \lvert \lvert x \rvert \rvert$ $\forall A \in \mathbb{R}^{n \times n}$, $\forall x \in \mathbb{R}^{n}$.
2. $\lvert \lvert I \rvert \rvert = 1$ (lattuk).
3. $\lvert \lvert A \cdot B \rvert \rvert \leq \lvert \lvert A \rvert \rvert \cdot \lvert \lvert B \rvert \rvert$ $\forall A, B \in \mathbb{R}^{n\times n}$ (szub multiplikativitas).


***Megj***.: Vannak egyeb, nem indukalt matrix normak. peldaul:
1. $\lvert \lvert A \rvert \rvert_{max? \text{ nincs neve}} = \max_{i, j} \lvert a_{ij} \rvert$
2. $\lvert \lvert A \rvert \rvert_{osszeg? \text{ nincs neve}} = \sum_{i, j = 1} ^{n} \lvert a_{ij} \rvert$
3. $\lvert \lvert A \rvert \rvert_{F} = \sqrt{ \sum_{i, j = n} ^{n} a_{ij}^{2} }$ (Frobenius norma)

Ezekre a tulajdonsagok nem mindig teljesulnek.


## Kondicioszam

Terjunk vissza a pertulbalt linearis egynlet rendszerek probeleajara.
Tekintsuk az (1)
$$
\begin{equation}
Ax = b
\end{equation}
$$
lin sys eqs -t, ahol $A \in \mathbb{R}^{n \times n}$, $\det A \neq 0$, $b \in \mathbb{R}^{n}$

Tfh $b$ helyett a pertulbalt $\tilde{b}$ van a jobb oldalon (1)':
$$
\begin{equation}
A\tilde{x} = \tilde{b}
\end{equation}
$$

jelolje:
$$
\Delta x = x- \tilde{x} \implies \tilde{x} = x - \Delta x
$$
$$
\Delta b = b - \tilde{b} \implies \tilde{b} = b - \Delta b
$$

$$
A\tilde{x} = \tilde{b}
$$
$$
A(x - \Delta x) = b - \Delta b
$$
$$
Ax - A\Delta x = b - \Delta b
$$
$$
A\Delta x = \Delta b
$$
$$
\Delta x = A^{-1}\Delta b
$$
Valamelyik $\mathbb{R}^{n}$-beli normaban:
$$
\lvert \lvert \Delta x \rvert  \rvert  = \lvert \lvert A^{-1}\Delta b \rvert  \rvert  \leq \lvert \lvert A^{-1} \rvert  \rvert  \cdot \lvert \lvert \Delta b \rvert  \rvert 
$$
$$
b = Ax
$$
$$
\lvert \lvert b \rvert  \rvert  = \lvert \lvert Ax \rvert  \rvert \leq \lvert \lvert A \rvert  \rvert \cdot \lvert \lvert x \rvert  \rvert 
$$
$$
\frac{1}{\lvert \lvert x \rvert  \rvert } \leq \lvert \lvert A \rvert  \rvert  \cdot \frac{1}{\lvert \lvert b \rvert  \rvert }
$$
$$
\implies \frac{\lvert \lvert \Delta x \rvert  \rvert }{\lvert \lvert x \rvert  \rvert } \leq \lvert \lvert A^{-1} \rvert  \rvert  \cdot \lvert \lvert A \rvert  \rvert  \cdot \frac{\lvert \lvert \Delta b \rvert  \rvert }{\lvert \lvert b \rvert  \rvert }
$$
$$
\text{Ha } \lvert \lvert A^{-1} \rvert  \rvert  \cdot \lvert \lvert A \rvert  \rvert  \text{ nagy, akkor nem annyira eles a becsles}
$$

***Jel***.: $\lvert \lvert A^{-1} \rvert  \rvert  \cdot \lvert \lvert A \rvert  \rvert := \operatorname{cond}(A)$: "Az $A$ matrix kondicio szama".

Amh a lin sys eq rosszul kondicionalt, ha $\operatorname{cond}(A) \gg 1$.

A multkori peldat vizsgaljuk meg ujra:

$$
A = \begin{bmatrix}
1 && 1  \\
1 && 1.01
\end{bmatrix}
$$
Alkalmazzuk az $\lvert \lvert \cdot \rvert \rvert_{1}$ altal indukalt matrix normat!
$$
\lvert \lvert A \rvert  \rvert _{1} = 2.01
$$
$$
A^{-1} =
\begin{bmatrix}
101 && -100 \\
-100 && 100
\end{bmatrix}
\implies \lvert \lvert A^{-1} \rvert  \rvert _{1} = 201
$$
$$
\operatorname{cond}(A) = 201 \cdot 2.01 = 404.01 \gg 1
$$
$\implies$ rosszul kondicionalt volt az egyenlet rendstzer!
