# Ify i Pętle

[wróć do strony głównej](../README.md) | [wcześniej: podstawy podstaw](basics.md)

***

## Spis treści

- [`if`](#if)
- [pętla `while`](#pętla-while) (+ [pętla `do`-`while`](#pętla-do-while))
- [pętla `for`](#pętla-for)

## `if`

`if` (ang. jeżeli) pozwala nam wykonywać kod tylko gdy warunek jest spełniony.

```c++
int a = 1;

if (a == 2){
	std::cout << "dlaczego a to 2?" << std::endl;
}
```

Po jeżeli chcemy wykonać kod także gdy warunek nie został spełniony, można użyć keyworda `else`.

```c++
if (a == 2){
	std::cout << "dlaczego pies przeskoczył nad płotem?" << std::endl;
}
else{
	std::cout << "jeżeli spodziewaliście się żartu to przepraszam." << std::endl;
}
```

Można też sprawdzać więcej niż jeden warunek, powtarzając `if` po `else`.

```c++
if(a == 2){
	std::cout << "a==2" << std::endl;
}
else if(a == 3){
	std::cout << "a==3" << std::endl;
}
else {
	std::cout << "baaa" << std::endl;
}
```

## pętla `while`

`while` to jedna z podstawowych pentli. Pozwala ona wykonywać kod raz po razie, dopuki warunek jest spełniony.

```c++
int a = 1;
int b = 1;

while(a < 100){
	a += b;
	b = a - b;
}
```

Lecz, czasami nie jesteśmy w stanie sprawidzić czy warunek jest spełniony, bez wykonania kodu raz. Do tego przydatna jest

### pętla `do`-`while`

```c++
int a = 1;

do{
	if (a % 2){
		a /= 2;
	}
	else {
		a *= 3;
	}
}
while(a >= 3); // <- średnik!
```

## pętla `for`

Głównym use-casem pętli `for` jest gdy musimy wykonać kod na zakresie wartości, na przykład od `1` do `20`.  
Można to zrobić za pomocą [pętli `while`](#pętla-while)

```c++
int i = 1;

while(i <= 20){
	// kod idk

	i ++;
}
```

lecz jest to mało czytelne. Linijka kodu która zwiękrza `i` jest daleko od reszty logiki pętli, itd.  
Dlatego w c++ istnieje pętla `for` która agreguje ten kod w jedno miejsce.

```c++
for(int i = 1; i <= 20; i++){
	// kod
}
```

W nawiasach po keywordzie `for` są trzy rzeczy oddzielone średnikami:

- kod inicjalizujący, wykonywany gdy "wchodzimy" do pętli
  ```c++
  int i = 1
  ```
- warunek
  ```c++
  i <= 20
  ```
- kod iteracyjny, którego zadaniem jest modyfikacja (w tym przypadku) `i`
  ```c++
  i++
  ```

***

[wróć do strony głównej](../README.md) | [dalej: funkcje](funcs.md)
