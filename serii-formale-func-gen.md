# Berlekamp-Massey + Serii Formale + Functii generatoare

# Recurente liniare

$V_{n} = a_{1} V_{n-1} + a_{2} V_{n-2} + ... + a_{k} V_{n-k}$


Generic: $a_0 V_{n} + a_1 V_n{n-1} + ... + a_{k} V_{n-K} = 0$



# Berlekamp-Massey

$1, 1, 2, 3, 5, ...$ -> $F_n = F_{n-1} + F_{n_2}$

$1, 2, 3, 4, 6, 12, 31, 88, 253, 722, ...$ -> ????

<!-- A_n = 4 A_{n-1} - 3 A_{n_2} - 2 A_{n-3} + 3 A_{n-4}-->

 

# Berlekamp-Massey 

https://mzhang2021.github.io/cp-blog/berlekamp-massey/

http://crypto.stanford.edu/~mironov/cs359/massey.pdf



# Berlemapf-Massey - Algorimtul

Stiind ca avem o recurenta liniara de lungime maxim K, algoritmul obtine una de lungime minima avand la dispozitie 2 * K termeni.

## Ideea algoriitmului? 

Calculam pe parcurs o recurenta. Cand da prost incercam sa o adaptam. 



# Pseudocod

```
C = [1] // recurenta originala
B = [1] // vechea recurenta
b = 1 // discrepanta veche
last = 0 // ultima modificare
for n in 0..A.length-1 {
    d = A[n] + sum A[n - i] * C[i] // discrepenta
    if d == 0 continue
    Cnew = C - d  / b * B * x^(i-last) // shiftat la dreapta cu i - last
    if C.length * 2 <= n { // se schimba lungimea
        B = C; b = d; last = i;
    }
    C = Cnew
}

```

 

# Berlekamp-Massey - trivial

https://infoarena.ro/problema/nkbiti - Cate siruri de N biti cu maximum K biti de 0 consecutivi exista?

https://infoarena.ro/problema/aiafarapalindroame - Cate siruri de exact N caractere exista care nu contin palindroame >= 3 ?

 

# Berlekamp-Massey - avansat

https://atcoder.jp/contests/abc198/tasks/abc198_f - Cate cuburi exista cu numere intregi pozitive pe fete si suma exact S?

https://codeforces.com/contest/506/problem/E - Se da un string. Cate palindroame diferite poti obtine adaugand exact N caractere?



# Berlekamp-Massey - matrici

Cate drumuri de lungime K ai intr-un graf cu N noduri de la nodul 1 la nodul N?

$A^k \begin{bmatrix}
1 \\
0 \\
... \\
0
\end{bmatrix}
= \begin{bmatrix}
d_{1_k} \\
d_{2_k} \\
... \\
d_{n_k}
\end{bmatrix}$

Pe noi ne intereseaza doar $B_n A^k \begin{bmatrix}
1 \\
0 \\
... \\
0
\end{bmatrix}$ unde $B_i = \begin{bmatrix} 0\ 0\ ...\ 1\ ... 0\ 0 \end{bmatrix}$ este matricea care selecteaza doar un rand din raspuns.



# Berlekamp-Massey - matrici

Stim ca matricele sunt solutie pentru polinomul lor caracteristic:
$f_A(x) = x^n + c_1 x^{n-1} + c_2 x^{n-2} + ... + c_n x^{0}$

=> $A^n + c_1 A^{n-1} + c_2 A^{n-2} + ... + c_n A^{0} = 0$
=> $A^m + c_1 A^{m-1} + c_2 A^{m-2} + ... + c_n A^{m-n} = 0$
=> $B_n (A^m + c_1 A^{m-1} + c_2 A^{m-2} + ... + c_n A^{m-n}) \begin{bmatrix}
1 \\
0 \\
... \\
0
\end{bmatrix}) = 0$
=> $d_{n_m} + c_1 d_{n_{m-1}} + c_2 d_{n_{m-2}} + ... + c_n d_{n_{m-n}} = 0$ - Recurenta liniara

 

# Berlekamp-Massey - matrici

Drumuri de lungime K de la o sursa la o destinatie intr-o matrice. Complexitate $O(N * K + N * M)$

https://infoarena.ro/problema/hprob - Ai 4 obiecte si la fiecare pas ai diferite probabilitati sa le permuti



# Serii Formale

## O generalizare abstracta a polinomului $A = 1 + X + X^2 + ...$

Are operatiile obisnuite polinoamelor:

* Adunare $A+B = (A_0 + B_0) + (A_1 + B_1) X + (A_2 + B_2) X^2 + ...$
* Inmultire: $A B = (A_0 B_0) + (A_1 B_0 + A_0 B_1) X + ...$
* Inmultire cu scalar: $k A = k A_0 + k A_1 X + ...$
* Ridicare la putere intreaga
* Compunere (doar cand B are termenul liber 0): 
$A(B(X)) = A_0 + A_1 B^1 + A_2 B^2 + ...$



# Serii Formale

* Inversa: $A^{-1}$ e seria formala care are proprietatea ca $A A^{-1} = 1$.
* Derivata: $A' = A_1 + 2 A_2 X + 3 A_3 X^2 + ...$
* Derivata k: $A^{(k)} = \frac{k!}{0!} A_k + ... + \frac{n!}{(n-k)!} A_n X^{n-k} + ...$ 
* $\sqrt{}$ - va urma
* $ln(A)$ - va urma
* $e^A$ - va urma 
* $A \equiv A_0 + A_1 X + ... + A_{n-1} X^{n-1} (mod\ X^n)$



# Serii Formale - inversa

$(1-X)^{-1} = 1 + X + X^2 + ...$

Incercam sa dublam mereu numarul de termeni pe care ii cunoastem

$B_i \equiv A^{-1}\ (mod\ X^i)$

$B_0 = A_0^{-1}$ 



# Serii Formale - inversa

Stim ca $B_k \equiv A^{-1}\ (mod\ X^k)$, vrem $B_{2k}$

$B_{2 k} = B_k + X^{k}C$

$A(B_k + X^k C) \equiv 1\ (mod\ X^{2k})$
$A B_k \equiv 1 + X^{k}D\ (mod\ X^{2k})$

$1 + X^{k}D + X^{k}AC \equiv 1\ (mod\ X^{2k})$ => $X^{k}(D + AC) \equiv 0\ (mod\ X^{2k})$

=> $D \equiv -AC\ (mod X^K)$ => $C \equiv -B_k D\ (mod X^k)$

=> $x^k C \equiv -x^k B_k D \equiv B_k (-x^k D) \equiv B_k (1 - A B_k)\ (mod\ X^{2k})$

=> $B_{2k} \equiv B_k (2 - A B_k)\ (mod\ X^{2k})$



# Functii generatoare

Fie A un sir generat de o recurenta liniara

$A_n + A_{n-1} c_{1} + A_{n-2} c_{2} + ... = 0$ pentru $n \ge n_0$

$G(A; X) = A_0 + A_1 X + A_2 X^2 + ... + A_n X^n + ...$
$C = c_0(=1) + c_1 X + c_2 X^2 + ... + c_n X^n$

$G(A; X) C = r_0 + r_1 X + .... + r_{n_0-1} X^{n_0-1} = R$

$G(A; X) \equiv R C^{-1}\ (mod X^{k})$



# Functii generatoare - exemplu

https://codeforces.com/gym/102268/problem/G - dupa mai multe hopuri problema cere partitii(N + 1) - 1

$\sum\limits_{k=-\inf}^{inf} (-1)^k * P_{n-\frac{k(3k - 1)}{2}} = 0$ (Teorema numerelor pentagonale)

R = 1 aici



# Functii generatoare - avansat

https://codeforces.com/gym/102268/problem/E - Tunelul groazei doar ca se cere raspunsul modulo $998 244 353$

## Cazul 1

Calculam $P_k =$ probabilitatea sa fim in nodul destinatie dupa exact k pasi
Atunci ne dorim: $P_1 + 2 P_2 + 3 P_3 + ... + n P_n + ... = P'(1)$

P'(1) se calculeaza dupa regulile de derivare: \
$P'(1) = (R/C)'(1) = \frac{R'(1)C(1) - R(1)C'(1)}{C(1)^2}$

## Cazul 2

Calculam $PP_k = P_k k$ 
Atunci ne dorim $PP_1 + PP_2 + ... + PP_n + ... = PP(1)$



# Expansiunea Taylor

$F(X) = F(a) + \frac{F'(a)}{1!}(X - a) + \frac{F''(a)}{2!}(X - a)^2 + ... + \frac{F^{(k)}(a)}{k!}(X-a)^k+...$



# Metoda lui Newton - inversa


Vrem o functie care sa aiba radacina pe seria formala cautata. 
Ex la inversa lui $X^{-1} = A$ => $F(X) = X^{-1} - A$

Folosim seria taylor acestei functii si observam ca de la al 3-lea termen incolo lucrurile se anuleaza modulo $X^{2k}$

$F(B_{2k}) \equiv F(B_k) + F'(B_k)(B_{2k} - B_k) + (B_{2k}-B_k)^2 ceva\ (mod\ X^{2k})$ \
$B_{2k} - B_k \equiv 0\ (mod\ X^k)$

$\implies B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$

La inversa:
$B_{2k} \equiv B_k - \frac{B_k^{-1} - A}{\frac{-1}{B_k^{-2}}} \equiv B_k - B_k(B_k A - 1) \equiv B_k (2 - B_k A)\ (mod\ X^{2k})$



# Logaritm

Greu de vizualizat, ne folosim de expansiunea taylor/ alte proprietati.

## Generic

$(ln(P(x)))' = \frac{P'(x)}{P(x)}$ - trebuie integrat ulterior

## Caz special

$ln(1 - P) = -P - \frac{P^2}{2} - \frac{P^3}{3} - ... - \frac{P^n}{n} - ...$

 

# Exponentiala

$ln X = A$

$F(X) = ln X - A$ => $F'(X) = 1 / X

$B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$
$B_{2k} \equiv B_k - B_k * (ln B_k - A) \equiv B_k(1 - ln B_k + A)\ (mod\ X^{2k})$



# Radical

$X^2 = A$

$F(X) = X^2 - A$ => $F'(X) = 2X$

$B_{2k} \equiv B_k - \frac{F(B_k)}{F'(B_k)}\ (mod\ X^{2k})$
$B_{2k} \equiv B_k - \frac{B_k^2 - A}{2B_k} \equiv B_k - \frac{B_k}{2} + \frac{A}{2B_k}\ (mod\ X^{2k}) \equiv \frac{B_k + \frac{A}{B_k}}{2}\ (mod\ X^{2k})$



# Rucsac Generic

https://www.codechef.com/JUNE20A/problems/PPARTS - Avem N tipuri de obiecte, fiecare tip are o cantitate si o valoare. In cate feluri putem obtine suma valorilor $1, 2, ..., Q(\le 150.000)$?



# Rucsac generic

## Avem maxim cantitate 1 din fiecare obiect

$S = (1 + X^{V_1})(1 + X^{V_2})...(1+X^{V_{N}})$



# Rucsac generic

$ln(S) = ln(1 + X^{V_1}) + ln(1 + X^{V_2}) + ... + ln(1+X^{V_{N}})$

 

# Rucsac generic

## Daca avem mai multe obiecte?

$S = (1 + X^{V_1} + X^{2V_1} + ... + X^{C_1 V_1})...(1 + X^{V_{N}} + X^{2V_{N}} + ... + X^{C_{N} V_{N}})$

$S = \frac{1 - X^{(C_1 + 1)V_1}}{1 - X^{V_1}} \frac{1 - X^{(C_2 + 1)V_2}}{1 - X^{V_2}} ... \frac{1 - X^{(C_N + 1)V_N}}{1 - X^{V_N}}$



# Recurente non-liniare

https://codeforces.com/problemset/problem/438/E - Cati arbori binari exista cu valori in noduri dintr-o multime $A = \{A0, A1, ..., An\}$ si suma totala S

$dp[0] = 1$

$dp[S] = \sum\limits_{a \in A}\sum\limits_{i = 0}^{S - a}dp[i] dp[S - a - i]$

Scris ca functie generatoare: $dp = 1 + dp^2 A$ unde $A = (X^{A_0} + X^{A_1} + X^{A_n})$



# Recurente non-liniare

## Solutie 1: Rezolvat ecuatia de graudul 2

$Adp^2 - dp + 1 = 0$
$\Delta = 1 - 4A$

$dp = \frac{1 \pm\sqrt{1 - 4A}}{2A}$ Dar 2A nu e inversabila, amplificam cu $1 \mp \sqrt{1 - 4A}$

$dp = \frac{1 - 1 + 4A}{2A(1\pm\sqrt{1 - 4A})} = \frac{4A}{2A(1\pm\sqrt{1 - 4A})} = \frac{2}{1\pm\sqrt{1 - 4A}}$. Alegem semnul convenabil jos sa avem coeficientul liber diferit de 0.

## Newton: $F(X) = A X^2 - X + 1$

$F'(X) = 2AX - 1$

$B_{2k} = B_k - (B_k^2 * A - B_k + 1) / (B_k * A - 1)$

 

# Exemple cod

e-maxxx: https://github.com/e-maxx-eng/e-maxx-eng-aux/blob/master/src/polynomial.cpp
