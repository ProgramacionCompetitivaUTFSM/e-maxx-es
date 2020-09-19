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

La Exponenciación Binaria (también conocida como exponenciación por cuadrados) es un truco que permite calcular $a^{n}$ utilizando sólo $\mathcal{O}(log (n))$ multiplicaciones (en vez de $\mathcal{O}(n)$ con el enfoque tradicional).

Esta técnica tiene importantes aplicaciones en áreas no relacionadas con la aritmética, dado que puede ser utilizada con cualquier operación que cumpla con la propiedad de **asociatividad**:

<div align="center">$(X \cdot Y) \cdot Z = X \cdot (Y \cdot Z)$</div>