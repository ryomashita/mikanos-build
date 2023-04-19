# 「ゼロからのOS自作入門」取り組みの記録

### 2023/3/21
+ 開発環境リポジトリをフォーク
    + https://github.com/uchan-nos/mikanos-build/branches
+ Ubuntuを20.(LTS)から22.(LTS)にアップグレード
    + https://zenn.dev/ryuu/articles/upgrade-ubuntu2204-wsl
    + `sudo do-release-upgrade -d`でUbuntu自身からアップグレードが可能
+ WSLからgit pushできるようにする
    + 鍵の追加
+ 開発環境の構築を再開する
    + Ansibleなど、READMEの不明な用語を調べてまとめる。
    + 開発環境を構築できたら、１章から再開する。

### 2023/3/22
+ 公開鍵を生成しgithubとSSH可能に
+ fishをインストールだけ行う
    + https://www.vultr.com/docs/installing-fish-shell-on-ubuntu/
    + fishの設定を持ってきて、導入する
+ mikanos-build: 開発ツールの導入
    + Ansibleを使用してセットアップを行う。
+ Ansible: RedHat製の構成管理・自動化ツール
    + 参考サイト
        + https://qiita.com/Brutus/items/1894629105d61f4854bc
        + https://zenn.dev/y_mrok/books/ansible-no-tsukaikata
    + 特徴
        * 構成記述にYAMLを使用
        + エージェントレス: PythonとSSH通信が可能なら、予めエージェントを導入したりする必要がない。
    + 基本用語
        + Playbook: 作業を記述した作業単位(.yml)
        + inventory: 導入対象となる機器の一覧表(.yml)
        + Module: クラウド関連モジュールなど、拡張を行う
+ AnsibleでリポジトリのREADME記載通りに、開発環境を導入。
    + ディレクトリ名はosbookとする必要があり、それだけ修正。

### 2023/3/23
+ BOOTX64.EFI
    + バイナリエディタ用にhexeditを導入。

→ hexeditの１行表示数を変更できるか調べる。
→ fish他、bashrcに記載のパッケージを導入する。
→ BOOTX64.EFIを作成する。

### 2023/3/25
+ BOOTX64.EFIを作成
    + 2箇所ミスがあったが、修正できた。
        + sumだと正解に近づいていることが分かる。
+ QEMUで起動
    + QEMU自体は起動できたが、Hello Worldは表示されない。
    + エラー文も出ている。

→ 正常動作の状態を確認し、QEMU実行時のエラーを解決する。

### 2023/3/26
+ BOOTX64.EFIをQEMUで起動し、Hello, World!を表示できた。
    + 末尾の0埋めが足りていなかった。
    + day01/bin/hello.efiに同じファイルがあった。
+ QEMU実行時のログ2つはwarningなので、動作には影響なさそう。
→ 次の内容に進む。

### 2023/3/27
+ 1.9 C言語でハローワールドの動作確認ができた。
→ コラムを読み返し、知らなかった単語・内容を軽く調べてまとめる。

### 2023/4/5
+ 第２章に入り、mikanosソースコードをfork, cloneした。
→ メモはこちらのosbookにとっていく。
-> gitで日本語ファイル名が正しく表示されていない。

### 2023/4/6
+ 51pのbuildでエラーが発生。
    + 同じログのエラーはあったが、解決策が面倒そう 
-> エラー解決を目指す

### 2023/4/8
+ buildエラーはgitバージョンを戻して解決
    + https://github.com/uchan-nos/mikanos-build/issues/6
```
cd $HOME/edk2
git checkout 4ac0296
git checkout edk2-stable202102 # こちらでも良い
```

### 2023/4/11
+ 62pまでの、メモリマップを取得しCSVファイルに書き出すプログラムを実行できた。
    + 取得したメモリマップが何かはあまり分かっていない。
        + 起動したブートローダのメモリマップ？

