---
id: dist
{{if .Meta.Status}}status: {{.Meta.Status}}{{end}}
{{if .Meta.Summary}}summary: {{.Meta.Summary}}{{end}}
{{if .Meta.Author}}author: {{.Meta.Author}}{{end}}
{{if .Meta.Categories}}categories: {{commaSep .Meta.Categories}}{{end}}
{{if .Meta.Tags}}tags: {{commaSep .Meta.Tags}}{{end}}
{{if .Meta.Feedback}}feedback link: {{.Meta.Feedback}}{{end}}
{{if .Meta.GA}}analytics account: {{.Meta.GA}}{{end}}

---

# AppSheetハンズオン【基礎編】
## データベースを作成しよう！
### 1-1. 新規スプレッドシートを作成する
下記URLをクリックして新規スプレッドシートを作成しましょう。このスプレッドシートに登録する書籍データベースを作成します。

[https://sheets.google.com/create](https://sheets.google.com/create)

ファイル名は `bookdata` としました。ヘッダーをそれぞれ登録します。ヘッダーの文字は太字にするとAppSheet側で認識されやすくなります。

* ISBNコード
* タイトル
* 保有チェック
* メモ
* 画像
* 作成日時
* 更新日時

Positive
: ISBN（アイエスビーエヌ）は、International Standard Book Number の略称。図書（書籍）および資料の識別用に設けられた国際規格コード（番号システム）の一種

![s100](images/s100.png)

### 1-2. 計算用スプレッドシートを作成する
Step3で使用するためのスプレッドシートを作成します。新規スプレッドシートを作成してください。

[https://sheets.google.com/create](https://sheets.google.com/create)

ファイル名は `Form` としました。ヘッダーをそれぞれ登録してください。

|ヘッダー名| 値|
|:--|:--|
|Key|1|
|Choice|持っている|

![s101](images/s101.png)

## AppSheetの設定をしよう！
### 2-1. AppSheetにサインアップする
AppSheetを設定します。下記URLにアクセスしてください。

[https://www.appsheet.com/](https://www.appsheet.com/)


すでにアカウントをお持ちの方はログインしておいてください。始めてAppSheetにアクセスされる方は、画面右上や画面中央にある `Start for free` ボタンをクリックします。

![s200](images/s200.png)

連携するデータベースを選択します。 `Google Sheets and Forms` をクリックしてください。

![s201](images/s201.png)

お持ちのGoogleアカウントでログインして［許可］ボタンをクリックします。

![s202](images/s202.png)

### 2-2. 新規アプリを作成する

`Make a new app` をクリックします。

![s203](images/s203.png)

`Start with your own data` をクリックします。

![s204](images/s204.png)

アプリ名を入力します。 `BookDatabase` としました。カテゴリは `Other` を選択します。 `Next step: Choose your data` ボタンをクリックしてください。

Negative
: アプリ名は日本語が使えないので注意してください。

![s205](images/s205.png)

スプレッドシートファイルを選択します。Step.1で作成した `bookdata` ファイルを選択して `Select` ボタンをクリックしてください。

![s206](images/s206.png)

これでAppSheetの画面が表示されます。

![s207](images/s207.png)

### 2-3. UXの設定をする
画面の見た目の設定を行います。左側メニューにある `UX` をクリックして、［シート1］をクリックしてください。

![s208](images/s208.png)

「シート1」という名前だとわかりにくいので、View nameを `BookListView` に変更してください。

![s209](images/s209.png)

下にスクロールして、VIEW OPTIONS項目にある `Primary header` は「タイトル」を、 `Secondary header` は「保有チェック」をそれぞれ選択します。これは見た目の問題なので、お好きな項目を選択して構いません。ISBNコードの方がわかりやすいという方はそちらを選択しても問題ありません。

![s210](images/s210.png)

下にスクロールして DISPLAY項目にある `Display name` を「書籍リスト」と名前を編集してください。

![s211](images/s211.png)


右上の `SAVE` ボタンをクリックすると、右側にあるアプリプレビュー画面のタブ部分が「BookListView」から「書籍リスト」と名前が変わります。

![s212](images/s212.png)

`Brand` タブをクリックして、一番下にある `HEADER & FOOTER` カテゴリにある `Show view name in header` を「ON」に切り替えてください。これで、アプリのヘッダーに先程設定した「書籍リスト」と表示されるようになります。

![s213](images/s213.png)

### 2-4. ローカライズを設定する
アプリのローカライズも簡単に設定することができます。今回のアプリで使う言葉だけをローカライズしてみましょう。

|項目|値|
|:--|:--|
|Save|保存する|
|Cancel|キャンセル|
|Select photo source|カメラロール|
|Take a Photo| 写真を撮る|
|Choose from Existing|カメラロール|

![s214](images/s214.png)

### 2-5. データベースを設定する
左側メニューにある「Data」をクリックして、「シート1」をクリックします。Table nameを 「Data」という名前に変更します。変更したら右上の `SAVE` ボタンをクリックします。

![s215](images/s215.png)

`Columns` タブをクリックしてデータの中身を設定します。設定するデータがどういう形式なのかを設定することができます。

|項目|値|
|:--|:--|
|ISBNコード|Text|
|保有チェック|Enum|
|画像|Image|
|作成日時|DateTime|
|更新日時|DateTime|

![s216](images/s216.png)

さらにそれぞれの項目に詳細設定を行います。まずは「ISBNコード」の左側にある編集ボタンをクリックします。 `OTHER PROPERTIES` 項目にある、 `Scannable` を有効化にしてください。これを有効化するとQRコードやバーコードの読み取りをすることができるようになります。

![s217](images/s217.png)

続いて「保有チェック」の設定を行います。編集ボタンをクリックします。 `TYPE DETAILES` 項目にある `Values` に「持っていない」「持っている」をそれぞれ追加してください。

![s218](images/s218.png)

作成日時と更新日時をそれぞれ編集します。 `AUTO COMPUTE` 項目にある `Initial value` をクリックしてください。

![s219](images/s219.png)

AppSheetで使える関数を設定することができます。 `NOW()` と入力すると、現在日時を取得することができます。設定したら右下にある［Save］ボタンをクリックします。

```
NOW()
```

![s220](images/s220.png)

更新日時は別途更新したときに日付を変更してほしいので、専用の設定を行います。 `UPDATE BEHAVIOR` 項目にある `Reset on edit?` を有効化してください。これで編集し終わったときにだけNOW()関数が実行されて、更新日時として日時が更新されるようになります。

![s221](images/s221.png)

### 2-6. 動作確認
それでは動作確認してみましょう。右側のプレビュー画面にある［＋］ボタンをクリックして書籍を新規登録してみましょう。Webシミュレーターではバーコードの読み取りができないので、スマホで確認してください。

![s222](images/s222.png)

### 2-7. アプリから動作確認
iPhoneの方はAppStore、Androidの方はPlayストアからそれぞれ「AppSheet」アプリをインストールしてください。お使いのGoogleアカウントでログインすると作成したアプリが表示されます。

[![s223](images/s223.png)](https://apps.apple.com/jp/app/appsheet/id732548900?mt=8)

■iPhoneの方  
[https://apps.apple.com/jp/app/appsheet/id732548900?mt=8](https://apps.apple.com/jp/app/appsheet/id732548900?mt=8)


[![s224](images/s224.png)](https://play.google.com/store/apps/details?id=x1Trackmaster.x1Trackmaster&hl=ja)

■Androidの方  
[https://play.google.com/store/apps/details?id=x1Trackmaster.x1Trackmaster&hl=ja](https://play.google.com/store/apps/details?id=x1Trackmaster.x1Trackmaster&hl=ja)

## AppSheet用関数を使ってみよう！
エクセルで言う関数をAppSheetで使うことができます。複雑な計算や文字列操作といった処理を行うことができます。

### 3-1. テーブルを追加する
Tablesタブをクリックして `+ Add New Table` をクリックします。

![s300](images/s300.png)

`Google` をクリックします。

![s301](images/s301.png)

Step1で作成した `Form` スプレッドシートファイルを選択して `Select` ボタンをクリックします。

![s302](images/s302.png)

このテーブルは特にデータベース自体を編集することはないので、 `Read-Only` を選択して `Add This Table` ボタンをクリックします。

![s303](images/s303.png)

テーブル名を `Form` に変更します。

![s304](images/s304.png)

### 3-2. 関数を設定する

`Columns` タブをクリックして `Add Virtual Column` ボタンをクリックします。計算用の仮想列を追加します。

![s305](images/s305.png)

下記のように設定します。設定したら右上にある `Done` ボタンをクリックします。これで「保有チェック」で「持っている」と設定しているものだけをリストでピックアップします。

|項目|値|
|:--|:--|
|Column name| Select |
|App formula | SELECT(Data[保有チェック], [保有チェック] = 持っている) |

![s306](images/s306.png)

続いて他にも列を追加します。下記を追加してください。

|項目|値|
|:--|:--|
|Column name| AllData |
|App formula | SELECT(Data[保有チェック], true) |

![s307](images/s307.png)

画面のように設定されていれば問題ありません。一度右上の `SAVE` ボタンをクリックします。

![s308](images/s308.png)

続いて仮想列を2つ追加します。下記を追加してください。追加したら再度 `SAVE` ボタンをクリックします。SELECTで抽出した条件のリストを `COUNT` 関数でいくつあるか数えています。

|項目|値|
|:--|:--|
|Column name| SelectCount |
|App formula | COUNT([Select]) |

|項目|値|
|:--|:--|
|Column name| SelectAllCount |
|App formula | COUNT([AllData]) |

![s309](images/s309.png)

最後に下記の仮想列を追加して、 `SAVE` ボタンをクリックします。 `CONCATENATE` で文字列を操作することができます。

|項目|値|
|:--|:--|
|Column name| 持っている数／登録数 |
|App formula | CONCATENATE([SelectCount], "／", [SelectAllCount], "冊") |

![s310](images/s310.png)

### 3-3. Viewをメニューに追加する
これまで設定したForm情報をメニュー画面に設置して、メニュー画面から表示します。 左側メニューにある `UX` をクリックして、 `+ Add New View` をクリックします。

![s311](images/s311.png)

Viewの設定を行います。下記のように設定してください。

|項目|値|
|:--|:--|
|View name|所持数|
|For this data | Form|
|View type| detail |
|Position| menu |

![s312](images/s312.png)

VIEW OPTIONS 項目にある `Column order` に先程追加した「持っている数／登録数」をプルダウンメニューから選択します。これで画面上には 「2／3冊」というように指定した項目のみを表示することができます。

![s313](images/s313.png)

DISPLAY 項目にある `Icon` でお好きなアイコンを指定してください。ここまで設定したら右上の `SAVE` ボタンをクリックします。

![s314](images/s314.png)

### 3-4. 余計なViewを削除する
自動的に余計なViewが追加されていまっているので削除しておきます。PRIMARY VIEWS項目にある「シート1」という名前のViewをクリックして、`Delete` ボタンをクリックして削除してください。忘れずに右上の `SAVE` ボタンをクリックしてください。

![s315](images/s315.png)

### 3-5. 動作確認する
シミュレーターの左上にあるメニューボタンをクリックしてください。メニューが展開されて「所持数」という項目が追加されています。クリックすると、「持っている数／登録数」が確認できるようになっています。
元の画面には画面下部にある「書籍リスト」をクリックしてください。

![s316](images/s316.png)

### まとめ
いかがでしたでしょうか？ノンコーティングでここまでのアプリを短時間で作成することができました。
10名までは無料で配布できるので、お友だちとシェアしてみてはいかがでしょうか？アイデア次第で面白いアプリを作ることができますので是非チャレンジしてみましょう！
