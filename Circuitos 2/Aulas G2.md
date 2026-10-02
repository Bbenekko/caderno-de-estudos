# Regime permanente senoidal

$$
\begin{align*}
x = e^{st} => H(s) => y = H(s) \ e^{st} \\
\\
s = j \ z\omega_0 \\
e^{j\omega_0t} => H(j\omega_0) * e^{j\omega_0t}
\end{align*}
$$

lembrando que esse st, que é uma entrada, possui parte complexa, que pode ser decomposta em cos e sen

$$
cos\omega_0t => |H(j\omega_0)| cos(\omega_0t + \phi_0)
$$
*sendo $\phi_0$ a diferença de fase*
*e $(j\omega_0)$ a amplitude*

---

$$
A \ cos (\omega_0t + \phi) = \Re \{ Ae^{j\phi} \ e^{j\omega_0t} \}
$$

*$Ae^{j\phi}$ é o ==fasor==*

O fasor pode ser encontrado pela função de transferência, sendo o fasor da **saída** relacionado ao fasor da **entrada**.

$$
\begin{align*}
A_0 e^{j\phi_0} => \text{Circuito H(s)} => A_1 e^{j\phi_1} \\
A_1 = |H(j\omega_0)| \ A_0 \\
\phi_1 = \phi_0 + H(j\omega_0)
\end{align*}
$$

==GERALMENTE A FASE ENTRADA É ZERO==

---

## Exemplo:

(foto da questão e das contas)

---

## Exercicio entregue em sala

### Letra a:
(foto da folha)

$$
\begin{align*}
i(t) = 2 \ cos (\omega_0t) \\
=> I = 2e^{j\times0} = 2 \\
I = 2 \ [mA]
\\
\\
i_R = 1 xos (\omega0t + \phi)
\end{align*}
$$

O período é:
$$
T_0 = 6 ms
$$
A (não lempro o nome):
$$
\Delta t = 1ms
$$

Logo a fase é:

$$
\begin{align*}
\phi = -\frac{\Delta t}{T_0} \times 2\pi \\
= -\frac{1}{6} \times 2\pi = - \frac{\pi}{3}
\end{align*}
$$


### Letra b:

$$
H(j\omega_0) = \frac{I_r}{I}
$$

*Ou seja, a função de transferência é o fasor de entrada sobre o fasor de saída (ou o contrário n lembro)*

onde:

$$
\omega_0 = \frac{2\pi}{T_0} = \frac{2\pi}{6\times10^{-3}} = \frac{1000\pi}{3}
\ \ \ rad/s
$$

NESSE CIRCUITO:

$$
\begin{align*}
I_R (s) = \frac{\frac{1}{sC}}{R + \frac{1}{SC}} * I(s) \\
\\
\frac{I_R(s)}{I(s)} = \frac{1}{1+sRC} = H(s)
\end{align*}
$$

Fazendo $s = j\omega_0$

$$
\begin{align*}
H(J\omega_0) = \frac{1}{1 + j\omega_0RC} \\
\\
H(j\frac{1000\pi}{3}) = \frac{1}{1 + j\frac{1000\pi}{3}RC} \\
\\
= \frac{I_r}{I}
\end{align*}
$$

---

$$
\begin{align*}
\frac{1e^{-j\frac\pi3}}{2} = \frac{1}{1+j\frac{1000\pi}{3}RC} \\
\\
2 e^{j \frac \pi 3} = 1 + j \frac{1000 \pi}{3} RC \\
\\
2 ( \frac 1 2 + j\frac{\sqrt3}{2}) = 1 + j \frac{1000\pi}{3}RC \\
\\
\sqrt3 = \frac{1000\pi}{3}RC
\end{align*}
$$