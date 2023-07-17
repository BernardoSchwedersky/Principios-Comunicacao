================
Série de Fourier
================

Definição
=========

A Série de Fourier é uma técnica matemática que permite representar uma função periódica como uma soma infinita de funções senoidais ou funções exponenciais complexas. Ela foi desenvolvida pelo matemático Jean-Baptiste Joseph Fourier no século XIX e tem uma ampla gama de aplicações em física, engenharia e matemática.

A formulação da Série de Fourier na forma exponencial envolve o uso das funções exponenciais complexas, especificamente a função exponencial imaginária, denotada por :math:`e^{(j \omega_0 t)}`, onde :math:`j` é representa a unidade imaginária (:math:`j = \sqrt{-1}`) e :math:`\omega_0` é a frequência angular.

Considere uma função periódica :math:`f(t)` com período :math:`T_0`, definida no intervalo :math:`[-T_0/2, T_0/2]`. A Série de Fourier na forma exponencial é expressa da seguinte maneira:

.. math::

	x(t) = \sum_{n=-\infty}^{\infty}D_n e^{(jn \omega_0 t)}

onde os coeficientes complexos de Fourier, :math:`D_n`, associados à frequência :math:`\omega`, são obtidos por 

.. math::

	D_n=\frac{1}{T_0}\int_{T_0}x(t)e^{(-jn \omega_0 t)}dt.

A representação da série de Fourier na forma exponencial é interessante pois é capaz de representar funções periódicas de forma mais compacta, em comparação com a forma trigonométrica da Série de Fourier. 

Os coeficientes da Série de Fourier possuem características fundamentais que descrevem a natureza da decomposição harmônica de uma função periódica. Os coeficientes de Fourier são complexos, o que significa que eles possuem uma parte real e uma parte imaginária. Essa função complexa pode ser representada por sua amplitude e fase, na forma polar. Nessa representação, a função complexa é representada pela amplitude (magnitude) de :math:`|D_n|`, e pela fase :math:`\angle(D_n)`. A amplitude representa a contribuição da componente harmônica na soma total da Série de Fourier, enquanto a fase indica a defasagem relativa da componente harmônica em relação à função original. Cada coeficiente :math:`D_n` está associado a uma componente harmônica específica na Série de Fourier. A frequência angular :math:`\omega` correspondente à componente harmônica é dada por :math:`\omega = 2\pi n/T_o` , onde n é um número inteiro. Quanto maior o valor de n, maior a frequência e o número de oscilações da componente harmônica.

O estudo da natureza dos coeficientes de Fourier permite compreender como as funções periódicas podem ser decompostas em componentes harmônicas e reconstruídas usando uma combinação dessas componentes. Essa análise é fundamental para a análise de sinais, processamento de sinais, síntese de formas de onda e diversas aplicações científicas e tecnológicas que envolvem fenômenos periódicos.

Exemplo da Série de Fourier
===========================

Considere um sinal periódico, definido como um trem de pulsos, variando entre 0 e 1 e com período fundamental :math:`T_o=2`. Esse sinal é representado, para cada período :math:`T_0`, como:

.. math::

	y(t) = \Bigg\{\begin{matrix}1, &t < T_0/2 \\	0, &t \ge T_o/2\end{matrix}


.. figure:: /figures/exemploFourierA.png
	:figwidth: 80%
	:align: center
	
	**Onda quadrada com período T=2.** 
	
	
Análise
=======

A série de Fourier pode ser utilizada para a análise de um sinal periódico. Como a série de Fourier permite decompor o sinal periódico em uma soma infinita de componentes harmônicos, que são múltiplos inteiros da frequência fundamental, podemos determinar os coeficientes de Fourier, que serão usados para determinar a amplitude e a fase de cada componente harmônico na série de Fourier do sinal analisado. Para o trem de pulsos que queremos analisar, os coeficientes da série de Fourier podem ser obtidos usando a equação:

.. math::

	D_n=\frac{1}{T_0}\int_{T}x(t)e^{(-jn \omega_0 t)}dt.   

Considerando o período fundamental como :math:`T_0=2`, temos :math:`\omega_0=2\pi /T_0=\pi`. Dessa forma, obtemos:

.. math::

	D_n=&\frac{1}{2}\int_{0}^{2}x(t)e^{(-jn \pi t)}dt, 
	
	D_n=&\frac{1}{2}\int_{0}^{1}1\times e^{(-jn \pi t)}dt+\frac{1}{2}\int_{1}^{2}0\times e^{(-jn \pi t)}dt, 
	
	D_n=&=\frac{1}{2}\int_{0}^{1}e^{(-jn \pi t)}dt.

Os coeficiêntes :math:`D_n` são representados pela equação:

.. math::

	D_n=\frac{-1}{2jn\pi}(e^{-jn\pi}-1).

Os coeficiêntes da série de Fourier do trem de pulsos podem ser representados na forma polar, como apresentado na figura a seguir.

.. figure:: /figures/exemploFourierB.png
	:figwidth: 80%
	:align: center
	
	**Coeficientes da série de Fourier para a onda quadrada.** 

Síntese
=======

A série de Fourier pode ser usada, também, para a síntese de um sinal a partir de senóides fundamentais. Se utilizarmos os coeficientes :math:`D_n` obtidos anteriormente, é possível reconstruir o sinal original, utilizando a equação:

.. math::

	x(t) = \sum_{n=-\infty}^{\infty}D_n e^{(jn \omega_0 t)}.
	
É importante notar que essa equação considera um número infinito de coeficiêntes, dessa forma, se :math:`D_n` tiver componentes não nulas ilimitadas, só será possível recontruir perfeitamente o sinal no limite quando :math:`n\rightarrow\infty`. 
	
.. figure:: /figures/exemploFourierC.png
	:figwidth: 80%
	:align: center
	
	**Senóide fundamental, com período T=2, e suas harmônicas.** 

.. figure:: /figures/exemploFourierD.png
	:figwidth: 80%
	:align: center

	**Exemplo da construção de uma onda quadrada por meio dos coeficientes da Série de Fourier.** 


.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt

		T = 2

		def f(t):
			return ((t % T)<=0.5*T).astype('float')

		t = np.linspace(-0.2,2.2*T,1000)
		x = f(t)

		plt.figure(figsize=(10,2))
		plt.plot(t,x,lw=2)
				
		plt.tight_layout()

		d = np.zeros(21, dtype=complex)
		n1=np.arange(0, 11, dtype=int)
		for k in n1:
			if k==0:
				d[k+10]=1/2;
			else:
				d[k+10] = -1 / (2j * k * np.pi) * (np.exp(-1j*k*np.pi)-1)
				if np.angle(d[k-11])==np.pi:
					d[k-11]=0

		n2=np.arange(-10, 0, dtype=int)
		for k in n2:
			if k==0:
				d[k-11]=1/2;
			else:
				d[k-11] = -1 / (2j * k * np.pi) * (np.exp(-1j*k*np.pi)-1)
				if np.angle(d[k-11])==np.pi:
					d[k-11]=0

		modulo=np.abs(d)
		plt.clf()
		plt.figure(figsize=(10,6))
		plt.subplot(2,1,1)
		plt.stem(modulo, use_line_collection=True)
		plt.xlabel(r'$n$')
		plt.ylabel(r'$|D_n|$')
		plt.grid(True)
		plt.xticks([0,5,10,15,20],['-10','-5','0','5','10'])
		
		fase=np.angle(d)		
		plt.subplot(2,1,2)
		plt.stem(fase, use_line_collection=True) #Usar o mod para transformar o angulo de -pi a pi para 0 a 2pi
		plt.xlabel(r'$n$')
		plt.ylabel(r'$\angle D_n$')
		plt.grid(True)
		plt.xticks([0,5,10,15,20],['-10','-5','0','5','10'])
		
		plt.savefig('source/figures/exemploFourierB.png',transparent=True)

		def phi(t, k):
			if k==0:
				return 1/2 * np.ones_like(t)
			return -1j / (2 * k * np.pi) * (1 - np.exp(-1j*k*np.pi)) * np.exp( 1j * k * 2 * np.pi / T * t)

		plt.clf()
		plt.figure(figsize=(10,10))
		for k in range(1,6,1):
			xak = phi(t,k)+phi(t,-k)
			plt.subplot(5,1,k)
			plt.plot(t,xak,lw=2)
			plt.axis([-0.2, 2.2*T, -1.2, 1.2])
			plt.ylabel('n{0}'.format(k))
			plt.xlabel('t')			
			
		plt.tight_layout()
		plt.savefig('source/figures/exemploFourierC.png',transparent=True)

		plt.clf()
		plt.figure(figsize=(10,10))
		
		xa = phi(t,0)
		for k in range(1,11,2):
			xak = phi(t,k)+phi(t,-k)
			xa = xa + xak			
			plt.subplot(5,1,int(k/2)+1)
			plt.plot(t,x,lw=1)
			plt.plot(t,xa,lw=2)
			plt.axis([-0.2, 2.2*T, -0.2, 1.2])
			plt.ylabel('x{0}'.format(k))
			plt.xlabel('t')
			
		plt.tight_layout()
		plt.savefig('source/figures/exemploFourierD.png',transparent=True)

Exemplo Numérico
================

Existem algumas formas distintas para obtenção da série de Fourier de um sinal. Os coeficientes podem ser obtidos usando bibliotecas simbólicas, na qual o sinal desejado será representado como uma função simbólica, com os coeficientes sendo obtidos a partir da definição, por meio da resolução simbólica do problema. Uma segunda forma consiste na utilização de outro algoritmo, do qual os coeficientes da série de Fourier podem ser extraídos. Esse algoritmo é o algoritmo FFT (*Fast Fourier Transform*), que obtém a transformada de Fourier, considerando apenas um período do sinal. A partir dos coeficiêntes da transformada de Fourier, podemos obter os coeficientes da série de Fourier. A relação entre a série de Fourier e a transformada de Fourier é apresentada na aula seguinte, que trata da transformada de Fourier.

-----------------
Solução Simbólica
-----------------

Podemos obter os coeficientes da série de Fourier de um sinal usando a biblioteca SYMPY, a qual é dedicada à matemática simbólica.

.. container:: toggle, toggle-hidden

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
		
		s2 = s.truncate(n=2)
		p = plot(x,s2, (x, 0, 1), show=False, legend=False)
		p.save('source/figures/exemploSerieSimbolica2.png')
		
		s3 = s.truncate(n=3)
		p = plot(x,s3, (x, 0, 1), show=False, legend=False)
		p.save('source/figures/exemploSerieSimbolica3.png')
		
		s5 = s.truncate(n=5)
		p = plot(x,s5, (x, 0, 1), show=False, legend=False)
		p.save('source/figures/exemploSerieSimbolica5.png')
		
		s10 = s.truncate(n=10)
		p = plot(x,s10, (x, 0, 1), show=False, legend=False)
		p.save('source/figures/exemploSerieSimbolica10.png')
		
		s100 = s.truncate(n=100)
		p = plot(x,s100, (x, 0, 1), show=False, legend=False)
		p.save('source/figures/exemploSerieSimbolica100.png')
		

		
		

.. figure:: /figures/exemploSerieSimbolica.png
	:figwidth: 80%
	:align: center

	**Exemplo da série de Fourier usando SYMPY.** 
	
--------------------
Solução usando a FFT
--------------------

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:

		import numpy as np
		from matplotlib import pyplot as plt

		def f(t):
			return (t % 1)
		t = np.linspace(0,1,50)
		x = f(t)
		
		n = len(x)
		COMPONENTES = [4]

		for c in COMPONENTES:
			colors = np.linspace(start=100, stop=255, num=c)
			for i in range(c):
				X = np.fft.fft(x)
				np.put(X, range(i+1, n), 0.0)
				ifft = np.fft.ifft(X)
				plt.plot(x, ifft, color=plt.cm.Reds(int(colors[i])), alpha=.70)

			plt.title("Primeiras {c} componentes da série de Fourier".format(c=c))
			plt.plot(t,x, label="Original dataset")
			plt.grid(linestyle='dashed')
			plt.legend()

Exercícios
==========

-----------
Exercício 1
-----------

Para os sinais apresentados a seguir, determine a energia:

a)

	
b)

c)

-----------
Exercício 2
-----------

Para os sinais apresentados a seguir, determine o período fundamental, a frequência e a potência:

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt

		T0 = 4

		def f(t):
			return (t % T0)
			

		t = np.linspace(-2.2,2.2*T0,1000)
		x = f(t)

		plt.figure(figsize=(10,2))
		plt.plot(t,x,lw=2)
		plt.tight_layout()
		plt.savefig('source/figures/exercicioFourier2a.png',transparent=True)
		
.. figure:: /figures/exercicioFourier2a.png
	:figwidth: 80%
	:align: center

	**Exercício 2a.** 
	
b) 

.. container:: toggle, toggle-hidden

	.. exec_code:: 
		:linenos:
		:hide_output:

		import numpy as np
		import matplotlib.pyplot as plt

		T0 = np.pi

		def f(t):
			return np.abs(np.sin(t))

		t = np.linspace(-10,10,1000)
		x = f(t)

		plt.figure(figsize=(10,2))
		plt.plot(t,x,lw=2)
		plt.tight_layout()
		plt.savefig('source/figures/exercicioFourier2b.png',transparent=True)
		
.. figure:: /figures/exercicioFourier2b.png
	:figwidth: 80%
	:align: center

	**Exercício 2b.** 
	
-----------	
Exercício 3
-----------

Para os sinais do exercício 2.a e 2.b, calcule a transformada de Fourier, e mostre graficamente os coeficientes da mesma.


