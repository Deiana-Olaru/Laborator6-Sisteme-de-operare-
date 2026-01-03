Memory Mapped Counter (Windows)
Acest proiect demonstreaza comunicarea intre doua procese pe Windows folosind:

memorie partajata (CreateFileMappingA + MapViewOfFile)
mutex numit (CreateMutexA)
sincronizare intre procese pentru acces sigur la o zona comuna de memorie
Primul proces creeaza memoria si mutex-ul, apoi lanseaza automat al doilea proces. Cele doua procese citesc si actualizeaza acelasi numar (de la 0 la 1000), "aruncand cu banul" cat timp cade 2.

Cum rulezi
Compilezi proiectul in Visual Studio.
Rulezi o singura data executabilul (F5 sau CTRL+F5).
Primul proces va deschide o fereastra.
Apoi deschide automat a doua fereastra (al doilea proces).
Cele doua procese vor lucra impreuna pe memoria partajata.
Nu sunt necesare argumente in linia de comanda.

Ce face programul
primul proces initializeaza valoarea 0
al doilea proces se conecteaza la aceeasi memorie
fiecare proces:
obtine mutex-ul
citeste valoarea curenta
arunca cu banul (random 1 sau 2)
cat timp iese 2, incrementeaza valoarea
elibereaza mutex-ul
procesarea se termina la 1000
Observatii
mutex-ul este necesar pentru a preveni accesul simultan la memoria partajata
memoria este comuna pentru ambele procese si se afla in RAM
codul a fost simplificat pentru a nu necesita argumente de rulare
Fisiere
laborator6_windows.cpp – codul sursa principal
