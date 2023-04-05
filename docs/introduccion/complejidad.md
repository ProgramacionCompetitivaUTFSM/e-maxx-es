# Complejidad algorítmica

> **Tabla de Contenidos**
> * [Definición simple](#definicion-simple)
> * [Ejemplos básicos](#ejemplos-basicos)
> * [Dato Freak](#dato-freak)

## Definición simple

La complejidad algorítmica corresponde a un área de estudio en el cual uno podrá determinar cuántos recursos utiliza un algoritmo, recursos como es el tiempo que utiliza y el espacio que utiliza. La complejidad se aplica para buscar la función que se comporte como el algoritmo, según el input que este reciba. Existe varias noticiones dentro de esta área: **o** o *"o chica"*, **O** o *"O grande"*, **$\theta$** o *"theta"*, **$\omega$** o *"Omega chica"* y **$\Omega$** o *"Omega grande"*. 

Para lo que es la programación competitiva, nos concentraremos en **O** o *O grande*. Esta notación corresponde a que el algoritmo que se esta aplicación a lo más se va a comportar como la función dada. Por ejemplo, $O(n)$ quiere decir que el algoritmo que siga esta función tenderá a demorarse en el peor de los casos $n$ unidades de tiempo. Como lo pueden deducir, este tópico es muy relevante para la disciplina, debido a que analizando el algoritmo uno podría saber si es que vale la pena programarlo para resolver el problema o no. Permitiendo así que no pierdan tiempo desarrollando una solución que no servirá.


## Ejemplo básicos

### Ejemplo 1: Tiempo 1

```cpp
#include<bits/stdc++.h> 
using namespace std;

int main(){
	int suma = 0;
	int n;
	cin >> n;
	suma = suma + 1;
	cout << suma << "\n";
	return 0;
}
```

En este ejemplo, se puede ver como simplemente aplica $5$ operaciones simples, entonces es aproximadamente $O(1)$.

### Ejemplo 2: Tiempo lineal

```cpp
#include<bits/stdc++.h> 
using namespace std;

int main(){
	int suma = 0;
	int n;
	cin >> n;
	for(int i = 0; i < n; i++){
		suma++;
	}
	cout << suma << "\n";
	return 0;
}
```

En este ejemplo, se puede ver que solo se aplica un `for`, que realiza $n$ operaciones suma, entonces la función que más se acerca es $n$, por lo que podemos decir que este algoritmo es de complejidad $O(n)$.

### Ejemplo 3: Tiempo cuadrático

```cpp
#include<bits/stdc++.h> 
using namespace std;

int main(){
	int suma = 0;
	int n;
	cin >> n;
	for(int i = 0; i < n; i++){
		for(int i = 0; i < n; i++){
			suma++;
		}
	}
	cout << suma << "\n";
	return 0;
}
```

En este ejemplo, se puede visualizar que existen dos `for` anidados y que ambos dependen de un $n$ ingresado por consola. El `for` de más adentro (llamémoslo $for_2$) debe realizar $n$ sumas de $1$, y el `for` de más afuera (llamémoslo $for_1$) debe realizar $n$ veces el $for_2$, por lo que al tener que hacer $n$ veces algo que hace $n$ operaciones la complejidad de este algoritmo será $O(n\cdot n)= O(n^2)$.

### Ejemplo 4: Tiempo logarítmico

```cpp
#include<bits/stdc++.h> 
using namespace std;

int main(){
	int suma = 0;
	int n;
	cin >> n;
	for(int i = 1; i <= n; i *= 2){
		suma += 1;
	}
	cout << suma << "\n";
	return 0;
}
```

En este ejemplo, se puede visualizar que el `for` que uno está realizando parte en `i = 1` y realiza aumentos multiplicando el $i$ actual por $2$. Entonces, $i$ tendrá los siguientes valores: $1$, $2$, $4$, $8$ y así, hasta que $i$ sea mayor que $n$. Si es que analizan correctamente cuantas veces hace la operación `suma += 1`, se darán cuenta que esta operación se hará $\log n$ veces aproximadamente. Por lo que la complejidad de este algoritmo será de $O(\log n)$.


## Dato Freak

Como se mencionó en la sección "¿Qué es la ProgComp?", cada problema tiene un tiempo definido y un input, gracias a esta información uno puede determinar que tipos de complejidades se esperan del problema y por lo tanto reducir el abanico de opciones a alguno más limitado. La siguiente tabla indica la complejidad de un algoritmo **APROXIMADAMENTE** debería tener para no pasar cierto tiempo límite.

| Tamaño del input: $n$            | Peor complejidad aceptada |
|--------------|---------------------------|
| $<= [10..11]$  | $O(n!)$, $O(n^6) $            |
| $<= [15..18]$  | $O(2^n \cdot n^2)$          |
| $<= [18..22]$  | $O(2^n \cdot n) $           |
| $<= 100$       | $O(n^4)$                    |
| $<= 400$       | $O(n^3) $                   |
| $<= 2000$     | $O(n^2 \log_2 n)$           |
| $<= 10000$    | $O(n^2)$                    |
| $<= 1000000$   | $O(n \log_2 n) $            |
| $<= 100000000$ | $O(n)$, $O(\log_2)$, $O(1)$     |
