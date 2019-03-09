# GameControllerizerハッカソン ソースコード

## 全体的な仕様
スマホ経由で送信されたセンサー情報を、bottleを使ってポート8080番で受け取り、リクエストされたURLによってOSにキーイベントを送信します
```bash
python3 main.py
```
でプログラムを実行できます
Windows特有のライブラリを使用しているため、他のプラットフォームでは動作しません。

## ファイル構成
 - main.py
   - メインスクリプトです
 - lib.py
   - OSにキーイベントを送信するための自作ライブラリです
 - keys.py
   - lib.pyでキーイベント送信に使うキー番号を定義しています
 - jump.py
   - 高くジャンプするには、一定時間キーを押し続ける必要があります
     ですが、`time.sleep()`してしまうと、その間リクエストを処理できなくなります
     なので、ジャンプするときバックグラウンドでこのファイルを実行します