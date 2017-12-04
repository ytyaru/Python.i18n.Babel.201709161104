# このソフトウェアについて

Babelでpyファイルから翻訳対象箇所とmsgidを取得する。

`./res/i18n/run.py`

# 手順

`.py`ソースコードから`po`ファイル書き出しまでの手順をBabelライブラリを使って実装する方法がわかった。

1. [pyファイルから翻訳対象箇所を取得する](http://babel.pocoo.org/en/latest/api/messages/extract.html#extraction-functions)
1. [翻訳データ(Catalog)を作成する](http://babel.pocoo.org/en/latest/api/messages/catalog.html)
1. [Catalogからpoファイルを書き出す](http://babel.pocoo.org/en/latest/api/messages/pofile.html)

## 主要属性

今回はBabelのうち以下のコンストラクタやメソッドを使った。

* babel.messages.extract.extract_from_dir()
* babel.messages.catalog.Catalog()
    * add()
* babel.messages.pofile.write_po()
    * babel._compat.BytesIO()

# 課題

* 翻訳処理を作る
    * 翻訳結果をCatalog作成時にセットする

上記を追加すれば自動翻訳したpoファイルが作成できるはず。

# 前回

* [pybabelを使ってみた](http://ytyaru.hatenablog.com/entry/2018/11/09/000000)。
* [pybabelコマンドを半自動実行するshスクリプトを作った。](http://ytyaru.hatenablog.com/entry/2018/11/10/000000)

# 今回

詳細は`./res/i18n/run.py`参照。

`catalog.add(msgid, string='翻訳後テキスト')`のようにして翻訳データを作る。

`write_po()`で以下のような出力を得られる。

```
#: main.py:9 sub.py:1
msgid "MSG000"
msgstr "翻訳後テキスト"

#: mypackage/mymodule.py:1
msgid "Good Luck !"
msgstr "翻訳後テキスト"
```

# 開発環境

* Linux Mint 17.3 MATE 32bit
* [pyenv](https://github.com/pylangstudy/201705/blob/master/27/Python%E5%AD%A6%E7%BF%92%E7%92%B0%E5%A2%83%E3%82%92%E7%94%A8%E6%84%8F%E3%81%99%E3%82%8B.md) 1.0.10
    * Python 3.6.1
* [pygettext.py](https://github.com/python/cpython/blob/6f0eb93183519024cb360162bdd81b9faec97ba6/Tools/i18n/pygettext.py)
* [msgfmt.py](https://github.com/python/cpython/blob/6f0eb93183519024cb360162bdd81b9faec97ba6/Tools/i18n/msgfmt.py)

# ライセンス

* https://sites.google.com/site/michinobumaeda/programming/pythonconst

Library|License|Copyright
-------|-------|---------
[Babel](https://github.com/python-babel/babel)|[BSD 3-clause](https://github.com/python-babel/babel/blob/master/LICENSE)|[Copyright (C) 2013 by the Babel Team, see AUTHORS for more information.](https://github.com/python-babel/babel/blob/master/LICENSE)
