# 前書き
プログラミングに向き合う、エンジニアとして仕事にする上での心構えみたいな話。  
書名がそうだからかもしれないけど、滅茶滅茶シリコンバレーを推してる。

# Lesson1 Pythonの基本
- 変数の宣言とか数値計算のやり方について  
「変数とはなんぞや」とか「型とはなんぞや」みたいな話はせず  
「Pythonでは変数はこう宣言します」で入るので全く初めてプログラムやる人向けって感じではない。

- 文字列操作について  
  「こんな関数あるで」っていろんな操作を紹介していく感じっぽい。  
  「`count`を使うと文字列の数を返してくれます」みたいなのが沢山あるのでレファレンス的に使えるかも。

# Lesson2 データ構造
# Lesson3 制御フロー
電車で読んだ。「こういう書き方ができる」っていうのが役に立ちそうなので章ごとの内容と別に立項していく。

# Lesson4 関数と例外処理
- *argsについて  
  時々関数の説明で見かける`*args`は引数として設定しておくとまとめてタプル化してくれるやつとのこと。
  ~~~
  def sample_args(*args):
    print(args)

  run: sample args("生脚", "魅惑の", "マーメイド")
  result: ("生脚", "魅惑の", "マーメイド")
  ~~~
  
- **kwargsについて  
  *argsと同様に`**kwargs`は引数として設定しておくと辞書化して受け取ってくれるやつとのこと
  ~~~
  def sample_kwargs(*kwargs):
    print(kwargs)

  run: sample kwargs(wind = "ぶりーげん", night = "いーふぉ", world = "えるな")
  result: {'wind': "ぶりーげん", 'night': "いーふぉ", 'world': "えるな"}
  ~~~

- クロージャー  
  関数内関数のこと。関数内関数を戻り値にすることで、外側の関数に渡した引数を保持して実行することができたりする。
  ~~~
  def sale_ratio(ratio):
    def calc_sale_value(now_value):
      return now_value * ratio

  first_sale = sale_ratio(0.9)
  ptint([first_sale(1000), first_sale(800)])
  result: [900, 720]

  second_sale = sale_ratio(0.5)
  ptint([first_sale(1000), first_sale(800)])
  result: [500, 400]
  ~~~

- デコレーター
  関数内関数を使って作られた「関数の実行前後に実行する関数」のこと。
  ~~~
  def decolate(func):
    def wrapper(*args, **kwargs):
      print("前処理だよ")
      result = func(*args, **kwargs):
      print("後処理だよ")
      return result

  def add(a, b):
    return a + b

  sum = decolate(add)
  print(sum(10, 20))
  result:
    前処理だよ
    後処理だよ
    30

  @decolate
  def minus(a, b):
    return a - b

  print(minus(20, 10))
  result:
    前処理だよ
    後処理だよ
    10
  ~~~

- ジェネレーター  
    辞書やリストのようなイテレーターと異なり、呼び出しの都度値を生成する関数。

# Lesson5 モジュールとパッケージ
- コマンドライン引数  
  　コマンドラインから`python manage.py`のような形でpythonスクリプトを実行する際に  
  `python manage.py runserver`のような形で引数を渡すことができる。

- インポート時のルール設定  
  - `import sys, os, collections`のようにインポートをカンマで繋げる形式はあまり推奨されない
  - importは一つづつアルファベット順に縦に並べ、サードパーティモジュールは一行開けて区別する
    ~~~
    import collections
    import os
    import sys

    import termcolor
    ~~~

- スクリプトが読み込まれるときの注意  
  　定義された関数ではなく、モジュールに直接スクリプトが書いてある場合には  
  インポートされた時点でそのスクリプトは実行されてしまうため注意が必要である。  
  `main()`に処理を書き、`__name__`が`__main__`だった場合に処理をするように書いた方が良い。
  ~~~
  def main():
    #メインの処理

  if __name__ == "__main__":
    main()
  ~~~

  # Lesson6 オブジェクトとクラス  
  - クラスの書き方  
    基本的なことが書いてあるので復習になった
    クラス内のメソッドは引数`self`が必要。

# 役に立ちそうな記述テクニック
- デフォルト引数に空のリストなどを使いたい時  
  `def default_list_sample(list=[])`などとすると、2度目に関数が呼び出されたときは`list=[]`で初期化されない。  
  そのためデフォルトでは`None`を使って関数内で初期化を行う。
  ~~~
  def default_list_sample(list=None):
    if list is None:
      list = []
  ~~~
