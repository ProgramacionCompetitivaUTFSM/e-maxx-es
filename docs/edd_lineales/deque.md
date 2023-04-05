# Cola doblemente terminada


> **Tabla de Contenidos**
> * [Definición](#definicion)
> * [Utilización](#utilizacion)
>   * [Declaración](#declaracion)
>   * [Operaciones](#operaciones)
>   * [Ejemplo](#ejemplo)
> * [Problemas](#problemas)

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

* `push_front(val)`: inserta `val` al principio de la deque.
* `push_back(val)`: inserta `val` al final de la deque
* `pop_front()`: elimina el elemento al principio de la deque.
* `pop_back()`: elimina el elemento al final de la deque.
* `front()`: retorna el elemento que esta al principio de la deque.
* `back()`: retorna el elemento que esta al final de la deque.
* `size()`: retorna la cantidad de elemento dentro de la deque.
* `empty()`: retorna verdadero si la deque esta vacía, en caso contrario retorna falso.

```cpp
#include<bits/stdc++.h>
using  namespace std;

int main() {

  deque<int> dq;
  
  dq.push_front(2);
  dq.push_front(3);
  
  cout << dq.front() <<  "\n";
  
  dq.push_back(-1);
  
  cout << dq.front() << "\n";
  cout << dq.back() << "\n";
  
  dq.push_back(2);
  
  bool flag = true;
  while(!dq.empty()) {
    if(flag) {
      flag = false;
      cout << "front: " << dq.front() << "\n";
      dq.pop_front();
    } else {
      flag = true;
      cout << "back: " << dq.back() << "\n";
      dq.pop_back();
    }
  }
	return  0;
}
```

## Problemas
