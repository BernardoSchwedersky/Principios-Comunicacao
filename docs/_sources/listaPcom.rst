=====================
Lista de Exercícios 1
=====================

Compilado de exercícios sugeridos para auxiliar o estudo na disciplina Princípios de Comunicação. 


Transmissão de Sinais
=====================

-----------
Exercício 1
-----------

Qual o motivo de não ser possível transmitir em banda base vários sinais em um canal compartilhado. Discuta como o processo de modulação resolve esse problema.

-----------
Exercício 2
-----------

A modulação consiste na multiplicação de um sinal por uma portadora senoidal. Apresente a formulação de uma portadora senoidal e obtenha a transformada de Fourier da mesma.

-----------
Exercício 3
-----------

A multiplicação de um sinal por uma portadora senoidal é equivalente à convolução das tranformadas de Fourier dos sinais. Mostre que, quando um dos sinais é um cosseno, o resultado dessa convolução é o deslocamento da transformada de Fourier do outro sinal. 

-----------
Exercício 4
-----------

Para uma mensagem definida como :math:`m(t)=sinc(5t)`, obtenha:

a) A energia do sinal, utilizando o teorema de Parseval;

b) Obtenha qual a largura de banda B, considerando como critério termos :math:`95\%` da potência do sinal.


Modulação em Amplitude
======================

-----------
Exercício 1
-----------

Considerando que se deseja transmitir 3 mensagens compartilhando o mesmo canal. Para tal, será utilizada a modulação utilizando portadoras senoidais, de forma a multiplexar as mensagens na frequência. O espectro em frequência desses sinais é apresentado na figura a seguir.

.. figure:: /figures/ExPcom1.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
	**Fig. 1: Espectros em frequência das mensagens.**
	
a) Determine qual a menor largura de banda que seria ocupada em um canal de transmissão, considerando que os sinais sejam transmitidos usando modulação AM-DSB-SC.

b) Caso o sinal :math:`m_2(t)` seja transmitido utilizando AM-SSB, e os demais sejam transmitidos usando AM-DSB, determine qual é a menor largura de banda necessária em um canal para a transmissão dos 3 sinais. 

c) Para o caso em que os 3 sinais são transmitidos utilizando AM-SSB, determine a frequência da portadora de cada um dos sinais, considerando que os sinais são transmitidos utilizando a menor largura de banda necessária. Esboce o espectro de frequência ocupado pelas mensagens.

-----------
Exercício 2
-----------

Para os sinais (i) :math:`m(t)=cos(100t)` e (ii) :math:`m(t)= cos(200t)+ sen(150t)`, esboce o espectro das mensagens :math:`m(t)` e o espectro das mensagens moduladas em AM-DSB-SC, modulados com portadora :math:`cos 500 t`. 

-----------
Exercício 3
-----------

O sinal de mensagem :math:`m(t)=2cos(400t)+4sen(500t)` modula um sinal de portadora :math:`c(t)=A cos(8000t)` usando modulação AM-DSB-SC. 

a) Determine as representações no domínio do tempo e da frequência do sinal modulado.
b) Esboce o espectro do sinal modulado.
c) Calcule a potência do sinal modulado.

-----------
Exercício 4
-----------

Para o sinal modulado em amplitude, descrito por :math:`\phi(t)=cos(5t)cos(1000t)`, desenhe o diagrama de blocos do processo de demodulação síncrona, determinando os sinais envolvidos. Esboce o espectro de frequência dos sinais envolvidos nesse processo de demodulação, e discuta qual interpretação desse processo de demodulação no domínio da frequência.

-----------
Exercício 5
-----------

A modulação AM-DSB-SC transmite um sinal com potência menor que a AM-DSB, o que é explicado pelo fato da modulação AM-DSB transmitir uma cópia da portadora do sinal. Se a mensagem a ser transmitida consistir em um sinal :math:`m(t)=sinc(t)`, determine:

a) Quais os sinais modulados para AM-DSB-SC e AM-DSB.
b) Qual a potência do sinal modulado em AM-DSB-SC. (Lembre-se do teorema de Parseval)
c) Qual o fator de modulação :math:`\mu` que minimiza a potência do sinal transmitido em AM-DSB.
d) Qual a razão entre a potência dos sinais AM-DSB e AM-DSB-SC.

-----------
Exercício 6
-----------

Duas formas para reduzir a largura de banda necessária para transmissão AM são as técnicas AM-SSB e AM-VSB. Discuta porque essas duas técnicas reduzem o tamanho do espectro necessário, e qual a diferença entre elas. 

-----------
Exercício 7
-----------

O processo de demodulação por detecção de envelope envolve três passos fundamentais: a retificação do sinal; a filtragem passa-baixas; e a retirada do valor DC do sinal. Dessa forma, desenhe uma mensagem :math:`m(t)=cos(t)` modulada em AM-DSB com fator de modulação :math:`\mu=1` e mostre graficamente cada etapa do processo de demodulação por detecção de envelope.

-----------
Exercício 8
-----------

Considerando duas estações meteorológicas que se comunicam com uma estação central de captação de dados e desejam transmitir informações compartilhando o mesmo meio físico (cabo). A tecnologia escolhida para transmissão é a modulação AM-DSB. Se o sinal da mensagem da estação 1 consistir em :math:`m_1(t)=sinc(t)` e o da mensagem da estação 2 consistir em um sinal :math:`m_1(t)=sinc(2t)`, determine qual a largura de banda necessária para transmitir cada mensagem garantindo que nenhuma informação seja perdida.

-----------
Exercício 9
-----------

O projetista de um dispositivo de recepção de sinais transmitidos com modulação AM criou o seguinte diagrama de blocos geral. Explique qual a função de cada um dos blocos.

.. figure:: /figures/Recepcao.png
	:figwidth: 100%
	:width: 50%
	:align: center
	
	**Fig. 2: Diagrama de blocos de um sistema de recepção AM**

------------
Exercício 10
------------

Na modulação QAM é possível transmitir dois sinais utilizando a mesma portadora, compartilhando a respectiva porção do espectro. Mostre, matematicamente, como podemos recuperar cada uma das mensagens, utilizando recepção síncrona. 

------------
Exercício 11
------------

Considerando uma mensagem modelada como :math:`m(t)=rect(\frac{t}{2})`, transmitida com a técnica AM-DSB-SC. Se transmitirmos esse sinal em um canal não linear, definido pela função :math:`y(t)=x(t)^2`, onde :math:`y(t)` representa a saída do canal, e :math:`x(t)` a entrada do canal, esboce qual será o espectro do sinal na entrada do canal, e o espectro do sinal na saída do canal. 
	
Modulação em Frequência
=======================

-----------
Exercício 1
-----------

Considerando um sinal modulado em ângulo, definido pela função

.. math::
	\phi(t)=100cos(2\pi f_c t + 4sen(2000 \pi t)),
	
na qual a frequência da portadora é :math:`f_c=1 \text{MHz}`, determine:

a) A potência média transmitida.
b) O desvio de fase.
c) O desvio de frequência.
d) Se o sinal transmitido é FM ou PM, e discuta.

-----------
Exercício 2
-----------

Para um sinal modulado em ângulo definido por

.. math::
	\phi(t)=cos(\omega_c t + tu(t)),

determine qual é a mensagem se o sinal foi modulado em (a) FM ou (b) PM.

-----------
Exercício 3
-----------

Para a mensagem :math:`m(t)=u(t)-u(t-5)`, encontre qual a frequência angular instantânea, a fase instantânea e esboce os sinais modulados, considerando que a mensagem foi transmitida em (a) PM e (b) FM.

-----------
Exercício 4
-----------

Explique qual a diferença entre o processo de demodulação usando o PLL e utilizando o detector de inclinação.

-----------
Exercício 5
-----------

Quando ao receptor superheteródino:

a) Discuta qual a ideia principal dele, que faz com que ele seja a alternativa comumente utilizada para recepção de sinais AM e FM;

b) Mostre matematicamente como o misturador (mixer) é capaz de transforma um sinal com frequência próxima da frequência sintonizada, :math:`\omega_c`, em um sinal com frequência próxima à frequência intermediária fixa, :math:`\omega_{if}`.

-----------
Exercício 6 
-----------

No Brasil, as estações de rádio FM estão espaçadas em faixas de :math:`200` kHz. Supondo que foi recebido um sinal por um receptor superheteródino FM, apresentado na subfigura (a), e o sinal captado pela antena seja o apresentado na subfigura (b). Com base no sinal recebido, apresente graficamente qual seriam os sinais nas etapas (1), (2), (3) e (4) do processo de demodulação se o filtro passa faixas de sintonia fosse ajustado para :math:`94.9` MHz.

.. figure:: /figures/SinalRecebido.png
	:figwidth: 100%
	:width: 50%
	:align: center
	
	**(a) Sinal Recebido**
	
.. figure:: /figures/SuperHet.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
	**(b) Receptor Superheteródino**

-----------
Exercício 7
-----------

Para a mensagem modulada em ângulo, definida por

.. math::
	m(t)=cos(5000t),

obtenha:

a) Qual seria o sinal modulado em FM;
b) Qual o desvio de frequência, para :math:`k_f=10` kHz;
c) Qual seria uma estimativa da largura de banda do sinal, utilizando a regra de Carson;
d) Quais seriam as componentes do espectro, utilizando a tabela de funções Bessel;

-----------
Exercício 8
-----------

Para um sinal representado pela função :math:`m(t)=\frac{sinc(t)}{\pi}`, transmitido em FM com um :math:`k_f=5`, determine:

a) Qual a largura de banda estimada, utilizando a regra de Carson;
b) Qual a largura de banda estimada, utilizando a função Bessel;
c) Se desejarmos obter um sinal com largura de banda máxima :math:`B=8` rad\s, qual deverá ser o :math:`k_f`?

-----------
Exercício 9
-----------

Discuta sobre a utilizade do filtro de pré-ênfase e de-ênfase.

Exercícios do Livro
===================

Lista de exercícios selecionados do livro "Lathi, B. P., Sistemas de Comunicações Analógicos e Digitais Modernos - 4ª Edição".

3.3-6

3.3-7

3.3-10

3.7-5

4.2-1

4.3-1

4.3-2

4.3-3 

4.3-4

4.3-8

4.4-2

5.1-2

5.2-1

5.2-2

5.2-5

5.4-1

5.4-2