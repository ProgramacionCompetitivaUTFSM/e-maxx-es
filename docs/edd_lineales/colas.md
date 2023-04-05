# Colas

> **Tabla de Contenidos**
> * [Definición](#definicion)
> * [Utilización](#utilizacion)
>   * [Declaración](#declaracion)
>   * [Operaciones](#operaciones)
>   * [Ejemplo](#ejemplo)
> * [Problemas](#problemas)

![Queue GIF Animation](https://www.google.com/url?sa=i&url=https%3A%2F%2Fdeepblade.com%2Fqueue-data-structure%2F&psig=AOvVaw3XXEmjOt5S7DbD3UB7m1s_&ust=1680670095506000&source=images&cd=vfe&ved=0CA8QjRxqFwoTCIih3pm2j_4CFQAAAAAdAAAAABAg)

## Definición

Las queue (colas en su traducción al español) son una estructura de datos lineal que permite almacenar los datos de forma contigua en la memoria. La forma de acceder a los datos es llamada FIFO (del inglés First In First Out), esto implica que solo tenemos acceso al último elemento que se ingresó a la cola.

Esta estructura de datos se puede asemejar a las colas de supermercados. Debido a que la primera persona en llegar, es la primera en ser atendida. Y una persona que llego después, debe esperar a que todas las personas que hayan llegado primero que ella sean atendidas.

Las colas tienen varias ventajas para el uso de algoritmos, como por ejemplo el algoritmo BFS.

La principal ventaja de la cola es el almacenamiento en memoria de forma contigua, esto permite un eficiente acceso, inserción y eliminación, siendo su complejidad $O(1)$ en todas las operaciones.

## Utilización

### Declaración

```cpp
#include<bits/stdc++.h>
using  namespace std;
  
int main() {
	/*
		Para crear una pila primero se debe usar la palabra
		queue seguida del tipo de dato que se va almacenar 
		encerrado en < >
	*/
	queue<int> S;

	// Se puede almacenar cualquier tipo de datos
	queue<char> A;
	queue<string> B;
	queue<short> C;
	queue<long> D;
	queue<long long> E;
	queue<float> F;
	queue<double> G;
	queue<long double> H;

	return  0;
}
```

### Operaciones

* `front()`: retorna el elemento que esta al principio de la cola.
* `push(val)`: inserta `val` al principio de la cola. 
* `pop()`: elimina el elemento al principio de la cola. **OJO**: si la cola esta vacía C++ tirará error.
* `size()`: retorna la cantidad de elementos dentro de la cola.
* `empty`: retorna verdadero si la cola esta vacía, en caso contrario retorna falso

### Ejemplo

```cpp
#include<bits/stdc++.h>

using  namespace std;

int main() {

	queue<int> Q;

  cout << "Tamanio actual de la cola: " << Q.size() << "\n";
  
  Q.push(2);
  Q.push(1);
  Q.push(123);
  Q.push(1254);
  Q.push(-13);
  
  cout << "Tamanio actual de la cola: " << Q.size() << "\n";
  cout << "El elemento al principio de la cola es: " << Q.front() << "\n";
  
  // eliminar los elementos utilizando un while
  // Por consola se vera: 2 1 123 1254 -13
  while(!Q.empty()) {
    cout << Q.front() << "\n";
    Q.pop();
  }
	return  0;
}
```

## Problemas

