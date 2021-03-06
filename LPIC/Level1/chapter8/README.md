####    [Chapter8 ユーザインターフェースとデスクトップ]
- **内容**
  - **Xのインストール**
  - **ディスプレイマネージャーとウィンドウマネージャー**
  - **アクセシビリティ**


- **X Window System**
  - GUIを実現するために`X Window System(X, X11)`が使われている 
  - **X.Org** : XFree86から派生したシステム

![Alt Text](https://github.com/yhidetoshi/Pictures/raw/master/Linux_Memo/x-server-client.jpg)


- X.Orgの設定
  - `/etc/X11/xorg.conf`
  - `Xorg -configure`
    - xorg.confファイルを自動生成する
  - `X -config <path_to_file>`
    - テストを実施
  - **xvidtuneコマンド**
    - ビデオモードの詳細設定 

|セクション　|説明         |
|:-----------|:------------| 
|ServerLayout|入出力デバイスとスクリーンの指定|
|Files|フォントやカラーデータベースファイルのパス名|
|Module|ダイナミックモジュールの設定|
|inputDevice|キーボードやマウスなどの入力装置|
|Monitor|モニターの設定|
|Device|ビデオカードの設定|
|Screen|ディスプレイの色深度(表示色数)や画面サイズ設定|


- ネットワーク経由でのX利用
  - xhostコマンドを利用する
    - `xhost [+-][ホスト名]` 

|オプション　|説明         |
|:-----------|:------------| 
|+ホスト名|指定したホストをXサーバ接続許可リストに追加する|
|-ホスト名|指定したホストをXサーバ接続許可リストから削除する|
|+|すべてのホストがXサーバに接続することを許可する(アクセス制御は無効)|
|-|Xサーバ接続許可リストによるアクセス制御を有効にする|

1. リモートPCのXクライアントがローカルPCのXサーバを利用できるように許可する
  - `$ xhost +remotepc`
2. リモートPCの環境変数DISPLAYでXサーバを指定し、環境変数DISPLAYをエクスポートする
   -  `$ DISPLAY=localpc:0`
   -  `$ export DISPLAY`

(書式)[ホスト名]:ディスプレイ番号
3.  リモートPC側でXクライアントを起動
   -  `$rxvt &`  

**[Xクライアントコマンド]**

|コマンド　|説明         |
|:-----------|:------------|
|# showrgb|Xで利用可能なRGB値を表示|
|# xlclients|実行中のXクライアントを表示|
|# xwininfo|指定したウィンドのサイズや位置、色深度などの情報を得る|
|# xdpyinof|ディスプレイ情報を表示|


- **Xフォントサーバ**
  - **xfs** 
    - フォントの管理
  - フォントサーバの起動
    - `/etc/init.d/xfs start` 
  - 利用できるフォントの一覧を表示
    - `# xlsfonts`
  
- Xサーバの起動
  - `startxコマンド` 

- **ディスプレイマネージャー**
  - ランレベル5で起動
  - ログイン画面でユーザ名とパスワードを入力して直接、GUI環境に入ることができる
(設定方法)
```
vi /etc/inittab

initdefaultが記述されているところに下記を書く

id:5:initdefault:
```

- XDM(X Display Manager)
  - **GDM**(Gnome Display Manager)
    - GNOMEで利用される 
  - **KDE**(KDE Display Manager) 
  - 認証:**XDMCP** 
 
  
- デスクトップ環境
  - 統合デスクトップ環境
    - GNOME
    - KDE
    - Xfce(より軽量)
  
- アクセシビリティ
  - 障害者にとって扱いやすいようにする機能
  - GUI設定ツール**AccessX**
  - スティッキーキー
  - スローキー
  - バウンスキー
  - トグルキー
  - マウスキー
