# Chapter 2: コンテナ

## 2.6 第2章のまとめ
- **コンテナの概要**  
  - 複数の値をまとめて扱える仕組み。  
  - 代表的なコンテナにリスト・ディクショナリ・タプル・セットがあり、データの性質や用途に応じて使い分ける。  
- **リスト（list）**  
  - 順序付き、重複許可。インデックス参照／スライス可能。`append()`, `remove()`, `insert()` で要素操作。  
- **ディクショナリ（dict）**  
  - キー⇔値のペア。キーは重複不可。`d[key]`／`d.get(key)` で参照、`d[key] = value` で追加・更新、`del d[key]` で削除。  
- **タプル（tuple）**  
  - 順序付き、不変（要素の変更・追加・削除不可）。アンパックや関数の複数返却で利用。  
- **セット（set）**  
  - 順序なし、重複排除。集合演算（`|`, `&`, `-`）が可能。`add()`, `remove()` で要素操作。  
- **用途に合わせた選択**  
  - 順序や重複要件、検索頻度などを踏まえてコンテナを選ぶ。  
  - コンテナ間の相互変換（`list(d.keys())`, `set(a_list)` など）も活用。

---

## 2.7 練習問題

### 練習2‑1: 要件に最も適当なコンテナを選ぶ  
1. 47都道府県の「都道府県名と人口」 → **ディクショナリ**  
2. 過去28日間分の「1日あたりのWebサイトアクセス数」 → **リスト**  
3. 「北」「南」「東」「西」といった4つの方角 → **セット**  
4. この世に存在する「メジャーなプログラミング言語の名称」 → **セット**  
5. ある航空機の200座席の予約状態（0＝空き、1＝予約済み） → **リスト**

---

### 練習2‑2: 試験結果の合計と平均を表示するプログラム  
```python
# 5教科の点数を入力 → 合計と平均を表示
scores = []
subjects = ["国語", "算数", "理科", "社会", "英語"]
for subj in subjects:
    score = float(input(f"{subj}の点数を入力してください: "))
    scores.append(score)

total = sum(scores)
average = total / len(scores)
print(f"合計点: {total:.1f}")
print(f"平均点: {average:.1f}")
```
### 練習2‑3: 趣味の相性診断プログラム
# 1人目と2人目の趣味をそれぞれセットで入力し、
# 積集合の割合（0～100%）を「相性度」として算出
hobbies1 = set(input("1人目の趣味を5つカンマ区切りで入力してください: ").split(","))
hobbies2 = set(input("2人目の趣味を5つカンマ区切りで入力してください: ").split(","))

intersection = hobbies1 & hobbies2
union = hobbies1 | hobbies2

if union:
    compatibility = len(intersection) / len(union) * 100
else:
    compatibility = 0.0

print(f"共通の趣味: {intersection}")
print(f"相性度: {compatibility:.1f}%")
