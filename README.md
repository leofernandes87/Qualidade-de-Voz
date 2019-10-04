# Análise de qualidade de voz em canal AWGN com codificador Reed - Solomon

# Introdução

A seguir é apresentado o resultado de uma série de testes que permitiram análisar a eficácia de diferentes configurações dos códigos de Reed - Solomon, como método de correção de erros em transmissões de voz, em um modelo de canal sem fio.

# Metodologia

Para realização dos testes foi utilizado um simulador implementado em MATLAB quer permite simular a transmissão de uma comunicação de voz, utilizando um modelo de canal AWGN *(Aditive White Gaussian Noise)*.  Foram utilizadas as seguintes técnicas de modulação:
- BPSK - *(Binary Phase Shift Keying)*
- QPSK - *(Quadrature Phase Shift Keying)*
- M - QAM *(Quadrature Amplitude Modulation)*

> Para o QAM foram utilizadas as variações de 16 - QAM, 64 - QAM e 256 - QAM.

Para cada transmissão foi adicionada uma variação da SNR *(Signal to Noise Ratio)* de **0**  a  **30 dB** com medições em intervalos de **1 dB**. Foram utilizadas **4** amostras de áudio, sendo 2 no idioma português e 2 em alemão. Para cada idioma foi utilizado um áudio com locução feminina e outra masculina. Cada amostra possui em média 8 segundos de duração. Os arquivos de áudio foram obtidos na  base de dados da **[ITU-T](https://www.itu.int/net/itu-t/sigdb/menu.aspx)**  (União Internacional de Telecomunicações).

Cada teste foi repetido 2 vezes para cada amostra de áudio. Os valores exibidos indicam a média de todos os testes executados.
Para quantificar o nível da qualidade do sinal de voz recebido foi utilizado o algoritmo definido pela Recomendação da **[ITU - T P.862](https://www.itu.int/rec/T-REC-P.862)**. Além disso foi feito uma análise do BER *(Bit Error Rate)* para comparação.

## Codificação do canal - *(FEC)*

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

# Resultados

Os resultados são exibidos individualmente para cada técnica de modulação.

## BPSK - *(Binary Phase Shift Keying)*

O gráfico apresenta o impacto do uso de diferentes códigos **RS** na qualidade do sinal de voz usando a modulação BPSK:

![BPSK MOS lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_mos_lineplot.svg)

![BPSK BER lineplot](https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/BPSK_ber_lineplot.svg)
