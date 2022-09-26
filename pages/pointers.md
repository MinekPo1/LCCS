# Wzkaźniki i Tablice

[wróć do strony głównej](../README.md) | [wcześniej: funkcje](funcs.md)

***

## Spis treści

- [Pamięć RAM](#pamięć-ram)
- [Wzkażniki](#wzkaźniki)
- [Tablice](#tablice)
  - [Tablice wielowymiarowe](#tablice-wielowymiarowe)

***

## Pamięć RAM

Można by pomyślieć, że sekcja o architekturze komputera, jest zbendna w poradniku programowania.  
Jednak wzkażniki i tablice, bez pośrednio interagują z pamięcią RAM, więc warto troche wiedzieć.

Pamięć RAM można zwizualizować jako długi pasek, na którym są zera i jedynki.  
Komputer jest w stanie znaleść sekcje tego paska używając tzwn. adresu,
oraz operować na danych które są tam zapisane lub zapisać tam nowe.

> :bulb: Więcej szczegółów:
>
> - Tak naprawde adresy są do bajtów a nie poszczególnych bitów
> - Gdyż ładowanie danych z RAM-u to processora jest "wolne", gdy processor operuje na dużej ilości danych lub na tych samych danych często,  
>   kopiuje je do tzwn. cashu, który znajduje się w CPU (to też jest symplifikacja lol)

## Wzkaźniki

Wzkażnik, jak nazwa sugeruje, wzkazuje. Jest to adres, do którego możemy pisać lub z którego możemy pisać.  
Jest to przydatne gdy chcemy interagować z danymi które przychodzą z miejsca którego nie znamy.

Aby zdefinować wzkaźnik, umieszczamy gwiazdkę po typie.

```c++
int *p;
```

Jednakowoż ten wzkaźnik ma teraz wartość która była w tym miejscu wcześniej.  
Lepiej nie próbować pisać do lub czytać z tego wzkaźnika, gdyż może to spowodować, że system operacyjny zamknie nasz process.

Aby stwożyć nowy wzkaźnik, możemy użyć `new`.

```c++
int *p = new int;
```

Aby czytać z tego wzkaźnika używamy ponownie gwiazdki, a by pisać do niego, należy wstawić gwiazdkę przed jego nazwą w operacji  
przypisywania.

```c++
*p = 4;
cout << *p << endl; // 4
```

Jeżeli chcemy zdobyć adres danych zapisanych w zmiennej, możemy to zrobić używając symbolu `&`.

```c++
int a   = 2;
int *p2 = &a;
*p2 = 0;
echo << a << endl; // 0
```

Leżeli przez przypadek wydrukujemy wartość wzkażnika, dostaniemy wartość wyglądającą trochę tak:

```
0x800000420
```

<!-- przyrzekam był to pierwszy address który mi został dany lol -->

Jest to cztero bajtowy (lub 64-bitowy) numer w systemie szesnastkowym. Dla systemów 32-bitowych, będzie odpowiednio krótszy.

Jak inne lidzby więc, możemy na wzkaźnikach operować.

```c++
cout << 5 + p << endl;
```

Jest to przydatne gdy wiemy że dane znajdują się jedne po drugich tak jak w tablicach.

## Tablice

Tablice pozwalają nam zapisywać większą lidzbę danych, bez używania dużej ilości zmiennych.  
Te dane są zapisane jedne po drugiej w pamięci ram.

Aby zdefinować tablicę, po nazwie zmiennej, wstawiamy nawiasy kwadratowe, w których umieszcza się rozmiar tablicy.

```c++
int tab[10];
```
