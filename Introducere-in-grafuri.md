# Introducere in grafuri
În matematică și mai specific în [teoria grafurilor](https://ro.wikipedia.org/wiki/Teoria_grafurilor), un **graf** este o structură care corespunde unui grup de obiecte, în care unele perechi de obiecte sunt într-un anumit sens "legate" reciproc. In termeni simpi, reprezinta de fapt o multime de puncte (noduri) conectate intre ele prin linii (muchii).


# Mica istorie

Grafurile pot fi  gasite inca din anul 1735, atunci cand matematicianul Leonhard Euler a rezolvat [problema podurilor din Königsberg](https://ro.wikipedia.org/wiki/Problema_podurilor_din_K%C3%B6nigsberg). Problema podurilor din Königsberg era un puzzle vechi care incerca sa verifice posibilitatea gasirii unui drum peste fiecare din cele 7 poduri peste un rau, dar care nu trece peste acelasi pod de doua ori. Euler a sustinut faptul ca nu exista un asemenea drum. Demonstratia lui a inclus referinte la aranjarea fizica a podurilor, dar, in esenta, acesta a demonstrat prima teorema din teoria grafurilor. 

 

![Harta podurilor](https://upload.wikimedia.org/wikipedia/commons/5/5d/Konigsberg_bridges.png)
![Simplificat](https://upload.wikimedia.org/wikipedia/commons/thumb/9/91/7_bridges.svg/179px-7_bridges.svg.png)
![Translatarea problemei intr-un graf](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/K%C3%B6nigsberg_graph.svg/180px-K%C3%B6nigsberg_graph.svg.png)


Grafurile cu proprietatea ca pot fi traversate sub aceste conditii au fost numite **grafuri euleriene.**

----------
# Utilizare

Ca sa intelegem cum se cuvine un anume lucru, trebuie intai sa intelegem la ce ne-ar folosi in viata de zi cu zi. De aceea, voi prezenta niste exemple la care ne ajuta grafurile (in afara de cel de mai sus).


## Exemplul 1

Hai sa consideram harta Metrorex din Bucuresti:

![Posibil outdated, intentia conteaza](https://harta-metrou.com/im/harta-metrorex.png)


Presupunem ca vrem sa luam metroul de la **Aviatorilor** pana la **Dristor**. 


- Putem lua, de exemplu, M2 pana la Piata Unirii, si acolo sa schimbam cu M1 sau M3. 
- De asemenea, putem lua M2 pana la Piata Victoriei, unde schimbam cu M1.

A doua varianta pare mai scurta decat prima, dar nu putem spune sigur  - *poate ratam metroul*. Dar putem, cu o anumita masura, sa estimam care este cea mai buna ruta intre doua statii uitandu-ne doar la aceasta harta. 


Dar, daca ne uitam pe harta metrourilor din Paris, nu mai e chiar asa simplu:

![Note: asta nici macar nu este harta completa a metroului din Paris](https://i0.wp.com/transitmap.net/wp-content/uploads/2015/11/tumblr_ny6vrpXh3Y1umx7dwo1_1280-1024x756.png?ssl=1)


Acest exemplu ne ajuta sa intelegem faptul ca algoritmii (si, in cazul de fata, grafurile) ne ajuta foarte mult atunci cand avem *retele* complexe, pe care nu le putem “deslusi” cu ochiul liber. Mai exact, harta aceasta poate fi translatata intr-un graf, pe care aplicam un algoritm de tip *Breadth-First-Search* sau *Algoritmul lui Dijkstra*. Voila, avem acum cel mai scurt drum de acasa la oricare statie de metrou 🙂 . 

Transformand harta noastra intr-un graf, nodurile vor reprezenta statiile, iar muchiile vor reprezenta tunelurile prin care trece metroul si care conecteaza statiile intre ele.






Bibliografie:

- https://en.wikipedia.org/wiki/Graph_theory
- https://www.britannica.com/topic/graph-theory

