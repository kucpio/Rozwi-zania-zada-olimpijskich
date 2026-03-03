# Zadania z Olimpiady Informatycznej i Potyczek Algorytmicznych

Repozytorium zawiera rozwiązania wybranych zadań z:
- Olimpiady Informatycznej (OI)
- Potyczek Algorytmicznych

Kod ma charakter konkursowy:
- pisany pod wydajność,
- bez komentarzy,
- zoptymalizowany pod limity czasowe i pamięciowe.

Pelne tresci zadan dostepne sa w serwisie Szkopul:
https://szkopul.edu.pl

------------------------------------------------------------

SRODOWISKO

Jezyk: C++17

Przykladowa kompilacja:

g++ -std=c++17 -O2 solution.cpp -o sol
./sol < input.txt

------------------------------------------------------------

OPIS ZADAN I ROZWIAZAN

------------------------------------------------------------

1. Rozklad Fibonacciego

Opis problemu:
Dana jest liczba k. W jednym kroku mozna przejsc do wartosci |k - F|,
gdzie F jest dowolna liczba Fibonacciego. Nalezy wyznaczyc minimalna
liczbe krokow potrzebnych do sprowadzenia k do zera.

Idea rozwiazania:
Najpierw generowane sa liczby Fibonacciego w zakresie typu long long.
W kazdym kroku wybierana jest taka liczba F, ktora minimalizuje
wartosc |k - F|. Proces powtarzany jest do momentu uzyskania zera.
Strategia ma charakter zachlanny (greedy).

Zastosowane techniki:
- preprocessing liczb Fibonacciego
- algorytm zachlanny
- operacje na long long

------------------------------------------------------------

2. Szeregowanie czynnosci

Opis problemu:
Dane sa pary liczb (a, b). Nalezy posortowac je wedlug wartosci
ilorazu a/b. W przypadku remisu decyduje kolejnosc wejsciowa.

Idea rozwiazania:
Zamiast wykonywac dzielenie (co moze powodowac bledy precyzji),
porownujemy ulamki przez mnozenie krzyzowe:
a1/b1 < a2/b2 wtedy i tylko wtedy, gdy a1 * b2 < a2 * b1.
Sortowanie realizowane jest przez std::sort z wlasnym komparatorem.

Zastosowane techniki:
- sortowanie O(n log n)
- porownywanie ulamkow przez mnozenie krzyzowe
- wlasny comparator

------------------------------------------------------------

3. Tetris Attack

Opis problemu:
Dany jest ciag dlugosci 2n, w ktorym kazda liczba wystepuje
dokladnie dwa razy. Nalezy symulowac proces dopasowywania par.

Idea rozwiazania:
Wykorzystana zostaje tablica jako stos oraz dodatkowa tablica
znacznikow informujaca, czy element jest aktualnie aktywny.
Algorytm operuje liniowo, bez uzycia ciezkich struktur STL.
Logika przypomina redukcje nawiasow przy pomocy stosu.

Zastosowane techniki:
- symulacja
- stos zaimplementowany jako tablica
- przetwarzanie liniowe

------------------------------------------------------------

4. Trojkaty jednobarwne

Opis problemu:
Policzyc liczbe trojkatow w grafie nieskierowanym.

Idea rozwiazania:
Zamiast sprawdzac wszystkie trojki wierzcholkow (O(n^3)),
liczymy liczbe wszystkich mozliwych trojek:
n*(n-1)*(n-2)/6,
a nastepnie odejmujemy te, ktore nie moga tworzyc trojkata,
wykorzystujac stopnie wierzcholkow.

Zastosowane techniki:
- kombinatoryka
- liczenie przez dopelnienie
- analiza stopni wierzcholkow

Zlozonosc:
O(n + m)

------------------------------------------------------------

5. Wiedzmak

Opis problemu:
Najkrotsza sciezka w grafie, gdzie kazda krawedz ma koszt oraz
wymaga posiadania okreslonych umiejetnosci. Umiejetnosci mozna
zdobywac w miastach.

Idea rozwiazania:
Zastosowana zostaje Dijkstra na grafie stanow.
Stan to para (miasto, maska_umiejetnosci).
Maska reprezentowana jest jako bitmask.
Przejscie krawedzia mozliwe jest tylko wtedy, gdy aktualna maska
zawiera wszystkie wymagane bity.

Zastosowane techniki:
- Dijkstra
- bitmaski
- graf stanow
- priority_queue

------------------------------------------------------------

6. Zima

Opis problemu:
Drzewo z wagami krawedzi. Parzystosc wag wplywa na sposob
liczenia wyniku. Nalezy wyznaczyc najlepsza sciezke,
ktora maksymalnie koryguje wynik globalny.

Idea rozwiazania:
Najpierw liczona jest suma bazowa.
Nastepnie DFS oraz DP na drzewie.
Dla kazdego wierzcholka przechowywane sa dwie najlepsze
wartosci sciezek schodzacych w dol.
Z nich budowana jest najlepsza sciezka przechodzaca
przez wierzcholek.

Zastosowane techniki:
- DFS
- DP na drzewie
- motyw srednicy drzewa

Zlozonosc:
O(n)

------------------------------------------------------------

7. Zajakniecia

Opis problemu:
Dwa ciagi liczb. Nalezy zmaksymalizowac liczbe dopasowanych
powtorzen tej samej wartosci w obu ciagach.

Idea rozwiazania:
Wyznaczane sa poprzednie wystapienia kazdej wartosci.
Nastepnie stosowane jest dynamic programming podobne do LCS,
z dodatkowymi warunkami dotyczacymi poprawnego laczenia par.

Zastosowane techniki:
- DP na sekwencjach
- poprzednie wystapienia
- wariant LCS

------------------------------------------------------------

8. Zdjecia krasnali

Opis problemu:
Dany graf nieskierowany. Nalezy sprobowac skierowac jego
krawedzie zgodnie z warunkami konstrukcji.
Jesli sie nie da, wypisac NIE.
Jesli sie da, wyznaczyc numeracje wierzcholkow.

Idea rozwiazania:
Najpierw konstruowany jest graf skierowany przy pomocy BFS
oraz lokalnych warunkow.
Nastepnie wykonywane jest sortowanie topologiczne
(algorytm Kahna).

Zastosowane techniki:
- BFS
- konstrukcja grafu
- topological sort

Zlozonosc:
O(n + m)

------------------------------------------------------------

9. Drogi rowerowe

Opis problemu:
Graf skierowany. Dla kazdego wierzcholka nalezy policzyc
wynik zwiazany z osiagalnoscia.

Idea rozwiazania:
Najpierw wyznaczane sa silnie spojne skladowe (Kosaraju).
Budowany jest graf kondensacji (DAG).
Wykonywane jest sortowanie topologiczne.
Nastepnie DP po DAG.

Zastosowane techniki:
- SCC (Kosaraju)
- kondensacja do DAG
- topological sort
- DP po DAG

Zlozonosc:
O(n + m)

------------------------------------------------------------

10. Marudny Bajtazar

Opis problemu:
Dany jest binarny napis oraz operacje zmiany pojedynczych bitow.
Po kazdej zmianie nalezy znalezc najmniejsza dlugosc podciagu,
dla ktorej nie wszystkie mozliwe wzorce wystepuja w napisie.

Idea rozwiazania:
Ograniczamy maksymalna dlugosc do 17.
Utrzymujemy licznik wystapien wszystkich podciagow dlugosci 1..k.
Wzorce kodowane sa jako liczby binarne w strukturze
przypominajacej trie zapisane w tablicy.
Po zmianie bitu aktualizowane sa tylko lokalne fragmenty.

Zastosowane techniki:
- bitmaski
- trie w tablicy
- aktualizacje lokalne

------------------------------------------------------------

11. Minusy

Opis problemu:
Na podstawie ciagu znakow + i - nalezy skonstruowac
wynikowy zapis z nawiasami i myslnikami.

Idea rozwiazania:
Jedno przejscie po danych oraz automat dwustanowy
okreslajacy, czy aktualnie jestesmy w nawiasie.

Zlozonosc:
O(n)

------------------------------------------------------------

12. Bony

Opis problemu:
Symulacja zaznaczania wielokrotnosci liczb oraz rejestrowania
momentow trafienia na specjalne pozycje.

Idea rozwiazania:
Dla kazdej liczby w przechodzimy po jej wielokrotnosciach,
oznaczamy jeszcze nieuzyte pozycje oraz zapisujemy trafienia.
Zapamietywana jest ostatnia sprawdzana wielokrotnosc,
co daje efekt amortyzacji.

Zastosowane techniki:
- przechodzenie po wielokrotnosciach
- visited array
- amortyzacja

------------------------------------------------------------
