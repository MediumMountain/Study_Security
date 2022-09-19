# HSTS

- HSTSとは、WebサーバがHTTPヘッダの中で指定する項目の一つで、Webブラウザに対して以降は常にHTTPSによる通信を行うよう指示するもの。RFC 6797として標準化されている  

- WebブラウザとWebサーバの通信にはHTTP（Hypertext Transport Protocol）が用いられるが、これをSSL/TLSで丸ごと暗号化したHTTPS（HTTP over SSL/TLS）が用いられることがある。

- Webサーバがブラウザとの初回通信時のHTTPレスポンス（応答）の一部としてヘッダ中で「Strict-Transport-Security」という項目を定義することで、Webブラウザは次回以降の通信で、必ずHTTPSで接続を開始する。

- HSTSが有効なサイトへは、たとえアクセス先として「http://」で始まるURLが指定されたとしても自動的に「https://」に置き換えて通信が行われる。これにより、暗号化されていないHTTP通信に通信経路上で介入する中間者攻撃などを防ぐことができる。

- 書式は「Strict-Transport-Security: max-age=有効期間;includeSubDomains」のようになっており、有効期間は現在を起点とする秒数で指定（0を指定するとHSTSオフ）する。「includeSubDomains」ディレクティブはオプションで、当該ドメインを含むすべてのサブドメインでHSTSを有効することを指示することができる。

# HSTSプリロード
- 米グーグル（Google）社では、HSTSが有効になっている（HTTPではアクセスしない）ドメイン名の一覧をWebブラウザに提供する「HSTSプリロード」（HSTS preload）という仕組みを提供している。

- 通常のHSTSは初回接続時にサーバ側から通知されるため、最初からHTTPSを利用してよいのかどうかをブラウザが知る術がなく、最初に安全でないHTTPでの接続を試みて攻撃を受ける隙が生じる危険がある。

- サーバとブラウザの通信ではこれを解決できないため、同社が運用するデータベースにHSTS適用サイトを登録し、ブラウザがサイトへのアクセス前に問い合わせてHSTSを有効化する仕組みが整えられた。同社のGoogle ChromeをはじめMozilla Firefox、Apple Safari、Microsoft Edgeなど主要なブラウザが対応している。