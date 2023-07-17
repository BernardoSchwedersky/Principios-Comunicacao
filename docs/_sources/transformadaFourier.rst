====================
Transformada Fourier
====================

Definição
=========

A transformada de Fourier em tempo contínuo é uma operação matemática que converte uma função contínua no domínio do tempo em uma representação no domínio da frequência. Ela permite decompor uma função contínua em suas componentes harmônicas de frequência, revelando informações sobre as diferentes frequências presentes na função original. Geralmente, ela é aplicada à sinais não periódicos, porém, pode ser aplicada também à sinais periódicos, com os coeficientes sendo equivalentes aos obtidos na série de Fourier.

Matematicamente, a transformada direta de Fourier em tempo contínuo de uma função :math:`x(t)` é definida como:

.. math::

	\mathcal{F}[x(t)]=X(\omega) = \int_{-\infty}^{\infty}[x(t) e^{-j\omega t}] dt

onde :math:`\mathcal{F}[\cdot]` representa o operador da transformada de Fourier, :math:`X(\omega)` representa a transformada de Fourier da função :math:`x(t)` no domínio da frequência, :math:`\omega` é a frequência angular. 

Por sua vez, a transformada inversa de Fourier é definida como:

.. math::
	
	x(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}[X(\omega)e^{j\omega t}d\omega].

------------------------------
Relação com a Série de Fourier
------------------------------

A formulação da transformada de Fourier pode ser obtida a partir da generalização da série de Fourier, considerando o período fundamental tendendo ao infinito.

Considerando um sinal periódico :math:`x_{T_0}(t)`, com período :math:`T_0`, se fizermos :math:`T_0` tender ao infinito (:math:`T_0 \rightarrow \infty`), o sinal que se repete a cada período só terá uma nova repetição após um intervalo infinito. Dessa forma, o sinal :math:`x(t)`, que se repetia a cada período :math:`T_0`, poderá ser representado por:

.. math::
		x(t)=\lim_{T_0 \rightarrow \infty}x_{T_0}(t).

Esse conceito pode ser visualizado na figura a seguir, na qual um sinal periódico é construído a partir da repetição de um sinal aperiódico. De forma semelhante, se o período do sinal periódico tender ao infinito, o sinal periódico passa a ser equivalente ao sinal aperiódico original.

.. figure:: /figures/construcaoSinalAperiodico.png
	:figwidth: 100%
	:align: center
	
	*Obtenção de um sinal periódico pela repetição de um sinal aperiódico. Se o período do sinal periódico tender ao infinitos, ambos os sinais são equivalentes.* 

Partindo da série exponencial de Fourier de :math:`x_{T_0}(t)`,definida como:

.. math::
	x(t) = \sum_{n=-\infty}^{\infty}e^{(jn \omega_0 t)},

com

.. math::

	D_n=\frac{1}{T_0}\int_{-T_0}x(t)e^{(-jn \omega_0 t)}dt,

podemos modificar os limites de integração da segunda equação, que originalmente eram entre um período :math:`T_0` (:math:`[\frac{-T_0}{2},\frac{T_0}{2}]`), para :math:`[-\infty,\infty]`, pois :math:`T_0 \rightarrow \infty`, fazendo com que:

.. math::

	D_n=\frac{1}{T_0}\int_{-\infty}^{\infty}x(t)e^{(-jn \omega_0 t)}dt.
	
Podemos definir uma função que auxilia a compreensão da natureza dos coeficiêntes :math:`D_n`, definida como:

.. math::

	X(\omega) = \int_{-\infty}^{\infty}[x(t) e^{-j\omega t}] dt.
	
Dessa forma, podemos representar :math:`D_n` como:

.. math::
	D_n=\frac{1}{T_0}X(n\omega_o).

A função :math:`X(\omega)`, é contínua em :math:`\omega`, com :math:`D_n` sendo amostras de :math:`X(\omega)`, obtidas em valores :math:`n\omega_0`, com n representando um número inteiro. Isso faz sentido, pois os coeficientes da série de Fourier existem apenas para valores múltiplos inteiros da frequência fundamental :math:`\omega_0`. É possível visualizar, também, que se considerarmos a envoltória dos coeficientes :math:`D_n`, a função :math:`X(\omega)` será :math:`T_0` vezes maior que a envoltória.

De fato, :math:`X(\omega)` é a transformada de Fourier de um sinal :math:`x(t)`, sendo que a obtenção da integral de Fourier a partir dessa aproximação pode ser verificada nos livros textos da disciplina.

-------
Exemplo
-------

Considere o sinal porta retangular, com largura 2, definido como:

.. math::
	ret(t) = \begin{cases} 1, & \text{se } |t| < 1 \\ 0, & \text{caso contrário} \end{cases}.


----------------------
Solução pela Definição
----------------------

A transformada de Fourier da porta retangular é calculada usando a seguinte equação:

.. math::
	\mathcal{F}[ret(t)] = \int_{-\infty}^{\infty} ret(t) e^{-j\omega t} dt

Podemos expressar a função da porta retangular em termos de uma função degrau :math:`u(t)`:

.. math::
	ret(t) = u(t+1) - u(t-1)
	
Substituindo essa expressão na equação da transformada de Fourier, temos:

.. math::
	\mathcal{F}[ret(t)] = \int_{-\infty}^{\infty} (u(t+1) - u(t-1)) e^{-j\omega t} dt

Podemos separar a integral em dois termos:

.. math::
	\mathcal{F}[rec(t)] = \int_{-\infty}^{\infty} u(t+1) e^{-j\omega t} dt - \int_{-\infty}^{\infty} u(t-1) e^{-j\omega t} dt
	
Vamos analisar cada integral separadamente.

Para a primeira integral, temos:

.. math::
	\int_{-\infty}^{\infty} u(t+1) e^{-j\omega t} dt

A função degrau :math:`u(t+1)` é nula para :math:`t < -1` e é igual a 1 para :math:`t \geq -1`. Portanto, podemos reescrever a integral como:

.. math::
	\int_{-1}^{\infty} e^{-j\omega t} dt

Integrando essa expressão, obtemos:

.. math::
	\int_{-1}^{\infty} e^{-j\omega t} dt = \left[-\frac{1}{j\omega} e^{-j\omega t}\right]_{-1}^{\infty} = -\frac{1}{j\omega} (e^{-j\omega \cdot \infty} - e^{-j\omega \cdot (-1)})

O termo :math:`e^{-j\omega \cdot \infty}` é igual a zero, pois o exponencial tende a zero quando o argumento se aproxima do infinito. Portanto, a primeira integral se simplifica para:

.. math::
	\int_{-\infty}^{\infty} u(t+1) e^{-j\omega t} dt = +\frac{1}{j\omega} e^{j\omega}
 
Agora, vamos analisar a segunda integral:

.. math::
	\int_{-\infty}^{\infty} u(t-1) e^{-j\omega t} dt

A função degrau :math:`u(t-1)` é nula para :math:`t < 1` e é igual a 1 para :math:`t \geq 1`. Portanto, podemos reescrever a integral como:

.. math::
	\int_{1}^{\infty} e^{-j\omega t} dt

Integrando essa expressão, obtemos:

.. math::
	\int_{1}^{\infty} e^{-j\omega t} dt = \left[-\frac{1}{j\omega} e^{-j\omega t}\right]_{1}^{\infty} = -\frac{1}{j\omega} (e^{-j\omega \cdot \infty} - e^{-j\omega \cdot 1})

Mais uma vez, o termo :math:`e^{-j\omega \cdot \infty}` é igual a zero. Portanto, a segunda integral se simplifica para:

.. math::
	\int_{-\infty}^{\infty} u(t-1) e^{-j\omega t} dt = -\frac{1}{j\omega} (0 - e^{-j\omega}) = \frac{1}{j\omega}e^{-j\omega}

Agora, somando as duas integrais, obtemos a transformada de Fourier da porta retangular:

.. math::
	\mathcal{F}[ret(t)] = \frac{1}{j\omega} e^{j\omega} - \frac{1}{j\omega} e^{-j\omega} = \frac{2}{j\omega} \sin(\omega) = sinc(\omega)

Portanto, a transformada de Fourier da porta retangular de largura 2 é dada por:

.. math::
	\mathcal{F}[ret(t)] = \frac{2}{j\omega} \sin(j\omega)

-------------------
Resolução Simbólica
-------------------

Podemos encontrar a transformada de Fourier da porta retangular computacionalmente por meio da resolução simbólica da integral associada à transformação. Essa solução, utilizando o pacote SYMPY é apresentada a seguir.

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:
		
		from sympy import fourier_transform, exp, cos, plot
		from sympy.functions.special.delta_functions import Heaviside
		from sympy.abc import f, t
				 
		d = Heaviside(t+1) - Heaviside(t-1)     

		p = plot(d, (t, -4, 4), show=False, legend=False)
		p.save('source/figures/exemploPorta.png')
		   
		X = fourier_transform(d, t, f)
				 
		q = plot(X, (f, -4, 4), show=False, legend=False)
		q.save('source/figures/exemploPortaTransformada.png')

.. figure:: /figures/exemploPorta.png
	:figwidth: 80%
	:align: center

	**Exemplo da uma função porta definida entre -1 e 1.**

.. figure:: /figures/exemploPortaTransformada.png
	:figwidth: 80%
	:align: center

	**Transformada de Fourier da função porta.**
	

Propriedades
============

A transformada de Fourier em tempo contínuo possui várias propriedades importantes, como a linearidade, o teorema da convolução e a dualidade entre o domínio do tempo e o domínio da frequência. Essas propriedades tornam a transformada de Fourier uma poderosa ferramenta para análise de sinais, filtragem, modulação e processamento de sinais em geral. Nesta seção serão apresentadas as principais propriedades da transformada de Fourier.

.. list-table::
   :widths: 10 10
   :header-rows: 1
   :class: tablefullwidth

   * - Tempo

     - Frequência

   * - Transformada Inversa

       .. math::
          x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(\omega)e^{j\omega t}d\omega

     - Transformada Direta

       .. math::
          X(\omega) = \int_{-\infty}^{\infty} x(t) e^{-j\omega t} dt

   * - Dualidade - Tempo

       .. math::
          x(t)\\
          X(t)

     - Dualidade - Frequência

       .. math::
          \mathcal{F}[x(t)] = X(\omega)\\
          \mathcal{F}[X(\omega)]= 2\pi x(-\omega)



   * - Escalamento no Tempo

       .. math::
          x(a t)

     - Escalamento na Frequência

       .. math::
          \frac{1}{|a|}X\Big(\frac{\omega}{a}\Big)

   * - Convolução

       .. math::
          x(t) \ast y(t) = \int_{-\infty}^{\infty} x(t-u) y(u) du

     - Multiplicação

       .. math::
          X(\omega) Y(\omega)


   * - Multiplicação

       .. math::
          x(t) y(t)

     - Convolução

       .. math::
          \frac{1}{2\pi} X(\omega) \ast Y(\omega)


Dentre as propriedades da série de Fourier, a que merece destaque nesta disciplina é a propriedade que relaciona a multiplicação no tempo com a convolução na frequência


Transformada de Sinais Importantes
==================================


-------
Impulso
-------

A função do impulso unitário, :math:`\delta(t)` é definida como:

.. math::

	\delta(t) = \begin{cases} 1, & \text{se } t = 0 \\ 0, & \text{caso contrário} \end{cases}


A transformada de Fourier do impulso unitário é obtida como:

.. math::
	\mathcal{F}[\delta(t)] = \int_{-\infty}^{\infty} \delta(t) e^{-j\omega t} dt

Usando a propriedade da integração do impulso unitário, definida como:

.. math::
	\int_{-\infty}^{\infty} f(t)\delta(t) dt = f(0),

obtemos:

.. math::
	\mathcal{F}[\delta(t)] = e^{-j\omega \cdot 0} = 1

Dessa forma, a transformada de Fourier do impulso unitário é igual a 1, ou seja:

.. math::

	\mathcal{F}[\delta(t)] = 1.


-------
Cosseno
-------

Considerando um sinal cossenoidal definido por:

.. math::
	x(t)=cos(2\pi f_0 t),

onde :math:`f_0` é a frequência fundamental da função cosseno. A transformada de Fourier dessa função é calculada usando:

.. math::
	\mathcal{F}[\cos(2\pi f_0 t)] = \int_{-\infty}^{\infty} \cos(2\pi f_0 t) e^{-j\omega t} dt,

Podemos simplificar a equação usando a identidade de Euler:

.. math::
	\cos(\theta) = \frac{e^{j\theta} + e^{-j\theta}}{2}

Aplicando essa identidade, temos:

.. math::
	\mathcal{F}[\cos(2\pi f_0 t)] = \int_{-\infty}^{\infty} \left(\frac{e^{j2\pi f_0 t} + e^{-j2\pi f_0 t}}{2}\right) e^{-j\omega t} dt

Podemos separar a integral em duas partes:

.. math:
	\mathcal{F}[\cos(2\pi f_0 t)] = \frac{1}{2} \int_{-\infty}^{\infty} e^{j(2\pi f_0 - \omega) t} dt + \frac{1}{2} \int_{-\infty}^{\infty} e^{-j(2\pi f_0 + \omega) t} dt

Vamos resolver a primeira integral:

.. math::
	\frac{1}{2} \int_{-\infty}^{\infty} e^{j(2\pi f_0 - \omega) t} dt

Usando a propriedade da integração do impulso unitário, temos:

.. math::
	\int_{-\infty}^{\infty} e^{j\omega t} dt = 2\pi \delta(\omega)

Dessa forma, podemos escrever a primeira integral como:

.. math::
	\frac{1}{2} \int_{-\infty}^{\infty} e^{j(2\pi f_0 - \omega) t} dt = \frac{1}{2} \cdot 2\pi \delta(2\pi f_0 - \omega)

Similarmente, podemos resolver a segunda integral na forma:

.. math::
	\frac{1}{2} \int_{-\infty}^{\infty} e^{-j(2\pi f_0 + \omega) t} dt

Usando a propriedade da integração do impulso, novamente, obtemos:

.. math::
	\frac{1}{2} \int_{-\infty}^{\infty} e^{-j(2\pi f_0 + \omega) t} dt = \frac{1}{2} \cdot 2\pi \delta(-(2\pi f_0 + \omega))

Portanto, a transformada de Fourier do cosseno é dada por:

.. math::
	\mathcal{F}[\cos(2\pi f_0 t)] = \frac{1}{2} \cdot 2\pi \delta(2\pi f_0 - \omega) + \frac{1}{2} \cdot 2\pi \delta(-(2\pi f_0 + \omega)).

Simplificando a equação, temos:

.. math::
	\mathcal{F}[\cos(2\pi f_0 t)] = \pi \left(\delta(2\pi f_0 - \omega) + \delta(2\pi f_0 + \omega)\right).

Então, a transformada de Fourier do cosseno é formada por dois impulsos localizados em frequências simétricas em relação à frequência fundamental do cosseno, :math:`2\pi f_0`.

	
Exercícios
==========

-----------
Exercício 1
-----------

Usando a definição, obtenha a transformada de Fourier do sinal :math:`x(t)=e^{-3t}`.

-----------
Exercício 2
-----------

Determine a transformada de Fourier do sinal :math:`x(t)=seno(3t)`.

-----------
Exercício 3
-----------

Usando a definição e as propriedades da transformada de Fourier, determine e esboçe a transformada de :math:`x(t)=ret(t)cos(5t)`.

-----------
Exercício 4
-----------

Obtenha, computacionalmente, a transformada de Fourier dos sinais apresentado nas figuras a seguir:

a)
--

.. figure:: /figures/exercicioTFourier4a.png
	:figwidth: 25%
	:align: center

	**Sinal dente de serra.**
	
b)
--

.. figure:: /figures/exercicioTFourier4b.png
	:figwidth: 25%
	:align: center

	**Sinal triangular.**