# What is this?
日本語解析ライブラリ[MeCab](http://taku910.github.io/mecab/)を使う際の、前処理を行うためのpython用ライブラリOcabです。  
Mecabを雌株と見たてて、雄株ことOcabと命名。  
使い方の詳細は、[こちらを参照](http://boomin.yokohama/archives/634)してください。

# How to use
## As a single program
単体で使うときは、以下のように使います。

```bash
$ python Ocab.py 南アルプスの天然水-Ｓｐａｒｋｉｎｇ*Ｌｅｍｏｎ+レモン一絞り
input     : 南アルプスの天然水-Ｓｐａｒｋｉｎｇ*Ｌｅｍｏｎ+レモン一絞り
normalized: 南アルプスの天然水-Sparking*Lemon+レモン一絞り
wakati    : 南アルプスの天然水 Sparking Lemon レモン 一 絞る
rmv st wds: 南アルプスの天然水 Sparking Lemon レモン 絞る
```

## As like Library in Python code
ライブラリとして使うときは、こんな感じです。

```python
$ python
from Ocab import Ocab, Regexp
c = Regexp()
text1 = c.normalize("南アルプスの天然水-Ｓｐａｒｋｉｎｇ*Ｌｅｍｏｎ+レモン一絞り")
print(text1) # 南アルプスの天然水-Sparking*Lemon+レモン一絞り
m = Ocab(target=["名詞","動詞","形容詞","副詞"])
text2 = m.wakati(text1)
print(text2) # 南アルプスの天然水 Sparking Lemon レモン 一 絞る
text3 = m.removeStoplist(text2, [])
print(text3) # 南アルプスの天然水 Sparking Lemon レモン 絞る
```

`m = Ocab(target=["名詞","動詞","形容詞","副詞"])`の部分でもっといろいろ指定できたりしますが、  
そこはコード読んでください。

# License
This program is applied MIT License.

# Reference
1. [解析前に行うことが望ましい文字列の正規化処理](https://github.com/neologd/mecab-ipadic-neologd/wiki/Regexp.ja)
1. [MeCabとPythonで品詞を選びつつ分かち書きをしたよ](https://foolean.net/p/576)
1. [日本語のストップワードのリスト](http://svn.sourceforge.jp/svnroot/slothlib/CSharp/Version1/SlothLib/NLP/Filter/StopWord/word/Japanese.txt)
