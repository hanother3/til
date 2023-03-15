# 新・Bランクレベルアップメニュー

【マップの扱い 2】マップの書き換え・縦横

```ruby
h, w = gets.chomp.split.map(&:to_i)
move = [-1, 1]
str = []

h.times do
  str << gets.chomp
end

y, x = gets.chomp.split.map(&:to_i)

if str[y][x] == "."
  str[y][x] = "#"
else
  str[y][x] = "."
end

move.each do |i|
  if 0 <= y + i && y + i < h
    if str[y + i][x] == "."
      str[y + i][x] = "#"
    else
      str[y + i][x] = "."
    end
  end

  if 0 <= x + i && x + i < w
    if str[y][x + i] == "."
      str[y][x + i] = "#"
    else
      str[y][x + i] = "."
    end
  end
end

str.each do |s|
  puts s
end

# このコードは、与えられた盤面に対して、指定された座標とその周囲のマスを反転させる処理を行い、変更後の盤面を出力するプログラムです。
# 最初の行では、盤面の高さを表す整数 h と、盤面の幅を表す整数 w を入力しています。
# getsメソッドで標準入力から取得した文字列を、splitメソッドで空白で区切って配列に分割し、mapメソッドで各要素を整数に変換して、それぞれ h と w に代入しています。
# 次に、移動する量を表す配列 move を定義し、空の配列 str を初期化しています。
# その後、 h 回ループを回しながら、getsメソッドで標準入力から取得した文字列を配列 str に格納しています。
# 次に、指定された座標を表す変数 y と x を、getsメソッドで標準入力から取得しています。
# その後、座標(y, x)のマスの状態によって、マスを反転させています。座標(y, x)のマスの状態が"."であれば、"#"に変更し、"#"であれば"."に変更します。
# 最後に、移動量を表す配列 move の要素を順番に取り出しながら、指定された座標から上下左右のマスを順番に反転させています。
# まず、座標(y + move[i], x)が盤面内に存在するかどうかをチェックし、存在する場合はそのマスの状態を反転させます。
# 次に、座標(y, x + move[i])が盤面内に存在するかどうかをチェックし、存在する場合はそのマスの状態を反転させます。
# 最後に、配列 str の要素を順番に取り出しながら、各行を改行付きで出力しています。
```

【文字列 1】疑似数字 
```ruby
s = gets.chomp

 # 0以上 s.length未満
(0...s.length).each do |i|
  (i...s.length).each do |j|
    if s[i].match?(/\d/) && s[j].match?(/\d/)
      puts s[i..j]
    end
  end
end

# このコードは、入力された文字列 s 中の数字の部分文字列を見つけて、それを出力するプログラムです。
# まず、 gets.chomp メソッドを使って、標準入力から文字列を受け取ります。受け取った文字列は、変数 s に格納されます。
# 次に、2重の each ループを使って、文字列中のすべての部分文字列の組み合わせを網羅します。
# i と j は、それぞれ部分文字列の最初の文字と最後の文字のインデックスを表します。 
# i のループ範囲は 0 から s.length - 1 までで、 j のループ範囲は i から s.length - 1 までです。
# 各部分文字列に対して、 if ステートメントを使って、文字列中の i 番目と j 番目の文字がどちらも数字である場合にのみ、その部分文字列を出力します。
# 数字であるかどうかを判断するには、 match? メソッドを使って正規表現 \d （数字）にマッチするかどうかを確認します。
# 最後に、 puts メソッドを使用して、数字の部分文字列を出力します。
# 部分文字列を取得するには、 [] メソッドによって文字列をスライスして、範囲演算子 .. を使用して、部分文字列を指定します。
# このコードでは、範囲演算子 ... を使用して、最初の値から最後の値を含まない範囲を指定することで、部分文字列の組み合わせを網羅しています。
# また、Rubyの場合、文字列の最初の文字を取得するには、0 を使う代わりに、[0] を使用することができます。

二重のeachループについて
# 外側のループが i=0 で始まり、内側のループが j=0 で始まる。
# j が増えるにつれて、s[i..j] が部分文字列になる。
# 内側のループが終了すると、外側のループが i=1 で再び始まり、内側のループが j=1 で始まる。
# これが最後の組み合わせになるまで、i と j の値を増やし続ける。

```

【条件判定 3】過剰コンプライアンス
```ruby
n = gets.chomp.to_i
ban = gets.chomp

n.times do
  str = gets.chomp

  if str.size == ban.size
    if str == ban
      puts "banned"
    elsif str[0...(str.size+1)/2] == ban[0...(str.size+1)/2]
      x = "x" * ((str.size+1)/2)
      puts x + str[(str.size+1)/2...str.size]
    elsif str[str.size/2...str.size] == ban[str.size/2...str.size]
      x = "x" * ((str.size+1)/2)
      puts str[0...str.size/2] + x
    else
      puts str
    end
  else
    puts str
  end
end

# このコードは、最初に整数 n と文字列 ban を読み込み、その後に n回ループを実行し、各ループで文字列 str を読み込んで処理を行うものです。
# 具体的には、各ループでは、str の長さが ban の長さと等しい場合には、以下の処理を行います。
# str が ban と等しい場合には、"banned" と出力します。
# str の前半部分が ban の前半部分と一致する場合には、str の前半部分に "x" をつなげ、str の後半部分をそのままつなげた文字列を出力します。
# str の後半部分が ban の後半部分と一致する場合には、str の前半部分をそのままつなげ、str の後半部分に "x" をつなげた文字列を出力します。
# 上記以外の場合には、str をそのまま出力します。
# str の長さが ban と等しくない場合には、str をそのまま出力します。
# 具体的な処理は、文字列のスライスを利用して行われています。
# 例えば、str[0...(str.size+1)/2] は、str の先頭から (str.size+1)/2 文字目までの部分文字列を取得することを意味します。
# また、"x" を繰り返しつなげる場合には、"x" * ((str.size+1)/2) のように、* 演算子を使って簡単に表現できます。
```

【全探索 1】高い寿司を食いたい！

```ruby
num, eat = gets.chomp.split.map(&:to_i)
price = []

num.times do |i|
    price << gets.chomp.to_i
end

eat_price = 0

(0...num).each do |i|
  sum = 0
  (0...eat).each do |j|
    sum += price[(i + j) % num]
  end
  
  # eat_price と sum の大きい方を eat_price に代入
  eat_price = [eat_price, sum].max
end

puts eat_price

# このコードは、与えられた数列から、連続した部分列の中で要素の和が最大になるものを見つけて、それを出力するプログラムです。
# 最初に、 gets.chomp.split.map(&:to_i)を使って、標準入力から2つの整数を読み込み、それぞれ num と eat に代入しています。
# num は数列の要素数を表し、eat は求める連続した部分列の長さを表します。
# 次に、配列 price を初期化し、num 回繰り返しを行います。
# 各繰り返しでは、 gets.chomp.to_iを使って標準入力から整数を読み込み、配列 price に追加しています。
# このようにして、与えられた数列が price 配列に格納されます。
# 次に、eat_price を初期化し、2重の繰り返しを行います。外側の繰り返しでは、num 回繰り返しを行い、内側の繰り返しでは、eat 回繰り返しを行います。
# 内側の繰り返しでは、現在の位置から eat 個先の要素を順に加算して sum に格納します。
# 内側の繰り返しが終了したら、eat_price と sum の大きい方を eat_price に代入します。
# 最後に、eat_price を出力します。これは、与えられた数列から求めた連続した部分列の中で、要素の和が最大になるものです。
```

【シミュレーション 2】perfuct shuffle
```ruby
k = gets.to_i
deck = []
upper_side = []
lower_side = []
mark = ["S", "H", "D", "C"]

mark.each do |m|
  (1..13).each do |n|
    deck.push(m + "_" + n.to_s)
  end
end

k.times do
  upper_side = deck[0..25]
  lower_side = deck[26..51]
  deck.each_with_index do |_val, i|
    if i % 2 == 0
      deck[i] = upper_side[i / 2]
    else
      deck[i] = lower_side[i / 2]
    end
  end
end

puts deck

# このコードは、トランプのカードをシャッフルする処理を行うものです。
# 最初に、gets.to_iを使って、トランプをシャッフルするための繰り返し回数を読み込み、 k に代入します。
# 次に、 deck という配列を定義し、mark の各スートと、各スートの1から13までの数字を組み合わせて作られる、52枚のカードを順に push していきます。
# その後、トランプをシャッフルするために、 upper_side と lower_side という配列を定義し、deck の上半分と下半分にそれぞれ格納します。
# そして、 deck の要素を順番に走査し、偶数番目の要素は upper_side の要素を、奇数番目の要素は lower_side の要素を挿入します。
# この処理で、トランプをシャッフルしていることになります。
# 最後に、 deck を出力することで、シャッフルされたトランプのカードが表示されます。
```
