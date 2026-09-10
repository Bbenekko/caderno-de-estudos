
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
- **T** - tempo de processador necessário para executar o programa
$$
T = I_c \times CPI \times \tau
$$
