# Introducere în programare

Salut!  
Tocmai ai făcut primul pas spre învățarea limbajului de programare **C++**

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img1.jpg" alt="User and computer" width="200" height="100" align="right" title="Tu și prietenul tău">

În continuare vei afla ce înseamnă un cod, ce este un algoritm, cum "comunică" omul cu calculatorul, și o introducere în **C++**

## Codul

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img2.png" alt="Code" width="200" height="100" align="right" title="Cod">

Un cod este, în esență, un sistem de transmitere a informației. Fie că este:
* [codul Morse](https://ro.wikipedia.org/wiki/Codul_Morse), în care literele sunt transformate în  "puncte" și "linii"
* [alfabetul Braille](https://ro.wikipedia.org/wiki/Alfabetul_Braille), unde caracterele sunt reprezentate sub formă de dreptunghiuri $3$ x $2$ (cu 3 linii și 2 coloane de puncte)

sau codul despre care urmează să înveți, toate fac același lucru, și anume că ne ajută să comunicăm între noi (sau cu mașinării), fiecare având beneficiul lui (codul Morse poate fi [transmis prin lumină](https://www.youtube.com/shorts/COCV8bZ4bjo?&ab_channel=GD%27sLatestHighlights), Braille este folosit de nevăzători, iar codul scris de voi îi va spune calculatorului să facă anumite instrucțiuni).

## Algoritmul

Algoritmul reprezintă un set de operații în urma cărora obținem un produs finit sau îndeplinim un scop. În continuare vom înșira niște exemple de algoritmi din viața de zi cu zi, dar sunteți încurajați să vă gândiți la ele pe cont propriu:

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img3.png" alt="Gordon" width="600" height="300" align="right" title="Gordon Ramsay, pregătit de algoritm">


<details><summary>Exemplu 1 (cel din poză)</summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Rețetă de gătit 👨‍🍳</b></details>
<details><summary>Exemplu 2</summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Program unei zi 📅</b></details>
<details><summary>Exemplu 3</summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Îmbrăcarea 👚</b></details>

În programare, algoritmul are 3 componente:
* datele de **intrare**
* algoritmul propriu-zis (setul de instrucțiuni)
* datele de **ieșire** (produsul finit)

Conceptele de **intrare** și **ieșire** sunt esențiale în programarea algoritmică.
<details><summary>Analogie</summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Datele de intrare = aluat, sos de roșii, mozzarella<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Algoritmul propriu-zis = punerea ingredientelor pe aluat + gătirea în cuptor<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Datele de ieșire = o pizza Margherita delicioasă 😋</details>

## Comunicarea om-calculator

Calculatorul este o invenție umană ce ne permite să facem operații la viteze inumane. (aproximativ 100 de milioane de operații ***pe secundă***)

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img4.png" alt="Cycle" title="Ciclul utilizator-calculator" width="200" height="120" align="right">

Așa cum bine știți, când folosim calculatorul avem nevoie de un mouse și de o tastatură, numite dispozitive periferice de **intrare**, pentru că permit informației să **intre** de la utilizator în calculator.\
De cealaltă parte, monitorul este un dispozitiv periferic de **ieșire**, deoarece informația (adică pixelii pe care îi numim imagine) sunt transmiși de la calculator la utilizator.

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img5.png" alt="Compiler" title="Rolul de traducător al compilatorului" height="150" width="300" align="left">

În programare, comunicarea funcționează altfel, dar pe același principiu. Calculatorul vorbește în $0$-uri și $1$-uri, iar noi în litere și cifre. Așa că ceva trebuie să facă traducerea din limbajul nostru (**C++**) în **codul masina** ($0$ și $1$). Acela este ***compilatorul***, care funcționează drept traducător dintr-o limbă în alta, ca [Google Translate](https://translate.google.com/) când ești într-o țară străină și nu știi să chemi un taxi.

## Introducere în C++

Pentru început, recomandăm [CodeBlocks](http://www.codeblocks.org/downloads/binaries/) (link direct de descărcare pentru Windows) drept **IDE** (**I**ntegrated **D**evelopment **E**nvironment), adică mediu pentru dezvoltarea de aplicații în C++.

Odată instalat, creați un proiect mergând prin <code style="color:#c7254e;">Create a new project --> Console application --> C++</code>, selectați folderul în care doriți să vă scrieți programele, iar apoi click pe **Finish**. În panoul din stânga, dați click pe `Sources --> main.cpp`. Ar trebui să vă apară o pagină asemănătoare cu aceasta:

<img src="https://github.com/Oepeling/DuoAlgo-images/blob/main/intro-in-programare/img6.png" alt="start" title="Primul proiect" height="450" width="900">

Dacă ați ajuns aici, felicitări! Apăsând pe tasta **F9**, sau pe iconița aceasta ![image](https://user-images.githubusercontent.com/63238264/176329368-a742a9f4-00d0-4a1a-bc76-67fc0271a83b.png) din tavanul aplicației CodeBlocks, vi se va deschide o fereastră neagră cu scris alb numită **consolă**, care va afișa pe prima linie mesajul **Hello world!** . Ca fapt divers, acest terminal este mijlocul de comunicare cel mai direct al omului cu calculatorul. Dacă apăsați **Enter** sau închideți fereastra, programul se va opri, dar îl puteți reporni oricând. Deoarece programul **rulează** (termen din vocabularul programatorilor) cât timp terminalul este deschis, modificările pe care le faceți la codul în C++ nu vor fi luate în considerare până la următoarea pornire a programului. 

Dar codul este încă străin. Ce înseamnă lucrurile acelea? Ei bine, vom explica linie cu linie. Prima, `#include iostream`, include o **bibliotecă**, adică o colecție de **funcții** din C++ ce servesc anumitor roluri. Specific, **iostream** vine de la **input-output stream**, adică un **curent** (în traducere liberă) de date **de intrare** și **de ieșire**. 

Fără prima linie, comanda `cout` de pe linia 7 nu ar funcționa, ea făcând parte din biblioteca **iostream**. Cout este un stream (curent) **standard** de ieșire, adică comunică cu terminalul, deci ce afișează, afișează pe el. Sintaxa (felul de scriere) specifică lui este `cout<<`, mesajul `Hello world!` se scrie între ghilimele (ca exercițiu, puteți să-l modificați în orice alt mesaj, dar nu uitați, dacă aveți terminalul deschis, trebuie închis și redeschis înainte să apară noul mesaj), iar `endl` (end-line) reprezintă caracterul `Enter`, care poate fi înlocuit cu `'\n'` (și recomandăm înlocuirea, din motive nesemnificative pe care le veți afla mai târziu).

Fratele lui `cout` este `cin`, care în loc să facă afișarea standard, face **citirea** standard, numită și **"de la tastatură"**, pentru că numerele sau literele băgate în terminal sunt scrise prin intermediul tastaturii, odată ce terminalul devine deschis. Utilizarea lui `cin` va fi prezentată într-o lecție viitoare. Ca să țineți minte mai ușor, litera `c` vine de la cuvânul **consolă**, iar restul cuvântului este **in** sau **out**, adică **intrare** sau **ieșire**.

**Funcția** `main` reprezintă corpul programului, la care se pot adăuga funcții auxiliare (ca lui [Mr. Potato Head](https://disney.fandom.com/wiki/Mr._Potato_Head?file=Potato_head_3.jpg) din Toy Story). Liniile `return 0;` și `using namespace std;` nu sunt de interes momentan.

Singurul cuvânt rămas neexplicat este `int`, care va apărea în lecția următoare, despre **tipuri de date**.
