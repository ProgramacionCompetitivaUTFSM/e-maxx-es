# Nuestro primer problema!!

> **Tabla de Contenidos**
> * [4A Watermelon - Codeforces](#4A Watermelon - Codeforces)
>   * [Enunciado](#Enunciado)
>   * [Input](#Input)
>   * [Output](#Output)
>   * [Análisis](#Análisis)
>   * [Código](#Código)

## 4A Watermelon - Codeforces

Para este ejemplo usaremos el problema que esta descrito en el siguiente enlace: [https://codeforces.com/problemset/problem/4/A](https://codeforces.com/problemset/problem/4/A). Este problema es de la página Codeforces así que se motiva a crearse una cuenta en esa página por si quieren intentar el problema y subirlo.

El problema dice lo siguiente:

### Enunciado

*One hot summer day Pete and his friend Billy decided to buy a watermelon. They chose the biggest and the ripest one, in their opinion. After that the watermelon was weighed, and the scales showed $w$ kilos. They rushed home, dying of thirst, and decided to divide the berry, however they faced a hard problem.*

*Pete and Billy are great fans of even numbers, that's why they want to divide the watermelon in such a way that each of the two parts weighs even number of kilos, at the same time it is not obligatory that the parts are equal. The boys are extremely tired and want to start their meal as soon as possible, that's why you should help them and find out, if they can divide the watermelon in the way they want. For sure, each of them should get a part of positive weight.*

### Input

*The first (and the only) input line contains integer number w ($1\leq w \leq 100$) — the weight of the watermelon bought by the boys.*

### Output

*Print `YES`, if the boys can divide the watermelon into two parts, each of them weighing even number of kilos; and `NO` in the opposite case.*

### Análisis

En resumen, el problema trata de que Pete y su amigo Billy quieren dividir la sandía, pero son muy fans de los números pares, por lo que quieren dividir la sandía en dos de tal forma que las dos partes sean de un peso par. Lo que tú sabes es que inicialmente recibes un número $w$ que corresponderá a los kilos de la sandía, añadiendo que como $w$ es positivo y menor a $100$, entonces el número basta con tener un tipo de dato `int` para almacenar la variable. 

Ahora, ¿Cómo se puede cumplir con el objetivo? Ellos quieren dividir la sandía en dos pedazos pares no necesariamente iguales, para ellos hay que darse cuenta de que $w = a + b$, donde $a$ y $b$ son números pares, pero la única forma de que un número se pueda dividir en dos números pares es que ese número sea par. Por lo tanto, $w$ debe ser par que poder mostrar por consola `YES`. Pero ¿Eso basta? No, ¿Existe algún número par, donde lo que dijimos anteriormente no se cumple? EXACTO, EN EL 2!!!! Entonces, la condición completa del problema es que para mostrar `YES`, $w$ debe ser par **Y** mayor a $2$.

Felicidades!!! Tenemos la idea, ahora a programar!

### Código

```cpp
// esta línea permite importar toda la librería estándar a nuestro código
// en este caso, es inútil, pero será muy útil a futuro
#include<bits/stdc++.h> 
// permite simplificar la sintaxis de C++, para no tener 
//que escibir por ejemplo std::cout
using namespace std;
 
int main(){
	// declaramos la variable w
	int w;
 
 	// leemos el input del problema
	cin >> w;
 
 	// condición planteada anteriormente y muestra por consola 
 	// según si es verdadera o no
	if(w % 2 == 0 && w > 2) cout << "YES\n";
	else cout << "NO\n";
 
	return 0;
}
```

