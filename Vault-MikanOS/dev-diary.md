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

