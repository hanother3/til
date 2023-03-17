# %w記法
```ruby
# %w記法を使わない場合
puts ["侍", "ブログ", "Ruby", "\"%w記法\""]
# %w記法を使う場合
puts %w(侍 ブログ Ruby "%w記法")

# %Wの場合（式展開あり）
blog = "ブログ"
puts %W(侍 #{blog})
#=> 侍
#=> ブログ
```

# 出力メソッド

```ruby
# 改行なしで出力
print 'hello'
```

```ruby
# 改行ありで出力
puts 'hello' 
```

```ruby
# デバッグ用出力（データ形式がわかる）
p 'hello'
```

# 入力メソッド

```ruby
# 入力値:文字列　改行：含まれる
input = gets
```

```ruby
# 入力値：文字列　改行：含まない
input = gets.chomp
```

```ruby
# 入力値：数値   改行：含まれる
input = gets.to_i
```

```ruby
# 入力値：数値　 改行：含まない
input = gets.chomp.to_i
```

# 入力メソッド + 配列
```ruby
# 入力値を配列に格納　　※map &:to_iで、数値に変換している　
input = gets.split.map(&:to_i)
```
```ruby
# 分割して配列に格納　　※それぞれの変数に格納
a,b,c = gets.split(" ").map &:to_i
```
```ruby
# 複数行の入力値を順番に格納
a = readlines.map &:to_i
```
```ruby
# 複数行 && 複数要素の格納  ※文字列
lines = []
while line = gets
  lines << line.chomp.split(' ')
end
```
```ruby
# 複数行 && 複数要素の格納  ※数値
lines = []
while line = gets
  lines << line.chomp.split(' ').map(&:to_i)
end
```

# 配列メソッド
デフォルト値の設定
```ruby
nums = Array.new(26, 0)
# 要素数26の配列を作成。各要素は初期値0で作成されます。
```

## splitメソッド
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

## mapメソッド
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

## selectメソッド
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

## 結合メソッド
## joinメソッド
配列の各要素を1つに連結する
```ruby
words = ['apple', 'melon', 'orange']
words.join 
#=> "applemelonorange"
```

引数に文字列を渡すとその文字列が間に挟み込まれる
```ruby
words = ['apple', 'melon', 'orange']
words.join(' ') 
#=> "apple melon orange"
```

## +メソッド
配列同士を連結する
```ruby
array1 = ['a', 'b']
array2 = ['c', 'd']
array3 = ['e', 'f']
array1 + array2 + array3
=> ["a", "b", "c", "d", "e", "f"]
```

## 重複メソッド
## include?
配列に指定した要素が存在するか確認する

```ruby
fruits = ["apple", "orange", "melon"]
puts fruits.include?("mel")
#=> false
```

## uniq/uniq!
重複を取り除いた新しい配列を返す
```ruby
a = [1, 1, 2, 2, 3, 4]
a.uniq
#=> [1, 2, 3, 4]
```
重複を判定するにはlengthメソッドと組み合わせる 
```ruby
arr = ["HND", "NRT", "KIX", "NGO", "NGO"]
puts arr.uniq.length != arr.length
#=>　true
```

## differenceメソッド
```ruby
# 指定した配列の要素と、同じ要素を取り除いた新しい配列を返す
ary1 = [1, 2, 3, 5, 4, 3]
ary2 = [2, 3]
newary = ary1.difference(ary2)
#=> [1, 5, 4]
```

## 置換メソッド
## sub()メソッド
置換対象の文字列のうち、最初に出現するものを置き換える

```ruby
article = "This is an apple. The apple is very delicious. Do you like this apple?"
article_replaced_1 = article.sub("apple", "orange")
p article_replaced_1 # "This is an orange. The apple is very delicious. Do you like this apple?"
# 最初の「apple」のみが「orange」に置き換わる。
```

## gsub()メソッド
置換対象の文字列すべてを置き換える

```ruby
article_replaced_2 = article.gsub("apple", "orange")
p article_replaced_2 # "This is an orange. The orange is very delicious. Do you like this orange?"
# 全ての「apple」が置き換わる
```

置換処理パターンをハッシュで定義し、引数に渡すことで、まとめて処理ができる
```ruby
article = "I like travel, rock and soccer."
pattern = { "rock" => "J-pop", "soccer" => "baseball" }
replaced = article.gsub(/rock|soccer/, pattern)
p replaced # "I like travel, J-pop and baseball."
```

## 削除メソッド
## popメソッド
末尾の要素を削除する
```ruby
array = [1, 2, 3]
array.pop
p array
#=> [1, 2]
```

## gsubでの削除
```ruby
# ハイフンを空白にして、削除している
input = gets.gsub("-", "")
```

## delete メソッド
```ruby
# 文字列から、指定の文字列を削除する
str = "abcdaaefaagh"
str.delete("a")
#=> "bcdefgh"
```

# transposeメソッド
配列を行列と見立て、行と列を入れ替えた配列を返す
```ruby
num = [[1,2,3],[4,5,6]]
p num.transpose
#=> [[1,4],[2,5],[3,6]]
```

## countメソッド
条件に合った要素の数を数える
```ruby
array = ["red","blue","yellow","red","green"]
p array.count("red")
#=> 2
```

## flattenメソッド
入れ子になった配列を平坦(１次元)にする
```ruby
array = [1, 2, [3, 4], 5, 6, [7, 8, 9]]
p array.flatten
#=> [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

# 文字列メソッド
## sliceメソッド
```ruby
# 文字列から、開始位置と取得文字数を指定して取り出す
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
# 繰り返し回数
n = 5
# 配列の設定
sample = []

# 繰り返し回数分、配列に格納
n.times do
  sample.push(gets.chomp.map &:to_i)
end
```

## returnの注意点
```ruby
# トップレベルで return した場合はプログラムが終了する。
# トップレベルとは、そのファイルの一番上のスコープのこと。

//ここのこと
def hoge
    //ここではない
end
//ここのこと
```

# eachメソッド + 配列
```ruby
# 入力値取得
sample = readlines.map &:to_i

# 変数宣言
n = 5

# eachメソッド
sample.each do |i|
  if n < 10
    n += 1
  else    
    puts "sample"
  end
end
```
範囲でeachメソッドを使う
```ruby
# 1以上 3以下
(1..3).each do |i|
 puts i
end
#=> 1
#=> 2
#=> 3
```
```ruby
# 1以上 3未満
(1...3).each do |i|
 puts i
end
#=> 1
#=> 2
```

# eachメソッド + 二重ループ
```ruby
board = []
result = 'D'

# 盤面の初期化
(1..5).each { board.push(gets.chomp.split('')) }

# 盤面の列番号をiで指定
(0..4).each do |i|
  o = 0
  x = 0
  
  # 盤面の行番号をrowで指定し、行ごとに判定する
  board.each do |row|
    if row[i] == 'O'
      o += 1
    elsif row[i] == 'X'
      x += 1
    end
  end

  if o == 5
    result = 'O'
    break
  elsif x == 5
    result = 'X'
    break
  end
end

puts result
```
## each_slice
配列を指定の要素数ごとに分割する
```ruby
ary = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j"]
# ５つごとに分割
p ary.each_slice(5).to_a
#=> [["a", "b", "c", "d", "e"], ["f", "g", "h", "i", "j"]]
```

## each_with_index
ループを回しつつ、index番号を取得する
```ruby 
fruit = ["りんご", "みかん", "いちご"]
fruit.each_with_index do |item, i|
  puts "#{i+1}番目のフルーツは、#{item}です。"
end
#=> 1番目のフルーツは、りんごです。
#=> 2番目のフルーツは、みかんです。
#=> 3番目のフルーツは、いちごです。
```

# ハッシュ
```ruby
hash = {Kyoko:"B",Rio:"O",Tsubame:"AB",KurodaSensei:"A"}	

# 繰り返し処理をする場合は|key,value|で、値を取り出せる
hash.each do |key,value|
    puts "#{key} #{value}"
end
#=> Kyoko B
#=> Rio O
#=> Tsubame AB
#=> KurodaSensei A
```
デフォルト値の設定
```ruby
# 無効キーを参照したときのデフォルト値を0に変更
hash = Hash.new(0)
puts hash[:age]
#=> 0
```

## 入力メソッドつき
```ruby
n = gets.chomp.to_i
blood = {}

n.times do |i|
    human = gets.chomp.split(" ")
    
    # hash[key] = value で値を入力
    blood[human[0]] = human[1]
    puts "#{human[0]} #{human[1]}"
end    
```
# ハッシュ + 繰り返し
## 重複加算
```ruby
count = gets.to_i
hash = {}

count.times do |i|
    str  = gets.split
    string = str[0]
    points = str[1].to_i
    
    # if hash[key]　で、keyが重複しているかをチェック
    if hash[string]
    # hash[key] = value で値を入力
       hash[string] += points
    else
       hash[string] = points
    end
end

# sort_byで、hashのvalueをソート
hash = hash.sort_by{|_,v| v }.reverse

hash.each do |key,value|
    puts "#{key} #{value}"
end
```

# ハッシュ + キーの取得
```ruby
fruit = {"Lemon" => 100, "Orange" => 150}
array = fruit.keys
puts array
#=> Lemon
#=> Orange
```
# ハッシュ + 値の取得
```ruby
fruit = {"Lemon" => 100, "Orange" => 150}
array = fruit.values
puts array
#=> 100
#=> 150
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
文字を数字(コードポイント)に変換
```ruby
puts 'A'.ord 
puts 'B'.ord 
#=> 65
#=> 66
```
数字(コードポイント)を文字に変換
```ruby
puts 65.chr
#=> A
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
#=> [400, 300, 200, 150, 100]
```

2次元配列のソート
```ruby
# arr[1]で昇順にソート
arr = [[1, 3], [1, 5], [1, 2], [2, 4], [2, 2]] 
p arr.sort {|a,b| a[1] <=> b[1]}
#=> [[1, 2], [2, 2], [1, 3], [2, 4], [1, 5]]
```

