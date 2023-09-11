=====================
Lista de Exercícios 1
=====================

Compilado de exercícios sugeridos para auxiliar o estudo na disciplina Princípios de Comunicação. 

Exercícios do Livro
===================

Lista de exercícios selecionados do livro "Lathi, B. P., Sistemas de Comunicações Analógicos e Digitais Modernos - 4ª Edição".

3.3-6

3.3-7

3.3-10

3.7-5

4.3-1

4.3-2

4.3-3 

4.3-4

4.4-2

4.5-1

5.2-1

5.2-2

5.4-1

5.4-2


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

Para o sinal modulado em amplitude, descrito por :math:`\phi(t)=cos(5t)cos(100t)`, desenhe o diagrama de blocos do processo de demodulação síncrona, determinando os sinais envolvidos. Esboce o espectro de frequência dos sinais envolvidos nesse processo de demodulação, e discuta qual interpretação desse processo de demodulação no domínio da frequência.


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