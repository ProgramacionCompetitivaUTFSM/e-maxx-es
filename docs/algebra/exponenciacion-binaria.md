# Exponenciación Binaria

> **Tabla de Contenidos:**
> * Algoritmo
> * Implementación
> * Aplicaciones
> 	* Cálculo eficaz de la operación módulo aplicada a grandes exponentes 
> 	* Cálculo eficaz de los Números de Fibonacci
> 	* Realizar *k* veces una permutación
> 	* Aplicación rápida de un conjunto de operaciones geométricas a un conjunto de puntos
> 	* Número de caminos de largo *k* en un grafo
> 	* Variación de la exponenciación binaria: Aplicar la operación módulo a la multiplicación de 2 números
> * Problemas para practicar

La Exponenciación Binaria (también conocida como exponenciación por cuadrados) es un truco que permite calcular $ a^{n} $ utilizando sólo $ O(\log n) $ multiplicaciones (en vez de $ O(n) $ con el enfoque tradicional).

Esta técnica tiene importantes aplicaciones en áreas no relacionadas con la aritmética, dado que puede ser utilizada con cualquier operación que cumpla con la propiedad de **asociatividad**:

<div align="center">$ (X \cdot Y) \cdot Z = X \cdot (Y \cdot Z) $</div>

## Algoritmo

La operación $ a^{n} $ es generalmente se ve como la multiplicación de $ a $ por sí mismo $ n-1 $ veces: $ a^{n} = a \cdot a \cdot \ldots \cdot a $. Sin embargo, este no es un enfoque práctico para grandes valores de $ a $ o de $ n $.

<div align="center">$ a^{b+c} = a^{b} \cdot a^{c}$ y $a^{2b} = a^{b} \cdot a^{b} = {(a^{b})}^{2}$</div>

La idea de la exponenciación binaria es dividir el trabajo utilizando la representación binaria del exponente.

Por ejemplo, escribamos el exponente $n = 13$ en base 2:

<div align="center">$3^{13} = 3^{1101_2} = 3^8 \cdot 3^4 \cdot 3^1$</div>

Dado que $n$ tiene exactamente $\lfloor \log_2 n \rfloor + 1$ dígitos en base 2, basta con realizar $O(\log n)$ multiplicaciones para calcularlo si conocemos las potencias de $ a^1, a^2, a^4, a^8, \dots, a^{\lfloor \log n \rfloor} $.

Ahora sólo necesitamos conocer una manera rápida de computar éstas potencias. Por suerte esto es muy fácil, dado que cada elemento de la secuencia es el cuadrado del elemento anterior.

<div align="center">
$
	\begin{alignedat}{2}
		3^1 &= 3 \\
		3^2 &= \left(3^1\right)^2 = 3^2 = 9 \\
		3^4 &= \left(3^2\right)^2 = 9^2 = 81 \\
		3^8 &= \left(3^4\right)^2 = 81^2 = 6561
	\end{alignedat}
$
</div>

Por lo tanto, para calcular $ 3^{13} $ sólo debemos multiplicar 3 elementos de la secuencia de arriba (ignorando $ 3^{2} $ porque el bit correspondiente no está encendido): $ 3^{13} = 6561 \cdot 81 \cdot 3 = 1594323 $

La complejidad final de este algoritmo es $O(\log n)$: debemos computar $ \log n $ potencias de $a$, y luego realizar a lo más $ \log n $ multiplicaciones para obtener la respuesta final.

También podemos expresar esta idea utilizando un enfoque recursivo:

<div align="center">$
a^n = \begin{cases}
1 &\text{if } n == 0 \\
\left(a^{\frac{n}{2}}\right)^2 &\text{if } n > 0 \text{ and } n \text{ even}\\
\left(a^{\frac{n - 1}{2}}\right)^2 \cdot a &\text{if } n > 0 \text{ and } n \text{ odd}\\
\end{cases}
$</div>

## Implementación

Para empezar, veamos un enfoque recursivo, el cual es una traducción directa de la fórmula anterior:

```cpp
long long binpow(long long a, long long b) {
    if (b == 0)
        return 1;
    long long res = binpow(a, b / 2);
    if (b % 2)   
        return res * res * a;
    else
        return res * res;
}
```

<div align="center">$
\begin{pmatrix}
a_{11} & a_ {12} & a_ {13} & a_ {14} \\
a_{21} & a_ {22} & a_ {23} & a_ {24} \\
a_{31} & a_ {32} & a_ {33} & a_ {34} \\
a_{41} & a_ {42} & a_ {43} & a_ {44} \\
\end{pmatrix}
$</div>

<div align="center">$
a^n = \begin{cases}
1 &\text{if } n == 0 \\
\left(a^{\frac{n}{2}}\right)^2 &\text{if } n > 0 \text{ and } n \text{ even}\\
\left(a^{\frac{n - 1}{2}}\right)^2 \cdot a &\text{if } n > 0 \text{ and } n \text{ odd}\\
\end{cases}
$</div>


<div align="center">$
a \cdot b = \begin{cases}
0 &\text{if }a = 0 \\
2 \cdot \frac{a}{2} \cdot b &\text{if }a > 0 \text{ and }a \text{ even} \\
2 \cdot \frac{a-1}{2} \cdot b + b &\text{if }a > 0 \text{ and }a \text{ odd}
\end{cases}
$</div>

## Aplicaciones

### Cálculo eficaz de la operación módulo aplicada a grandes exponentes 

### Cálculo eficaz de los Números de Fibonacci

### Realizar *k* veces una permutación

### Aplicación rápida de un conjunto de operaciones geométricas a un conjunto de puntos

### Número de caminos de largo *k* en un grafo

### Variación de la exponenciación binaria: Aplicar la operación módulo a la multiplicación de 2 números

## Problemas para practicar
