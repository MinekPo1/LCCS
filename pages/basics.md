# Podstawy podstaw

[wróć do strony głownej](../README.md)

***

## Spis treści

- [funkcja `main`](#funkcja-main)
- [zmienne](#zmienne)
- [podstwowe typy](#podstawowe-typy)
- [`#include`](#include)
- [biblioteka `iostream`](#biblioteka-iostream)

## funkcja `main`

Funcja main to to co jest wykonywane. **Musi** zwracać [`int`](#int).

```c++
int main(){
	//code :D
}
```

Aby wcześnie zakończyć program, można użyć keyworda `return`.  
Opcionalnie można dodać wartość, gdzie `0` oznacza poprawne wykonanie programu a inne wartości jakiś błąd.

```c++
int main(){
	return 0;
}
```

Patrz na rozdział [funkcje](funcs.md) jeżeli chcesz dowiedzeć się więcej o funkcjiach

## zmienne

Zmienne można wyobrasić sobie jako szufladki do których można coś włożyć aby przechować na później.

W c++ie zmienne narpiew trzeba zdefinować. Można im wtedy też dać domyślną wartość.

```c++
//typ nazwa
  int   a;
//      v wartość
int b = 1;
```

Po zdefinowaniu można taką funkcję użyć, wpisując jej nazwę.

```c++
int c = a + b;
```

## podstawowe typy

Typ to spodób zapisywania danych w pamięci komputera (wielkie uproszczenie, patrz [struktury i klasy](structs_n_classes.md))  
Te najczęstrze zapisują lidzby lub ciągi znaków.

Więcej typów można znaleść w [bibliotekach](std.md)

### `int`

Lidzba całkowita.

Przykład: `123`

Wariacje: `short`, `long`, `long long`, w praktyce też [`char`](#char)

### `float`

Lidzba naturalna. Zapisana z użyciem notacji nakukowej. (np.: `1.13 * 10^5`)

Przykład: `0.0000113`

Wariacje `double`

### `char`

Znak, lub mała lidzba całkowita.

Przykład: `'a'` lub `1`

Wariacje: `wchar`

### `std::string`

> Jeżeli użyto nagłówka `using namespace std;` (patrz [`#include`](#include)) można też użyć `string`

Ciąg znaków.

Przykład `"Hello world!"`

Wariacje: `char[]`

## `#include`

`#include` używane jest aby załączyć [biblioteki](std.md) lub inne pliki.  
Dla bibliotek, nazwa biblioteki zamykana jest w `<` `>`, a dla plików w cudzysłowach `"` `"`.

```c++
#include <math.h>
#include "file.cpp"
```

Dużo bibliotek zawiera rzeczy których nazwa jest prefixowana `std::`.  
Można zrobić aby było to domyślne używając `using namespace std;`, lecz jest to nie zalecane.

```c++
using namespace std;
```

## biblioteka `iostream`

Biblioteka `iostream` zawiera dwa przydatne elementy:

- `std::cout`
- `std::cin`

Są to tak zwane strumienie, lecz nie będę wchodzić w to tutaj. (patrz [pełniejszą wersję](std/iostream.md))  
`cout` (console/c out) pozwala pokazywać (aka drukować, ang print) do konsoli, a `cin` (console/c in) pozwala wprowadzić coś przez użydkownika.

```c++
std::cout << "Witajcie!" << std:endl; //std::endl przechodzi do następnej linijki (ang end line, zkończ linikę)

std::cin >> a; // wprowada do zmiennej a **KTÓRA MUSI BYĆ WCZEŚNIEJ ZDEFINOWANA**
```

***

[wróć do strony głównej](../README.md) | [dalej: ify i pętle](ifs_n_loops.md)
