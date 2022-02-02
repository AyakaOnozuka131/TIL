# しまぶーのIT大学：モジュールの基礎を学ぶ
## ES Modules形式の書き方
### モジュールがない場合
- モジュールがない場合、名前空間が被ってしまうデメリットがある
- ファイルが多くなるほど問題が多くなる

値が再代入されて上書きされてしまう。
```
<script>
  let name = "しまぶー";
</script>
<script>
  name = "ピカチュウ";
  document.body.textContent = name;
</script>
```

### モジュールを使った場合
- type="module"を使用すると、影響範囲を閉じることができる
- head内に読み込んでもOK（遅延評価ができる）
- モジュール同士のデータのやり取りができる


**例）影響範囲を閉じることができる**  
```
<script type="module">
  const name = "しまぶー";
</script>
<script type="module">
  name = "ピカチュウ";
  document.body.textContent = name;
</script>
```

**例）モジュール同士のデータのやり取りができる**  
```
// user.js
export const name = "しまぶー";
```
```
// index.js
import { name } from "./user.js";
document.body.textContent = name; // しまぶー
```

## 名前付きimport/export(named import/ named export)
### エイリアス（別名）
エイリアスとは？
識別子（変数や関数）に自分で別名をつけることができる
```
const name = "ピカチュウ";
export { name as pika }; // 別名が使えるようになった。今回はpikaが使える
```
- importでエイリアスが使われることが多い
- まとめてではなく個別に毎回exportすることができる

## Default import / export
[Codesandbox](https://codesandbox.io/s/default-export-import-5uic2?file=/src/index.js)
- export defaultはモジュールに対して1回しか使うことができない
- import時に{}で囲わない
- 宣言と一緒にできるのは関数のみ。（変数はカンマ区切りでまとめて宣言できてしまうため、export defaultの用途と合わない）
- 宣言と同時にexport defaultをする場合は識別子がいらない

## モジュールの特殊な Import / Export について学ぶ
