
# Conceitos de Desempenho

## Fatores de desempenho:
- ** $f$ ** - Velocidade de clock
- **$\tau$** - Tempo de Clock
$$
\tau = \frac{1}{f}
$$ 
### CPI

- **$CPI$** - Média de ciclos por instrução
- **$I_i$** - número de instruções de máquina do tipo *i* executada pelo programa
- **$CPI_i$** - número de ciclos por instrução do tipo *i*
- **$I_c$** - número de instruções de máquina executadas pelo programa

$$
I_c = \sum_{i=1}^n{I_i}
$$
$$
CPI = \frac{\sum_{i=1}^n CPI_i \times I_i}{I_c}
$$
### T

- **T** - tempo de processador necessário para executar o programa
$$
T = I_c \times CPI \times \tau
$$
- **p** - número de ciclos de processador necessários para decodificar e executar a instrução
- **m** - número de referências da memória necessárias
- **k** - razão entre o tempo de ciclo da memória e o tempo de ciclo do processador
- Pode ser refinado para:
$$
T = I_c \times [p+(m \times k)] \times \tau
$$

### MIPS
- **MIPS** ou Milhões de instruções por segundo, é a taxa de execução de instrução.
- Fortemente dependente do conjunto de instruções , projeto de compilador , implementação do processasdor , hirarquia de cache e memória.
$$
MIPS = \frac{I_c}{T \times 10^6} = \frac{f}{CPI \times 10^6}
$$

### Atributos do sistema que afetam os fatores de desempenho
![[Pasted image 20260910113735.png]]

## Lei de Amdahl

- Estima o speedup potencial de um programa utilizando múltiplos processadores

- **T** - tempo total de execução de um programa em um único processador
- **N** - número de processadores que exploram totalmente as partes paralelizáveis do código
- **f** - fração do código que pode ser paralelizada, sem overhead de escalonamento
- **(1 - f)** - fração do código que é inerentemente serial
$$
Speedup = \frac{T(1-f)+Tf}{T(1-f)+\frac{Tf}{N}} = \frac{1}{(1-f)+\frac{f}{N}}
$$

#### Conclusões:
- Se *f* for pequeno, o uso de processadores paralelos é pouco efetivo.
- N-> $\infty$, speedup é limitado a 1/(1-f)

*Falta finalzinho de lei de Amdahl*