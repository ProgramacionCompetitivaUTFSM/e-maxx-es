# Diccionarios

> Tabla de Contenidos
> * [Definición](#definicion)
> * [Diccionarios Ordenados](#diccionarios-ordenados)
>   * [Declaración](#declaracion)
>   * [Almacenar y Acceder](#almacenar-y-acceder)
>   * [Borrar](#borrar)
>   * [Aprovechar que esta ordenado](#aprovechar-que-esta-ordenado)
>   * [Recorrer el diccionario](#recorrer-el-diccionario)
> * [Diccionarios Desordenados](#diccionarios-desordenados)
> * [Complejidades](#complejidades)
> * [Referencias](#referencias)
> * [Problemas](#problemas)

## Definición

Los diccionarios corresponden a una estructura de datos que permite almacenar una relación entre una llave y un valor, con la restricción que solo se puede almacenar una llave una única vez. Si es que se intenta almacenar una llave con un valor y esa llave ya se encuentra presente, se reemplaría el valor.

Por ejemplo, las personas chilenas tienen un rut que es un identificador único, entonces se podría almacenar el rut de las personas para relacionarlo su rut con algo valor útil, como el nombre.

Dentro de la familia de los diccionarios existen dos tipos: ordenados y no ordenados. Los diccionarios ordenados y no ordenados poseen la misma carácteristica, pero con diferencia en la implementación la cual nos podrá dar ciertas ventajas y desventajas.

## Diccionarios Ordenados

Los diccionarios ordenados tienen la carácteristica que a medida que se van insertando los elementos, esto los va ordenando según su propia función de comparación. Estos almacenan los elementos utilizando una estructuras de datos llamada [Red-Black Tree](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree), esta estructura consiste en un tipo de AVL, no es importante que sepan el detalle, pero nos será útil para después.

### Declaración

Los diccionarios ordenados se declaran utilizando la palabra `map< T1, T2 >`, donde `T1` es el tipo de dato de la llave y `T2` es el tipo de dato del valor.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  // aquí se inicializa un diccionario 
  // donde la llave es tipo int y el valor es tipo int
  map< int, int > int_int;

  // aquí se inicaliza un diccionario
  // donde la llave es tipo int y el valor es tipo string
  map< int, string > int_string;

  // aquí se inicializa un diccionario
  // donde la llave es tipo int y el valor es tipo vector de enteros
  map< int, vector< int > > int_vector_int;
  return 0;
}
```

### Almacenar y Acceder

Para almacenar y acceder a los elementos del diccionario se puede realizar de donde formas.

La primera forma consiste en utilizar el operador `[]`. Hay que tener ojo si al utilizar el `[]`, puesto que al usarlo se inserta automaticamente una llave en el diccionario.

Aquí un ejemplo de como usarlo.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  map< char, int > mp;

  // aqui almacenamos 3 llaves: a, c y D
  // donde a -> 2, c -> 3 y D -> 1
  mp['a'] = 2;
  mp['c'] = 3;
  mp['D'] = 1;
  
  // se muestre por pantalla la cantidad de pares (llave, valor)
  // hay en el diccionario
  cout << mp.size() << "\n";

  // acceder al valor que corresponde a la llave a
  cout << mp['a'] << "\n";
  // sobreescribimos la llave a con un nuevo valor 0
  mp['a'] = 0;
  cout << mp['a'] << "\n";
  
  return 0;
}
```

La segunda forma consiste en utilizar las siguientes dos funciones:

* `mp.insert({llave, valor})`, la cual recibe un `pair` que contiene la llave y el valor relacionado a esa llave
* `mp.find(llave)`, la cual recibe la llave a buscar y retorna un iterador a un par, correspondiente al par (llave, valor).

Aquí un ejemplo de como usarlo.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  map< char, int > mp;

  // aqui almacenamos 3 llaves: a, c y D
  // donde a -> 2, c -> 3 y D -> 1
  mp.insert({'a', 2});
  mp.insert({'c', 3});
  mp.insert({'D', 1});

  // se muestre por pantalla la cantidad de pares (llave, valor)
  // hay en el diccionario
  cout << mp.size() << "\n";

  // se busca la llava a
  map< char, int >::iterator itr = mp.find('a');
  // si el iterador es equivalente al .end(), entonces llave no se encuentra
  // en el diccionario
  if(itr != mp.end()) {
    // se debe utilizar -> para acceder al primer y segundo elemento del par 
    // si no puedes usar el * y acceder usando el .
    cout << "(" << itr->first << ", " << itr->second << ")\n";
    // son equivalentes
    cout << "(" << (*itr).first << ", " << (*itr).second << ")\n";
  } else {
    cout << "La llave no esta\n";
  }
  return 0;
}
```

### Borrar 

Para borrar se tienen dos formas de borrar elementos: `mp.erase(llave)` (por su llave) o `mp.erase(iterador al par)` (un iterador al par llave, valor).

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  map< char, int > mp;

  // aqui almacenamos 3 llaves: a, c y D
  // donde a -> 2, c -> 3 y D -> 1
  mp['a'] = 2;
  mp['c'] = 3;
  mp['D'] = 1;

  cout << mp.size() << "\n";
  mp.erase('a');
  cout << mp.size() << "\n";

  map< char, int >::iterator itr = mp.find('c');
  // se debe verificar que no sea el .end(), sino no se puede borrar
  if(itr != mp.end())
    mp.erase(itr);
  cout << mp.size() << "\n";
  return 0;
}
```

### Aprovechar que esta ordenado

Ahora, dado que es un diccionar ordenado se podrán aplicar operaciones que nos permitirán no solo verificar si un elemento está o no. Se tiene acceso a dos funciones:

* `mp.lower_bound(llave)`, el cual retorna un iterador que apunta al primer par donde la llave del par que no sea menor a la llave preguntada.
* `mp.upper_bound(llave)`, el cual retorna un iterador que apunta al primer par donde la llave del par que sea mayor a la llave preguntada.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  map< int, int > mp;
  mp.insert({2, 3});
  mp.insert({1, 10});
  mp.insert({4, 4});
  mp.insert({7, 20});
  mp.insert({8, 21});

  map< int, int >::iterator itr = mp.lower_bound(4);
  // siempre verificar primero que el iterador no sea el .end(), porque eso 
  // significaría que la llave no esta
  if(itr != mp.end()) {
    // se mostrará (4, 4)
    cout << "(" << itr->first << ", " << itr->second << ")\n";
  }

  itr = mp.lower_bound(6);
  if(itr != mp.end()) {
    // en el ejemplo se mostraría: (7, 20)
    cout << "(" << itr->first << ", " << itr->second << ")\n";
  }
  
  itr = con.upper_bound(4);
  if(itr != con.end()) {
    // en el ejemplo se mostraría: (7, 20)
    cout << "(" << itr->first << ", " << itr->second << ")\n";
  }
  return 0;
}
```

### Recorrer el diccionario

Gracias a C++, se puede recorrer todos los pares (llave, valor) de manera ordenada en el diccionario, el diccionario ordena en base a la llave.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main() {
  map< int, int > mp;
  mp.insert({2, 3});
  mp.insert({1, 10});
  mp.insert({4, 4});
  mp.insert({7, 20});
  mp.insert({8, 21});

  // metodo 1: iteradores
  // * se inicializa el iterador en el .begin() del diccionario, o sea en el primer par (llave, valor)
  // * el for dura mientras el iterador sea distinto de .end(), ya que si llega significa 
  //   esta en el final y por lo tanto debe dejar de recorrer
  // * la operacion ++ esta sobrecargada y permite avanzar al siguiente iterador en la estructura
  // 
  // para este ejemplo, se mostrarán los elementos de menor a mayor
  for(map< int, int >::iterator itr = mp.begin(); itr != mp.end(); itr++)
    cout << "(" << itr->first << ", " << itr->second << ") ";
  cout << "\n";
  
  // metodo 2: for each
  // por cada ciclo del for se generará una copia de los pares (llave, valor) del diccionario
  // partiendo desde .begin() hasta el .end()
  // 
  // al igual que antes, se mostrarán los elementos de menor a mayor
  for(pair< int, int > p : mp)
    cout << "(" << p.first << ", " << p.second << ") ";
  cout << "\n";
  return 0;
}
```

## Diccionarios Desordenados

Los conjuntos desordenados, a diferencia del otro tipo de diccionarios, este no mantiene un orden entre los pares (llave, valor). Esto debido a que realiza el manejo de los datos a través de una [función de hashing](https://en.wikipedia.org/wiki/Hash_function). Los diccionarios desordenados tienen casi las mismas funciones, pero al no estar ordenados pierden la habilidad de aplicar funciones como `lower_bound` o `upper_bound`.

```cpp
#include<bits/stdc++.h> 
using namespace std;
 
int main(){
  unordered_map< char, int > mp;

  // aqui almacenamos 3 llaves: a, c y D
  // donde a -> 2, c -> 3 y D -> 1
  mp.insert({'a', 2});
  mp.insert({'c', 3});
  mp.insert({'D', 1});

  // se busca la llava a
  map< char, int >::iterator itr = mp.find('a');
  if(itr != mp.end()) {
    cout << "(" << itr->first << ", " << itr->second << ")\n";
  } else {
    cout << "La llave no esta\n";
  }

  // también se pueden recorrer
  for(pair< int, int > p : mp)
    cout << "(" << p.first << ", " << p.second << ") ";
  cout << "\n";
  return 0;
}
```

## Complejidades

Ahora que se conocen las dos formas de utilizar diccionarios en C++, analizemos las complejidades. 

Comenzando por los diccionarios ordenados, usan una implementación de *Red-Black Tree* y este es un árbol binario balanceado, las complejidades de las operaciones se regirán en cuánto nos costaría recorrer una rama del árbol para poder buscar/insertar/eliminar. Es por esto que las operaciones buscar/insertar/eliminar son todos $O(log n)$ en peor caso.

En cambio, los diccionarios desordenados para insertar/buscar elementos lo realiza a través de una función de hashing, gracias a esto las operaciones se pueden hacer en tiempo promedio $O(1)$, pero puede llegar a tener peor caso $O(n)$, donde $n$ es la cantidad de pares en el diccionario. Entonces, se debe usar con preocupación, cuando las llaves tienden a ser muy parecidos puede causar que las operaciones sean más lentas.

Aquí se presenta una tabla resumen al respecto de las complejidades y de algunas operaciones:

| Operaciones  | Diccionario Ordenado | Diccionario Desordenado         |
|--------------|-------------------|------------------------------|
| insert       | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| erase        | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| find         | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| lower_bound  | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |
| upperd_bound | Worst $O(log n)$  | Average $O(1)$, Worst $O(n)$ |

## Referencias

* Map - [https://cplusplus.com/reference/map/map/](https://cplusplus.com/reference/map/map/)
* Unordered Map - [https://cplusplus.com/reference/unordered_map/](https://cplusplus.com/reference/unordered_map/)
  
## Problemas
