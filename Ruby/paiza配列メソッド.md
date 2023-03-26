# 配列メソッド
配列の作成
```ruby
arr = Array.new(2)
p arr
#=> [nil, nil]
# 要素数2の配列を作成。
```

デフォルト値の設定
```ruby
nums = Array.new(26, 0)
# 要素数26の配列を作成。各要素は初期値0で作成される。
```

二次元配列の作成
```ruby
# ２行３列の配列を作成。初期値はnil
arr = Array.new(2) {Array.new(3)}
p arr
#=> [[nil, nil, nil], [nil, nil, nil]]

# ２行３列の配列を作成。初期値は０
arr = Array.new(2) {Array.new(3, 0)}
p arr
#=> [[0, 0, 0], [0, 0, 0]]
```

## splitメソッド
文字列を指定した区切り文字で分割し、配列で返す。数値は不可。
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

## 取得メソッド
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

## sliceメソッド
配列の範囲を指定して取り出す
```ruby
# 配列のインデックスの範囲を指定する
arr = ["Ruby","Python","Java"]
p arr.slice(0..2)
#=> ["Ruby", "Python", "Java"]

# 開始位置と取得要素数を指定する
arr = ["Ruby","Python","Java"]
p arr.slice(0,2)
#=> ["Ruby", "Python"]
```

## 追加メソッド
## unshiftメソッド
配列の先頭に要素を追加
```ruby
arr = [1,2,3]
arr.unshift(0)
p arr
#=> [0, 1, 2, 3]
```

## pushメソッド
配列の末尾に要素を追加
```ruby
fruits = ["apple", "orange"]

fruits.push("strawberry") 
#fruits << "strawberry"  でも可。

p fruits
#=> ["apple", "orange", "strawberry"]
```

## insertメソッド
配列の指定の位置に要素を挿入する
```ruby
a = [1, 2, 3]
a.insert(1, 4)  #(挿入位置, 挿入する要素)
print a 
#=> [1, 4, 2, 3]
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
## deleteメソッド
引数と同じ要素を削除
```ruby
a = [1, 2, 2, 3, 3]
a.delete(2)
print a
#=> [1, 3, 3]
```

## delete_atメソッド
指定位置の要素を削除
```ruby
a = ["a", "b", "c", "d"]
a.delete_at(2)
print a
#=> ["a", "b", "d"]
```

## shiftメソッド
先頭の要素を削除する
```ruby
array = [1, 2, 3]
array.shift
p array
#=> [2, 3]
```

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


## 配列その他メソッド
## indexメソッド
配列内の指定した要素の位置を取得
```ruby
# 最初の要素の位置しか得られないので注意
arr = ["apple", "grape", "orange", "banana", "meron", "banana"]
p arr.index("banana")
#=> 3
```

## countメソッド
条件に合った要素の数を数える
```ruby
array = ["red","blue","yellow","red","green"]
p array.count("red")
#=> 2
```

## transposeメソッド
配列を行列と見立て、行と列を入れ替えた配列を返す
```ruby
num = [[1,2,3],[4,5,6]]
p num.transpose
#=> [[1,4],[2,5],[3,6]]
```

## flattenメソッド
入れ子になった配列を平坦(１次元)にする
```ruby
array = [1, 2, [3, 4], 5, 6, [7, 8, 9]]
p array.flatten
#=> [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## ソートメソッド
配列内の要素を逆順に並び替える
```ruby
ary = [3, 2, 1, 5, 4]
p ary.reverse
#=> [4, 5, 1, 2, 3]
```

配列内の一部の要素を入れ替える
```ruby
arr = [5,10]
arr[0], arr[1] = arr[1], arr[0]
p arr
#=> [10, 5]
```

昇順でソート
```ruby
array = [300, 200, 150, 400, 100]
p array.sort  #文字列も可
#=> [100, 150, 200, 300, 400]
```

降順でソート
```ruby
array = [300, 200, 150, 400, 100]
p array.sort.reverse  #文字列も可
#=> [400, 300, 200, 150, 100]
```

二次元配列のソート
```ruby
# arr[1]で昇順にソート
arr = [[1, 3], [1, 5], [1, 2], [2, 4], [2, 2]] 
p arr.sort {|a,b| a[1] <=> b[1]}
#=> [[1, 2], [2, 2], [1, 3], [2, 4], [1, 5]]
```
