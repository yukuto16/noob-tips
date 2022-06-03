# C言語のgccコンパイルに関するあれこれ

- 複数ファイルをコンパイルする際は、オプションで一つの実行ファイルにするとよい。
 
    `gcc -o maintest2 .\main_1.c .\main_2.c`

- コマンドプロンプトで動かすとき、文字化け防止で文字コード指定してあげる

    `gcc -fexec-charset=CP932 -o maintest2 .\main_1.c .\main_2.c`

- 自作ヘッダーを参照する場合は、-Iでパス指定。

    `gcc -fexec-charset=CP932 -I .\include\ -o maintest2 .\main_1.c .\main_2.c`