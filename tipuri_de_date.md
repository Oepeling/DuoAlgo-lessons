# Tipuri de date

Salut din nou!

În lecția precedentă ți-ai făcut primul proiect funcțional în C++, deci ești pe drumul cel bun! Dar probabil știi că un calculator poate face mai mult decât să afișeze un mesaj pe o fereastră alb-negru. Până la a face [jocuri](https://www.epicgames.com/fortnite/en-US/home), [aplicații de streaming](https://www.netflix.com/) sau alte lucruri mai complicate, va trebui să înveți multe. Așa că hai să începem!

În primul rând, vom discuta despre noțiunea de **variabilă**. Aceasta este un **container**, o "ladă" în care vom stoca, pentru început, un număr sau un caracter.

În cod, **declararea** variabilei arată așa:

![declarare](https://github.com/Kripton2005/DuoAlgoPics/blob/main/pics/declarare.PNG)

De menționat că *majoritatea* rândurilor de cod se vor termina în `;`

Înainte să discutăm despre `int`, vom explica ce reprezintă acum litera `a` pentru calculator. Răspunsul este **nimic**. Calculatorul, așa cum am spus înainte, tot în `0` și `1` gândește, doar atât. Dar, pentru **compilator** (vezi lecția introductivă), lucrurile stau altfel.

Acesta, de acum înainte, oriunde vede doar litera `a` în cod, o va asocia unei **valori** de tip `int`. Cuvântul `int` vine de la **integer**, adică întreg, deci în lada numită de noi `a` se va afla un număr *întreg* (care are anumite limite, dar vom vorbi despre ele mai încolo). Hai să vedem ce se întâmplă dacă încercăm să afișăm variabila `a`:
![aleator](https://github.com/Kripton2005/DuoAlgoPics/blob/main/pics/aleator.PNG)

De menționat că spațiile și rândurile goale nu sunt necesare, dar ajută la citirea mai ușoară a codului. De asemenea, numele variabilelor pot fi orice combinație (de maximum `255` de caractere) de litere, cifre și caracterul `_` (sau `!`, `@`, `#` ori `$`, dar nu fac nume elegante de variabile, deși nu vă oprește nimeni să le folosiți), care începe neapărat cu o literă (recomandăm variabile cât mai scurte, pentru ușurința folosirii, sau variabile cu nume legate de conținutul problemei sau rolul lor în rezolvarea problemei). O ultimă adăugare, pentru zoom-in și zoom-out folosiți tasta `Ctrl` + rotița de la mouse.

Observăm o valoare total necunoscută. Asta se întamplă pentru că nu am **inițializat** variabila, adică nu i-am acordat o valoare în momentul **declarării**. În loc de `int a;`, vom scrie `int a = 37;`. Să vedem ce ne afișează acum:
![hooray](https://github.com/Kripton2005/DuoAlgoPics/blob/main/pics/hooray.PNG)

Yaay! A afișat 37, adică valoarea pe care i-am dat-o variabilei `a`. Puteți să vă jucați cu acea valoare, să o modificați în alte numere *întregi*, dar pentru unele mai mari, va afișa iarăși valori necunoscute. Asta se întâmplă pentru că **tipul de date** `int` permite stocarea în variabile a unor numere de la `-2147483648` la `2147483647` (par aleatoare, dar nu sunt).

De asemenea, dacă `a = 37` apare pe o alta linie decât cea de declarare, adică așa:

![atribuire](https://github.com/Kripton2005/DuoAlgoPics/blob/main/pics/atribuire.PNG)

Numim acest fel de a îi da unei variabile o valoare, ***atribuire***, nu **inițializare**, pentru că valoarea nu este acordată **inițial**, ci este **atribuită**. Putem modifica valoarea unei variabile de oricâte ori vrem în cod.

Revenind la expresia **tip de date**, aceasta reprezintă un fel de a îi transmite calculatorului ce fel de valoare se stochează in variabilă, și câtă **memorie** trebuie să aloce pentru aceasta. Memoria calculatorului este, la fel ca și limba lui, un set de `1`-uri și `0`-uri prin care el reține informația, sau **datele** (tip de <ins>date</ins>).

Înainte să vorbim despre tipurile de date prezente în limbajul `C++`, trebuie să explicăm (la nivel de suprafață) memoria calculatorului. Unitatea de bază a acesteia este **bitul**, o cifră de `0` sau `1`. **Biții** sunt grupați in grupuri numite **octeți** (denumirea în română, sugestivă pentru numărul `8` de biți ce formează un octet) sau **bytes** (pronunțat **baiți**, denumirea în engleză, și cea mai folosită). Un *megabyte* reprezintă `1024` de biți, un *kilobyte* este `1024` de *megabytes*, iar un *gigabyte* este format din `1024` de megabytes (de remarcat că `8` și `1024` sunt puteri ale lui `2`, și anume 2<sup>3</sup> și 2<sup>10</sup>). Ceva este familiar, pentru că probabil ai mai intâlnit această denumire în specificațiile unor dispozitive cum ar fi calculatoare, telefoane "smart" și tablete ("are 128 de *gigabytes* de **stocare** și 8 *gigabytes* de [**RAM**](https://ro.wikipedia.org/wiki/Memorie_cu_acces_aleator)").  

Deoarece sunt doar `1`-uri și `0`-uri, [baza de numerație](https://ro.wikipedia.org/wiki/Baz%C4%83_de_numera%C8%9Bie) `2` este foarte importantă în programare. Numărul `2147483647`, care părea arbitrar, este de fapt **2<sup>31</sup>-1**, deoarece tipul de date `int` folosește 4 bytes de memorie, adică 32 de biți, dintre care unul (primul) pentru **semnul** valorii:
![int](https://github.com/Kripton2005/DuoAlgoPics/blob/main/pics/int.PNG)

Folosind 31 de cifre în baza `2`, putem scrie orice număr între **0** și **2<sup>31</sup>-1**.

Alte tipuri de date sunt:

* `long long`, fratele mai mare al lui `int`, ce folosește 8 bytes și stochează valori întregi între **-2<sup>63</sup>** și **2<sup>63</sup>-1**
* `short int`, fratele mai mic al lui `int`, ce folosește 2 bytes și stochează valori întregi între **-2<sup>15</sup>** și **2<sup>15</sup>-1**
* `float`, vărul lor, ce folosește 4 bytes și stochează valori ***reale*** 
* `double`, fratele mai mare al lui `float`, ce folosește 8 bytes și stochează tot valori ***reale*** (limitele lor sunt ciudate, dar le folosim când avem nevoie de calcule "cu virgulă", și optăm pentru `double` când nu suntem siguri că ne este destul `float`)
* `char`, bunicul lor, ce folosește 1 byte și stochează **caractere** sub formă de valori intregi între **-127** și **127** (vezi [codul ASCII](https://ascii.cl/))
* `bool`, altă rudă (am rămas fără idei), ce folosește 1 byte (**nu** bit) și stochează o valoare de `0` sau `1`
* toate tipurile de date întregi permit și varianta `unsigned` (`unsigned int`, `unsigned long long`, etc.), ce realocă primul bit spre a reprezenta numărul propriu-zis, adică putem stoca valori întregi de 2 ori mai mari, dar doar **pozitive**.

Ca temă, trebuie să te joci cu variabile cu diferite tipuri de date, cu inițializări și atribuiri, și să le afișezi (încearcă și împreună cu mesaje text, spre exemplu `cout << "Mama mea are " << a << " ani!"`).

Acum, la inceput, vom folosi majoritar tipul de date `int`, dar toate sunt utile! Ne revedem în lecția următoare, despre **operații cu variabile**.
