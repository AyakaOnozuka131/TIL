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
- importでエイリアスが使われることが多い

## Default import / export
- export default1モジュールに対して1回しか使うことができない
