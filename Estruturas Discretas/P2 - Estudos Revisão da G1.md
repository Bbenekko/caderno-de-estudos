
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
## Definições que posso esquecer:
- Definição de passeio:![[Pasted image 20260621203055.png]]
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
