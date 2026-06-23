
# Grafos - Introdução
---
## Definições que posso esquecer:
- Um grafos **simples** é um grafo que não tem **loops** e nem **arestas**.

## Teoremas relevantes:
- Para qualquer grafo G = (V, E), soma dos graus = 2 x arestas
	S(G) = 2 * |E|

- Em todo grafo, o número de vértices (nós) de **grau ímpar** é **par**.
	*Menos relevante!!*

# Grafos - Caminhos e passeios
---
## Definições:
- Definição de **passeio**:![[Pasted image 20260621203055.png]]
- **Caminho:** É um passeio em que todos os vértices são distintos.

## Teoremas e lemas relevantes:
- Se existe um **passeio** de *u* para *v* , então existe um caminho de *u* pra *v* ?
	*Sim!* Começa-se um passeio e vai cortando as repetições!

- Considere um grafo **simples** *G*. Suponha que o grau de todos os nós em *G* é pelo menos *k* . Então *G* possui um caminho com ≥ k + 1 nós.

---

## Conectividade:
Um grafo é **conexo/conectado** se para todo par de nós *u* e *v*, existe um caminho no grafo entre *u* e *v*.
![[Pasted image 20260621203915.png]]
### Grafo conexos                                x                   não conexo
![[Pasted image 20260621203851.png]]

# Grafos - Ciclos e Árvores
---
## Ciclo:
É um caminho que começa e termina no mesmo nó.
#### Proposição:
Seja *G* um grafo **simples** onde todos os nós tem grau pelo menos *2*. Então *G* tem um ciclo.

## Árvores:
Uma **árvore** é um grafo conexo e sem ciclos *(acíclico)*.

#### Teorema:![[Pasted image 20260622103516.png]]

![[Pasted image 20260622104222.png]]

## Floresta:
Uma floresta é um grafo *G* em que todos os componentes conexos são árvores (ou seja, é uma união de árvores disjuntas)

#### Preposição:

![[Pasted image 20260622103721.png]]
#### Teorema:
![[Pasted image 20260622103814.png]]
*OBS: Olhar prova no slide*


# Grafos - Árvores e Árvores geradoras mínimas
---
## Árvore Geradora Mínima
Supõe-se que grafos possuem "custos".

![[Pasted image 20260622104422.png]]

Forma "mais barata" de formar um caminho entre dois vértices.

Esse subconjunto deve:
1. Ser conexo
2. Esse subconjunto mínimo deve ser menor ou igual a todos os outros subconjuntos possível.

### Exemplo:
![[Pasted image 20260622104626.png]]

### Observação:
Se um grafo possui ciclos, sempre é possível encontrar a árvore mínima, através da eliminação de certas arestas!
#### Propriedades:
![[Pasted image 20260622104840.png]]

## Algoritmos para encontrar AGM

### Simples:
![[Pasted image 20260622105012.png]]
*Na prática usaremos algoritmos mais simples!*

### AGM Clustering:
![[Pasted image 20260622105323.png]]

# Grafos Bipartidos
---
## Definição:
![[Pasted image 20260622105432.png]]

## Grafo bipartido completo
Um grafo simple bipartido é completo quando todo vértice possui ligação com todos os vértices da outra extremidade.
Imagem de exemplo:
![[Pasted image 20260622105649.png]]

Utilizasse $$K_{m,n}$$
onde $$|X| = n \text{ e } |Y| = m$$

## Definições:
![[Pasted image 20260622110500.png]]
OU SEJA

**TODO GRAFO SIMPLES SEM NENHUM CICLO DE COMPRIMENTO ÍMPAR PODE SER BIPARTIDO**

### Adicionais:

Toda **árvore é um grafo bipartido**, pois árvores não possuem ciclos, logo não tem ciclo impar.
Porém **nem todo grafo bipartido é uma árvore**, pois grafos bipartidos podem ter ciclos pares.

# Grafos Eulerianos
---
## Definição:
Um **trajeto euleriano** é um **passeio** onde cada **aresta** é visitada apenas **1 única** vez!

Exemplos:
![[Pasted image 20260622111137.png]]

### Teoremas:
![[Pasted image 20260622111650.png]]

Como consequência, temos:

![[Pasted image 20260622111751.png]]

#### Consequências disso:
![[Pasted image 20260622111843.png]]
E
![[Pasted image 20260622111857.png]]

# Grafos direcionados:
---
## Definição:
![[Pasted image 20260622111957.png]]
### Grau de entrada:
![[Pasted image 20260622112114.png]]

### Grau de saída:
![[Pasted image 20260622112124.png]]

### Relação entre eles:
![[Pasted image 20260622112250.png]]

### Logo:
![[Pasted image 20260622112857.png]]
## Lemas:
![[Pasted image 20260622112333.png]]

## Grafos Direcionados Acíclicos (DAG):

![[Pasted image 20260622112406.png]]

## Ordenação topológica:
![[Pasted image 20260622112536.png]]

Exemplo:
![[Pasted image 20260622112634.png]]

### IMPORTANTE!
![[Pasted image 20260622112939.png]]

## Representações computacionais:
### Matrix
![[Pasted image 20260622113053.png]]

Dessa forma, caso o grafo seja direcionado, a matrix será assimetrica:

![[Pasted image 20260622113135.png]]

### Lista:
![[Pasted image 20260622113243.png]]

# Caminho mais curto
--- 
Caminho mais curto ou CMC

## Lemas:
![[Pasted image 20260622113530.png]]

## Algoritmo Dijkstra
A ideia é encontrar o CMC até o vértice mais próximo, e fazer isso consecutivamente até o destino.

Explicação: https://youtu.be/_lHSawdgXpI?si=b9A4j3CHhlzEubLM

# Coloração de Vértices
---
## Definições:

![[Pasted image 20260622114548.png]]
![[Pasted image 20260622114605.png]]

Número cromático:
![[Pasted image 20260622114622.png]]

### Outras definições:
![[Pasted image 20260622114901.png]]

### Mais definições:

**Se o grafo possui nós com graus pequenos, o número cromático também será pequeno!!**

## Proposições:

![[Pasted image 20260622115033.png]]

# Emparelhamento
---

## Definição:
Um **emparelhamento** *M* é um conjunto de **arestas** que não compartilham nenhum **nó**.

Também pode ser chamado de **casado**!

## Caminho aumentante:

![[Pasted image 20260622120339.png]]

Por exemplos:
![[Pasted image 20260622120431.png]]

O caminho:  **de -> eg -> ga -> af -> fb** é um caminho aumentante!

Porém: **de -> eg -> ga -> af -> fb -> bc -> cd** não é, pois repete nós, o que não o torna um caminho!

## Teorema de Berge:

![[Pasted image 20260622120917.png]]

![[Pasted image 20260622120950.png]]

## Emparelhamento perfeito:
![[Pasted image 20260622121012.png]]

![[Pasted image 20260622121024.png]]

## Teorema de Hall:
![[Pasted image 20260622121523.png]]

![[Pasted image 20260622121534.png]]


# Fluxo em redes
---
## Definição:
![[Pasted image 20260622143222.png]]

### Exemplo:
![[Pasted image 20260622143443.png]]

## Outras definições:
![[Pasted image 20260622234323.png]]

![[Pasted image 20260622234343.png]]

## Corte:
![[Pasted image 20260622234402.png]]
![[Pasted image 20260622234520.png]]

### Lema de corte:
![[Pasted image 20260622234553.png]]

![[Pasted image 20260622234625.png]]

# Fluxo em Redes II
---

## Rede residual:
![[Pasted image 20260622234759.png]]

![[Pasted image 20260622234812.png]]
![[Pasted image 20260622235006.png]]
![[Pasted image 20260622235023.png]]

![[Pasted image 20260622235040.png]]

![[Pasted image 20260622235046.png]]
![[Pasted image 20260622235057.png]]

## Algoritmo de Ford-Fulkerson

![[Pasted image 20260622235124.png]]

![[Pasted image 20260622235143.png]]

