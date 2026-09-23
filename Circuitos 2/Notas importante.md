# Capacitores e Indutores

## Capacitor em regime permanente:

**Quando a fonte está desligada:**
*Equivale a um circuito aberto!*

(inserir imagem)

**Quando a fonte é ligada:**

*O capacitor momentaneamente funciona como curto circuito!

(inserir imagem)
## Indutor em regime permanente:

**Quando a fonte está desligada:**
*Equivale a um curto circuito!*

(inserir imagem)

**Quando a fonte é ligada:**

*O capacitor momentaneamente funciona como circuito aberto!

(inserir imagem)
# Circuito RLC

## RLC paralelo

- **Polinômio característico:**
$$
\lambda ^2 + \frac{1}{RC}\lambda + \frac{1}{LC} = 0
$$
## RLC Série

- **Polinômio característico:**
$$
\lambda^2 = \frac{R}{L}\lambda + \frac{1}{LC} = 0
$$
## Circuito superamortecido:

$$
y(t) = k_1 e ^{\lambda_1 t} + k_2 e^{\lambda_2 t}
$$
- Encontra-se o tau:
$$
\tau = \frac{1}{min\{| \lambda_1 , \lambda_2 | \}}
$$
## Circuito amortecido:

$$
y(t) = (k_1 + k_2 t ) e ^{\lambda t}
$$
- Encontra-se o tau:
 $$
\tau = \frac{1}{ | \lambda | }
$$
## Circuito subamortecido:

$$
y(t) = e^{\alpha t} (k_1 cos(\omega_d )t + k_2 sen(\omega_d)t)
$$
- Encontra-se o tau:

$$
\tau = \frac{1}{|\alpha|} \ \text{onde} \ \alpha = \Re \{ \lambda_i \}
$$

# Calc IV

## Soma e Produto

$$
S = \frac{-b}a \ \ \ \ P = \frac ca
$$

Sendo S a soma das raízes e P o produto

## Fatoração de polinômio de segundo grau

$$
ax^2 + bx + c = 0 \ \ \ \ \text{ou} \ \ \ \ a(x-r_1)(x-r_2)
$$


## Equações diferenciais

$$
y(t) = y_h(t) + y_p(t)
$$

onde $y_h$ é solução homogenea e $y_p$ é solução particular

### Solução homogenea