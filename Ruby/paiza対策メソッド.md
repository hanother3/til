# **入力メソッド**

・入力値:文字列　改行：あり

input = gets

・入力値：文字列　改行：なし

input = gets.chomp

・入力値：数値   改行：あり

input = gets.to_i

・入力値：数値　 改行：なし

input = gets.chomp.to_i

# **配列メソッド**

・入力値を配列に格納　　※数値　

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
