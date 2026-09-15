
# Conceitos de Desempenho

## Fatores de desempenho:
- **$f$** - Velocidade de clock
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

### Conclusões:
- Se *f* for pequeno, o uso de processadores paralelos é pouco efetivo.
- N-> $\infty$, speedup é limitado a 1/(1-f)
### Generalização:
- Generalização de qualquer melhoria:
$$
Speedup = \frac{tempo \ de \ execução \ antes \ da \ melhoria}{tempo \ de \ execução \ depois \ da \ melhoria}
$$
- Suponha que o recurso do sistema seja usado durante a execução de uma
fração do tempo $f$, antes da melhoria, e que o $speedup$ desse recurso após a
melhoria seja $SU_f$

$$
Speedup = \frac{1}{(1-f)+\frac{f}{SU_f}}
$$

## Benchmarks

![[Pasted image 20260913135424.png]]

- **O que são:** São programas *projetados para testar desempenho*
- Escritos em *linguagem de alto nível* (python, javascript, etc) -> **Portáveis!!**
- Amplamente distribuídos

### Mais a fundo
- A coleção mais conhecida é a SPEC *(Standard Performance Evaluation Corporation)*
- A suíte mais conhecida da SPEC é a *CPU2017*
	- Contém 43 benchmarks organizados em quatro suítes
	- Contém uma métrica opcional para medir consumo de energia

---

### Continuando
- Ao executar *m* diferentes benchmarks, obtém-se uma comparação mais confiável
- A taxa de execução de instruções pode ser expressa por meio de:

$$
R_a = \frac1m \sum^m_{i=1}R_i \ \ \ \ Média \ Aritmética!
$$
ou
$$
R_h = \frac{m}{\sum^m_{i=1}\frac1{R_i}} \ \ \ \ Média \ Harmônica!
$$

*Onde $R_i$ é a taxa de execução de instrução do i-ésimo benchmark*

---

- Benchmarks SPEC não se preocupam com as taxas de execução de instrução.
- O runtime básico é definido para cada programa de benchmark usando uma máquina de referência.
- A métrica de velocidade é a **razão** entre o **tempo de execução de referência** e o **tempo de execução do sistema em teste**.
$$
r_i = \frac{Tref_i}{Tsut_i}
$$
	- $Tref_i$ - tempo de execução do benchmark *i* na referência
	- $Tsut_i$ - tempo de execução do benchmark *i* no teste

## SPEC speed meter

- O desempeho geral é calculado para o sistema em teste considerando a média dos valores para as razões de todos os benchmarks.

$$
r_G = (\prod^n_{i=1}r_i)^{1/n}
$$

---

# Códigos de Detecção e correção de erro

## Ideia Básica

- **m** = tamanho da palavra
- Para representar $2^m$ palavras utilizam-se **n = r + m** bits (*r* bits além do necessário)
- Com todos esses bits, pode-se representar:
	- $2^{m+r}$ palavras possível
	- $2^m$ palavras **válidas**
	- $2^m (2^r-1)$ palabras **inválidas**
- **O sistema só gera palavras válidas!!**
- Logo, *palavras inválidas são erros!*

## Definições

- **Código**
	- Conjunto de Palavras válidas!
- **Erro Simples**
	- Alteração de uma palavra válidas em um único bit
- **Distância de Hamming entre palavras**
	- É o número de bits em que palavras diferem.
	![[Pasted image 20260913181748.png]]
	- Também referida como **H**!
- **Distância de Hamming de um código**
	- é a menor distância de Hamming entre 2 palavras do código
	![[Pasted image 20260913181823.png]]

## Detecção de erro

- Para que uma plalavra válida de um código com
$$
H = d
$$
	se transforme numa outra palavra válida do mesmo código, deverão ocorrer pelo menos **d** erros simples.

- Logo, um código capaz de detectar **d** erros simples deve ter:
$$
H \ge d+1
$$
### Exemplo: Bit de paridade

![[Pasted image 20260913182224.png]]

---

![[Pasted image 20260913182235.png]]

## Correção de erro
### Ideia Básica

- **Qualquer palavra inválida é substituída pela válida mais próxima ( em termos de distância de Hamming)
- Logo, um código será capaz de corrigir até **c** erros simples, se e somente se
$$
H \ge 2c+1
$$
### Problema
Suponha que se deseja construir um código contendo $2^m$ palavras válidas, capaz de corrigir até *1* erro simples.
Quantos bits extra serão necessários **(r=?)**?

### Solução
![[Pasted image 20260913183216.png]]

### Conclusão

![[Pasted image 20260913183315.png]]

---

![[Pasted image 20260913183331.png]]

## Código de Hamming

https://youtu.be/yx79VIMEBMw?si=XJIhTtxUbpRstnZ6

Construindo um código de correção de *1* erro simples para $2^m$ palavras
- Acrescentam-se **r** bits de paridade: total de $m+r$ bits por palavra
- Bits são numerados de 1 a $m+r$
- Posições de potência inteira de 2 têm os bits de paridade

![[Pasted image 20260913191026.png]]

![[Pasted image 20260913191038.png]]

O que acontece no caso de **2** erros simples?

![[Pasted image 20260913191103.png]]

## SECDED (Single Error Correction, Double Error Detection)

NEcessário adicionar **1 bit de paridade global**
Código SECDED $2^m$ palavras
![[Pasted image 20260913191223.png]]

![[Pasted image 20260913191255.png]]

---

*Voltando:* O que acontece no caso de **2** erros simples?

![[Pasted image 20260913191344.png]]

# Memória Interna

## Operação de uma Célula de Memória

Em geral, uma célula de memória possui três terminais funcionais capazes de transportar um sinal elétrico.

![[Pasted image 20260913191551.png]]

## Características da Memória


| Características                           | Descrição                                                                                                                      |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Volátil vs. Não-Volátil                   | Se a memória perde ou retém seu conteúdo quando a energia é desligada.                                                         |
| Velocidade de<br>Leitura/Escrita          | A velocidade com que os dados podem ser lidos ou gravados na memória.                                                          |
| Resistência (Endurance)                   | O número de ciclos de gravação/apagamento que uma memória pode sofrer antes de<br>começar a falhar.                            |
| Densidade                                 | A quantidade de dados que pode ser armazenada em uma determinada área física.                                                  |
| Consumo de Energia                        | Importante para dispositivos alimentados por bateria.                                                                          |
| Custo                                     | Especialmente importante para implantações em larga escala ou eletrônicos de<br>consumo.                                       |
| Durabilidade e<br>Confiabilidade          | A capacidade da memória de suportar estresse físico, variações de temperatura e outros<br>fatores ambientais sem perder dados. |
| Capacidade de Apagamento<br>(Erasability) | A facilidade com a qual os dados podem ser apagados e reprogramados.                                                           |
| Retenção de Dados                         | A capacidade da memória de reter dados ao longo do tempo, especialmente no caso de<br>memórias não-voláteis.                   |
## História da memória

==Vou pular! Caso seja necessário, é o slide 4 do material, pág. 5==

## Tipos de Memória Semicondutora

![[Pasted image 20260913192152.png]]

## Tipos de ROM (Read Only Memory)

### Mask ROM

Usada na fabricação de CIs (Circuitos Integrados).
Usada quando o volume necessário é alto (centenas de milhares).

**PROS:**
- Não-Volátil;
- Altas Velocidades de leitura;
- Alta Resistência (endurance) para leitura;
- Baixo consumo de energia;
- Durabilidade e excelente retenção de dados.

**CONS:**
- Não pode ser reescrita

### PROM (Programmable ROM)

Para cada bit de PROM, existe um fusível.
**Uma vez queimado, o fusível não pode ser restaurado!**

**PROS:**
- Não-Volátil;
- Altas Velocidades de leitura;
- Alta Resistência (endurance) para leitura;
- Densidade relativamente menor;
- Bom custo-benefício;
- Baixo custo de energia
- Durabilidade e excelente retenção de dados.

**CONS:**
- Programabilidade única (só pode ser programada uma vez).

### EPROM (Erasable Programmable ROM)

Pode ser programada e apagada muitas vezes.
Especialmente usada no desenvolvimento de protótipos.
Seu conteúdo pode ser apagado incidindo radiação UV através de uma janela – leva cerca de 5 a 20 minutos.

**PROS:**
- Não-Volátil;
- Velocidade moderadas de leitura e escrita;
- Resistência (endurance) comparativamente limitada para leitura;
- Densidade moderada;
- Maior consumo de energia durante a leitura/escrita;
- Alta durabilidade e excelente retenção de dados.

**CONS:**
- Custo mais alto em relação às PROMS;
- Demora para apagar os dados. *(Eu que suponho isso)*

### EEPROM (Electrically EPROM)

Pode ser programada e apagada enquanto está na placa do sistema – não exigindo dispositivo externo.
A gravação é instantânea.
No entanto, é necessário um circuito especial na placa do sistema para utilizá-la totalmente.

**PROS:**
- Não-volátil;
- Leituras relativamente rápidas e velocidade de gravação moderadamente mais lentas;
- Alta resistência (endurance) em comparação com as EPROMS;
- Densidade moderada;
- Maior consumo de energia durante leitura/gravação;
- Alta Durabilidade e excelente retenção de dados.

**CONS:**
- Menor densidade e custo mais alto em relação às PROMS.

### Flash
Será vista posteriormente... (inserir link)

## RAM (Random Access Memory)

Nomeada de forma imprecisa, pois a maioria das memórias semicondutoras é de acesso aleatório!

**Características:**
- Realiza Leitura/Escrita
- Volátil
- Armazenamento temporário
- Estática ou dinâmica

![[Pasted image 20260913194355.png]]

### Static RAM

- Bits armazenados em chaves on/off.
- Sem vazamento de cargas.
- Não necessita de *refresh* enquanto estiver energizada.
- Mais complexa.
- Maior tamanho por bit (em relação a DRAM).
- Mais cara.
- Mais rápida.
- Usada principalmente em **memória cache**.
- Digital -> Usa flip-flop.

#### Estrutura:

![[Pasted image 20260913194642.png]]

![[Pasted image 20260913194652.png]]

---

#### Leitura:
![[Pasted image 20260913194706.png]]

#### Escrita:
![[Pasted image 20260913194714.png]]

### Dynamic RAM (DRAM)

- Bits armazenados como carga em capacitores.
- As cargas vazam (dissipam).
- Necessita de *refresh* mesmo energizada.
- Construção mais simples.
- Menor tamanho por bit.
- Mais **barata**.
- Mais **lenta**.
- Usada na memória principal.
- Essencialmente analógica -> o nível de carga determina o valor.

#### Escrita
![[Pasted image 20260913195044.png]]

#### Leitura
![[Pasted image 20260913195107.png]]

#### Leitura e Escruta:

![[Pasted image 20260913195122.png]]

#### Refreshing

- A carga flui para o capacitor ou a partir dele.
- Precisa ser atualizado *(refresh)* regularmente.
- Circuito de atualização incluído no chip.
- Durante a atualização, o chip fica desativado.
- Feito linha por linha (row-wise).
- A atualização envolve leitura e escrita.
- Leva Tempo.
- Reduz o desempenho aparente.

![[Pasted image 20260913200156.png]]

#### Típica 16 mB DRAM (4M por 4)

![[Pasted image 20260913200237.png]]

![[Pasted image 20260913200255.png]]

#### Operação de um chip DRAM

![[Pasted image 20260913200328.png]]

#### Operação de Refresh

![[Pasted image 20260913200507.png]]

#### Organização Modular

**Exemplo:** Construindo uma memória de 256K com palavras de 8-bits usando DRAM de 256K bit

![[Pasted image 20260913200550.png]]

**Exemplo:** Construindo uma memória de 1M com palavras de 8-bits usando DRAM de 256K bit

![[Pasted image 20260913200620.png]]

### DRAM vs. SDRAM vs. DDR SDRAM
#### DRAM
A **DRAM** original exige a definição dos endereços de linha e coluna para cada dado acessado.

![[Pasted image 20260913200743.png]]

#### SDRAM
Na **DRAM Síncrona (SDRAM)**, uma vez estabelecidos os endereços iniciais de linha e coluna, ela aproveita a sincronização com o clock do sistema para acessar dados subsequentes em cada borda de subida do ciclo de clock.

![[Pasted image 20260913200826.png]]

#### DDR SDRAM
A **SDRAM de Taxa de Transferência Dobrada (DDR SDRAM)** acessa dados tanto na borda de
subida quanto na de descida do ciclo de clock, após os endereços de linha e coluna terem sido definidos.

![[Pasted image 20260913200914.png]]

### Gerações DDR

![[Pasted image 20260913201013.png]]

![[Pasted image 20260913201022.png]]

### Função de Corretor de Erros

![[Pasted image 20260913201134.png]]

### SRAM vs. DRAM

![[Pasted image 20260913201150.png]]

## Hierarquia

Hierarquia de memória típica:
![[Pasted image 20260913201223.png]]

## Memória Flash

- Mosfet NMOS.
- Uma pequena tensão aplicada ao gate pode ser usada para controlar o fluxo de uma corrente grande entre o source e o drain.

![[Pasted image 20260913201339.png]]

---
- Em uma célula de memória flash, o *floating gate* é adicionado ao transistor.
- Inicialmente, o floating gate não interfere no funcionamento.
- Nesse estado, a célula é considerada representando o valor **1**.

![[Pasted image 20260913201505.png]]

---
- Aplicando alta tensão através da camada de óxido, elétrons conseguem atravessem e ficam presos no floating gate.
- Nesse estado, a célula é considerada como representando o valor 0.
- Este estado permanece mesmo que a energia seja desligada.

![[Pasted image 20260913201627.png]]

---
- O estado da célula pode ser lido usando circuitos externos para verificar se o transistor está conduzindo ou não.
- Aplicando uma alta tensão na direção oposta (drain ou source), os elétrons são removidos do floating gate, retornando ao estado de valor binário 1.
- Depende se é do tipo *NOR* ou *NAND*.
- Uma característica importante da memória flash é que ela é uma memória **não volátil**.

## PC-RAM (Phase-change RAM)

Acredito que não caíram, mas caso apareça, é no slide 4, pág. 58

## ReRAM (Resistive RAM)

Acredito que não caíram, mas caso apareça, é no slide 4, pág. 61

# Estruturas de Interconexão

## Tipos de Unidades

### Processador

- Lê instruções e dados
- Escreve dados
- Usa sinais de controle para controlar a operação geral do sistema
- Recebe sinais de interrupção

![[Pasted image 20260914003613.png]]

### Memória

- Normalmente, um módulo de memória consiste de **N** palavras do mesmo tamanho
- Cada palavra recebe um endereço numérico **exclusivo**
- Uma palavra de dados pode ser lida ou escrita na memória
- A natureza da operação é indicada por sinais de controle de leitura e escrita
- O local para a operação é especificado por um endereçõ

![[Pasted image 20260914003918.png]]

### Módulo de E/S (IO)

- Existem duas operações: **leitura** e **escrita**
- Um módulo de E/S pode controlar mais de um dispositivo externo
- Cada interface para dispositivo externo pode ser vista como uma porta, contendo um endereço exclusivo
- Existem caminhos de dados externos para a entrada e saída de dados de dispositivos externos
- **Um módulo de E/S pode ser capaz de enviar sinais de interrupção ao processador**

![[Pasted image 20260914004152.png]]

## Tipos de Transferência

- **Memória para processador:**
	- processador lê uma instrução ou uma unidade de dados da memória.

- **Processador para memória:**
	- processador escreve uma unidade de dados na memória.

- **E/S para processador:**
	- processador lê dados de um dispositivo de E/S por meio de um módulo de E/S.

- **Processador para E/S:**
	- processador envia dados para o dispositivo de E/S.

- **E/S de ==ou== para a memória:**
		- um módulo de E/S tem permissão para trocar dados diretamente com a memória, sem passar pelo processador, usando o DMA (Direct Memory Access)

## Estruturas de interconexão

1. Estruturas de **barramento paralelo** e múltiplos barramentos paralelos.
2. Estruturas de **interconexão ponto a ponto** com transferência de dados em pacotes.

## Barramentos

Um **barramento** *(bus)* é um caminho elétrico comum entre múltiplos dispositivos.

![[Pasted image 20260914004715.png]]

![[Pasted image 20260914004729.png]]

---
### Barramento de Dados

- Transporta **dados** %%EU SEI KKKKKKKKKKKKKKKKKKKK%%
	- *Não há diferença entre "dado" e "instrução" neste nível!*
- A **largura de barramento** de dados determina a **quantidade de dados movidos** em um único acesso, por ex: *8*, *16*, *32*, *64 bits*

![[Pasted image 20260914004953.png]]

### Barramento de Endereço

- Identifica a **origem** ou **destino** dos dados
	- *Ex:* A *CPU* necessita ler uma instrução *(dado)* a partir de uma localização da memória.

- A **largura de barramento de endereço** determina a capacidade de memória máxima do sistema
	- *Ex:* Z80 possui barramento de endereço de 16-bit oferecendo 64k de espaço de endereço

![[Pasted image 20260914005222.png]]

### Barramento de Controle

- Transporta informações de controle e sincronização

- Linhas de controle típicas:
	- **Escrita/Leitura de Memória**
	- **Escrita/Leitura de E/S**
	- **Requisição/ACK de interrupção**
	- **Requisição/ACK de barramento**
	- **Clock**
	- **Reset**

![[Pasted image 20260914005405.png]]

### Arquitetura Típica de barramento

![[Pasted image 20260914005429.png]]

### História dos barramentos

Vou pular, slide 5

### Arquitetura tradicional

Exemplos: ISA Bus

![[Pasted image 20260914010741.png]]

### Arquitetura de Alto Desempenho

Exemplo: PCI Bus

![[Pasted image 20260914010811.png]]

### Tipos de barramento

#### Dedicado

- Linhas separadas de dados e endereços

#### Multiplexado

- Linhas compartilhadas
- Linha de controle de endereço/dado válido
- **Vantagens**
	- Menos Linhas
- **Desvantagens**
	- Circuito mais complexo
	- Redução de desempenho

### Métodos de arbitragem

Pode haver mais de um mestre de barramento potencial.
**Ex:**
- CPU e controlador de DMA.
	- *DMA - Direct Memory Acessa*
- Múltiplas CPUs num sistema de barramento compartilhado paralelo.

Um mecanismo de **arbitragem** é necessário para garantir que apenas um mestre controle o barramento por vez

Porque?

![[Pasted image 20260914102758.png]]

#### Centralizado

Um **único** árbitro garante acesso ao barramento.

![[Pasted image 20260914102838.png]]

#### Distribuído

- Cada módulo contém lógica de controle de acesso
- módulos atuam juntos para compartilhar o barramento

![[Pasted image 20260914102946.png]]

- Dispositivos solicitantes ajustam **Bus request=0**.
- Dispositivos solicitantes geram **Out=0**; não solicitantes geram **Out=In**.
- Dispositivo solicitante com **In=1**, ganha o barramento.
- Ele aguarda até que **Busy=1**, ajusta **Busy=0** e assume o controle.
- Ao final, ele libera o barramento ajustando **Busy=1**.

## Sincronização

### Síncrono
- Eventos determinador pelo sinal do clock
- Barramento de controle inclui o clock
- **Geralmente sincroniza na borda de subida**
- Geralmente um único ciclo para um evento
- Uma linha *READY/WAIT* sinaliza quando se espera que o acesso tenha finalizado

- **Vantagens:**
	- Implementação simples

![[Pasted image 20260914103355.png]]


| Símbolo  | Parametro                                         | Min | Max | Unidade |
| -------- | ------------------------------------------------- | --- | --- | ------- |
| $T_{ad}$ | Address output delay                              |     | 4   | nsec    |
| $T_{ML}$ | Address stable prior to *MREQ*                    | 2   |     | nsec    |
| $T_{M}$  | *MREQ* delay from falling edge of $\phi$ in $T_1$ |     | 3   | nsec    |
| $T_{RL}$ | *RD* delay from falling edge of $\phi$ in $T_1$   |     | 3   | nsec    |
| $T_{DS}$ | Data setup time prior to falling edge of $\phi$   | 2   |     | nsec    |
| $T_{MH}$ | *MREQ* delay from falling edge of $\phi$ in $T_3$ |     | 3   | nsec    |
| $T_{RH}$ | *RD* delay from falling edge of $\phi$ in $T_3$   |     | 3   | nsec    |
| $T_{DH}$ | Data hold time from negation of *RD*              | 0   |     | nsec    |

### Assíncrona

- Sem sinal de clock
- Depende da ocorrência dos eventos anteriores
- Linhas de estado indicam que o acesso foi finalizado

- **Vantagens:**
	- Permite "ciclo fracionado"
	- Não há tempo minimo de acesso
	- Possibilita barramentos maiores (distorção clock)

![[Pasted image 20260914104114.png]]

---

### Transferência de dados

![[Pasted image 20260914104150.png]]


## Problemas com barramentos

### Problemas como barramentos únicos

- Limitações de **Largura de Banda**:
	- Todos os dispositivos compartilham o mesmo caminho de comunicação.
	- Com mais dispositivos, menor a largura de banda disponível por dispositivo.
	- **Gargalo no desempenho!!**

- **Latência:**
	- Os dispositivos muitas vezes devem esperar para acessar o barramento.
	- A espera aumenta a latência, o que é particularmente problemático para aplicativos de alta velocidade ou de tempo real

- Problemas de **escalabilidade:**
	- Barramentos têm um limite físico e elétrico no número de dispositivos que podem ser conectados.
	- Escalar sistemas sem afetar o desempenho ou a estabilidade é difícil.

*Portanto, a maioria dos sistemas usa múltiplos barramentos para superar esses problemas...*

### Problemas com barramentos paralelos

**Clock skew** (Desvio de clock)
- Fenômeno em circuitos síncronos
- Sinal de clock chega a componentes diferentes em momentos diferentes

- Possíveis causas:
	- comprimento do fio;
	- variação em dispositivos intermediários;
	- acoplamento capacitivo;
	- imperfeições do material;
	- ...

- À medida que a taxa de clock aumenta, menos variação pode ser tolerada
- Isso impõe um **limite de taxa de clock** ao barramento paralelo

## PCIe (Peripheral Component Interconnect Express)

- Arquitetura **ponto-a-ponto** (Peer-to-Peer).
- A comunicação flui através de um ou mais **pares de conexões**, unidirecionais, chamadas **lanes** (faixas).
- Cada conexão de uma faixa utiliza sinalização diferencial com dois fios *(transmitindo o mesmo sinal com polaridades opostas)*, o que proporciona **alta imunidade a ruídos**.
- Dispositivos PCIe se comunicam através de um link, que é construído a partir de um conjunto de uma ou mais faixas.
- São permitidos links com 1, 2, 4, 8, 16, e 32 faixas.

### Dispositivos PCIe

![[Pasted image 20260914112129.png]]

![[Pasted image 20260914121150.png]]

### Evolução do PCIe

Não vou transcrever, não parece muito necessário

![[Pasted image 20260914121232.png]]

### PCIe 6.0 com PAM4

- Acima de uma certa frequência, o sinal não é estável a longas distâncias
- Para dobrar a taxa de dados, o PCIe 6.0 adotou o PAM4.
- PAM4 transmite 2 bits por intervalo unitário

![[Pasted image 20260914121929.png]]

## Protocolo de camadas PCIe

### Physical

- **Physical:** Consiste nos fios reais que transportam os sinais, bem como nos circuitos e na lógica para suportar recursos auxiliares necessários na transmissão e recepção dos *1* e *0*.

![[Pasted image 20260914123326.png]]

- Cada conexão ponto a ponto consiste em um ou mais pares de links (lanes).

![[Pasted image 20260914123514.png]]

- Sem clock mestre – a codificação 128b/130b garante transições de clock suficientes para manter a sincronização.

#### Distribuição PCIe Multilane

![[Pasted image 20260914123544.png]]

### Data Link

- **Data Link Layer (DLL):** Responsável pela transmissão confiável e controle de fluxo.
	- Gerencia o controle de fluxo, detecção de erros e correção de erros.
	- Garante que os dados sejam transmitidos sem erros e na ordem correta.
	- Divide os dados em pacotes menores e adiciona cabeçalhos e rodapés para verificação de erros e endereçamento.
	- Gerencia a ordenação de pacotes e a remontagem na receptora.

![[Pasted image 20260914123726.png]]

#### Pacote PCIe

- DLLP carrega informações de gerenciamento do próprio link.
- *Ex.:* mensagens de ACK *(CONFIRMAR)*, NAK *(NÃO-CONFIRMAR)*, dados de controle de energia, e controle de fluxo.
- CRC (Checagem de Redundância Cíclica) serve para detecção de erros.

![[Pasted image 20260914201508.png]]

### Transaction

- **Transaction Layer (TLP)**: Gera e consome pacotes de dados para implementar mecanismos de transferência de dados de carga/armazenamento (load/store) e gerencia o controle de fluxo desses pacotes entre os dois componentes em um link.

![[Pasted image 20260914201615.png]]

### Pacote PCIe

- **Header:** contém informação sobre o tipo de transação (e.g., read/write), endereço de destino, etc.
- **Data:** é a carga útil (payload), os dados reais que estão sendo transferidos.
- **ECRC:** checagem derros ponta a ponta.

![[Pasted image 20260914201731.png]]

---

# Memória Cache

## Hierarquia de Memória

- Trade off custo **x** velocidade.
- Memória dividida em níveis hierárquicos.
- A requisição é enviada para o nível inferior seguinte até que seja atendida.

![[Pasted image 20260914202025.png]]

## Cache e Memória Principal

![[Pasted image 20260914202112.png]]

## Endereçamento da Cache

- **Onde a cache se localiza?**
	- Entre o processador e a unidade de gerenciamento de memória virtual *(MMU)*.
	- Entre a MMU e a memória principal.

- A cache lógica (virtual) armazena dados usando endereços virtuais.
	- O processador acessa a cache diretamente.
	- O acesso é mais rápido, antes da tradução de endereços da MMU.
	- Endereços virtuais usam o mesmo espaço de endereçamento para diferentes aplicações.
		- **É necessário limpar (flush) a cache em cada troca de contexto!**

- A cache física armazena dados usando os endereços físicos da memória principal.


![[Pasted image 20260914202400.png]]

## Operação da Cache

- A cache inclui tags para identificar qual bloco da memória principal está em cada compartimento do slot da cache
- A CPU solicita o conteúdo de um endereço de memória
- Verificam-se as tags presentes na cache em busca desses dados
	- **Se** estiverem presente, são obtidos da cache (rápido)
	- **Senão**, o bloco necessário é lido da memória principal para a cache
- Os dados são entregues da cache para a CPU

### Leitura

![[Pasted image 20260914232248.png]]

## Princípios de localidade

- **Espacial**
	- *O processador tende a acessar poucas áreas restritas do espaço de endereçamento.*

- **Temporal**
	- *O processador tende a acessar no futuro próximo endereços que foram acessados no passado recente.*

## Definições

- **Hit**: Acesso atendido pela cache
- **Miss**: acesso **não** atendido pela cache
- **Hit ratio**: proporção de hits

$$
h = \frac{number \ of \ accesses \ served \ by \ the \ cache}{total \ number \ of \ accesses}
$$
- **Miss ratio**: proporção de misses

$$
m = \frac{number \ of \ accesses \ not \ served \ by \ the \ cache}{total \ number \ of \ accesses}
$$

- Logicamente, $m + h = 1$

### Exemplo:
Considere:
- $h$ como hit *ratio*
- $t_{hit}$ tempo de acesso de um *hit*
- $t_{miss}$ tempo de acesso em um *miss*

O tempo médio de acesso à memória *t* **será:**

$$
t = h \ t_{hit} + (1-h)t_{miss}
$$

![[Pasted image 20260914232918.png]]

### Bloco

- Todo o conjunto de $2^b$ bytes em endereços consecutivos, começando em endereços cujos $b$ bits menos significativos são zero.
- Observe que os endereços dos bytes pertencentes ao mesmo bloco são coincidentes à esquerda dos $b$ bits menos significativos.
- A troca de dados entre a cache e a memória principal é realizada bloco a bloco.
- Isso faz sentido? *(Eu não entendi bulhufas)*

![[Pasted image 20260914233110.png]]

---
## Cache Totalmente Associativa

### Arquitetura

![[Pasted image 20260914233159.png]]

### Operação

![[Pasted image 20260914233214.png]]

- O controlador da cache compara o número do bloco e o campo TAG de todas as linhas simultaneamente (busca associativa).
- Se uma TAG coincidir com o número do bloco e o bit de validade estiver "ligado", é um *hit*, caso contrário, é um *miss*.
- Os $b$ bits menos significativos são usados como ponteiros para o byte/palavra dentro do bloco.


### Problema

Para comparar o número do bloco com os campos TAG de todas as linhas da cache simultaneamente (busca associativa), são necessários muitos comparadores.

**Consequência**
- O design totalmente associativo (fully associative) é utilizado apenas para caches de pequena capacidade

---
## Cache com mapeamento Direto

### Ideia Principal

- Cada bloco da memória principal é mapeado em uma única linha da cache
- Cada bloco só pode ser carregado na linha da cache para qual está mapeado
- Não é mais necessário verificar todas as linhas, apenas uma.

![[Pasted image 20260914233636.png]]

### Operação

![[Pasted image 20260914233658.png]]

- O controlador da cache compara o campo de endereço à esquerda com o campo TAG da (única) linha de cache definida pelos bits *L* bits.

### Problema

- Algumas linhas podem ser solicitadas frequentemente por blocos diferentes...
- Enquanto outras linhas podem ser raramente solicitadas...
- Uso não otimizado da capacidade da cache!

---
## Cache com Conjuntos Associativos

### Ideia Principal

- Em vez de atribuir cada bloco da memória principal a uma única linha da cache, cada bloco é atribuído a um conjunto (associativo) de linhas da cache.
- Um bloco pode ser carregado em qualquer linha de cache do conjunto associativo ao qual foi atribuído.

![[Pasted image 20260914234215.png]]

### Arquitetura

![[Pasted image 20260914234249.png]]

![[Pasted image 20260914234300.png]]
### Operação

![[Pasted image 20260914234318.png]]

O controlador da cache compara o campo de endereço à esquerda com o campo TAG de todas as linhas do conjunto associativo definido pelos bits *S* (busca associativa).

### Definições

#### Cache Totalmente Associativa
- São *caches com conjuntos associativos* que possuem apenas **um único** **conjunto** associativo.

#### Cache com Mapeamento Direto
- São *caches com conjuntos associativos* que com conjuntos que possuem apenas **uma linha** cada.

#### Tamanho do Conjunto
- Mantendo a capacidade total da cache constante e alterando o número de linhas por conjunto...

![[Pasted image 20260914234633.png]]

![[Pasted image 20260914234647.png]]

---
## Política de Substituição

- **LRU - Least Recently Used**
	- A linha usada menos recentemente será removida da cache abrindo espaço para um novo bloco da memória principal.

- **Pseudo LRU**
	- Exemplo:
	- A linha usada menos recentemente, da metade usada menos recentemente, é escolhida para deixar a cache.

![[Pasted image 20260914235027.png]]

### Exemplo:

![[Pasted image 20260914235050.png]]

---

## Política de Atualização da Memória Principal

### Write Trought

- Todas as escritas são realizadas na cache e na memória principal
- A CPU espera até que a memória principal seja atualizada
- **Vantagem**:
	- A memória principal está sempre atualizada
- **Problemas**:
	- Grande volume de tráfego → especialmente prejudicial em multiprocessadores.
	- 15% das referências de memória são escritas

### Write Back

- Cada linha de cache possui um bit *(dirty)* que indica se a cópia do bloco na cache difere da memória principal.
- Quando o bloco é trazido da memória principal para a cache, *dirty* = 0.
- Todas as escritas são realizadas apenas na cache, *dirty* = 1
- A memória principal é atualizada quando o bloco selecionado para substituição tem o bit *dirty* = 1.

- **E/S deve acessar a memória principal através da cache!**

### Write on allocate (Miss na Escrita)

- A cache traz o bloco correspondente da memória principal antes da operação de escrita.

### Write Around (Miss na Escrita)

- A cache não traz o bloco correspondente da memória principal e escreve o byte/palavra endereçado apenas na memória principal.

---
## Caches Multinível

- A alta densidade lógica permite caches no chip
	- Mais rápido que o acesso via barramento
	- Libera o barramento para outras transferências
- Comum usar tanto cache dentro quanto fora do chip
	- L1 no chip, L2 fora do chip em RAM estática
	- O acesso à L2 é muito mais rápido que à DRAM ou ROM
	- A L2 frequentemente usa um caminho de dados separado
	- A L2 pode estar no chip...
	- Resultando na cache L3
		- Acesso via barramento ou no chip...

![[Pasted image 20260914235734.png]]

## Cache Unificado vs Separada

### Unificada

- Uma única cache para dados e instruções
- Maior taxa de acerto (*hit rate*)
- Equilibra a carga de busca de instruções e de dados
- Apenas uma cache para projetar e implementar

### Separada

- Uma cache para dados e outra para instruções
- Elimina a contenção de cache entre a unidade de busca/decodificação de instruções e a unidade de execução
	- Importante em *pipelining*


*AQUI ACABA!!!!*

---

