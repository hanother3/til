# 入力メソッド

入力値:文字列　改行：含まれる
```ruby
input = gets
```

入力値：文字列　改行：含まない
```ruby
input = gets.chomp
```

入力値：数値   改行：含まれる
```ruby
input = gets.to_i
```

入力値：数値　 改行：含まない
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

文字列を指定した区切り文字で分割し、配列で返す
```ruby
"Tokyo:Saitama:Okinawa".split(':')
#=> ["Tokyo", "Saitama", "Okinawa"]
```
1バイトの空白文字も指定可。　※この場合、改行(\n)、タブ(\t)も対象となる
```ruby
" abc def g ".split(' ')
#=> ["abc", "def", "g"]
```
("")を使って、１文字ずつ分割する
```ruby
str = "123456"
array = str.split("")
p array
#=> ["1", "2", "3", "4", "5", "6"]
```

# mapメソッド

配列の要素の数だけブロック内で処理を繰り返し、新しい配列を返す
```ruby
# 通常の書き方
["RUBY", "PHP", "JAVA"].map { |s| s.downcase }
#=> ['ruby', 'php', 'java']

# 省略した書き方
["RUBY", "PHP", "JAVA"].map(&:downcase)
#=> ["ruby", "php", "java"]

# 実行する処理が複数行に渡る場合
配列.map do |変数|
  実行する処理
end
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
'abcdefg'.count('c')
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
# 配列の各要素を1つに連結する
## joinメソッド
```ruby
words = ['apple', 'melon', 'orange']
words.join 
#=> "applemelonorange"
```

引数に文字列を渡すとその文字列が間に挟み込まれる
```ruby
words = ['apple', 'melon', 'orange']
words.join(', ') 
#=> "apple, melon, orange"
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

## uniq/uniq!での削除
重複を取り除いた新しい配列を返す
```ruby
a = [1, 1, 2, 2, 3, 4]
a.uniq
#=> [1, 2, 3, 4]
```

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

範囲オブジェクト
```ruby
range = [1, 2, 3, 4, 5]
puts range[1..3]
#=> 2
#=> 3
#=> 4
```
範囲オブジェクト + each
```ruby
(1..5).each do |i|
  p i
end
#=>1
#=>2
#=>3
#=>4
#=>5
```

配列の最大値、最小値
```ruby
sample = [5, 8, -6, 15]
puts sample.max (min)
#=> 15 (5)
```
絶対値取得 ※正の数の場合はそのまま、負の数の場合は符号を取り、正の数にした数値を取得
```ruby
n = 5
sample = n.abs
```

文字列を大文字⇔小文字に変換

```ruby
str = "Hello World"
puts str.downcase
#=> hello world
```
```ruby
str = "Hello World"
puts str.upcase
#=> HELLO WORLD
```

昇順でソート
```ruby
array = [300, 200, 150, 400, 100]
p array.sort
#=> [100, 150, 200, 300, 400]
```

降順でソート
```ruby
array = [300, 200, 150, 400, 100]
p array.sort.reverse
=> [400, 300, 200, 150, 100]
```

