![GitHub last commit](https://img.shields.io/github/last-commit/leofernandes87/Qualidade-de-voz)

# Análise de qualidade de voz em canal AWGN com codificador Reed - Solomon

A seguir é apresentado o resultado de uma série de testes que permitiram análisar a eficácia de diferentes configurações dos códigos de Reed - Solomon, como método de correção de erros em transmissões de voz, em um modelo de canal sem fio.

**Read this in other language:**

<p float="left">
  <a href="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/README.md">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/Pt-Br_badge.svg" width="80"></a>
  <a href="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/README.en.md">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/En_badge.svg" width="68"></a>
</p>


## Índice

- [Overview](#Overview)
- [Cenário de simulação](#Cenário-de-simulação)
    - [Codificação do canal](#Codificação-do-canal)
- [Resultados](#Resultados)
- [Algoritmo Reed - Solomon adaptativo](#Algoritmo-Reed---Solomon-adaptativo)

## Overview

Um dos serviços mais utilizados atualmente é o serviço de voz sobre IP (VoIP), que permite que dados de voz sejam transmitidos pela rede utilizando protocolos de Internet. Este serviço se tornou uma boa alternativa ao tradicional serviço de telefonia analógica, pois tem um custo de ligação relativamente mais baixo.

Porém o serviço de transmissão de voz, bem como outras formas de distribuição de mídias pela internet, como é o caso do streaming, são consideravelmente sensíveis a taxas elevadas de atraso ou perdas de pacote. Por isso tais aplicações necessitam de mecanismos especiais que sejam capazes de manter sua integridade sem a necessidade de retransmissão.

Canais sem fio são muito mais suscetíveis a erros que redes cabeadas. Em transmissões baseadas em pacotes, dependendo da qualidade do canal, um pacote pode se perder durante a transmissão, ou chegar corrompido ao receptor. Para minimizar as degradações de transmissão, diferentes técnicas são implementadas no sistema de comunicação. Uma das técnicas mais relevantes é a codificação do canal ou Forward Error Correction (FEC), que insere bits redundantes em cada bloco de dados do conteúdo transmitido para detectar e corrigir erros de bit. Esta técnica ajuda a melhorar a qualidade da fala nos serviços de comunicação. Por outro lado a adição de bits redundantes pode aumentar consideravelmente os requisitos de largura de banda do canal. Além disso, a eficiência de um código de correção está diretamente relacionado às condições do canal.
      
## Cenário de simulação

Para realização dos testes foi utilizado um simulador implementado em MATLAB quer permite simular a transmissão de uma comunicação de voz, utilizando um modelo de canal AWGN *(Aditive White Gaussian Noise)*.  Foram utilizadas as seguintes técnicas de modulação:
- BPSK - *(Binary Phase Shift Keying)*
- QPSK - *(Quadrature Phase Shift Keying)*
- M - QAM *(Quadrature Amplitude Modulation)*

> Para o QAM foram utilizadas as variações de 16 - QAM, 64 - QAM e 256 - QAM.

<p align="center">
  <strong>Codificador e decodificador de canal em um sistema de comunicação</strong>
</p>

<p align="center">
  <img width="800" height="400" src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/modelo_transmissao.svg">
</p>

<p align="center">
  Fonte: Adaptado de M. Viswanathan, “Wireless communication systems in matlab,”2013
</p>



Para cada transmissão foi adicionada uma variação da SNR *(Signal to Noise Ratio)* de **0**  a  **30 dB** com medições em intervalos de **1 dB**. Foram utilizadas **4** amostras de áudio, sendo 2 no idioma português e 2 em alemão. Para cada idioma foi utilizado um áudio com locução feminina e outra masculina. Cada amostra possui em média 8 segundos de duração. Os arquivos de áudio foram obtidos na  base de dados da **[ITU-T](https://www.itu.int/net/itu-t/sigdb/menu.aspx)**  (União Internacional de Telecomunicações).

Cada teste foi repetido 2 vezes para cada amostra de áudio. Os valores exibidos indicam a média de todos os testes executados.
Para quantificar o nível da qualidade do sinal de voz recebido foi utilizado o algoritmo definido pela Recomendação da **[ITU - T P.862](https://www.itu.int/rec/T-REC-P.862)**. Além disso foi feito uma análise do BER *(Bit Error Rate)* para comparação.

## Codificação do canal

Foram definidos **8** configurações <math>(n, k)<math> de códificação baseados nos códigos de Reed - Solomon com diferentes **taxas de código** *(code rate)*. A seguir é apresentado uma tabela que mostra os códigos **RS** utilizados com sua respectiva taxa de código:

|Código *(n, k)*          |Taxa de código *(code rate)*
|-------------------------|-----------------------------|
|	(255, 247)              |0.968                        |
|	(255, 225)              |0.882                        |  
|	(240, 200)              |0.833                        |  
|	(255, 205)              |0.803                        |  
|	(360, 280)              |0.777                        |  
|	(255, 185)              |0.725                        |  
|	(255, 165)              |0.647                        |    
|	(400, 240)              |0.600                        |   

> **Nota:**  a taxa de código de um código **FEC** é a proporção do fluxo de dados que é útil (não redundante). Em um código *n, k* a taxa de código é equivalente a *k/n*. Para cada *k* bits de informação útil, o codificador gera um total de *n* bits de dados, dos quais *n - k* são redundante

## Resultados

Os resultados são exibidos individualmente para cada técnica de modulação. 
- o primeiro gráfico apresenta o impacto do uso de diferentes códigos **RS** na qualidade do sinal de voz considerando a avaliação do MOS determinado pelo algoritmo **ITU - T P.862**
- o segundo  gráfico apresenta uma avaliação baseada na taxa de erros de *bit* utilizando os mesmos códigos **RS**.

> **Nota:** os gráficos exibem apenas o intervalo considerado mais relevante para análise dos resultados.

## BPSK - *(Binary Phase Shift Keying)*

![BPSK MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_mos_lineplot.svg)

![BPSK BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_ber_lineplot.svg)

## QPSK - *(Quadrature Phase Shift Keying)*

![QPSK MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/QPSK_mos_lineplot.svg)

![QPSK BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/QPSK_ber_lineplot.svg)

## 16 - QAM *(Quadrature Amplitude Modulation)*

![16QAM MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/16%20-%20QAM_mos_lineplot.svg)

![16QAM BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/16%20-%20QAM_ber_lineplot.svg)


## 64 - QAM *(Quadrature Amplitude Modulation)*

![64QAM MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/64%20-%20QAM_mos_lineplot.svg)

![64QAM BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/64%20-%20QAM_ber_lineplot.svg)

## 256 - QAM *(Quadrature Amplitude Modulation)*

![256QAM MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/256%20-%20QAM_mos_lineplot.svg)

![256QAM BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/256%20-%20QAM_ber_lineplot.svg)

## Algoritmo Reed - Solomon adaptativo

<p align="left">
O seguinte gráfico exibe a variação dos valores de SNR em razão de um intervalo de tempo.
Os valores de SNR foram gerados de forma aleatória, com uma distribuição uniforme, entre os valores de 2 a 14 dB considerando        uma transmissão utilizando a modulação <strong>BPSK</strong>. 
</p>

<p align="left">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/snr_variation.svg">
</p>

<p align="left">
Os seguintes gráficos demostram a avaliação da qualidade de voz dentro do intervalo do intervalo de tempo exibido acima.
No primeiro caso a avaliação e feita <strong>sem codificação do canal</strong>, no segundo caso a avaliação é feita utilizando o código <strong>RS (255, 247)</strong> e no último caso a avaliação é feita mediante uso da <strong>codificação adaptativa</strong> onde o melhor código RS é escolhido de acordo com a situação do canal no momento da transmissão.
<p>
  
<p align="left">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_snr_variation_nocode.svg">
</p>

<p align="left">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_snr_variation_RS(255-247).svg">
</p>

<p align="left">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK%20RS_adaptative.svg">
</p>

> **Nota:** Os arquivos originais gerados pelo simulador, bem como o *[script](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Resultados/script.ipynb)* usado para gerar os gráficos automaticamente se encontram na pasta **[Resultados](https://github.com/leofernandes87/Qualidade-de-Voz/tree/master/Resultados)**
