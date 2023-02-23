# 入力メソッド

```ruby
//入力値:文字列　改行：あり
input = gets
```

```ruby
//入力値：文字列　改行：なし
input = gets.chomp
```

```ruby
//入力値：数値   改行：あり
input = gets.to_i
```

```ruby
//入力値：数値　 改行：なし
input = gets.chomp.to_i
```

# 出力メソッド

```ruby
//改行なしで出力
print 'hello'
```

```ruby
//改行ありで出力
puts 'hello' 
```

```ruby
//デバッグ用出力（データ形式がわかる）
p 'hello'
```

# splitメソッド

・文字列を指定した区切り文字で分割し、配列で返す

"Tokyo:Saitama:Okinawa".split(':')

=> ["Tokyo", "Saitama", "Okinawa"]


・1バイトの空白文字を指定することも出来る

※この場合、改行(\n)、タブ(\t)も対象となる

" abc def g ".split(' ')

=> ["abc", "def", "g"]

# 配列メソッド

・入力値を配列に格納　　※map &:to_iで、数値に変換している　

input = gets.split.map(&:to_i)

・分割して配列に格納　　※それぞれの変数に格納

a,b,c = gets.split(" ").map &:to_i

・入力値を順番に格納

a = readlines.map &:to_i

・複数行 && 複数要素の格納  ※文字列

lines = []

while line = gets

  lines << line.chomp.split(' ')

end

・複数行 && 複数要素の格納  ※数値

lines = []

while line = gets

  lines << line.chomp.split(' ').map(&:to_i)

end

# countメソッド

要素の数を数える

'abcdefg'.**count**('c')

=> 1

# 置換メソッド

## sub()メソッド

・置換対象の文字列のうち、最初に出現するものを置き換える

article = "This is an apple. The apple is very delicious. Do you like this apple?"

article_replaced_1 = article.sub("apple", "orange")

p article_replaced_1 # "This is an orange. The apple is very delicious. Do you like this apple?"

※最初の「apple」のみが「orange」に置き換わる。

## gsub()メソッド

article_replaced_2 = article.gsub("apple", "orange")

p article_replaced_2 # "This is an orange. The orange is very delicious. Do you like this orange?"

※全ての「apple」が置き換わる

## 複数の置換処理

article = "I like travel, rock and soccer."

pattern = { "rock" => "J-pop", "soccer" => "baseball" }

replaced = article.gsub(/rock|soccer/, pattern)

p replaced # "I like travel, J-pop and baseball."

※置換処理パターンをハッシュで定義し、引数に渡すことで、一括処理ができる

# 削除メソッド

## gsubでの削除

※ハイフンを空白にして、削除している

input = gets.gsub("-", "")

## delete メソッド

※文字列から、指定の文字列を削除する

str = "abcdaaefaagh"

str.delete("a")

=> "bcdefgh"

## sliceメソッド

※文字列から、開始位置と取得文字数を指定して取り出す

str = "0123456789"

str.slice(3, 5)

=> "34567"

# timesメソッド

3.times do |num|

　p num

end

※num は 0から

# timesメソッド + 配列

//繰り返し回数
n = 5
//配列の設定
sample = []

//繰り返し回数分、配列に格納
n.times do

  sample.push(gets.chomp.map &:to_i)

end

## returnの注意点

※トップレベルで return した場合はプログラムが終了する。

※トップレベルとは、そのファイルの一番上のスコープのこと。

//ここのこと
 
def hoge

    //ここではない

end
 
//ここのこと

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
