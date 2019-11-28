![GitHub last commit](https://img.shields.io/github/last-commit/leofernandes87/Qualidade-de-voz)

# Voice Quality Analysis with Reed - Solomon Encoder in AWGN Channel

The following is the result of a series of tests that allowed us to analyze the effectiveness of different Reed - Solomon code configurations as a method for error correction in voice transmissions in a wireless channel model.

**Read this in other language:**

<p float="left">
  <a href="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/README.md">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/Pt-Br_badge.svg" width="80"></a>
  <a href="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/README.en.md">
  <img src="https://github.com/leofernandes87/Qualidade-de-Voz/blob/master/Imagens/En_badge.svg" width="68"></a>
</p>

## Overview

One of the most widely used services today is Voice over IP (VoIP), which allows voice data to be transmitted over the network using Internet protocols. This service has become a good alternative to the traditional analog telephony service as it has a relatively lower call cost.

However, the voice transmission service, as well as other forms of internet media distribution, such as streaming, are considerably sensitive to high delay rates or packet losses. Therefore, such applications require special mechanisms capable of maintaining their integrity without the need for retransmission.

Wireless channels are much more susceptible to errors than wired networks. In packet-based transmissions, depending on the quality of the channel, a packet may get lost during transmission or get corrupted at the receiver. To minimize transmission degradation, different techniques are implemented in the communication system. One of the most relevant techniques is channel coding or Forward Error Correction (FEC), which inserts redundant bits into each block of transmitted content data to detect and correct bit errors. This technique helps to improve speech quality in communication services. On the other hand, the addition of redundant bits can considerably increase channel bandwidth requirements. In addition, the efficiency of a patch code is directly related to channel conditions.
