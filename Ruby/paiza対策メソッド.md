# 入力メソッド

入力値:文字列　改行：あり
```ruby
input = gets
```

入力値：文字列　改行：なし
```ruby
input = gets.chomp
```

入力値：数値   改行：あり
```ruby
input = gets.to_i
```

入力値：数値　 改行：なし
```ruby
input = gets.chomp.to_i
```

# 出力メソッド

改行なしで出力
```ruby
print 'hello'
```

改行ありで出力
```ruby
puts 'hello' 
```

デバッグ用出力（データ形式がわかる）
```ruby
p 'hello'
```

# splitメソッド

```ruby
//文字列を指定した区切り文字で分割し、配列で返す
"Tokyo:Saitama:Okinawa".split(':')
#=> ["Tokyo", "Saitama", "Okinawa"]
```
```ruby
//1バイトの空白文字を指定することも出来る
※この場合、改行(\n)、タブ(\t)も対象となる
" abc def g ".split(' ')
#=> ["abc", "def", "g"]
```

# 配列メソッド
```ruby
//入力値を配列に格納　　※map &:to_iで、数値に変換している　
input = gets.split.map(&:to_i)
```
```ruby
//分割して配列に格納　　※それぞれの変数に格納
a,b,c = gets.split(" ").map &:to_i
```
```ruby
//入力値を順番に格納
a = readlines.map &:to_i
```
```ruby
//複数行 && 複数要素の格納  ※文字列
lines = []
while line = gets
  lines << line.chomp.split(' ')
end
```
```ruby
//複数行 && 複数要素の格納  ※数値
lines = []
while line = gets
  lines << line.chomp.split(' ').map(&:to_i)
end
```

# countメソッド
```ruby
要素の数を数える
'abcdefg'.**count**('c')
#=> 1
```

# selectメソッド + 配列

配列、ハッシュから、ある条件を満たす要素だけを取り出す。

```ruby
list = [1, 2, 3, 4, 5]
 
list_new = list.select do |x|
  x > 3
end
 
p list_new
#=> [4, 5]
```
```ruby
list =  ["yamamoto", "tanaka", "oyama", "yano"]
 
list_new = list.select {|x| x.include?("yama")}
 
p list_new
#=>["yamamoto", "oyama"]
```



# 配列に指定した要素が存在するか確認する
## include?

```ruby
fruits = ["apple", "orange", "melon"]
puts fruits.include?("mel")
#=> false
```

# 配列の最初と最後の要素を取得
## firstメソッド
配列の最初の要素を取得

```ruby
name = ["taro", "hanako", "ichiro", "jiro"]
p name.first
#=> "taro"
```
## lastメソッド
配列の最後の要素を取得

```ruby
fruits = ["apple", "orange", "melon", "banana", "pineapple"]
p fruits.last
#=> "pineapple"
```

# 置換メソッド
## sub()メソッド

```ruby
//置換対象の文字列のうち、最初に出現するものを置き換える
article = "This is an apple. The apple is very delicious. Do you like this apple?"
article_replaced_1 = article.sub("apple", "orange")
p article_replaced_1 # "This is an orange. The apple is very delicious. Do you like this apple?"
※最初の「apple」のみが「orange」に置き換わる。
```

## gsub()メソッド
```ruby
article_replaced_2 = article.gsub("apple", "orange")
p article_replaced_2 # "This is an orange. The orange is very delicious. Do you like this orange?"
※全ての「apple」が置き換わる
```

## 複数の置換処理
```ruby
article = "I like travel, rock and soccer."
pattern = { "rock" => "J-pop", "soccer" => "baseball" }
replaced = article.gsub(/rock|soccer/, pattern)
p replaced # "I like travel, J-pop and baseball."
※置換処理パターンをハッシュで定義し、引数に渡すことで、一括処理ができる
```

# 削除メソッド
## gsubでの削除

```ruby
//ハイフンを空白にして、削除している
input = gets.gsub("-", "")
```

## delete メソッド

```ruby
//文字列から、指定の文字列を削除する
str = "abcdaaefaagh"
str.delete("a")
#=> "bcdefgh"
```

## sliceメソッド

```ruby
//文字列から、開始位置と取得文字数を指定して取り出す
str = "0123456789"
str.slice(3, 5)
#=> "34567"
```

# timesメソッド

```ruby
3.times do |num|
  p num
end
※num は 0から
```

# timesメソッド + 配列

```ruby
//繰り返し回数
n = 5
//配列の設定
sample = []

//繰り返し回数分、配列に格納
n.times do
  sample.push(gets.chomp.map &:to_i)
end
```

## returnの注意点

```ruby
//トップレベルで return した場合はプログラムが終了する。
※トップレベルとは、そのファイルの一番上のスコープのこと。

//ここのこと
def hoge
    //ここではない
end
//ここのこと
```

# eachメソッド + 配列

```ruby
//入力値取得
sample = readlines.map &:to_i

//変数宣言
n = 5

//eachメソッド
sample.each do |i|
  if n < 10
    n += 1
  else    
    puts "sample"
  end
end
```
# その他

少数点の計算
```ruby
num.to_f / 3
#=> 0.3333333333333333
```
