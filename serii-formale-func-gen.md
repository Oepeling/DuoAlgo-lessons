# Berlekamp-Massey + Serii Formale + Funcții generatoare

# Recurențe liniare

$V_{n} = a_{1} V_{n-1} + a_{2} V_{n-2} + ... + a_{k} V_{n-k}$

Generic: $a_0 V_{n} + a_1 V_{n-1} + ... + a_{k} V_{n-k} = 0$

# Berlekamp-Massey

$1, 1, 2, 3, 5, ...$ -> $F_n = F_{n-1} + F_{n_2}$

$1, 2, 3, 4, 6, 12, 31, 88, 253, 722, \cdots$ -> ????

<details><summary>Răspuns</summary> $A_n = 4 A_{n-1} - 3 A_{n-2} - 2 A_{n-3} + 3 A_{n-4}$</details>

# Berlekamp-Massey 

https://mzhang2021.github.io/cp-blog/berlekamp-massey/

http://crypto.stanford.edu/~mironov/cs359/massey.pdf

# Berlekamp-Massey - algorimtul

Știind că avem o recurență liniară de lungime maxim K, algoritmul obține una de lungime minimă având la dispoziție 2 * K termeni.

## Ideea algoritmului 

Calculăm pe parcurs o recurență. Când dă prost încercăm să o adaptăm. 

# Pseudocod

```cpp
C = [1] // recurența originala
B = [1] // vechea recurență
b = 1 // discrepanța veche
last = 0 // ultima modificare
for n in 0..A.length-1 {
    d = A[n] + sum A[n - i] * C[i] // discrepanța
    if d == 0 continue
    Cnew = C - d  / b * B * x^(i-last) // shiftat la dreapta cu i - last
    if C.length * 2 <= n { // se schimbă lungimea
        B = C; b = d; last = i;
    }
    C = Cnew
}

```

# Berlekamp-Massey - trivial

https://infoarena.ro/problema/nkbiti - Câte șiruri de N biți cu maximum K biți de 0 consecutivi există?

https://infoarena.ro/problema/aiafarapalindroame - Câte șiruri de exact N caractere există care nu conțin palindroame >= 3 ?

# Berlekamp-Massey - avansat

https://atcoder.jp/contests/abc198/tasks/abc198_f - Câte cuburi există cu numere întregi pozitive pe fețe și suma exact S?

https://codeforces.com/contest/506/problem/E - Se dă un string. Câte palindroame diferite poți obține adăugând exact N caractere?

# Berlekamp-Massey - matrice

Câte drumuri de lungime K ai într-un graf cu N noduri de la nodul 1 la nodul N?

$A^k \begin{bmatrix}
1 \\
0 \\
\cdots \\
0
\end{bmatrix}
= \begin{bmatrix}
d_{1_k} \\
d_{2_k} \\
\cdots \\
d_{n_k}
\end{bmatrix}$

Pe noi ne interesează doar $B_n A^k \begin{bmatrix}
1 \\
0 \\
\cdots \\
0
\end{bmatrix}$ unde $B_i = \begin{bmatrix} 0\ 0\ \cdots\ 1\ \cdots 0\ 0 \end{bmatrix}$ este matricea care selectează doar un rând din răspuns.

# Berlekamp-Massey - matrice

Știm că matricele sunt soluție pentru polinomul lor caracteristic:
$f_A(x) = x^n + c_1 x^{n-1} + c_2 x^{n-2} + \cdots + c_n x^{0}$

=> $A^n + c_1 A^{n-1} + c_2 A^{n-2} + \cdots + c_n A^{0} = 0$\
=> $A^m + c_1 A^{m-1} + c_2 A^{m-2} + \cdots + c_n A^{m-n} = 0$\
=> $B_n (A^m + c_1 A^{m-1} + c_2 A^{m-2} + \cdots + c_n A^{m-n})$ $\begin{bmatrix}
1 \\
0 \\
\cdots \\
0
\end{bmatrix}) = 0$\
=> $d_{n_m} + c_1 d_{n_{m-1}} + c_2 d_{n_{m-2}} + \cdots + c_n d_{n_{m-n}} = 0$ - Recurența liniară

# Berlekamp-Massey - matrice

Drumuri de lungime K de la o sursă la o destinație într-o matrice. Complexitate $O(N * K + N * M)$

https://infoarena.ro/problema/hprob - Ai 4 obiecte și la fiecare pas ai diferite probabilități să le permuți

---

# Serii Formale

## O generalizare abstractă a polinomului $A = 1 + X + X^2 + ...$

Are operațiile obișnuite polinoamelor:

* Adunare $A+B = (A_0 + B_0) + (A_1 + B_1) X + (A_2 + B_2) X^2 + \cdots$
* Inmulțire: $A B = (A_0 B_0) + (A_1 B_0 + A_0 B_1) X + \cdots$
* Inmulțire cu scalar: $k A = k A_0 + k A_1 X + \cdots$
* Ridicare la putere întreagă
* Compunere (doar când B are termenul liber 0):\
$A(B(X)) = A_0 + A_1 B^1 + A_2 B^2 + \cdots$

# Serii Formale

* Inversa: $A^{-1}$ e seria formala care are proprietatea ca $A A^{-1} = 1$.
* Derivata: $A' = A_1 + 2 A_2 X + 3 A_3 X^2 + \cdots$
* Derivata de ordin k: $A^{(k)} = \frac{k!}{0!} A_k + \cdots + \frac{n!}{(n-k)!} A_n X^{n-k} + \cdots$ 
* $\sqrt{}$ - va urma
* $ln(A)$ - va urma
* $e^A$ - va urma 
* $A \equiv A_0 + A_1 X + \cdots + A_{n-1} X^{n-1} (mod\ X^n)$

# Serii Formale - inversa

$(1-X)^{-1} = 1 + X + X^2 + ...$

Incercăm să dublăm mereu numărul de termeni pe care îi cunoaștem

$B_i \equiv A^{-1}\ (mod\ X^i)$

$B_0 = A_0^{-1}$ 

# Serii Formale - inversa

Știm că $B_k \equiv A^{-1}\ (mod\ X^k)$, vrem $B_{2k}$

$B_{2 k} = B_k + X^{k}C$

$A(B_k + X^k C) \equiv 1\ (mod\ X^{2k})$
$A B_k \equiv 1 + X^{k}D\ (mod\ X^{2k})$

$1 + X^{k}D + X^{k}AC \equiv 1\ (mod\ X^{2k})$ => $X^{k}(D + AC) \equiv 0\ (mod\ X^{2k})$

=> $D \equiv -AC\ (mod X^K)$ => $C \equiv -B_k D\ (mod X^k)$

=> $x^k C \equiv -x^k B_k D \equiv B_k (-x^k D) \equiv B_k (1 - A B_k)\ (mod\ X^{2k})$

=> $B_{2k} \equiv B_k (2 - A B_k)\ (mod\ X^{2k})$

# Funcții generatoare

Fie A un șir generat de o recurență liniară

$A_n + A_{n-1} c_{1} + A_{n-2} c_{2} + \cdots = 0$ pentru $n \ge n_0$

$G(A; X) = A_0 + A_1 X + A_2 X^2 + \cdots + A_n X^n + \cdots$
$C = c_0(=1) + c_1 X + c_2 X^2 + \cdots + c_n X^n$

$G(A; X) C = r_0 + r_1 X + \cdots + r_{n_0-1} X^{n_0-1} = R$

$G(A; X) \equiv R C^{-1}\ (mod X^{k})$

# Funcții generatoare - exemplu

https://codeforces.com/gym/102268/problem/G - după mai multe hopuri problema cere partiții(N + 1) - 1

$\sum\limits_{k=-\inf}^{inf} (-1)^k * P_{n-\frac{k(3k - 1)}{2}} = 0$ (Teorema numerelor pentagonale)

R = 1 aici

# Funcții generatoare - avansat

https://codeforces.com/gym/102268/problem/E - [Tunelul groazei](https://infoarena.ro/problema/tunel) doar că se cere răspunsul modulo $998 244 353$

## Cazul 1

Calculăm $P_k =$ probabilitatea să fim în nodul destinație după exact k pași\
Atunci ne dorim: $P_1 + 2 P_2 + 3 P_3 + \cdots + n P_n + \cdots = P'(1)$

P'(1) se calculează după regulile de derivare: \
$P'(1) = (R/C)'(1) = \frac{R'(1)C(1) - R(1)C'(1)}{C(1)^2}$

## Cazul 2

Calculăm $PP_k = P_k k$\
Atunci ne dorim $PP_1 + PP_2 + \cdots + PP_n + \cdots = PP(1)$

# Expansiunea Taylor

$F(X) = F(a) + \frac{F'(a)}{1!}(X - a) + \frac{F''(a)}{2!}(X - a)^2 + \cdots + \frac{F^{(k)}(a)}{k!}(X-a)^k+\cdots$

# Metoda lui Newton - inversa

Vrem o funcție care să aibă rădăcina pe seria formală căutată.\
Ex. la inversa lui $X^{-1} = A$ => $F(X) = X^{-1} - A$

Folosim Seria Taylor a acestei funcții și observăm că de la al 3-lea termen încolo lucrurile se anulează modulo $X^{2k}$

$F(B_{2k}) \equiv F(B_k) + F'(B_k)(B_{2k} - B_k) + (B_{2k}-B_k)^2 ceva\ (mod\ X^{2k})$\
$B_{2k} - B_k \equiv 0\ (mod\ X^k)$

$\implies B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$

La inversă:\
$B_{2k} \equiv B_k - \frac{B_k^{-1} - A}{\frac{-1}{B_k^{-2}}} \equiv B_k - B_k(B_k A - 1) \equiv B_k (2 - B_k A)\ (mod\ X^{2k})$

# Logaritm

Greu de vizualizat, ne folosim de expansiunea Taylor/ alte proprietăți.

## Generic

$(ln(P(x)))' = \frac{P'(x)}{P(x)}$ - trebuie integrat ulterior

## Caz special

$ln(1 - P) = -P - \frac{P^2}{2} - \frac{P^3}{3} - \cdots - \frac{P^n}{n} - \cdots$

# Exponențială

$ln X = A$

$F(X) = ln X - A$ => $F'(X) = 1 / X

$B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$\
$B_{2k} \equiv B_k - B_k * (ln B_k - A) \equiv B_k(1 - ln B_k + A)\ (mod\ X^{2k})$

# Radical

$X^2 = A$

$F(X) = X^2 - A$ => $F'(X) = 2X$

$B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$
$B_{2k} \equiv B_k - \frac{B_k^2 - A}{2B_k} \equiv B_k - \frac{B_k}{2} + \frac{A}{2B_k}\ (mod\ X^{2k}) \equiv \frac{B_k + \frac{A}{B_k}}{2}\ (mod\ X^{2k})$

---

# Rucsac Generic

https://www.codechef.com/JUNE20A/problems/PPARTS - Avem N tipuri de obiecte, fiecare tip are o cantitate și o valoare. În câte feluri putem obține suma valorilor $1, 2, ..., Q(\le 150.000)$?

# Rucsac generic

## Avem maxim cantitate 1 din fiecare obiect

$S = (1 + X^{V_1})(1 + X^{V_2})\cdots(1+X^{V_{N}})$

# Rucsac generic

$ln(S) = ln(1 + X^{V_1}) + ln(1 + X^{V_2}) + \cdots + ln(1+X^{V_{N}})$

# Rucsac generic

## Dacă avem mai multe obiecte?

$S = (1 + X^{V_1} + X^{2V_1} + ... + X^{C_1 V_1})\cdots(1 + X^{V_{N}} + X^{2V_{N}} + \cdots + X^{C_{N} V_{N}})$

$S = \frac{1 - X^{(C_1 + 1)V_1}}{1 - X^{V_1}} \frac{1 - X^{(C_2 + 1)V_2}}{1 - X^{V_2}} \cdots \frac{1 - X^{(C_N + 1)V_N}}{1 - X^{V_N}}$

# Recurențe non-liniare

https://codeforces.com/problemset/problem/438/E - Câți arbori binari există cu valori în noduri dintr-o mulțime $A = \{a_0, a_1, \cdots, a_n\}$ și suma totală S?

$dp[0] = 1$

$dp[S] = \sum\limits_{a \in A}\sum\limits_{i = 0}^{S - a}dp[i] dp[S - a - i]$

Scris ca funcție generatoare: $dp = 1 + dp^2 A$ unde $A = (X^{A_0} + X^{A_1} + \cdots + X^{A_n})$

# Recurențe non-liniare

## Soluție 1: Rezolvat ecuația de gradul 2

$Adp^2 - dp + 1 = 0$\
$\Delta = 1 - 4A$

$dp = \frac{1 \pm\sqrt{1 - 4A}}{2A}$\
Dar 2A nu e inversabilă, așa că amplificăm cu $1 \mp \sqrt{1 - 4A}$

$dp = \frac{1 - 1 + 4A}{2A(1\pm\sqrt{1 - 4A})} = \frac{4A}{2A(1\pm\sqrt{1 - 4A})} = \frac{2}{1\pm\sqrt{1 - 4A}}$.\
Alegem semnul convenabil jos ca să avem coeficientul liber diferit de 0.

## Newton: $F(X) = A X^2 - X + 1$

$F'(X) = 2AX - 1$

$B_{2k} = B_k - (B_k^2 * A - B_k + 1) / (B_k * A - 1)$

# Exemple cod

e-maxx: https://github.com/e-maxx-eng/e-maxx-eng-aux/blob/master/src/polynomial.cpp
