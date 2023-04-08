# 記法
## 改行
```ruby
str = "今日の天気は、\n晴れ"
puts str
#=> 今日の天気は、
#=> 晴れ
```

## 正規表現
```ruby
^  #行頭
/^abc/  #abcで始まる行
```
```ruby
$  #行末
/abc$/  #abcで終わる行
```
```ruby
.  #改行を除く任意の１文字
/a.b/  #aとbの間に1文字
```
```ruby
+  #1回以上の繰り返し
/a+/  #1回以上のaの繰り返し
```

## 三項演算子
if分よりも簡潔に記述できる
```ruby
a,b = 0,1

# 条件式? 真の時の値 : 偽の時の値
# a,b どちらも １の場合、1を出力する
puts (a == 1 && b == 1)? 1:0
#=> 0
```

## 範囲オブジェクト
```ruby
range = [1, 2, 3, 4, 5]
puts range[1..3]
#=> 2
#=> 3
#=> 4
```

## %w記法
※数値は文字列となるので注意

一次元配列
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
二次元配列
```ruby
input = %w(6 5 4 3 2 1),%w(3 1 8 8 1 3)
p input
#=> [["6", "5", "4", "3", "2", "1"], ["3", "1", "8", "8", "1", "3"]]
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
# 入力値を数値に変換して、配列に格納　　※splitのデフォルトは、空白文字で分割
input = gets.split.map &:to_i
```
```ruby
# 分割して配列（それぞれの変数）に格納　　※splitの引数に文字を指定することも可能。
a,b,c = gets.split(" ").map &:to_i
```
```ruby
# 複数行に１つずつ要素が存在する場合、順番に格納
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

# 文字列メソッド
## sliceメソッド
```ruby
# 文字列から、範囲を指定して取り出す
str = "0123456789"
p str.slice(3..5)
#=> "345"
```
```ruby
# 文字列から、開始位置と取得文字数を指定して取り出す
str = "0123456789"
p str.slice(3, 5)
#=> "34567"
```

## splitメソッド
文字列を指定した区切り文字で分割し、配列で返す。数値は不可。
```ruby
"Tokyo:Saitama:Okinawa".split(':')
#=> ["Tokyo", "Saitama", "Okinawa"]
```
１文字ずつ分割することも可能
```ruby
str = "123456"
arr = str.split("")
p arr
#=> ["1", "2", "3", "4", "5", "6"]
```

## insertメソッド
```ruby
# 指定したインデックスに文字を挿入する
str = "abcdefgh"
p str.insert(2, "zzz")
#=> "abzzzcdefgh"
```

## delete メソッド
```ruby
# 文字列から、指定の文字列を削除する
str = "abcdaaefaagh"
p str.delete("a")
#=> "bcdefgh"
```

## 置換メソッド
```ruby
str = "abcdefgh"
str[1] = "X"
p str
#=> "aXcdefgh"
```
```ruby
# 後ろから数える場合は、[-1]で表す
str = "abcdefgh"
str[-1] = "X"
p str
#=> "abcdefgX"
```

## indexメソッド
```ruby
# 文字列の文字が何文字目か検索する
str = "ABCDEFGHI"
p str.index('B')
#=> 1
```

## include?メソッド
```ruby
# 文字列の中に、指定した文字列が含まれるか確かめる
str = "ABCDEFGHI"
p str.include?("DEF")
#=> true
```

## a〜zを出力
```ruby
("a".."z").each do |i|
    puts i
end
```

## 文字列を小文字に変換
```ruby
str = "Hello World"
puts str.downcase
#=> hello world
```
## 文字列を大文字に変換
```ruby
str = "Hello World"
puts str.upcase
#=> HELLO WORLD
```
## 文字列を大文字・小文字それぞれに変換
```ruby
str = "Hello World"
puts str.swapcase
#=> hELLO wORLD
```

## 文字列に大文字を含むか判定する
```ruby
str = "Hello"
if str =~ /[A-Z]/   #大文字があるかチェック
    puts "YES"
end    
#=> YES
```

## 文字を数字(コードポイント)に変換
```ruby
puts 'A'.ord 
puts 'B'.ord 
#=> 65
#=> 66
```
## 数字(コードポイント)を文字に変換
```ruby
puts 65.chr
#=> A
```

# 繰り返しメソッド
## break
breakはループを抜ける

## return
return はメソッドを抜ける
```ruby
# さらに、トップレベルで return した場合はプログラムが終了する。
# トップレベルとは、そのファイルの一番上のスコープのこと。

//ここのこと
def hoge
    //ここではない
end
//ここのこと
```

## timesメソッド
基本形
```ruby
3.times do |num|
  puts num
end
※num は 0から
```

省略形
```ruby
3.times { |num| puts num }
```

## timesメソッド + 配列
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

## downtoメソッド
基本形
```ruby
# 初期値から1ずつ引いていき、（）の中の最小値になるまで繰り返し処理を行う
5.downto(3) do |i|
  puts i
end
#=> 5
#=> 4
#=> 3
```
省略形
```ruby
5.downto(3) { |i| puts i }
```

## eachメソッド
基本形
```ruby
nums = [1, 2, 3]
nums.each do |i|
    puts i
end
#=> 1
#=> 2
#=> 3
```
省略形
```ruby
nums = [1, 2, 3]
nums.each { |i| puts i }
```

## eachメソッド + 範囲
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

## reverse_eachメソッド
逆順に出力する
```ruby
nums = [1, 2, 3]
nums.reverse_each do |i|
  puts i
end
#=> 3
#=> 2
#=> 1
```

## eachメソッド + 二重ループ
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

## each_charメソッド
文字列内の文字を１文字ずつ取り出しながら処理を行う
```ruby
"hello世界".each_char {|c| print c, ' ' }
#=> h e l l o 世 界
```

## whileメソッド
指定した条件が真（true）の間、繰り返し処理を行う
```ruby
N, K = gets.split.map &:to_i
count = 0

while N < K do  # NがKの値を超えるまで中の処理を繰り返す
    N = N * 2
    count += 1
end    

puts count
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
## ハッシュ + 繰り返し
重複加算
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

## すべてのキーの取得
```ruby
fruit = {"Lemon" => 100, "Orange" => 150}
puts fruit.keys
#=> Lemon
#=> Orange
```
## キーの存在確認
```ruby
planet = { Mercury: 'emerald',　Venus: 'diamond' }
p planet.key?(:Mercury)
#=> true
```

## すべての値の取得
```ruby
fruit = {"Lemon" => 100, "Orange" => 150}
puts fruit.values
#=> 100
#=> 150
```

## 特定の値の取得
```ruby
fruit = {"Lemon" => 100, "Orange" => 150}
puts fruit["Lemon"]
#=> 100
```

# Set
## 空のセットを作成
```ruby
# 標準ライブラリーなので、require しないと使えない
require 'set'
s = Set.new
p s
#=> #<Set: {}>
```

## セットを作成
```ruby
# セットは重複する値を許さない
require 'set'
s = Set[3, 1, 2, 1]
p s
#=> #<Set: {3, 1, 2}>
```

# 計算メソッド

mod
```ruby
# 剰余演算子%のこと
puts 5 % 3
#=> 2
```

10進数を2進数に変える
```ruby
n = 10
puts n.to_s(2)
#=> 1010

# 10進数に戻す場合
n = "1010"
puts n.to_i(2)
#=> 10
```

少数点の計算
```ruby
puts 1.to_f / 3
#=> 0.3333333333333333
```

小数点の切り捨て
```ruby
puts (814 * 1.1).to_i
#=> 895
```

小数点以下、四捨五入
```ruby
puts 1.23456.round(2)  #　引数で桁数を指定
#=> 1.23
```

配列同士の掛け算（injectメソッド）
```ruby
arr = [1, 2, 3]
puts arr.inject(:*)
#=> 6
```

配列同士の掛け算（ループ）
```ruby
arr = [1, 2, 3]
result = 1
arr.each do |i|
    result *= i
end
puts result
#=> 6
```

配列の最大値、最小値
```ruby
sample = [5, 8, -6, 15]
puts sample.max (min)
#=> 15 (5)
```

配列の平均値を取得
```ruby
arr = [2, 3]
p arr.sum.fdiv(arr.length)
#=> 2.5  #浮動小数点数の商を返す
```

絶対値取得 ※正の数の場合はそのまま、負の数の場合は符号を取り、正の数にした数値を取得
```ruby
n = 5
sample = n.abs
```

累乗
```ruby
# この場合はxの2乗
x = 5
puts x ** 2
#=> 25
```

# その他
nil判定
```ruby
# オブジェクトが存在しないかを判定する
str = []
puts str[0].nil?
#=> true
```
