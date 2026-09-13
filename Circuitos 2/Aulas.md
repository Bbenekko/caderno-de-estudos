# Aula 3
## Exemplo 1

(inserir circuito)

$$ R1 = 1k\Omega , R2 = 3k\Omega , c = 1\micro F $$
$$ 
\begin{align*}
v(t) = 8\micro _{-1}(-t)\quad [V] \\
I(t) = 10\micro _{-1}(t)\quad [mA]
\end{align*}
$$
**Questão:** Faça um esboço do gráfico para t > 0

$$ v_{R1}(t) = v^h_{R1}(t)t \quad \text{-> Solução Homogênea!} $$
$$ v_{R1}^p(t) \quad \text{-> Solução Particular!} $$

### Parte 1: Solução homogênea

==(Fontes desligadas!!; consideramos apenas as C.I.s)==

$$ t = 0^- \quad \text{-> circuito no RP} $$ (inserir circuito)

$$ v_c (t = 0^-) = \frac{R2}{R1+R2} * V $$
-> **(Divisor de tensão)**

$$ \frac{3}{1+3} * 8 = 6V* $$
-> **6V -> condição inicial**
Não esquecer:
$$ t = 0^t $$

(Inserir circuito)

$$ Req = R1//R2 $$
$$ = 1K//3K $$
 $$ = \frac{1K * 3K}{1K + 3K} = 750 \Omega $$
$$ z = ReqC = 750 * 10^6 $$

$$ v_c(t) = v_c(0)e^{⁻t/z} $$

$$ = 6e^{-t/750*10^{⁻6}}$$
$$ = 6e^{-4000t/3}$$
$$v_{R1}^h (t) = -6e^{4000t/3}$$

-> t >= 0

### Parte 2 : Solução particular

==(fontes ligadas em t>0; CIs desconsideradas)==

(inserir cirucito)
(inserir cirucito)
(inserir cirucito)

$$ V_{fh} = -Req * I$$
$$
\begin{align*}
= - 750 * 10 * 10~{3} \\
= - 7,5V
\end{align*}
$$

*OBS: circuito RC série, resposta ao degrau unitário, saindo no capacitor*

$$v_c(t) = (1-e^{-t/\tau})u_{-t}(t)$$

Nesse caso, como o drgrau tem amplitude -7,5V:

$$
\begin{align*}
V_c(t) = -7,5 (1 - e^{4000t/3})u_{-1}(t) \\
V_{R1}^p(t) = 7,5(1-e^{4000t/3})u_{-1}(t)
\end{align*}
$$

### Parte 3: Somar S.H. + S.P.

$$
V_{R1} (t) = [7,5-7,5e^{-4000t/3} - 6e^{-4000t/3}] u_{-1}(t) 
$$

$$
\bbox[black]
{
V_{R1}(t) = [7,5-13,5e^{-4000t/3}] u_{-1}(t)
}
$$
(inserir gráfico)

$$
\tau = \frac{3}{4000} => 5\tau = \frac{15}{4000} = 3,75 ms
$$


## Exemplo 2:
(inserir circuito)

$$
I(t) = 10 u_{-1}(t) \quad mA
$$
$$
i_R(t)=(10-8e^{-\alpha t})u_{-1}(t) \quad mA
$$

**(a) X = R,L ou C
(b) determine $\alpha$**

Sabe-se que:
$$
\begin{align*}
t = 0: i_R = 2mA \\
t ->\infty: i_R = 10mA
\end{align*}
$$

Se X = L
$$
i_C(0) = i_L(0) = 0 \ne 8 \qquad \text{Impossível}
$$
Se X = C
$$
ic(0) = 10mA \ne 8mA \qquad \text{impossível}
$$
Logo:

**X = R**

$$
\alpha = \frac{1}{\tau} \qquad \tau = Req * C
$$
$$
Req = R + R_X
$$

(inserir circuito)

$$
\begin{align*}
2 = R_X * 8 *10^{-3} \\
R_X = \frac{2}{8*10^{-3}} = \frac{1000}{4} \\
= 250\Omega
\end{align*}
$$
---
$$
\begin{align*}
Req = 1000 + 250 \\
= 1250\Omega \\
\alpha = \frac{1}{ReqC} = \frac{1}{1250*10^{-6}} = \quad ...
\end{align*}
$$

==PERDI PERDI PERDI==

## Exemplo 3


---
# Aula 4

## Circuitos de 2a Ordem
### Solução Homogênea

(insira gráfico)

$$
y(t) = k_1 e^{\lambda_1 t} +k_2e^{\lambda_2}t
$$
(insira gráfico)

$$
y(t) = (k_1+k_2t)e^{\lambda t}
$$

(insira gráfico)

$$
\begin{align*}
y(t) = e^{\alpha t}(k_1 cos (\omega_d) t + 
k_2 sen (\omega_d) t) \\
\alpha = \Re \{ \lambda _{1,2} \} \\
\omega_d = | \Im \{ \lambda_{1,2} \}|
\end{align*}
$$
#### Exemplos:

##### 1

(insira circuito)

$$
\begin{align*}
t_s = 10 ms \\
t_s' = 100ms
\end{align*}
$$
###### (a) Valor de c?

(foto do quadro)

###### (b) Tipo de amortecimento quando L é inserido?

(foto do quadro)

**Solução Homogênea: fonte desligada**

(inserir foto do quadro)

*OBS: Sabemos a tensão e usaremos isso para encontrar a tensão em relação a corrente, para achar a corrente ( e o sentido dela).*

*OBS: anotar a fórmula na box (polinômio característico RLC paralelo) para por na folha de cola!!*

**Ver mais sobre em [[Notas importante]]**

(inserir foto ( a partir de: *Comparação: RLC série*))

**Ver mais sobre em [[Notas importante]]**
(Inserir foto)

Conclusão: **Superamortecido!**
###### (c) $\lambda_1 = 1/20 = 0,05$

$$
\begin{align*}
| - \frac{1}{2RC} + \frac{1}{2} \sqrt{(\frac{1}{RC})^2- \frac{4}{LC}}| = 0,05 \\
\frac{1}{2*2*10^{-3}}-\frac{1}{2} \sqrt{(\frac{1}{2*10^{-3}})^2 - \frac{4}{L*2*10^{-5}}} = 0,05 \\
L = ...
\end{align*}
$$
##### 2

(inserir foto do circuito)

$$
i(t) = 12 \ u_{-1}(-t)
$$
**Calcule $v_c(t) , t \ge 0$ :**


(inserir imagem)

---
# Aula 5 - Circuitos de Segunda ordem

## Solução Particular

(inserir circuito)

**(a)** Calcule
$$
H(s) = \frac{I_{R1}(s)}{V_i(s)}
$$
**(b)** Considerando
$$
R_1 = 100 \ohm \ ; C = 100 \micro F \ ; L = 10mH 
$$
calcule $R_2$ tal que o circuit oseja **criticamente amortecido**

**(c)** Determine $i_{R1}(t)$, $t > 0$ , para a entrada abaixo

(inserir gráfico)

### Resolvendo:

**(a):**

(Inserir foto)

**(b):**

==(pegar caderno de alguem)==
(inserir foto)

**(c):**

(inserir foto)

## Questão 2

(inserir foto do circuito)

**(a)** Natureza de X1 e X2. Em qual deles foi medido $v_0(t)$?

(Inserir foto)

**(b):**

(inserir foto)

**(c)** Calcule o valor da constante $A$:

(inserir foto)

---
# Aula 6 - Revisão P1

