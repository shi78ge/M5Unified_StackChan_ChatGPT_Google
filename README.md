# M5Unified_StackChan_ChatGPT_Google

//しげき(shi78ge)追記  
Key-Unit押下でｽﾀｯｸﾁｬﾝに質問ができて、質問したことと回答をOLED-Unitに表示するようにしました。  
体はレゴで作っています。[こちら](https://www.amazon.co.jp/gp/product/B07FNTTF54/ref=ppx_yo_dt_b_search_asin_image?ie=UTF8&psc=1) 
の商品を買えば同じものが組み立てできます。  
  
<img src="https://github.com/shi78ge/M5Unified_StackChan_ChatGPT_Google/assets/67863963/fa0d4497-034b-4b1c-b186-5d45a96968b5" width="300">

<img src="https://github.com/shi78ge/M5Unified_StackChan_ChatGPT_Google/assets/67863963/8b294bea-41da-4585-8aa1-3228334108a1" width="300">

<img src=https://github.com/shi78ge/M5Unified_StackChan_ChatGPT_Google/assets/67863963/7fc69287-52d9-4a33-96cc-47436060ea1d width="300">  


https://github.com/shi78ge/M5Unified_StackChan_ChatGPT_Google/assets/67863963/d34a1814-61ef-4f1c-9162-0ce0432dc4f7  
  
//追記ここまで 
  

Google Cloud Speech to Text を使って音声で会話できるｽﾀｯｸﾁｬﾝです。多言語対応です。

[English](README_en.md)<br>


![画像1](images/image1.png)<br><br>

これは @mongonta555 さんの[ｽﾀｯｸﾁｬﾝ M5GoBottom版組み立てキット](https://raspberrypi.mongonta.com/about-products-stackchan-m5gobottom-version/ "Title")に対応したｽﾀｯｸﾁｬﾝファームです。<br><br>

---

### M5GoBottom版ｽﾀｯｸﾁｬﾝ本体を作るのに必要な物、及び作り方 ###
こちらを参照してください。<br>
* [ｽﾀｯｸﾁｬﾝ M5GoBottom版組み立てキット](https://raspberrypi.mongonta.com/about-products-stackchan-m5gobottom-version/ "Title")<br>

### プログラムをビルドするのに必要な物 ###
* [M5Stack Core2](http://www.m5stack.com/ "Title")<br>
* VSCode<br>
* PlatformIO<br>

使用しているライブラリ等は"platformio.ini"を参照してください。<br>

---

### サーボモーターを使用するGPIO番号の設定 ###
* M5Unified_StackChan_ChatGPT.inoの42行目付近、サーボモーターを使用するGPIO番号を設定してください。


### ChatGPTのAPIキーの取得 ###

ChatGPTのAPIキー取得方法は以下の通りです。(詳細はこのページ一番下のリンクを参照してください。)

* [OpenAIのウェブサイト](https://openai.com/ "Title")にアクセスして、アカウントを作成します。メールアドレスと携帯電話番号が必要です。
* アカウント作成後、APIキーを発行します。APIキーは有料ですが、無料期間やクレジットがあります。<br>

### Google Cloud Speech to Text のAPIキーの取得 ###

Google Cloud Speech to TextのAPIキー取得方法は以下の通りです。(詳細はこのページ一番下のリンクを参照してください。)

* [Google Cloud Platformのウェブサイト](https://cloud.google.com/?hl=ja/ "Title")にアクセスして、アカウントを作成します。メールアドレスと携帯電話番号が必要です。カードの登録が必須ですが、無料トライアルや無料枠があります。
* アカウント作成後、APIキーを取得します。<br>

---

### 使い方 ###
* SDカードのルートに以下の2つのファイルを作成しておくと、使用できるようになります。<br>
【設定が上手くいったらSDカードは必ず抜いておいてください。】<br>

1. wifi.txtファイル：ファイル名は"wifi.txt"で、中身は次の通りです。<br>
YOUR_WIFI_SSID<br>
YOUR_WIFI_PASS<br>

2. apikey.txtファイル：ファイル名は"apikey.txt"で、中身は次の通りです。<br>
YOUR_OPENAI_APIKEY<br>
YOUR_GOOGLE_STT_APIKEY<br>

* もしM5Stackが以前にWifiに接続していた場合、SDカードが必要なく自動的にWifiに接続されます。<br>
この場合、ブラウザで"http://XXX.XXX.XXX.XXX/apikey"にアクセスし、APIキーを設定できます。<br>
(xxxx.xxxx.xxxx.xxxxはAIスタックチャンの起動時に表示されるIPアドレスです。)<br>

* ~ｽﾀｯｸﾁｬﾝの額にタッチすると聞き取りを開始します。~<br>
~聞き取り時間は3秒程度です。~<br>

* ブラウザで"http://xxxx.xxxx.xxxx.xxxx/role"にアクセスすると、ロールを設定できます。<br>
(xxxx.xxxx.xxxx.xxxxはAIスタックチャンの起動時に表示されるIPアドレスです。)<br>
テキストエリアに何も入力せずに送信すると、以前に設定されたロールが削除されます。<br><br>
ロール情報は自動的にspiffsに保存されます。<br>
<br>

* ブラウザで"http://xxxx.xxxx.xxxx.xxxx/role_get"にアクセスすると、現在設定しているロールを取得できます。<br>

* スピーカーの音量を調整できます。<br><br>
例：http://xxxx.xxxx.xxxx.xxxx/setting?volume=180<br>
volumeの値は0～255

* AIスタックチャンの表情を会話内容に合わせて変更できます。<br>
ロール設定で以下の２行をそのまま入力してください。<br><br>
(Happy)のように、必ず括弧で囲んで感情の種類を表し、返答の先頭に付けてください。<br>
感情の種類には、Neutral、Happy、Sleepy、Doubt、Sad、Angryがあります。<br><br>
他にもロールを設定する際は、これらの2行を最後にしてください。<br>
出来ればこの2行のみでやってみてください。<br>
ロールを増やすと失敗しやすくなります。<br>
<br>

* 独り言モードを追加しました。ランダムな時間間隔で、ランダムに喋ります。<br>
感情表現機能と組み合わせると楽しいです。<br>
ボタンAで独り言モードをON/OFFできます。<br>
独り言モードでも従来通りスマホから会話できます。<br>
<br>

* 直近５回分の会話の履歴を保存する機能があります。<br>

* 音声認識プログラムは別途ユーザーが用意する必要があります。<br>
音声認識プログラムからこのようにhttpコマンドでテキスト(UTF-8)を渡します。<br>
(テキストはURLエンコードして渡してください。)<br><br>
http://XXX.XXX.XXX.XXX/chat?text=こんにちは<br><br>
XXX.XXX.XXX.XXXの部分は起動時に表示されるM5StackのIPアドレスに置き換えてください。<br><br>
* 上記と同様にしてブラウザを使ってアクセスすることも出来ます。<br><br>
![画像2](images/image2.png)<br>

* 私は音声認識にiPhoneのショートカット機能を使っています。<br>
このように簡単に音声認識が使えます。<br><br>
![画像3](images/image3.png)<br>

* M5Stack Core2の画面中央付近にタッチするとｽﾀｯｸﾁｬﾝの首振りを止められます。<br>

* M5Stack Core2のボタンCを押すと、音声合成のテストが出来ます。<br>

---

### 使用する言語の設定方法 ###

次の２つの設定をします。<br><br>

1. ChatGPTの設定をする<br><br>
言語を英語に設定する例：ブラウザで "http://xxxx.xxxx.xxxx.xxxx/role" にアクセスして、以下のようにロールを設定します。<br><br>
![画像4](images/image4.png)<br><br>

2. TTSの言語設定をする<br><br>
言語を英語に設定する例：ブラウザで以下のように設定します。<br><br> http://xxxx.xxxx.xxxx.xxxx/setting?lang=en-US<br><br>en-US が英語の場合の言語コードです。その他の言語コードは下記リンクを参照してください。<br><br>

* [Cloud Speech-to-Text 言語サポート](https://cloud.google.com/speech-to-text/docs/languages?hl=ja/ "Title")<br><br>

---

### ChatGPTのAPIキー取得の参考リンク ###

* [ChatGPT API利用方法の簡単解説](https://qiita.com/mikito/items/b69f38c54b362c20e9e6/ "Title")<br>

### Google Cloud Speech to TextのAPIキー取得の参考リンク ###

* [Speech-to-Text APIキーの取得／登録方法について](https://nicecamera.kidsplates.jp/help/feature/transcription/apikey/ "Title")<br>

### ChatGPTのキャラクター設定の参考リンク ###

* [ChatGPTのAPIでキャラクター設定を試してみた](https://note.com/it_navi/n/nf5f702b36a75#8e42f887-fb07-4367-9f3f-ab7f119eb064/ "Title")<br>
<br><br>

