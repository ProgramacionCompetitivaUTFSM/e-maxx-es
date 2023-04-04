# Stack

> **Tabla de Contenidos**
> * [Definición](#Definición)
> * [Utilización](#Utilización)
>   * [Declaración](#Declaración)
>   * [Acceso y almacenamiento](#Acceso y almacenamiento)
> * [Problemas](#Problemas)

![Stack GIF Animation](https://miro.medium.com/max/1280/1*lb-0r80YYhcnoVcQ3HY-1g.gif)
## Definición
Los stacks (pilas en su traducción al español) son una estructura de datos lineal que permite almacenar los datos de forma no contigua en la memoria. La forma de acceder a los datos es llamada **LIFO** (del inglés Last In First Out, el último en entrar, el primero en salir), esto nos da a entender que solo tenemos acceso al ultimo elemento que se ingresó a la pila.

Como se puede observar en la animación que está en la parte superior, podemos hacer una analogia a un monto de libros apilados de forma vertical, en la cual solo podemos sacar el ultimo libro que coloquemos en la pila de forma sencilla (asumimos que no se pueden sacar libros de la mitad). 

La pilas se ha tenido varios usos en la vida cotidiana como en algoritmos, uno de los más comunes podria ser el historial de cambios o la verificación de los parentesis abiertos y cerrados de una secuencia.

La principal ventaja de la pila es el almacenamiento en memoria de forma contigua, esto permite un eficiente acceso, inserción y eliminación, siendo su complejidad $O(1)$ en todas las operaciones. Esta complejidad será así, siempre y cuando sea el último elemento, ya que no se pueden acceder **DIRECTAMENTE** a los elementos que este en la mitad de la pila, si es que se quiere llegar a algún elemento que este en la mitad de la pila se tendrá que sacar todo elemento que este arriba de ese elemento.

## Implementación

### Declaración
```cpp
#include<bits/stdc++.h>
 
using  namespace std;
  
int main() {
	/*
		Para crear una pila primero se debe usar la palabra
		stack seguida del tipo de dato que se va almacenar 
		encerrado en < >
	*/
	stack<int> S;

	// Posibles tipos de datos
	stack<char> A;
	stack<string> B;
	stack<short> C;
	stack<long> D;
	stack<long long> E;
	stack<float> F;
	stack<double> G;
	stack<long double> H;

	return  0;
}
```

### Acceso y almacenamiento
```cpp
#include<bits/stdc++.h>

using  namespace std;

int main() {

	stack<int> S;

	/* Para añadir un elemento a la pila se usa el método
	push.
	*/
	S.push(1);
	 
	/* Para ver cual es el valor del ultimo elemento ingresado
	se usa el método top.
	*/
	S.top();
	
	/* Para saber la cantidad de elemento dentro de la pilas
	se usa el método size.
	*/
	S.size();
	
	/* Para saber si la pila esta llena o no, se usa el método
	empty.
	*/
	S.empty();
	
	return  0;
}
```

## Problemas
-  343B Alternating Current
https://codeforces.com/problemset/problem/343/B
- 373 Parenthesis Balance
https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=614
- 101343H Give Me This Pizza
https://codeforces.com/problemset/gymProblem/101343/H
 
