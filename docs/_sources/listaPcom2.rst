=====================
Lista de Exercícios 2
=====================

Compilado de exercícios sugeridos para auxiliar o estudo na disciplina Princípios de Comunicação. 

Exercícios do Livro
===================

Lista de exercícios selecionados do livro "Lathi, B. P., Sistemas de Comunicações Analógicos e Digitais Modernos - 4ª Edição".


6.1-1

6.2-1

6.2-3

7.2-1

7.2-2 a)

7.2-3

7.3-4

8.1-7

8.1-9

9.1-1

9.1-2

9.1-3

9.1-4

9.1-5




Modulação por Pulsos
====================

-----------
Exercício 1
-----------

Para as mensagens a seguir, determine: qual a frequência de amostragem que respeita o critério de Nyquist; obtenha a sequência de valores amostrados, considerando que o sinal foi amostrado com a frequência de Nyquist; e determine qual o formato do sinal se considerarmos que a mensagem foi transmitida em PAM, PWM e PPM.

a) :math:`cos(t)`

b) :math:`sinc(2\pi t)`

-----------
Exercício 2
-----------

Para as mensagens amostradas no exercício 1, realize o processo de quantização considerando que o sistema de transmissão considere mensagens com 4 e 8 bits.

Modulação Digital
=================

-----------
Exercício 1
-----------

O processo de transmissão de um sinal digital é composto por várias etapas, resposnáveis por transformar o sinal. Dentre as principais etapas, destaca-se as codificações de fonte e linha, modulação com portadora, multiplexação e repetição. Desenhe o diagrama de blocos que representa todo o processo de transmissão digital e explique sucintamente a função de cada uma dessas etapas.

-----------
Exercício 2
-----------

Um aluno da disciplina de Princípios de Comunicação está interassado em tentar captar sinais provenientes do espaço. Para isso, hipotéticamente, o aluno direcionou uma antena para a posição estimada do Planeta X, na esperança de captar uma mensagem "alienígena". Misteriosamente, após uma série de processamentos e filtragens, o aluno conseguiu detectar uma sequência de pulsos que aparentam ser digitais. Essa sequência de pulsos é a seguinte:

.. figure:: /figures/ExPulsos.png
	:figwidth: 100%
	:width: 60%
	:align: center

Para tentar decodificar qual a informação desses pulsos, o aluno lembrou que na disciplina foram estudados alguns tipos de codificações de linha, como a unipolar, polar, bipolar e Manchester, com formatos que podem ter retorno ao zero ou não. Dessa forma, se você for esse aluno, determine qual seriam as possíveis codificações que seriam possíveis de gerar o sinal recebido, e qual seria a mensagem em cada caso.

-----------
Exercício 3
-----------

Considerando uma sequência de bits definida por 01001 codificada utilizando a codificação Manchester. Caso esse sinal seja transmitido com um portadora, desenhe a forma de onda resultante para ASK, PSK e FSK.

Processos Aleatórios
====================

-----------
Exercício 1
-----------

Para um processo aleatório definido por :math:`X(t)=kt`, em que k é uma variável uniformemente distribuída no intervalo [-1,1]

a) Esboce as funções amostras (realizações) do processo;

b) Determine o valor esperado, E[X(t)];

c) Determine a autocorrelação de X(t);

d) Discuta se o processo é estacionário e se é ergódico;

e) Determine a potência :math:`P_x = E[X(t)^2]`;

Desempenho de Sistemas de Comunicação
=====================================

-----------
Exercício 1
-----------

Considerando uma mensagem, modulada em AM-DSC, definida como :math:`m(t)=A_m cos(2\pi f_m t)`, determine qual seria:

a) A SNR do canal quando o fator de modulação é :math:`\mu=1`;

b) A SNR do demodulador por deteção de envoltória;

c) A figura de mérito para o caso AM-DSB com detector de envoltória;

d) A figura de mérito caso a detecção fosse síncrona.

-----------
Exercício 2
-----------