# C言語のWindows環境構築で沼ったお話

## 状況
- VScode、GCCをインストール済み
- おなじみのHelloworldを作成
- コンパイルでエラー
- エラーの内容はヘッダーファイルが開けないという内容
- 設定ファイルにヘッダーファイルのパスを指定してもダメ

## 原因
- そもそも手順違うやん！？

## 解決
- 下記の手順を実施

    https://code.visualstudio.com/docs/cpp/config-mingw

頼りになるのは公式です。。。