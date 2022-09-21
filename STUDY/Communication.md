# EAP 【Extensible Authentication Protocol】 PPP EAP
- 二地点間の接続の確立に用いられるPPP（Point-to-Point Protocol）の拡張仕様で、様々な認証方式を利用する手順を定めたもの。
- LAN上で認証を行う方式を定めたIEEE 802.1Xにも標準の認証手順として採用された。

![](../PICTURE/Communication/EAP.png)

# PPP 【Point-to-Point Protocol】
- 標準的な通信プロトコルの一つで、二台の機器の間で仮想的な専用の伝送路を確立し、相互に安定的にデータの送受信を行うことができるようにするもの。
- 1992年に最初の仕様が策定されたが、1994年にRFC 1661として標準化された仕様が広く普及している。
- OSI参照モデルではデータリンク層（第2層）にあたる。
- 電話回線で発呼や着信ができるようにした方式を「ダイヤルアップPPP」と呼び、1990年代に家庭などからインターネットサービスプロバイダ（ISP）に接続する手段として標準的に使われた。
- 近年主流となったADSLや光ファイバーによるデータ通信専用回線による接続では、EthernetやATMなどの上位層で2地点間の接続を確立するのにも使われ、それぞれ「PPP over Ethernet」（PPPoE）「PPP over ATM」（PPPoA）などと呼ばれる。

# ADSL


# PPPoE「PPP over Ethernet」
# PPPoA「PPP over ATM」

# SLIP (Serial Line Internet Protocol)