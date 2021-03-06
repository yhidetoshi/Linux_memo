####    [Chapter3 GNU & UNIXコマンド ]
  - **コマンドライン操作**
  - **パイプとリダイレクトr**
  - **テキスト処理フィルタ**
  - **正規表現を使ったテキスト検索**
  - **viエディタ**

- **シェル**
  - ユーザからのコマンドを受け付け、必要なプログラムを実行するもの
  - **Bourne**
    - UNIXの標準的なシェル
  - **bash**
    - UNIXのシェルを改良したもので、多くのLinuxディストリビューションで使われている
  - **Cシェル**
    - C言語に似たスクリプトが利用できるシェル
  - **tcsh**
    - LinuxでCシェルとして使われちえる
  - **Kornシェル**
    - Bourneシェルを拡張したもの
  - **zsh**
    -  kshにbashやtcshの機能を取り入れた高機能シェル 

**環境変数**

|環境変数|説明|         
|:-----------|:------------|
|HISTFILE|コマンド履歴保存ファイルのパス|
|HISTSIZE|現在のシェルでのコマンド履歴の保存数|
|HISTFILESIZE|コマンド履歴保存ファイルへの履歴保存数|
|HOSTNAME|ホスト名|
|LANG|ロケール(言語設定)|
|PATH|コマンドやプログラムを検索するディレクトリのリスト|
|PWD|カレントディレクトリのパス|
|USER|ログインしているユーザ|

**man [option] [セクション番号] キーワード**

|オプション|説明|         
|:-----------|:------------|
|-k|キーワードに一部一致するコマンドやファイルのmanページを一覧表示(aproposコマンドと同じ)|
|-f|キーワードに完全一致するコマンドやファイルのmanページを一覧表示(whatisコマンドと同じ)|

- whatisデータベースの作成コマンド
  - `makewhatis` 

**manページのセクション番号**

|セクション番号|内容|         
|:-----------|:------------|
|1|ユーザーコマンド|
|2|システムコール(カーネルの提供する関数)|
|3|ライブラリ関数|
|4|デバイスファイル|
|5|ファイルのフォーマット|
|6|ゲームプログラム|
|7|マイクロパッケージ、プロトコル、ファイルシステムなど|
|8|システム管理コマンド|
|9|カーネルルーチン|


**メタキャラ**

|メタキャラ|説明|         
|:-----------|:------------|
|*|0文字以上の文字列|
|?|任意の1文字|
|$|変数|
|'|「'」で囲まれた部分を文字列とみなす(メタキャラクタを無視)|
|"|「"」 で囲まれた部分を文字列と見なす(メタキャラクタを無視)ただし、$ ` | " は除く|
|`|「`」の中で囲まれた文字列(変数の場合は格納されている値)をコマンドと見なす。そのコマンドの実行結果を表示|
|¥|次の文字(メタキャラ)を無視|
|コマンド1 ; コマンド2|コマンドを続けて実行|
|コマンド1 && コマンド2|コマンド1が成功した場合のみ、コマンド2を実行|
|コマンド1 || コマンド2|コマンド1が失敗した場合のみ、コマンド2を実行|
|~|ホームディレクトリ|
|.|カレントディレクトリ|
|..|カレントディレクトリの上の階層|

**設定されている変数を一覧で確認**

|コマンド|説明|         
|:-----------|:------------|
|set|全てのシェル変数と環境変数を表示|
|env|全ての環境変数を表示|
|pritenv|一部、または全ての環境変数を表示|

- すでに設定されている環境変数やシェル変数を削減するコマンド
  - `unset`
  - `unset 変数名`
  - (ex) `unset hoge`

- シェル変数HOGEを設定
  - `$ HOGE=stduy_linux`
  - シェル変数を環境変数にするコマンド
    - `export HOGE` 
  
**uniq [option] [入力ファイル[出力ファイル]]**

|オプション|説明|         
|:-----------|:------------|
|-d|重複している行の身を表示|
|-u|重複していない行のみを表示|

```
# cat hoge.txt
aaaa
bbbb
cccc
cccc
# uniq -u hoge.txt
aaaa
bbbb
# uniq -d hoge.txt
cccc
```

**head [option] [ファイル名]**

|オプション|説明|         
|:-----------|:------------|
|-n 行数|指定した行数をファイルの先頭から表示|
|-行数|指定した行数をファイルの先頭から表示|
|-c バイト数|指定したバイト数をファイルの先頭から表示|

**tail [option] [ファイル名]**

|オプション|説明|         
|:-----------|:------------|
|-n 行数|指定した行数をファイルの末尾から表示|
|-行数|指定した行数をファイルの末尾から表示|
|-c バイト数|指定したバイト数をファイルの末尾から表示|
|-f |ファイルの末尾に追加された行を表示し続ける|

- fmtコマンド
  - 1行あたりの最大文字数を指定してテキストを整形するコマンド
  - `fmt [-w 文字数] [ファイル名]`
  - 指定しないとデフォルトで75文字

**pr [option] [ファイル名]**

|オプション|説明|         
|:-----------|:------------|
|-l 行数|ヘッダ、フッタを含めたページの行数を指定(デフォルトは66行)|
|-h 文字列|ヘッダに表示されるファイル名を指定した文字列に変更|
|+開始ページ [:終了ページ]|開始ページを指定|


**wc [option] [ファイル名]**

|オプション|説明|         
|:-----------|:------------|
|-l|行数を表示|
|-w|単語数を表示|
|-c|文字(バイト数を表示)|

**改行コード**

|改行コード|説明|         
|:-----------|:------------|
|CRLF (\r\n)|Windows|
|LF (\n)|Unix OS(Linux, Mac OS Xなど)|
|CR (\r)|古いMacOS (バージョン9まで)|

**tr [option] [文字列1[文字列2]]**

|オプション|説明|         
|:-----------|:------------|
|-d|文字列1で指定した文字を削除|
|-s|文字列1で指定した文字が連続した場合、1文字に置き換える|

-> オプションを指定しな場合は、文字列1を文字列2に変換する

|文字クラス|説明|
|:-----------|:------------|
|[:alpha:]|英文字|
|[:lower:]|英小文字(a-z)|
|[:upper:]|英大文字(A-Z)|
|[:digit:]|数字(0-9)|
|[:alnum:]|英数字|
|[:space]|スペース|

**od [option] [ファイル名]**

|オプション|説明|         
|:-----------|:------------|
|-t|出力フォーマットを指定|
|-o (デフォルト)|8進数2バイト区切りで表示(-t o2と同じ)|
|-x|16進数2バイト区切りで表示(-t x2と同じ)|
|-c|ASCII文字またはバックスラッシュ付きのエスケープ文字で表示(-t cと同じ)|
