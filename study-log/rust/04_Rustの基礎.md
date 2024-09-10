
## パターンマッチングと構造化分解
- Rustでのパターンマッチング
	- 簡潔で明確な方法でデータ型を分解し条件チェックするツール
	- `match`と`if let`が主に利用される
	- `match`
		- 値を一連のパターンと比較しどれに一致するかに基づいてコードを実行
	- `if let`
		- 特定のパターンに一致する値をより簡潔に処理可能
### match
https://rust-book.cs.brown.edu/ch06-02-match.html
- 値が収まる最初のパターンで実行中に使用されるコードブロックに落ちる
- ifに似ているが、大きな違いがある
	- 条件をBoolで評価しなくても任意の型にすることができている
- https://github.com/ryosuke-horie/rust-basic/tree/main/match
- Enumで判定する上から２つをやった
- 所有権の話がでてきたので後回しに...


	