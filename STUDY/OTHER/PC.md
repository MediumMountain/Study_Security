# BIOS 【Basic Input/Output System】
- パソコンなどの主基板（マザーボード）などに格納されたコンピュータプログラム（ファームウェア）の一種
- 起動時のOSの読み込みや、接続された装置・機器に対する基本的な入出力制御などを行うもの。

##
##
##


# UEFI 【Unified Extensible Firmware Interface】 EFI
- コンピュータ内の各装置を制御するファームウェアとオペレーティングシステム（OS）の間の通信仕様を定めた標準規格の一つ。
- 従来のBIOSに代わるもの。UEFI対応ファームウェアを指してUEFIと呼ぶこともある。

    - コンピュータには、本体内部の回路や装置などの基本的な制御を司るファームウェアと呼ばれる機種毎に固有のソフトウェアが内蔵されており、OSはファームウェアに処理を依頼してハードウェアを動作させる。
    - UEFIはOSとファームウェアを連携させるための標準仕様を定めている。
    - 装置を制御するデバイスドライバの開発は各プロセッサ固有の仕様を用いる従来の手法に加え、EBC（EFI Byte Code）と呼ばれる独自に策定されたCPU非依存の中間言語で開発することもできる。
    - ストレージ管理には従来のMBR（Master Boot Record）に代えてGPT（GUID Partition Table）と呼ばれる仕様が導入され、2TB（テラバイト/正確には2TiB）を超える大容量の領域を作成し、OSを導入して起動（ブート）することができる。


    - 一台のコンピュータにOSを複数導入して起動時に選択するブートローダの機能もUEFIブートマネージャとして提供されるようになり、OS側でブートローダを用意する必要がなくなった。
    - OSのデジタル署名を検証して正当なものしか起動しないセキュアブートにも対応し、盗難対策として利用できる。

    - UNIX系OSのシェルのようにファームウェアを操作できるコマンドライン画面としてUEFIシェルが提供され、システム管理のためのコマンドやアプリケーションを実行することができる。
    - ネットワークインターフェース（NIC）を介してLANに接続し、TCP/IPなどで通信することもできる。

    - 従来使われてきたBIOS（Basic Input/Output System）は16ビットマイクロプロセッサの時代に設計されたもので、マルチタスク環境で利用されることを想定していない点や、メインメモリの先頭から640KB目から1MB目のわずか384KBの領域にしか配置できない点など、現在のハードウェアやOSから見ると時代遅れで窮屈な制約が多い。

    - これを克服するため、64ビット環境を想定して新たに設計された近代的で拡張可能なファームウェアのインターフェース仕様としてUEFIの開発が始まった。


## ACPI 【Advanced Configuration and Power Interface】
- ACPIとは、コンピュータの電源管理やハードウェアの構成管理を行うための標準規格の一つ。
- オペレーティングシステム（OS）側から高度な電源制御を行うことができる。

    - マザーボード上の装置の構成をOS側から把握し、設定や制御を行う標準的な仕様を定めている。
    - 特に、ソフトウェアからの電源や省電力モードの制御、機器ごとの細かな動作状態（温度など）の把握や電源や動作モードの制御などを行う電力管理機能のことを指してACPIと呼ぶことが多い。

    - ACPIではシステム全体の稼働状態を「S0」から「S5」までの6段階で定義している。
        - S0は通常の稼働状態
        - S1は通電したまま動作を一時停止するスタンバイ
        - S2はスタンバイとスリープの中間
        - S3はメインメモリ（RAM）以外の電源を落とすスリープ（STR：Suspend To RAM）
        - S4はメモリの内容をストレージに退避して電源を切るハイバネーション（STD：Suspend To Disk）
        - S5は完全な電源断（シャットダウン）状態である。

- ACPIはx86系プロセッサなどを搭載した一般的な仕様のパソコンなどで採用されており、利用するにはコンピュータ本体のBIOSやUEFI、制御される各装置、OSのすべてが対応している必要がある。

    - 最初の規格は1996年に米インテル（Intel）社、米マイクロソフト（Microsoft）社、東芝の三社により策定され、それまでのAPM規格に代わって普及した。
    - 2000年にバージョン2.0、2004年に3.0、2009年に4.0、2011年に5.0と改訂を重ね、2013年には上記三社を含む企業連合からUEFI Forumに移管された。


### APM (Advanced Power Management)
- ACPI以前に普及していた、パソコンの電源の管理・制御に関する標準規格。
- 1992年に米インテル（Intel）社と米マイクロソフト（Microsoft）社が共同で策定した。

    - OSなどのソフトウェアがパソコンの電源機能を操作するための技術標準を定めたもので、ソフトウェア側から電源の切断や、メモリの記憶内容を保持したまま一時停止して電力消費を抑えるサスペンド状態への移行などを実行することができる。

    - これにより、ノートパソコンなどで長時間操作がないときに自動的にサスペンドするといった動作が可能になった。
    - デスクトップ型など据え置き型のパソコンでも、利用者のOS操作で電源を切るといった用途のために用いられた。



# IPL 【Initial Program Loader】 イニシャルプログラムローダ
- コンピュータを起動した時に最初期にメインメモリ（RAM）に読み込まれて実行されるプログラム。以下の二つの異なる意味で用いられることがある。
- 起動時にCPUが一番最初に読み込んで実行するのは、マザーボード上に設けられたROM（読み出し専用メモリ）に記録されたプログラムで、OSなどが記録された起動デバイス（ハードディスクなど）の先頭部分（MBR：Master Boot Record）に記録されたプログラムを読み込んで実行する。これをIPLということがある。

- 一方、このMBRに記録されたプログラムのことをIPLと呼ぶこともある。これは一般にはブートローダ（boot loader）と呼ばれ、起動するOSを利用者に選択させたり、指定されたOSの起動プログラムを読み込んで実行したりする。