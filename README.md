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
