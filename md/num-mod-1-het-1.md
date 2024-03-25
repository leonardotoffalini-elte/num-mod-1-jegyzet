2024.02.12

## Numerikus moddelezés lepesei

1. **Valodi problema**
   Halpopulacio idobeli fejlodese
2. **Tudomanyos modell**
   Vannak zsakmanyhalak es ragadozo halak
   - termezetes szaporulat
   - ragadozok esznek zsakmanyokat
   - termeszetes pusztulas

3. **Matematikai modell**
   - jelolje $x(t)$ a zsakmanyhalak $t$ idobeli ossztomeget
   - jelolje $y(t)$ a ragadozohalak $t$ idobeli osszomeget
$$
\begin{equation}
x' = ax - bxy
\end{equation}
$$
$$
\begin{equation}
y' = -cy + dxy
\end{equation}
$$
$$
x(0) = x_{0}
$$
$$
y(0) = y_{0}
$$
4. **Numerikus modell**
Kozelito modszert alkalmazva a Lotka Volterra egyenlet rendszerre

5. **Szamitogepes modell**
Lekodoljuk es futtatjuk a numerikus modellnek a programjat


## Hibaforrasok

1. **Modellhiba**
A tudomanyos/matematikai modellben egyszerusitesekkel eltunk

2. **Keplethiba**
A matematikai/numerikus modellben egy egyszerubb kifejezessel helyettesitettunk egy bonyolultabbat, pl.:
$$
\exp(2) = \sum_{k=0}^{\infty} \frac{2^{k}}{k!} \approx \sum_{k=0}^{N} \frac{2^{k}}{k!}
$$
-> diszkretizacios hiba
- folytonos fuggveny <—> racs pont fuggveny
- derivalt <-> differencial hanyados
- integral <-> veges osszeg

3. **A bemeno adatok hibaja**
pl.: meresi hiba

4. **Szamabrozolasbol eredo hiba**
pl.: flooting point error


## Hibafogalmak

$a:=$ pontos ertek $(a \in \mathbb{R})$
$\tilde{a} :=$ szamitott ertek $(\tilde{a} \in \mathbb{R})$

***Def***.: Az $\tilde{a}$ abszolut hibajanak az $\Delta a := a - \tilde{a}$ szamot ertjuk.

***Def***.: Az $\Delta_{a} \in \mathbb{R}_{0}^{+}$ szamot az $\tilde{a}$ egy abszolut hibakorlatjanak nevezzuk, ha $|\Delta a| \leq \Delta_{a}$.

***Jel***.: $a = \tilde{a} \pm \Delta_{a}$

***Def***.: $\tilde{a}$ relativ hibaja: $\delta a .= \frac{\Delta a}{|\tilde{a}|}$

***Def***.: $\tilde{a}$ relativ hibakorlatja: $\delta_{a} \in \mathbb{R}_{0}^{+}$ szam melyre $|\delta a| \leq \delta_{a}$

***Megj***.: $\delta_{a} = \frac{\Delta_{a}}{|\tilde{a}|}$ mindig jo lesz


### Az alapmuveletek hibaja

tfh $x, y \in \mathbb{R}$ helyett a hibas $\tilde{x},\tilde{y} \in \mathbb{R}$ szamokkal vegezzuk ele az alapmuveleteket.

1. **osszeadas**
$$
|(x+y) - (\tilde{x}+ \tilde{y})| = | x - \tilde{x} + y - \tilde{y} | \leq |x - \tilde{x}| + |y - \tilde{y}| \leq \Delta_{x} + \Delta_{y}
$$

2. **kivonas**
$$
|(x - y) - (\tilde{x} - \tilde{y})| = |x-\tilde{x} + \tilde{y} - y| \leq |x - \tilde{x}| + |\tilde{y} -y| = |x - \tilde{x}| + |y - \tilde{y}| \leq \Delta_{x} + \Delta_{y}
$$

3. **szorzas**
$$
| xy - \tilde{x}\tilde{y} | = |xy + x\tilde{y} - x\tilde{y} -\tilde{x}\tilde{y}| = |x(y-\tilde{y}) + \tilde{y}(x-\tilde{x})| \approx |\tilde{x}(y-\tilde{y}) + \tilde{y}(x-\tilde{x})| \leq |\tilde{x}|\Delta_{y} + |\tilde{y}| \Delta_{x} := \Delta_{xy}
$$

4. **hanyados**
$$
|\frac{x}{y} - \frac{\tilde{x}}{\tilde{y}}| \leq \frac{\Delta_{xy}}{\tilde{y}^{2}}
$$

### Korrekt kitozesu feladatok

*Elvarasok a megoldando feladattol*:
1. Letezzen megoldas (egzisztencia)
2. csak egy mo legyen (unicitas)
3. a feladat pontos mo-ja folytonosan fuggjon a bemeno adatoktol
pl $Ax = b$ nem ilyen


## Normalt ter

Eddig feltettuk: $a, \tilde{a} \in \mathbb{R}$
Mi van, ha $a,\tilde{a} \in X$ (pl.: $X = \mathbb{R}^{n}$ vagy valami mas halmaz)
kellene ertelmezi a kovetkezoket:
- elemek kulombese -> tfh $X$ vektorter
- analog az abszolut fv-re