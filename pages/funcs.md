# Funkcje

[wróć do strony głównej](../README.md) | [wcześniej: ify i pętle](ifs_n_loops.md)

***

## Spis treści

- [Czym jest funkcja?](#czym-jest-funkcja)
- [Budowa funkcji](#budowa-funkcji)
  - [Argumenty](#argumenty)
  - [Zwracanie](#zwracanie)
  - [Procedury](#procedury)
- [Rekursja](#rekursja)

***

## Czym jest funkcja?

Często w kodzie powtarzamy tą samą czyność wielokrotnie, dla przykładu uznajmy że w kodzie często obliczamy deltę

> Δ = b<sup>2</sup> - 4 × a × c

<sup>^ wzór na deltę jeżeli ktoś nie pamięta</sup>

Ciągłe wypisywanie tej ekspresji jest możliwe, lecz jest czasochłonne, oraz mało czytelne.

```c++
float f1_delta = f1_b * f1_b - 4 * f1_a * f1_c;
float f2_a = f1_a + 1;
float f2_delta = f1_b * f1_b - 4 * f2_a * f1_c;
float f3_c = f1_c + 1;
float f3_delta = f1_b * f1_b - 4 * f1_a * f3_c;
float f4_delta = f1_b * f1_b - 4 * f2_a * f3_c;
```

Możemy więc napisać funkcję która to oblicza.

```c++
float delta(float a, float b, float c){
	return b * b - 4 * a * c;
}
```

Teraz możemy zmienić powyszsze piekło w:

```c++
float f1_delta = delta(f1_a, f1_b, f1_c);
float f2_a = f1_a + 1;

float f2_delta = delta(f2_a, f1_b, f1_c);

float f3_c = f1_c + 1;

float f3_delta = delta(f1_a, f1_b, f3_c);
float f4_delta = delta(f2_a, f1_b, f3_c);
```

Od razu lepiej prawda?

## Budowa funkcji

Deklaracja funkcji przypomina lekko definicje zmiennej:

```c++
               │
               │ int func(){
int a;         │ // kod
               │ }
               │
```

Różnicami są:

- nawiasy po nazwie funkcji
- nawiasy klamrowe po nawiasach  
  (w których umieszcza się kod funkcji)

### Argumenty

W nawiasach możemy zdefinować tzwn. argumenty: jest to sposób przekazywania danych do funkcji.  
We wcześniejszym przykładzie funkcji obliczacającej deltę, możemy znaleść je:

```c++
//  tutaj! -------+--------+--------\
//                v        v        v
float delta(float a, float b, float c){
...
```

Oczywiście tu, kratka w kratkę jest to identyczne do definiji zmiennej!  
Jednak zamiast średnika jest tu przecinek.

### Zwracanie

Gdzie typ przed nazwą w deklaracji zmiennej definuje jej typ, dla funkcji jest to typ, który funkcja zwraca (ang. return).  
Ponownie używając przykładu z wcześniej, tam typem zwracanym jest `float`.  
Możemy też znaleść tam znajomy `return`, z funkcji `main`! Jak można odgadnąć pozwala on nam "wyjść" z funkcji.

Jak w funkcji main, wartość zwracana nie jest jednak wymagana. Jeżeli funkcja dojdzie do końca albo do `return`, bez wartości,  
zwrócona zostanie domyślna wartość (zwykle coś odpowiadającego zeru).

### Procedury

Jednak, nie wrzystkie funkcje wykonują operację która ma wynik. Na przykład funkcja która wyświetla coś na ekranie, lub drukuje to konsoli.  
Takie funkcjie nazywamy procedurami.

W c++-ie aby oznaczyć funkcję jako procedurę, w miejscu gdzie normalnie jest typ, umieszczamy `void` (ang. pustka).

Nadal możemy użyć `return`-a, lecz tylko bez wartości.

## Rekursja

Wiele problemów można przekrztałcić na problem, którego częścią jest tem sam problem, lecz mniejszy oraz przy danym rozmiarze wynik jest nam znany.

Prostym przykładem jest wieża hanoi, która polega na przeniesieniu wieży z krążków na inny słupek, lecz:

- można przenosić tylko jeden krążek na raz
- więkrzego krążka nie można umieścić na krążku mniejszym

```
  -|-       |        |
 --|--      |        |
---|---     |        |
-------  -------  -------
```

Można zobaczyć że kiedyś musimy przemieścić najwiękrzy krążek z pierwszego słupka na ostatni.  
Aby to osiągnąć jednak pozostałe krążki muszą być na pozycji drugiej.

```
   /-----------------\
   |                 v

   |        |        |
   |       -|-       |
---|---   --|--      |
-------  -------  -------
```

Jednak teraz musimy zagłowić się jak przenieść krążek drugi oraz pierwszy na słupek drugi.  
Można tu zauważyć że aby to zrobić, musimy przemieścić wrzystkie krążki mniejsze od drugiego na słupek trzeci.

```
   /--------\
   |        v

   |        |        |
 --|--      |        |
---|---     |       -|-
-------  -------  -------
```

Jednak teraz musmimy zagłowić się jak przenieść krążek pierwszy oraz... Nie tylko pierwszy, na pozycję trzecią.

```
   /-----------------\
   |                 v

  -|-       |        |
 --|--      |        |
---|---     |        |
-------  -------  -------
```


Jednak gdy przeniesieniemy krążek drugi na drugi, trzeci słupek jest zablokowany krążkiem pierwszym. Przenieśmy go więc.

```
            /--------\
            v        |

   |        |        |
   |        |        |
---|---   --|--     -|-
-------  -------  -------
```

Teraz gdy najwiękrzy krążek jest na pozycji trzeciej, musimy nałożyć na niego drugi i pierwszy krążek...  
Jednak już przekładaliśmy krążki pierwszy i drugi na inną kolumę! Zróbmy to ponownie!

```
   /-----------------\
   |        /--------+
   +--------+        |
   v        |        v

   |        |        |
   |       -|-       |
   |      --|--   ---|---
-------  -------  -------
```

Więc funkcja która rozwiązuje wieżę hanoi wyglądała by tak (psełdo kod):

```
def wieża_hanoi(od = 1, do = 3, wys = 3):
	if wys == 1:
		print("1",od,"->",do)
	else:
		if od != 1 and do != 1:
			półka = 1
		elif od != 2 and do != 2:
			półka = 2
		else:  # musi być to 3.
			półka = 3
		wieża_hanoi(od, półka, wys - 1)
		print(wys,od,"->",do)
		wieża_hanoi(półka, do, wys - 1)
```

<!-- Tak. Jest to python :P -->

***

[wróć do strony głównej](../README.md) | [dalej: wskaźniki i tablice](pointers.md)
