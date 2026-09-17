# Memória Externa

**Memória principal (primária):** Memória de execução de programas

**Memória externas (secundária):** Não volátil, que mantem os dados armazenados mesmo com a máquina desligada.

## Disco Magnético

- Substrato de disco de material não magnético revestido com material **magnetizável** (óxido de ferro... **sujeito a ferrugem!!**)
- O substrato constumava ser alumínio; agora é vidro
	- Melhor uniformidade da superfície: aumenta a confiabilidade
	- Redução de defeitos na superfície -> reduz erros de leitura/escrita
	- Alturas de voo (do cabeçote) menores
	- Melhor rigidez
	- Melhor resistência a choques e danos

![[Pasted image 20260917092325.png]]

### Mecanismo de leitura e escrita

![[Pasted image 20260917093058.png]]

### Operação de escrita

- A eletrônica da unidade recebe dados binários e os converte em uma corrente que flui através da bobina.
- A direção do fluxo da corrente muda a cada "1" e permanece inalterada a cada "0“.
- A interação com o meio magnetiza o material, cuja direção depende da direção da corrente na bobina.

### Operação de Leitura (tradicional)

- Utiliza a **mesma** bobina para leitura e escrita
- A variação do campo magnético devido ao movimento relativo à bobina produz corrente.
- A direção da corrente induzida indica o que está gravado.

### Operação de Leitura (contemporânea)

- Cabeçote de leitura **separado**, próximo ao cabeçote de escrita!
- Sensor magnetorresistivo (MR) parcialmente blindado.
- A resistência elétrica depende da direção do campo magnético.
- Operação em alta frequência
	- **Maior densidade de armazenamento e velocidade**

![[Pasted image 20260917093546.png]]

### Fator de Perda de Espaçamento de Wallace

**“A perda de potência do sinal magnético é proporcional à distância entre o cabeçote e a mídia”**

Portanto, o dispositivo de leitura e escrita é mantido o mais próximo possível da superfície, com um "colchão de ar" entre eles.

### Cabeça de leitura e escrita

- Dispositivo de leitura MR
	- Sua resistência elétrica varia com o campo magnético
	- Alta robustez contra ruído elétrico

- Dispositivo de escrita indutivo (bobina)
	- Gera um campo magnético forte no intervalo entre os polos
	- Magnetiza a área da mídia logo abaixo dos polos

![[Pasted image 20260917093912.png]]

### Layout de Dados do Disco

- Anéis concêntricos ou trilhas
	- Intervalos (gaps) entre trilhas
	- Reduzir o intervalo para aumentar a capacidade
	- Mesmo número de bits por trilha (densidade de empacotamento variável)
	- Velocidade angular constante (CAV)

Trilhas divididas em setores Intervalo entre setores (Intersector Gap).

![[Pasted image 20260917094221.png]]


![[Pasted image 20260917094257.png]]

*O Disco da direita tem menos "zonas", mas todas são do mesmo tamanho (densidade), o que torna mais fácil de trabalhar*
### Velocidade do disco de dados
- Um bit perto do centro do disco giratório passa por um ponto fixo mais devagar do que um bit na parte externa
- Aumenta-se o espaçamento entre bits nas trilhas externas
- O disco gira em *Velocidade Angular Constante* (CAV)
	- Gera setores em formato de fatia de torta e trilhas concêntricas 
	- Trilhas e setores individuais são endereçáveis
	- Move-se a cabeça para a trilha desejada e aguarda o setor específico
	- **Desperdício de espaço nas trilhas externas** -> **Menor densidade de dados!**

- Pode-se usar zonas para aumentar a capacidade
	- Dentro de uma zona, os bits por trilha são constantes
	- Zonas mais distantes/perto do centro contêm mais/menos setores
	- **Circuitos mais complexos**


### Características

- Cabeça **Fixa** (raro) $\times$ **Móvel**

- **Removível** $\times$ **Fixo**

- Faces **simples** $\times$ **duplas** (geralmente)

- Prato **único** $\times$ **múltiplos**

- Mecanismo de cabeçote:
	- **Contato** (floppy)
	- **Gab fixo** 
	- **Flutuante** (Winchester)

#### Cabeçote fixo/móvel

- **FIxo**
	- Uma cabeça de leitura/escrita por trilha
	- Cabeças montadas em um braço rígido fixo

- **Móvel**
	- Uma cabeça de leitura/escrita por face
	- Montada em um braço móvel

#### Removível ou não removível

- **Disco Removível**
	- Pode ser removido da unidade e substituído por outro disco
	- Fornece capacidade de armazenamento ilimitada
	- Fácil transferência de dados entre sistemas

- **Disco Não Removível**
	- Montado permanentemente na unidade
	- O disco e o mecanismo de leitura/escrita formam uma unidade selada única
### Visualização

![[Pasted image 20260917095444.png]]

#### Cilindros

![[Pasted image 20260917100555.png]]

#### Parte de uma trilha do disco
Dois setores

![[Pasted image 20260917100928.png]]

#### Formato de disco Winchester

Exemplo:
![[Pasted image 20260917100956.png]]

### Controlador de Disco

- Tipicamente embutido na unidade de disco, agindo como uma **interface entre a CPU e o hardware do disco**
- O controlador possui um **cache interno** que utiliza para **bufferizar dados** em requisições de leitura/escrita

![[Pasted image 20260917101125.png]]

### Métricas de Velocidade

- **Tempo de Busca (Seek time)**
	- Tempo necessário para mover o cabeçote até a trilha correta

- **Latência (Rotational Latency)**
	- Tempo que o disco leva para girar até que o setor desejado esteja sob o cabeçote de leitura/escrita

- **Tempo de transferência ou leitura (Transfer/Read time)**
	- Uma vez que o cabeçote está posicionado sobre os dados, este é o tempo necessário para a transferência efetiva dos dados.

- **Tempo de Acesso (Access time)**
	- ~~Seek + Latency (De acordo com Stalling)~~
	- Seek + Latency + Transfer (De acordo com Parhami) 

### Desfragmentação

Tentativa de resolver a *fragmentação* %%Pasmem%%
- **Fragmentação**: É quando a informação fica dividida pelo disco.

![[Pasted image 20260917102319.png]]
(Isso é uma animação, ver nos slides)

## RAID (Redundant Array of Independent Disks)

Antes era **Redundant Array of Inexpensive Discs**

- **Um conjunto de discos físicos vistos como uma única unidade lógica pelo SO**

As duas palavras-chave:
- **Redudant**
	- Dados redundantes em múltiplos discos fornecem **tolerância a falhas**

- **Array**
	- Um conjunto de múltiplos discos **acessados em paralelo** fornecerá uma taxa de **transferência maior** do que um único disco isolado.

### Non-Redundant - RAID 0

- **Dados distribuídos** por todo os discos
- Round Robin
- **Aumento da velocidade**
	- Múltiplas requisições provavelmente em discos diferentes
	- Busca em paralelo
	- Conjunto de dados espalhado por múltiplos discos

- **Sem redundância**
	- Não possui duplicata de dados

![[Pasted image 20260917103330.png]]

### Mirrored - RAID 1

- **Redundância** é alcançada duplicando todos os dados
- Uma requisição de leitura pode ser atendida por qualquer um dos discos → **desempenho é ditado pelo mais rápido**
- Uma requisição de escrita exige que ambos os discos sejam atualizados → **desempenho é ditado pelo mais lento**
- **Recuperação simples** → Se uma unidade falhar, os dados estão prontamente disponíveis em outra unidade

![[Pasted image 20260917103523.png]]

### RAID 1 + 0

- Duas cópias de cada fatia em discos separados (*mirroring*)
- **Vantagens:**
	- Leitura de qualquer um dos discos (o que possuir menor tempo de busca)
	- Recuperação simples – Basta trocar o disco defeituoso, sem necessidade de interromper o sistema
- **Desvantagens:**
	- Caro

![[Pasted image 20260917103653.png]]

### Memory Style - RAID 2
*APARENTEMENTE NÃO CAI, mas não tenho certeza*

- Tipicamente, os discos são sincronizados – cabeças na mesma posição
- Tipicamente, os discos são sincronizados – cabeças na mesma posição
- Correção de erros calculada entre os bits correspondentes
- Em uma única escrita, todos os discos de paridade devem ser acessados
- **Muita redundância**
	- Caro
	- Eficaz apenas se ocorrerem muitos erros de disco → não é usado hoje em dia

![[Pasted image 20260917104043.png]]

### Bit-Interleaved Parity - RAID 3
*APARENTEMENTE NÃO CAI, mas não tenho certeza*

- SImilar ao *RAID 2*
- Apenas um disco redundante, não importa o tamanho do conjunto
- Bit de paridade simples para cada conjunto de bits correspondentes
- Dados em uma unidade com falha podem ser reconstruídos utilizando os outros discos e paridade
- Taxas de transferência **altas**

![[Pasted image 20260917104332.png]]

### Block-Interleaved Parity - RAID 4

- Cada disco opera de forma independente → Requisições de E/S separadas podem ser atendidas em paralelo
- **Ideal para alta taxa de requisições de E/S**
- Paridade armazenada em um disco dedicado
- Escritas envolvem 2 leituras e 2 escritas – necessário ler o dado e a paridade antiga
- **disco de paridade torna-se um gargalo e fica sobrecarregado**

![[Pasted image 20260917104512.png]]

### Block-Interleaved Distributed-Parity - RAID 5

- Paridade distribuída por todos os discos
- Alocação Round Robin para as fatias de paridade
- **Evita o gargalo** do RAID 4 no disco de paridade
- Comumente usado em servidores de rede

![[Pasted image 20260917104918.png]]
### P+Q redundancy - RAID 6

- RAID 5, porém com dois cálculos de paridade
- Exigência de N+2 discos
- Alta disponibilidade de dados:
	- Três discos precisam falhar para perda de dados
	- Penalidade de escrita significative (30% em comparação com RAID 5)
![[Pasted image 20260917105112.png]]
### Níveis de RAID

(Não irei fazer tabela obisidian, visto que o prof falou q n prexisa decorar)

![[Pasted image 20260917104701.png]]

