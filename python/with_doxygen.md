# Docstring を doxygen で処理する 2020.07.20

pythonコメントを[GoogleスタイルのDocstring](https://qiita.com/11ohina017/items/118b3b42b612e527dc1d#基本的なコメントの書き方)で書く

1. `$ pip3 install doxypypy` [doxypypy](https://github.com/Feneric/doxypypy)
1. パスの通ったところにpy_filterをおく
   ```bash
   #!/bin/bash
   doxypypy -a -c $1
   ```
2. `$ chmod +x py_filter`
3. Doxyfileの以下の項目を変更 (doxygen -g で生成できる)
   ```
   PROJECT_NAME = "プロジェクト名"
   PROJECT_NUMBER = 1.0 # (バージョン)
   PROJECT_BRIEF = 簡単な説明
   OUTPUT_LANGUAGE = Japanese # (or English)
   EXTRACT_ALL = YES
   INPUT = . # (Doxyfileのある場所)
   FILE_PATTERNS = *.py *.pyw
   RECURSIVE = YES
   FILTER_PATTERNS = *.py=py_filter
   HTML_OUTPUT = doc # (出力フォルダ)
   GENERATE_LATEX = NO
   ```
4. Doxyfileのある場所で`doxygen`とすればドキュメントができる

注意：モジュールのコメントは上手く反映されない
