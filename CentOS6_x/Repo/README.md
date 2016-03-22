### リポジトリ周り

#### リポジトリ
- epel 
  - 標準のリポジトリでは提供されていないパッケージを、yum コマンドでインストールすことを可能にする。 
  - EPEL は、エンタープライズ向けのリポジトリなので、サードパーティー製リポジトリの中では信頼性の高い。
     
- Remi
  - 使用すると基本リポジトリで提供されていないパッケージをyumでインストールすることができる     
  
#### 優先度
- 各リポジトリにpriorityを設定.数値が小さいほど優先的が高く、優先的に利用されます。

(ex)
```
CentOS-Base.repo
[base]
…
priority=1

[updates]
…
priority=2

[extra]
…
priority=2

[centosplus]
…
priority=2
```