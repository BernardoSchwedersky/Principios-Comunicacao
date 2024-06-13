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

Modulação em Amplitude
======================

-----------
Exercício 1
-----------

Considerando que se deseja transmitir 3 mensagens compartilhando o mesmo canal. Para tal, será utilizada a modulação utilizando portadoras senoidais, de forma a multiplexar as mensagens na frequência. O espectro em frequência desses sinais é apresentado na figura a seguir.

.. figure:: /figures/EXPcom1.png
	:figwidth: 100%
	:width: 70%
	:align: center
	
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

Modulação em Frequência
=======================

-----------
Exercício 1
-----------

Considerando um sinal modulado em ângulo, definido pela função

.. math::
	\phi(t)=100cos(2\pi f_c t + 4sen(2000 \pi t)),
	
na qual a frequência da portadora é :math:`f_c=1 \text{MHz}` , determine:

a) A potência média transmitida.
b) O desvio de fase.
c) O desvio de frequência.
d) Se o sinal transmitido é FM ou PM, e discuta.

Continua ...

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

5.2-1

5.2-2

5.4-1

5.4-2