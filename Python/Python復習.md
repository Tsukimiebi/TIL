# Pythonの基礎
## 文法
- 通常は改行で命令文は終了。1行1命令になっている。  
  - 命令文にバックスラッシュ（\）を入れることで、複数行を繋げることができる。  
  - 逆に、セミコロン（;）を使うことで1行に複数の命令を入れることも可能。

- コメントは行頭にハッシュ（#）。
  - Docstringとしてダブルクォート（"）やシングルクォート（'）3個で挟むことでもコメント的に使用可能。
  - Doctsringは用途が定められているので基本的にはコメントとして使用はしない。

- ブロックはインデントを元に構成される
  - インデントは半角スペース4つ、もしくはタブ文字
    - 半角とタブのインデントが混ざっているとエラーになるので注意

## 言語としての機能
- リスト型  
  複数のデータを格納してインデックスの数字で呼び出して使用する。型の違うデータを格納することも可能。  
  []で表現する。
  ~~~~
  [10, "数字" ]
  ~~~~

- 辞書型  
  複数のデータを格納することができるのはリストと同じ。インデックスの数字ではなくキーで呼び出して使用する。  
  {}で表現する。
  ~~~
  {'野菜': "すいか", '果物': "みかん"}
  ~~~

- 繰り返し処理
  - while文  
  - for文

- 分岐処理
  - if文
  - swich文は**無い**

- 関数

- クラス

- 例外処理
