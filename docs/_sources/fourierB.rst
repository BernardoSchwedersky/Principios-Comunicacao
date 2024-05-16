======================
Revisão - Apresentação
======================

* [22000274] - Princípios de Comunicação
* Professor: Bernardo Barancelli Schwedersky, Dr. Eng.


Agenda
======

* Sinais
* Série de Fourier
* Transformada de Fourier
* Diagrama de Bode
* Filtragem

Sinais
======

Definição de Sinal
------------------

* "Uma função de uma ou mais variáveis independentes que carrega informações ou transmite um determinado significado." (B. P. Lathi) 

Degrau Unitário
---------------

.. math::

	u(t) = \Bigg\{\begin{matrix}0, &t < 0 \\	1, &t \ge 0\end{matrix}

.. figure:: /figures/degrau.png
	:figwidth: 100%
	:width: 50%
	:align: center

Impulso Unitário
----------------

* Impulso unitário ou função delta de Dirac  
* Sinal especial com valor indeterminado em :math:`t=0` e zero para qualquer outro valor

.. math::

	\delta(t) = \Bigg\{\begin{matrix}\infty, &t = 0 \\	0, &t \neq 0\end{matrix}

.. revealjs-break::
	:notitle:

.. figure:: /figures/impulso.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
	Representação gráfica do impulso
	

Impulso Unitário - Propriedade da Integração
--------------------------------------------

* A integral de um impulso entre :math:`-\infty` e :math:`\infty` é 1

.. math::

	\int_{-\infty}^{+\infty}\delta(t) = 1.


Sinais Periódicos
-----------------

* Se repete em intervalos regulares de tempo
* :math:`f(t)` é periódico se :math:`f(t + T) = f(t)`, onde T é o período fundamental do sinal

.. figure:: /figures/sinal_periodico.png
	:figwidth: 100%
	:width: 50%
	:align: center

	**Exemplo de sinal periódico com período T.** 

Função Senoidal
---------------

* Sinal definido como

.. math::

	x(t) = C\cos(2\pi \cdot f_0 t + \theta)
	
:math:`f_0` representando a frequência em Hz

:math:`T_0=\frac{1}{f_0}` representando o período em segundos

:math:`\theta` representando a fase

.. revealjs-break::
	:notitle:
	
* Podemos representar também como

.. math::

	x(t) = C\cos(\omega_0 t + \theta)

:math:`\omega_0` representando a frequência angular em rad/s

Função Senoidal - Harmônicas
----------------------------

* Componentes senoidais múltiplas da frequência fundamental do sinal original

* Estão relacionadas à decomposição do sinal em uma série de Fourier

.. revealjs-break::
	:notitle:
		
.. figure:: /figures/harmonicas.png
	:figwidth: 100%
	:width: 80%
	:align: center
		

Representações de Fourier
=========================	

* Formas de representar sinais por meio de suas componentes no domínio da frequência

.. revealjs-break::
	:notitle:

+----------------------+------------------------------------+-------------------------------------------+
| Propriedade de tempo | Periódica                          | Não-Periódica                             |
+----------------------+------------------------------------+-------------------------------------------+
| Contínuo             | Série de Fourier                   | Transformada de Fourier                   |
+----------------------+------------------------------------+-------------------------------------------+
| Discreto             | Série de Fourier de Tempo Discreto | Transformada de Fourier de Tempo Discreto |
+----------------------+------------------------------------+-------------------------------------------+


Série de Fourier - Definição
----------------------------

* Representação de um sinal periódico como uma soma infinita de funções senoidais

* Formulações fundamentais

	* Série trigonométrica
	
	* Série trigonométrica compacta
	
	* **Série exponencial**

			
Série de Fourier - Formulação
-----------------------------

* Considere uma função periódica :math:`f(t)` com período :math:`T`, definida no intervalo :math:`[-T/2, T/2]`

.. revealjs-break::
	:notitle:
	
* A Série de Fourier na forma exponencial é expressa da seguinte maneira:

.. math::
	x(t) = \sum_{n=-\infty}^{\infty}D_n e^{(jn \omega_0 t)}

onde os coeficientes complexos de Fourier, :math:`D_n`, associados à frequência :math:`\omega`, são obtidos por 

.. math::
	D_n=\frac{1}{T_0}\int_{T_0}x(t)e^{(-jn \omega_0 t)}dt



.. revealjs-break::
	:notitle:

* Análise de um sinal

.. math::
	D_n=\frac{1}{T_0}\int_{T_0}x(t)e^{(-jn \omega_0 t)}dt

* Note que :math:`n` é inteiro

* :math:`D_n` é discreto


.. revealjs-break::
	:notitle:

* Síntese de um sinal

.. math::
	x(t) = \sum_{n=-\infty}^{\infty}D_n e^{(jn \omega_0 t)}
	
* Note que temos um número infinito de coeficientes
* Se :math:`D_n` tiver componentes não nulas ilimitadas, só será possível recontruir perfeitamente o sinal no limite quando :math:`n\rightarrow\infty`
	
Exemplo da Série de Fourier
---------------------------	
	
* Considere o sinal

.. figure:: /figures/exemploFourierA.png
	:figwidth: 100%
	:width: 100%
	:align: center

.. revealjs-break::
	:notitle:

.. figure:: /figures/exemploFourierB.png
	:figwidth: 100%
	:width: 90%
	:align: center
	
	Coeficientes da série de Fourier para a onda quadrada.

Exemplo de Síntese com a Série
------------------------------

* Podemos construir o sinal original usando os coeficientes :math:`D_n`

.. figure:: /figures/exemploFourierA.png
	:figwidth: 100%
	:width: 80%
	:align: center
	
.. revealjs-break::
	:notitle:	

* Componentes :math:`e^{(jn \omega_0 t)}` para cada :math:`n`

.. figure:: /figures/exemploFourierC.png
	:figwidth: 100%
	:width: 60%
	:align: center


.. revealjs-break::
	:notitle:
	
* Síntese usando diferente número de coeficientes
	
.. figure:: /figures/exemploFourierD.png
	:figwidth: 100%
	:width: 60%
	:align: center	

Obtendo a Série em Python
-------------------------

* Temos que usar a biblioteca de matemática simbólica SYMPY

.. exec_code:: 
	:linenos:
	:hide_output:
		
	from sympy import fourier_series, pi, plot
	from sympy.abc import x
	import matplotlib.pyplot as plt
	import numpy as np

	f = x*1
	s = fourier_series(f, (x, 0, 1))
	s1 = s.truncate(n=1)
	p = plot(x,s1, (x, 0, 1), show=False, legend=False)
	p.save('source/figures/exemploSerieSimbolica1.png')

.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=1` componentes

.. figure:: /figures/exemploSerieSimbolica1.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=2` componentes

.. figure:: /figures/exemploSerieSimbolica2.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=3` componentes

.. figure:: /figures/exemploSerieSimbolica3.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=5` componentes

.. figure:: /figures/exemploSerieSimbolica5.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=10` componentes

.. figure:: /figures/exemploSerieSimbolica10.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
* Reconstruindo com :math:`n=100` componentes

.. figure:: /figures/exemploSerieSimbolica100.png
	:figwidth: 100%
	:width: 70%
	:align: center	

Condições de Dirichlet
----------------------

* O sinal deve ser absolutamente integrável

* O sinal deve ter um número finito de descontinuidades dentro de um período

* O sinal deve conter um número finito de máximos e mínimos em um período


Transformada de Fourier
=======================

* Converte uma função contínua no domínio do tempo em uma representação no domínio da frequência

* Permite decompor uma função contínua em suas componentes harmônicas de frequência

* Ela é aplicada à sinais não periódicos, porém, pode ser aplicada também à sinais periódicos


.. revealjs-break::
	:notitle:
	
* Transformada direta

.. math::

	\mathcal{F}[x(t)]=X(\omega) = \int_{-\infty}^{\infty}[x(t) e^{-j\omega t}] dt

onde :math:`\mathcal{F}[\cdot]` representa o operador da transformada de Fourier

:math:`X(\omega)` representa a transformada de Fourier da função :math:`x(t)` no domínio da frequência

:math:`\omega` é a frequência angular

.. revealjs-break::
	:notitle:
	
* Transformada inversa

.. math::
	
	x(t)=\frac{1}{2\pi}\int_{-\infty}^{\infty}[X(\omega)e^{j\omega t}d\omega]
	
Relação da Transformada com a Série de Fourier
----------------------------------------------

* Transformada é uma generalização da Série

* Considerando um sinal periódico :math:`x_{T_0}(t)`, com período :math:`T_0`

* Se :math:`T_0 \rightarrow \infty`, o sinal que se repete a cada período só terá uma nova repetição após um intervalo infinito.

.. math::
		x(t)=\lim_{T_0 \rightarrow \infty}x_{T_0}(t).


.. revealjs-break::
	:notitle:
	
.. figure:: /figures/construcaoSinalAperiodico.png
	:figwidth: 100%
	:width: 90%
	:align: center	
	
Exemplo da Transformada de Fourier
----------------------------------

* Considere o sinal porta retangular, com largura 2, definido como:

.. math::
	ret(t) = \begin{cases} 1, & \text{se } |t| < 1 \\ 0, & \text{caso contrário} \end{cases}

.. revealjs-break::
	:notitle:
	
.. figure:: /figures/exemploPorta.png
	:figwidth: 100%
	:width: 70%
	:align: center	
	
	
Obtenção da Transformada de Fourier em Python
---------------------------------------------

* Podemos obter usando a biblioteca simbólica SYMPY

.. exec_code:: 
	:linenos:
	:hide_output:
	
	from sympy import fourier_transform, exp, cos, plot
	from sympy.functions.special.delta_functions import Heaviside
	from sympy.abc import f, t
				 
	d = Heaviside(t+1) - Heaviside(t-1)        
	X = fourier_transform(d, t, f)
				 
	plt = plot(X, (f, -4, 4), show=False, legend=False)
	plt.save('source/figures/exemploPortaTransformada.png')
	
.. revealjs-break::
	:notitle:
	
.. figure:: /figures/exemploPortaTransformada.png
	:figwidth: 100%
	:width: 70%
	:align: center	

	Transformada de Fourier da função porta.

Propriedades da Transformada
----------------------------

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
          \mathcal{F}[X(t)]= 2\pi x(-\omega)

.. revealjs-break::
	:notitle:
	
.. list-table::
   :widths: 10 10
   :header-rows: 1
   :class: tablefullwidth

   * - Tempo

     - Frequência
	 
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

.. revealjs-break::
	:notitle:
	
.. list-table::
   :widths: 10 10
   :header-rows: 1
   :class: tablefullwidth

   * - Tempo

     - Frequência
	 
   * - Multiplicação

       .. math::
          x(t) y(t)

     - Convolução

       .. math::
          \frac{1}{2\pi} X(\omega) \ast Y(\omega)


Relembrando a Convolução
------------------------

* A convolução entre dois sinais é definida como

.. math::
	c(t)=f(t)\ast g(t) = \int_{-\infty}^{\infty}f(\tau)g(t-\tau)d\tau.
	

.. revealjs-break::
	:notitle:
	
.. figure:: /figures/conv1.png
	:figwidth: 100%
	:width: 100%
	:align: center	

.. revealjs-break::
	:notitle:
	
.. figure:: /figures/conv2.png
	:figwidth: 100%
	:width: 100%
	:align: center	
	
.. revealjs-break::
	:notitle:
	
.. figure:: /figures/conv3.png
	:figwidth: 100%
	:width: 100%
	:align: center	
	
Convolução de um Sinal com Impulso
----------------------------------

* Quando realizamos a convolução entre um sinal e o impulso deslocado (:math:`\delta(t-T)`) temos

.. math::
	c(t)=\delta(t-T)\ast g(t) = \int_{-\infty}^{\infty}\delta(\tau-T)g(t-\tau)d\tau.

* Usando a propriedade do impulso :math:`\int_{-\infty}^{\infty}\delta(t-a)g(t)dt=g(a)` temos

.. math::
	c(t)=\delta(t-T)\ast g(t) = g(t-T).

.. revealjs-break::
	:notitle:
	
.. figure:: /figures/convImpulso.png
	:figwidth: 100%
	:width: 70%
	:align: center

Transformada do Impulso
-----------------------

* A transformada de um impulso deslocado :math:`\delta(t-a)`

.. math::
	\mathcal{F}[\delta(t-a)]&=\int_{-\infty}^{\infty}\delta(t-a)e^{j\omega t}d\omega \\	
	\mathcal{F}[\delta(t-a)]&=e^{-j a \omega}

* Se o impulso for centrado em 0 a transformada é 1

Transformada do Exponencial
---------------------------

* A transformada de um exponencial :math:`x(t)=e^{j \omega_0 t}` pode ser obtida partindo da transformada do impulso. Se

.. math::
	\mathcal{F}[\delta(t-a)]=e^{-j a \omega}

então

.. math::
	\mathcal{F}^{-1}[e^{-j a \omega}]&=\frac{1}{2\pi}\int_{-\infty}^{\infty}e^{-j a \omega}e^{j t \omega}d\omega \\
	\mathcal{F}^{-1}[e^{-j a \omega}]&=\frac{1}{2\pi}\int_{-\infty}^{\infty}e^{j\omega (t-a)}d\omega=\delta(t-a)


.. revealjs-break::
	:notitle:

* Pela definição, a transformada de :math:`e^{j\omega t}` é

.. math::
	\mathcal{F}[e^{j\omega a}]=\int_{-\infty}^{\infty}e^{j a t}e^{-j\omega t}dt=\int_{-\infty}^{\infty}e^{j t (a-\omega)}dt
	
* Dessa forma

.. math::
	\mathcal{F}[e^{j\omega a}]=2 \pi \delta(a-\omega)=2 \pi \delta(\omega-a).
	
Transformada do Cosseno
-----------------------

* Relembrando que

.. math::
	cos(\omega_0 t)=\frac{e^{j \omega_0 t}+e^{-j \omega_0 t}}{2}
	
então

.. math::
	\mathcal{F}[cos(\omega_0 t)]=\mathcal{F}[\frac{e^{j \omega_0 t}+e^{-j \omega_0 t}}{2}]=2 \pi\frac{\delta(\omega + \omega_0)+\delta(\omega -\omega_0)}{2}



.. revealjs-break::
	:notitle:


* Representação gráfica da transformada do cosseno.
	
.. figure:: /figures/transformadaCos.png
	:figwidth: 100%
	:width: 100%
	:align: center
	
Transformada do Seno
--------------------

* De forma análoga, a transformada do seno é obtida considerando


.. math::
	sen(\omega_0 t)=\frac{e^{j \omega_0 t}-e^{-j \omega_0 t}}{2j}
	
.. math::
	\mathcal{F}[sen(\omega_0 t)]=\mathcal{F}[\frac{e^{j \omega_0 t}-e^{-j =\omega_0 t}}{2j}]=2 \pi\frac{\delta(\omega - \omega_0)-\delta(\omega \omega_0)}{2j}
	
.. revealjs-break::
	:notitle:
		
* Representação gráfica da transformada do seno.
	
.. figure:: /figures/transformadaSen.png
	:figwidth: 100%
	:width: 100%
	:align: center


Sinais Limitados no Tempo
-------------------------

* Um sinal limitado no tempo será ilimitado na frequência

.. figure:: /figures/sinalLimitado.png
	:figwidth: 100%
	:width: 100%
	:align: center

Sinais Ilimitados no Tempo
--------------------------

* Um sinal ilimitado no tempo será limitado na frequência
	
.. figure:: /figures/sinalIlimitado.png
	:figwidth: 100%
	:width: 100%
	:align: center
	
Largura de Banda de um Sinal
----------------------------

* Para um sinal contínuo no tempo, a largura de banda pode ser definida como a diferença entre as frequências mais altas e mais baixas presentes no sinal

* Se o sinal for ilimitado na frequência, existem dois critérios

	- Largura Nulo a Nulo: é considerado como critério o ponto em que o sinal cruza com 0
	
	- Largura 3 dB: é considerado como critério o ponto em que o sinal atinge 3 dB do sinal original

.. revealjs-break::
	:notitle:
	
* Largura Nulo a Nulo

	
.. figure:: /figures/larguraNuloANulo.png
	:figwidth: 100%
	:width: 100%
	:align: center


.. revealjs-break::
	:notitle:
	
* Largura 3 dB
	
* Largura de banda de sinal passa-baixa
	
.. figure:: /figures/larguraPassaBaixa.png
	:figwidth: 100%
	:width: 70%
	:align: center
	

.. revealjs-break::
	:notitle:
		
* Largura de banda de sinal passa-faixa
	
.. figure:: /figures/larguraPassaFaixa.png
	:figwidth: 100%
	:width: 100%
	:align: center
	
	
	
Resposta de Sistemas a Entradas Senoidais
-----------------------------------------

Considerando um sistema descrito pela função de transferência 

.. math::
	H(s)=\frac{P(s)}{Q(s)}=\frac{P(s)}{(s-\lambda_1)\dots(s-\lambda_n)},

a resposta :math:`y(t)` desse sistema, para uma entrada exponencial complexa

.. math::
	x(t)=e^{jwt}u(t) 

pode ser obtida utilizando a transformada de Laplace de :math:`X(s)` de :math:`x(t)`, calculando a transformada inversa de 

.. math::
	Y(s)=H(s)X(s).

.. revealjs-break::
	:notitle:

A transformada de Laplace unilateral, :math:`X(s)`, de :math:`x(t)` é

.. math::
	X(s)=\frac{1}{s-j\omega},
	
com isso 

.. math::
	Y(s)=H(s)X(s)=\frac{P(s)}{(s-\lambda_1)\dots(s-\lambda_n)(s-j\omega)}.
	
Obtendo a expansão de :math:`Y(s)` por frações parciais, obtemos

.. math::
	Y(s)=\sum_{i=1}^{n}\frac{k_i}{s-\lambda_i}+\frac{P(s)}{Q(s)}\Bigg|_{s=j\omega} \frac{1}{s-j\omega}=\sum_{i=1}^{n}\frac{k_i}{s-\lambda_i}+H(j\omega)\frac{1}{s-j\omega}.

.. revealjs-break::
	:notitle:
	
A saída do sistema para essa entrada exponencial é

.. math::
	y(t)=\sum_{i=1}^{n}k_i e^{\lambda_i t}+H(j\omega)e^{j\omega t}, \hspace{1cm} t\ge 0.
	
a qual é composta por dois termos.

O primeiro termo é a componente que define o regime transitório da resposta, a qual tende a zero quando o tempo tende a infinito, já que

.. math::
	\lim_{t\rightarrow  \infty}\sum_{i=1}^{n}k_i e^{\lambda_i t}=0 ,
	
considerando que o sistema é BIBO estável. 

.. revealjs-break::
	:notitle:

Já a segunda parcela é o componente que define o comportamento durante o regime permanente de :math:`y(t)`, pois

.. math::
	\lim_{t\rightarrow  \infty}y(t)=\lim_{t\rightarrow  \infty}\sum_{i=1}^{n}k_i e^{\lambda_i t}+\lim_{t\rightarrow  \infty}H(j\omega)e^{j\omega t}, \hspace{1cm} t\ge 0.

e :math:`\lim_{t\rightarrow  \infty}\sum_{i=1}^{n}k_i e^{\lambda_i t}=0`, fazendo com que, em regime permanente, a saída seja definida por

.. math::
	y_{ss}(t)=H(j\omega)e^{j\omega t}, \hspace{1cm} t\ge 0.

.. revealjs-break::
	:notitle:

Considerando que :math:`h(s)` é representado na forma polar como

.. math::
	H(s)=|H(j\omega)| e^{j\angle H(j\omega)}, 
	

A resposta de um sistema dinâmico à uma entrada pode ser interpretada como o espectro do sinal de entrada escalado por um ganho :math:`|H(j\omega)|`, e deslocado por uma fase :math:`\angle H(j\omega)`



Diagrama de Bode
----------------

.. figure:: /figures/exemploBode.png
	:figwidth: 100%
	:width: 70%
	:align: center


Filtro Ideais
-------------

* Um filtro atenua seletivamente um conjunto de frequências do seu sinal de entrada

.. figure:: /figures/blocosFiltro.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
.. math:: 
		x_f(t)=h(t)\ast x(t) \\
		X_f(omega)=H(\omega)X(\omega)

.. revealjs-break::
	:notitle:
	
- **Filtro passa-baixas ideal**: Todas as frequências abaixo da frequência de corte, :math:`w_c`, são mantidas, enquanto todas frequência acima de :math:`w_c` são definidas como zero

.. math::
    H(j\omega) = 	\begin{cases}
						1 &: \omega\leq\omega_c\\
						0 &: \text{caso contrário}
					\end{cases}

.. revealjs-break::
	:notitle:
	
- **Filtro passa-altas ideal**: o filtro passa-altas mantém as frequências acima de :math:`w_c` e atenua completamente as frequências abaixo de :math:`w_c`

.. math::
    H(j\omega) = 	\begin{cases}
						1 &: \omega>\omega_c\\
						0 &: \text{caso contrário}
					\end{cases}
     
.. revealjs-break::
	:notitle:
	
- **Filtro passa-bandas ideal**: um filtro passa-bandas mantém as frequências entre :math:`\omega_L` e :math:`\omega_H` atenuando todas as demais frequências

.. math::
    H(j\omega) = 	\begin{cases}
						1 &: \omega_L\leq\omega\leq\omega_H\\
						0 &: \text{caso contrário}
					\end{cases}

.. revealjs-break::
	:notitle:

- **Filtro rejeita-bandas ideal**: o filtro rejeita-bandas define um conjunto de frequências, entre :math:`\omega_L` e :math:`\omega_H`, que será rejeitado, com as demais frequências sendo mantidas

- **Filtro Notch**: projetado para rejeitar uma frequência bem específica (em sistemas de áudio é geralmente a frequência da rede de alimentação)

.. math::
    H(j\omega) = 	\begin{cases}
						0 &: \omega_L\leq\omega\leq\omega_H\\
						1 &: \text{caso contrário}
					\end{cases}

.. revealjs-break::
	:notitle:
	
.. figure:: /figures/filtrosIdeais.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
	
Filtros Reais
-------------

.. figure:: /figures/exemploBodeSenos.png
	:figwidth: 100%
	:width: 100%
	:align: center

	**Diagrama de Bode para o filtro passa-baixas *Butterworth* de segunda ordem.**