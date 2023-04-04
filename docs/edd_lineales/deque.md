# Cola doblemente terminada


> **Tabla de Contenidos**
> * [Definición](#Definición)
> * [Utilización](#Utilización)
>   * [Declaración](#Declaración)
>   * [Operaciones](#Operaciones)
> * [Problemas](#Problemas)

## Definición

La deque (Double-Ended Queue o cola doblemente terminada en su traducción al español) es una estructura de datos bastante parecida a la [Queue](/edd_lineales/colas.md). La principal diferencia entre estas dos es que la deque tiene acceso al principio y al final, además se puede ingresar/eliminar tanto al comienzo como al final.

## Utilización

### Declaración
```cpp
#include<bits/stdc++.h>
 
using  namespace std;
  
int main() {
	/*
		Para crear una pila primero se debe usar la palabra
		deque seguida del tipo de dato que se va almacenar 
		encerrado en < >
	*/
	deque<int> S;

	// Se puede almacenar cualquier tipo de datos
	deque<char> A;
	deque<string> B;
	deque<short> C;
	deque<long> D;
	deque<long long> E;
	deque<float> F;
	deque<double> G;
	deque<long double> H;

	return  0;
}
```

### Operaciones
```cpp
#include<bits/stdc++.h>

using  namespace std;

int main() {

	deque<int> dq;

  /* Para ingresar un elemento al principio de la deque se 
  utiliza el método push_front */
  dq.push_front(7);
  
  /* Para ingresar un elemento al final de la deque se utiliza
  el método pop_front */ 
  dq.push_back(2);
  
  /* Para ver cual es el elemento al principio de la deque se utiliza
  el método front */
  dq.front();
  
  /* Para ver cual es elemento al final de la deque se utiliza
  el método back */
  dq.back();
  
  /* Para saber la cantidad de elementos dentro de la deque se utiliza
  el método size */
  dq.size();
  
  /* Para saber si la pila esta llena o no, se usa el método
	empty.
	*/
	dq.empty();
	
  /* Para eliminar el elemento que se encuentra al principio de la deque se utiliza
  el método pop_front */
  dq.pop_front();
  
  /* Para eliminar el elemento que se encuentra al principio de la deque se utiliza
  el método pop_back */
  dq.pop_back();
  
	return  0;
}
```

## Problemas
