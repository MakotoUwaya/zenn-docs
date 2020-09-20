---
title: "steamでゲームパッドを使えるようにする"
emoji: "🎮"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["steam"]
published: true
---

# この記事でわかること

* steam でコントローラー設定がうまくできないときの確認ポイント

# 筆者の状況

* はじめて steam でゲームを購入
* キーボードでも十分遊べるけど、ゲームパッドでやってみたい
    * 10年以上前に購入したPS2コントローラーをUSB変換して使える[BUFFALO BSGC201](https://www.buffalo.jp/product/detail/manual/bsgc201.html#tab-link)を利用
    * 余談だがBUFFALOは古い製品の情報をしっかり残してくれてるので助かる
* ん？ゲームでコントローラーが認識されてないぞ？
* そもそもコントローラーってどこで設定するんだっけ

# 確認ポイント

## コントローラーのドライバーインストール

* OS が Windows 10 なら、ほとんどのデバイスは個別にドライバーをインストールしなくても動作する
* しかし、ドライバーをインストールしないと **一部の機能** が動作しないことがある
    * 私の環境ではアナログスティックの操作が反応しなくなっていた
* BUFFALOの[商品情報サイト](https://www.buffalo.jp/product/detail/software/bsgc201.html#tab-link)からドライバーをダウンロードしてインストール
    * ドライバーは 32bit と 64bit 版で分かれているので、自分の環境に合わせて選ぶ
* もし以前にインストールしていたとしても、最新版のドライバーをインストールすることで不具合が改善するケースもある
    * デバイスマネージャーで見てインストール済かどうか確認しても良いが、問答無用で再インストールの方が早いかも

## Steam でコントローラー設定をする

* コントローラーを正しく認識できるようになったら、 Steam で使えるように設定していく
* 起動中のゲームはすべて終了する
* Steam のメイン画面を開き、Settings を開く
![](https://storage.googleapis.com/zenn-user-upload/q5279pwm5flo7vhg4aato9013frd)
![](https://storage.googleapis.com/zenn-user-upload/xw74me4cfmb0w2ea9v6qzzothxkq)
* 自分のコントローラー種別に合う設定ヘルパーをチェックする
    * BSGC201の場合はPlayStationベースではあるが、1P/2Pを1つのUSBで入力する作りなので特殊
    * そのためより汎用的な Generic を選択した
![](https://storage.googleapis.com/zenn-user-upload/0zf1noler1z1uygt9iu6jbf41jkt)
* 接続しているコントローラーが表示されていることを確認
    * 表示されていなければ、接続ケーブルを抜き差しする
    * 抜き差しでも認識されないならPCを再起動
    * 再起動しても認識されなかったら他の原因を疑う(物理的故障、断線、USBコネクタ接触不良、などなど)
![](https://storage.googleapis.com/zenn-user-upload/uwa2wqgptam1vzmklj9swpusu0hi)
* コントローラーのボタンをマッピングしていく
![](https://storage.googleapis.com/zenn-user-upload/d9e8s6ivtcx39q0wuamr7mx8sddm)
* 設定に名前を付けて保存
![](https://storage.googleapis.com/zenn-user-upload/lzibwvdk9q2uqtqj9zvwx2thldpw)

## Steam のコントローラー設定を初期化する

* ドライバーインストール前に Steam で設定をしていると、ドライバーインストール後も誤った状態で設定が保持される
* 一方、Steamの画面からはコントローラー設定を初期化することができない
* 他に良い方法があるかも知れないが、直接設定ファイルを編集する危険な方法を記載する
    * 実行は自己責任で
    * 作業前にかならずファイルをバックアップすること
* Steamが起動していたら削除
    * 常駐起動しているので、タスクバーから右クリックで終了する
* `{Steamのインストールディレクトリ}\config\config.vdf` というファイルを編集する
* controller 関連は以下の4行なので、まるっと削除
![](https://storage.googleapis.com/zenn-user-upload/xtd0xuxf3o6j69s3a61z996icmm3)
* Steam を起動する
* Steam でコントローラー設定をする手順に戻る

## ゲーム毎に設定をする

* 今回は [FALL GUYS](https://ja.wikipedia.org/wiki/%E3%83%95%E3%82%A9%E3%83%BC%E3%83%AB%E3%82%AC%E3%82%A4%E3%82%BA_%E3%82%A2%E3%83%AB%E3%83%86%E3%82%A3%E3%83%A1%E3%83%83%E3%83%88_%E3%83%8E%E3%83%83%E3%82%AF%E3%82%A2%E3%82%A6%E3%83%88) を例とする
* ゲーム起動画面を表示して、コントローラー設定をする
![](https://storage.googleapis.com/zenn-user-upload/cw6apmdqc7ykbstfip05lxxyidvc)
* Controller setting を開くと、認識されているコントローラーの情報が表示される
    * この画面でゲーム毎のコントローラー微調整ができるようになっている
    * この記事では割愛する
![](https://storage.googleapis.com/zenn-user-upload/gnhczcowa2wb0wbbhggbseaorm07)
* 情報が表示できれば問題はないので、特に何も変更せず設定画面を閉じる
* ゲームを起動する
* この時点で FALL GUYS のメニューがコントローラーで操作可能になっているはず
    * 操作できなければコントローラーの設定を初期化してやり直す
![](https://storage.googleapis.com/zenn-user-upload/ppfyllf18t7quo83tga58t2pnp19)
* FALL GUYS のコントローラー設定画面を開く
![](https://storage.googleapis.com/zenn-user-upload/72d7yb3t60ygwix1z5syp2zulwp7)
* デフォルトのボタンバインドが設定されていることを確認する
    * もし設定されていなければ個別に設定していく
![](https://storage.googleapis.com/zenn-user-upload/g1q4b5lc7ft563womvrgp8dmdw45)
* ゲームを遊んでみて、設定通りに動作することを確認する
* お疲れ様でした

# まとめ

* ゲームコントローラーのドライバーは最新版をインストール
    * BUFFALOさん古い製品のドライバー提供ありがとう
* Steamのコントローラー認識がおかしいときは設定を初期化
* ゲーム側でもコントローラーの個別設定があるので確認
