=================
Sinais e Sistemas
=================

Sinais
======

O conceito de sinal, conforme definido por B. P. Lathi, refere-se a uma função de uma ou mais variáveis independentes que carrega informações ou transmite um determinado significado. Em outras palavras, um sinal é uma representação matemática de algum fenômeno físico, como um som, uma imagem, um movimento, uma medida elétrica, entre outros.

Um sinal pode ser considerado como uma função que varia no tempo, espaço ou em qualquer outra dimensão relevante para o fenômeno em questão. Essa variação do sinal ao longo do tempo ou espaço pode ser descrita por uma função matemática, geralmente expressa em termos de amplitude, frequência e fase.

---------------
Degrau Unitário
---------------

O sinal degrau unitário, também conhecido como função degrau unitário ou degrau unitário de Heaviside, é um sinal que tem valor zero para qualquer tempo anterior a zero e um valor constante de 1 para qualquer tempo após zero.

Matematicamente, o sinal degrau unitário :math:`u(t)` pode ser definido como:

.. math::

	u(t) = \Bigg\{\begin{matrix}0, &t < 0 \\	1, &t \ge 0\end{matrix}

Essa função é representada graficamente como uma linha horizontal a partir do ponto :math:`t=0`, com valor 0 para :math:`t<0` e valor 1 para :math`t>=0`.

O sinal degrau unitário é frequentemente utilizado em sistemas e análise de sinais para representar eventos que ocorrem no tempo, como o acionamento de um interruptor ou o início de uma operação. Ele também é usado em cálculos e modelagem matemática para simplificar a representação de sistemas e fenômenos que mudam de estado abruptamente em um determinado instante de tempo.

.. container:: toggle, toggle-hidden

	.. exec_code:: figura_degrau 
		:linenos:
		:hide_output:
		
		import matplotlib.pyplot as plt
		import numpy as np
		import locale
		locale.setlocale(locale.LC_NUMERIC, "pt_BR")
		plt.rcdefaults()
		plt.rcParams['axes.formatter.use_locale'] = True
		
		x = np.array([-5, 0, 5])
		y = np.array([0, 1, 1])
		  
		plt.step(x, y,'k', where='post')
		plt.grid()
		plt.ylabel("u(t)")
		plt.xlabel("t")
		
		plt.savefig('source/figures/degrau.png',transparent=True)

.. figure:: /figures/degrau.png
	:figwidth: 80%
	:align: center

	**Exemplo de um degrau unitário.** 

----------------
Impulso Unitário
----------------

O sinal impulso unitário, também conhecido como função impulso unitário ou função delta de Dirac, é um sinal especial que possui um valor indeterminado em t=0 e é zero para qualquer outro valor de tempo.

Matematicamente, o sinal impulso unitário :math:`\delta(t)` pode ser definido como:

.. math::

	\delta(t) = \Bigg\{\begin{matrix}\infty, &t = 0 \\	0, &t \neq 0\end{matrix}
	

No entanto, a função impulso unitário :math:`\delta(t)` não é uma função no sentido clássico, pois não é definida para todos os valores de t. Em vez disso, é uma distribuição generalizada, que é uma ferramenta matemática usada para descrever fenômenos como pulsos infinitamente estreitos e pontuais.

O sinal impulso unitário tem propriedades únicas e importantes. Uma delas é a propriedade de integração, onde a integral do sinal impulso unitário em relação ao tempo resulta em 1. Isso é conhecido como a propriedade de área unitária. Essa propriedade é definida matematicamente como:

.. math::

	\int_{-\infty}^{+\infty}\delta(t) = 1.

.. container:: toggle, toggle-hidden

	.. exec_code:: figura_impulso
		:linenos:
		:hide_output:
		
		import matplotlib.pyplot as plt
		import numpy as np
		from scipy import signal
		import locale
		locale.setlocale(locale.LC_NUMERIC, "pt_BR")
		plt.rcdefaults()
		plt.rcParams['axes.formatter.use_locale'] = True
		
		impulso = signal.unit_impulse(1000, 'mid')
		  
		plt.plot(np.arange(-5, 5, 0.01), impulso, 'k')
		plt.plot(0, 1, 'k^')
		plt.margins(0.1, 0.1)
		plt.xlabel('t')
		plt.ylabel('$ \delta $ (t)')
		plt.grid(True)
		
		plt.savefig('source/figures/impulso.png',transparent=True)

.. figure:: /figures/impulso.png
	:figwidth: 80%
	:align: center

	**Exemplo de um impulso unitário.** 

-----------------------
Exponencial Decrescente
-----------------------

O sinal exponencial :math:`e^{-at}`, onde :math:`e` é a base do logaritmo natural e :math:`a` é uma constante real positiva, é uma função matemática que descreve um decaimento exponencial no tempo.

Matematicamente, o sinal exponencial e^(-at) pode ser definido como:

.. math::

	f(t) = e^{(-at)}

Nessa equação, "t" representa a variável independente, geralmente associada ao tempo, e "a" é um coeficiente que determina a taxa de decaimento. Quanto maior o valor de "a", mais rápido será o decaimento exponencial.

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:
		
		import matplotlib.pyplot as plt
		import numpy as np
		import locale
		locale.setlocale(locale.LC_NUMERIC, "pt_BR")
		plt.rcdefaults()
		plt.rcParams['axes.formatter.use_locale'] = True
		
		t = np.linspace(0, 2, 100)
		  
		y1 = np.exp(-1*t)
		y2 = np.exp(0*t)
		y3 = np.exp(1*t)

		plt.subplot(3,1,1)
		plt.plot(t,y1,'k')
		plt.xlabel('t')
		plt.ylabel('y (t)')
		plt.ylim(0,1.2)		
		plt.grid(True)
		
		plt.subplot(3,1,2)
		plt.plot(t,y2,'k')
		plt.xlabel('t')
		plt.ylabel('y (t)')
		plt.ylim(0,1.2)	
		plt.grid(True)
		
		plt.subplot(3,1,3)
		plt.plot(t,y3,'k')
		plt.xlabel('t')
		plt.ylabel('y (t)')
		plt.ylim(0,10)	
		
		plt.grid(True)
		plt.tight_layout()
		
		plt.savefig('source/figures/exponencial.png',transparent=True)

.. figure:: /figures/exponencial.png
	:figwidth: 80%
	:align: center

	**Exemplo de sinais exponenciais.** 

-----------------
Sinais Periódicos
-----------------

Um sinal periódico é um sinal que se repete em intervalos regulares de tempo. Matematicamente, um sinal periódico pode ser descrito como uma função :math:`f(t)` que possui a propriedade de periodicidade, ou seja, :math:`f(t + T) = f(t)`, onde T é o período fundamental do sinal.

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:
		
		import matplotlib.pyplot as plt
		import numpy as np
		import locale
		locale.setlocale(locale.LC_NUMERIC, "pt_BR")
		plt.rcdefaults()
		plt.rcParams['axes.formatter.use_locale'] = True
		
		t = np.linspace(0, 1, 100)
		  
		y = np.exp(-1*t)
		
		yp = y
		for i in range(1,10):
			yp = np.concatenate((yp, y), axis=0)
			
		tp = np.linspace(0, 10, 1000)
		plt.plot(tp,yp,'k')

		plt.xlabel('t')
		plt.ylabel('y (t)')
		plt.xlim(0,5)	
		plt.ylim(0,1.2)		
		plt.grid(True)
		plt.xticks([1,2,3,4],['T','2T','3T','4T'])
		
		plt.savefig('source/figures/sinal_periodico.png',transparent=True)
		
.. figure:: /figures/sinal_periodico.png
	:figwidth: 80%
	:align: center

	**Exemplo de sinal periódico com período T.** 
	
Por exemplo, um sinal periódico representado por uma onda senoidal pode ser definido matematicamente como:

.. math::

	f(t) = \sin(2\pi \cdot \frac{t}{T})

onde, a função fundamental é uma senoide com frequência angular de :math:`2\pi/T`, com :math:`T` representando o período do sinal. 

À um sinal periódico é associado o conceito de harmônicas. As harmônicas de um sinal são componentes senoidais que compõem a sua representação periódica. Elas são múltiplos da frequência fundamental do sinal e estão relacionadas à decomposição do sinal em uma série de Fourier, que será vista nas próximas seções.

As harmônicas superiores têm frequências múltiplas da frequência fundamental. A primeira harmônica é a fundamental e tem a frequência angular :math:`\omega_0=2\pi/T`. As harmônicas subsequentes são chamadas de harmônicas de ordem superior e têm frequências angulares :math:`\omega_n=2\pi n/T`, onde n é um número inteiro positivo.

.. container:: toggle, toggle-hidden

	.. exec_code:: exemplo_harmonicas signalplots
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt

		plt.clf()
		T = 5
		t = np.linspace(0,T,1000)

		K = 5
		fig, axs = plt.subplots(nrows=K, sharex=True)
		for k in range(1,K+1):
			axs[k-1].plot(t, np.sin(2*k*np.pi*t / T),'k')
			axs[k-1].set_ylabel('sen({0}t/T)'.format(k))
			
		plt.xlabel('t')
		plt.savefig('source/figures/harmonicas.png',transparent=True)

.. figure:: /figures/harmonicas.png
	:figwidth: 80%
	:align: center

	**Exemplo de uma senóide e suas harmônicas.** 

------------------
Energia e Potência
------------------

A energia de um sinal contínuo é calculada integrando o quadrado do valor absoluto do sinal em relação ao tempo. Para um sinal discreto, a energia é obtida somando o quadrado dos valores absolutos de cada amostra. A fórmula para calcular a energia de um sinal é dada por:

.. math::

	E = \int_{-\infty}^{\infty} |x(t)|^2 \, dt \quad \text{(para sinais contínuos)},

	E = \sum_{n=-\infty}^{\infty} |x[n]|^2 \quad \text{(para sinais discretos)},

onde :math:`x(t)` é o sinal contínuo no tempo, :math`x[n]` é o sinal discreto na amostra n, e :math:`|x|` é o valor absoluto de x.

A energia de um sinal indica a quantidade total de energia contida no sinal ao longo de todo o tempo (ou amostras). É uma medida útil para sinais de duração finita.

A potência de um sinal é uma medida da média da energia do sinal em relação ao tempo. Para um sinal contínuo, a potência é calculada como o limite da energia média por unidade de tempo quando o tempo tende ao infinito. Para um sinal discreto, a potência é obtida dividindo a energia pelo número total de amostras. A fórmula para calcular a potência de um sinal é dada por:

.. math::

	P = \lim_{{T \to \infty}} \frac{1}{T} \int_{-T/2}^{T/2} |x(t)|^2 \, dt \quad \text{(para sinais contínuos)},

	P = \frac{1}{N} \sum_{n=0}^{N-1} |x[n]|^2 \quad \text{(para sinais discretos)},

onde T é o período de observação (para sinais contínuos); N é o número total de amostras (para sinais discretos).

A potência de um sinal fornece uma medida da taxa de energia média do sinal ao longo do tempo (ou amostras). É útil para sinais de duração infinita ou para caracterizar sinais estatisticamente. 

É importante notar que a energia e a potência são conceitos distintos. A energia é uma quantidade total, enquanto a potência é uma medida média. Em alguns casos, a energia e a potência podem ser equivalentes, mas, em geral, são usadas para diferentes propósitos de análise de sinais.


Sistemas
========

Um sistema é definido como a entidade que recebe um sinal de entrada e produz um sinal de saída, de acordo com uma relação ou transformação específica. Em outras palavras, um sistema é uma função ou operação que mapeia um sinal de *entrada* para um sinal de *saída*. Um sistema pode ser físico ou abstrato. Um sistema físico refere-se a um dispositivo ou componente físico que recebe um sinal de entrada, como um circuito eletrônico, um sistema de comunicação, um motor, entre outros. Já um sistema abstrato é uma representação matemática ou conceitual de um processo que transforma o sinal de entrada em um sinal de saída, como um algoritmo, uma equação ou um modelo matemático.

Existem diversas classificações de sistemas, sendo uma das mais importantes a linearidade. Um sistema linear exibe propriedades de aditividade e homogeneidade, o que significa que a resposta do sistema a uma combinação linear de sinais de entrada é igual à combinação linear das respostas individuais a cada sinal de entrada. Já um sistema não-linear não obedece a essas propriedades.

Outra classificação importante diz respeito à invariância no tempo. Um sistema invariante no tempo possui propriedades que não mudam com o tempo, ou seja, sua resposta é a mesma independentemente do instante em que o sinal de entrada é aplicado. Já um sistema variante no tempo possui propriedades que mudam com o tempo, e sua resposta pode variar ao longo do tempo.

