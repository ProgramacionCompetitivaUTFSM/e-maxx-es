# Conjuntos

> Tabla de Contenidos
> * [Definición](#definicion)
> * [Conjuntos Ordenados](#conjuntos-ordenados)
>   * [Declaración](#declaracion)
>   * [Verificar presencia de un elemento](#verificar-presencia-de-un-elemento)
>   * [Insertar y eliminar](#insertar-y-eliminar)
>   * [Aprovechar que esta ordenado](#aprovechar-que-esta-ordenado)
>   * [Recorrer el conjunto](#recorrer-el-conjunto)
> * [Conjuntos Desordenados](#conjuntos-desordenados)
> * [Complejidades](#complejidades)
> * [Referencias](#referencias)
> * [Problemas](#problemas)

## Definición

Los conjuntos corresponden a una estructura de datos que permite almacenar el mismo elemento una única vez. Si es que se intentase añadir un elemento que ya se encuentra en el conjunto, entonces no se almacenaría nada. 

Por ejemplo, si se tiene los números $\{1, 4, 2, 3, 2, 5\}$ y los almaceno todos en un conjunto, el conjunto resultante sería $\{1, 4, 3, 2, 5\}$. Hay que notar que el orden de los elemento antes y después de la inserción no tiene mayor relación.

Dentro de la familia de los conjuntos existen dos tipos: ordenados y no ordenados. Los conjuntos ordenados y no ordenados poseen la misma carácteristica de almacenar los elementos una única vez, pero con diferencia en la implementación la cual nos podrá dar ciertas ventajas y desventajas.

## Conjuntos Ordenados

Los conjuntos ordenados tienen la carácteristica que a medida que se van insertando los elementos, esto los va ordenando según su propia función de comparación. Estos almacenan los elementos utilizando una estructuras de datos llamada [Red-Black Tree](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree), esta estructura consiste en un tipo de AVL, no es importante que sepan el detalle, pero nos será útil para después.

### Declaración

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  // aquí se inicializa un conjunto de enteros
  set< int > con_ints;

  // aquí se inicaliza un conjunto de strings
  set< string > con_string;

  // aquí se inicializa un conjunto de conjuntos de enteros
  set< set< int > > con_con_int;
  return 0;
}
```

¿Qué es lo que debe tener el conjunto para almacenarse en un conjunto? Debe tener acceso los operadores para compararse (`==`, `<=`, `>=`, etc), puesto que de esa forma puede verificar si dos elementos son iguales o no.

### Verificar presencia de un elemento

Para buscar elementos dentro del conjunto se debe hacer uso de la función `con.find(elemento a buscar)`, esta retorna un `set< T >::iterator` que apunta al elemento buscado, si el elemento no existe retorna un interador equivalente al `con.end()`.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  set< int > con;
  
  // aqui insertamos elementos

  set< int >::iterator itr = con.find(3);
  if(itr != con.end())
    cout << "El elemento esta en el conjunto\n";
  else
    cout << "El elemento no esta en el conjunto\n";
  return 0;
}
```

### Insertar y Eliminar

Para insertar elementos al conjunto se debe utilizar la función `con.insert(valor a insertar)`, la cual recibe el valor a insertar. Para borrar se debe utilizar la función erase la cual tiene dos opciones: `con.erase(valor a borrar)` y `con.erase(iterador al elemento a borrar)`

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  set< int > con;
  
  // aquí insertamos 4 elementos al conjunto {3, 2, 1, 4}
  con.insert(3);
  con.insert(2);
  con.insert(1);
  con.insert(4);

  // de esta forma podemos ver cuantos elementos hay en el conjunto
  cout << con.size() << "\n";

  con.insert(4);

  // se comprueba que al insertar un elemento que ya esta en el conjunto
  // no crece el tamaño
  cout << con.size() << "\n";

  // se borra el elemento 2 del conjunto
  con.erase(2);
  cout << con.size() << "\n";

  //
  iterador::set< int > itr = con.find(1);
  if(itr != con.end()) {
    // dado que el elemento esta en el conjunto puedo borrarlo con la variable
    // `itr`
    con.erase(itr);
    // SI EL ITR == CON.END() NO SE PUEDE USAR LA FUNCIÓN ERASE
  }
  // se comprueba el tamaño
  cout << con.size() << "\n";
  return 0;
}
```

### Aprovechar que esta ordenado

Ahora, anteriormente se dijo que de algo sería útil tener un conjunto ordenado, esto se debe a que gracias a que el conjunto esta ordenado, se podrán aplicar operaciones que nos permitirán no solo verificar si un elemento está o no. Se tiene acceso a dos funciones:

* `con.lower_bound(elemento)`, el cual retorna un iterador que apunta al primer valor que no sea menor que el elemento.
* `con.upper_bound(elemento)`, el cual retorna un iterador que apunta al primer valor que sea mayor que el elemento.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  set< int > con;
  con.insert(4);
  con.insert(2);
  con.insert(3);
  con.insert(3);
  con.insert(10);
  con.insert(7);

  set< int >::iterator itr = con.lower_bound(4);
  // siempre verificar primero que el iterador no sea el .end(), porque eso 
  // significaría que el elemento no esta
  if(itr != con.end()) {
    // el uso del asterisco es para acceder al valor apuntado por el iterador
    // en el ejemplo se mostraría: 4
    cout << *itr << "\n";
  }

  itr = con.lower_bound(6);
  if(itr != con.end()) {
    // en el ejemplo se mostraría: 7
    cout << *itr << "\n";
  }
  
  itr = con.upper_bound(4);
  if(itr != con.end()) {
    // en el ejemplo se mostraría: 7
    cout << *itr << "\n";
  }
  return 0;
}
```

### Recorrer el conjunto 

Gracias a C++, se puede recorrer todos los elementos del conjunto de manera ordenada.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  set< int > con;
  con.insert(4);
  con.insert(2);
  con.insert(3);
  con.insert(3);
  con.insert(10);
  con.insert(7);

  // metodo 1: for clasico
  // * se inicializa el iterador en el .begin() del conjunto, o sea el primer elemento
  // * el for dura mientras el iterador sea distinto de .end(), ya que si llega significa 
  //   esta en el final y por lo tanto debe dejar de recorrer
  // * la operacion ++ esta sobrecargada y permite avanzar al siguiente iterador en la estructura
  // 
  // para este ejemplo, se mostrarán los elementos de menor a mayor
  for(set< int >::iterator itr = con.begin(); itr != con.end(); itr++) {
    cout << *itr << " ";
  }
  cout << "\n";

  // metodo 2: for each
  // por cada ciclo del for se generará una copia de los elementos del conjunto
  // partiendo desde .begin() hasta el .end()
  // 
  // al igual que antes, se mostrarán los elementos de menor a mayor
  for(int e : con) {
    cout << e << " ";
  }
  cout << "\n";
  return 0;
}
```

## Conjuntos Desordenados

Los conjuntos desordenados, a diferencia del otro tipo de conjuntos, este no mantiene un orden entre los elementos. Esto debido a que realiza el manejo de los datos a través de una [función de hashing](https://en.wikipedia.org/wiki/Hash_function). Los conjuntos desordenados tienen casi las mismas funciones, pero al no estar ordenados pierden la habilidad de aplicar funciones como `lower_bound` o `upper_bound`.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  unordered_set< string > con;
  
  con.insert("hola");
  con.insert("ayuda");
  con.insert("haol");
  con.insert("hola");

  // obtenemos la cantidad de elementos en el conjunto
  cout << con.size() << "\n";
  // al igual que antes se puede buscar un elemento
  unordered_set< string >::iterator itr = con.find("hola");
  if(itr != con.end())
    cout << "El elemento esta en el conjunto\n";
  else
    cout << "El elemento no esta en el conjunto\n";

  // también se puede recorrer al igual que los otros
  for(unordered_set< int >::iterator itr = con.begin(); itr != con.end(); itr++) {
    cout << *itr << " ";
  }
  cout << "\n";

  for(int e : con) {
    cout << e << " ";
  }
  cout << "\n";

  return 0;
}
```

## Complejidades

Ahora que se conocen las dos formas de utilizar conjunos en C++, analizemos las complejidades. 

Comenzando por los conjuntos ordenados, usan una implementación de *Red-Black Tree* y este es un árbol binario balanceado, las complejidades de las operaciones se regirán en cuánto nos costaría recorrer una rama del árbol para poder buscar/insertar/eliminar. Es por esto que las operaciones buscar/insertar/eliminar son todos $O(log n)$ en peor caso.

En cambio, los conjuntos desordenados para insertar/buscar elementos lo realiza a través de una función de hashing, gracias a esto las operaciones se pueden hacer en tiempo promedio $O(1)$, pero puede llegar a tener peor caso $O(n)$, donde $n$ es la cantidad de elementos en el conjunto. Entonces, se debe usar con preocupación, cuando los elementos tienden a ser muy parecidos puede causar que las operaciones sean más lentas.

Aquí se presenta una tabla resumen al respecto de las complejidades y de algunas operaciones:

| Operaciones  | Conjunto Ordenado | Conjunto Desordenado         |
|--------------|-------------------|------------------------------|
| insert       | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| erase        | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| find         | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| lower_bound  | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| upperd_bound | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |

## Referencias

* Set - [https://cplusplus.com/reference/set/](https://cplusplus.com/reference/set/) 
* Unordeded Set - [https://cplusplus.com/reference/unordered_set/](https://cplusplus.com/reference/unordered_set/)

## Problemas
