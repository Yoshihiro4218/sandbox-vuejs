# 基礎から学ぶVue.js

- 構造の本体はDOMではなくJSのデータ → Vue.jsでは最初にデータが存在してそのデータの状態に適したDOMを構築する。(データ駆動)
- データバインディング → データと描画を同期させる仕組み
- `v-` ディレクティブ → 主にデータバインディングを行うために使用 → `v-bind`(ディレクティブ) `:value`(引数) `.sync`(修飾子) `="message"`(JSの式)
- リアクティブデータ → Vue.jsによって取得した時と代入したときのフック処理が登録された反応できるデータのこと。
- `{{ message }}` Mustache マスタッシュ（二重の中括弧） JSの記述も出来る
- `v-bind`の修飾子 → `.prop`: 属性の代わりにDOMプロパティとしてバインド `.camel`: ケバブケースをキャメルケースに変換 `.sync` 双方向バインディングを行う
- データバインディングされた`v-bind:class`と普通のclassを併用した場合、描画結果はマージ・上書きされる
- 条件を満たさなかった場合、`v-if`はコメント化(DOMレベルで削除され全ての監視が解除される)、`v-show`は`display: none`が付与されている(リアクティブで監視)
- templateタグに`v-if`つけてグループ化
- `v-for="各要素を代入する変数名 in 繰り返したい配列やオブジェクト"`
- 双方向データバインディング`v-model`

- ライフサイクル
1. beforeCreate: インスタンスが作成され、リアクティブの初期化がされる前
2. created: インスタンスが作成され、リアクティブの初期化がされた後
3. beforeMount: インスタンスがマウントされる前
4. mounted: インスタンスがマウントされた後
5. beforeUpdate: データが変更され、DOMに適用される前
6. updated: データが変更され、DOMに適用された後
7. beforeDestroy: Vueインスタンスが破棄される前
8. destroyed: Vueインスタンスが破棄された後
9. errorCaptured: 任意の子孫コンポーネントからエラーが補足された時

- テンプレート制御ディレクティブ
1. v-pre: テンプレートのコンパイルをスキップして静的なコンテンツとして扱う
2. v-once: 一度だけバインディングを行い、それ以降は静的なコンテンツとして扱う
3. v-text: Mustacheの代わりにテキストコンテンツを描画
4. v-html: HTMLタグをそのまま描画する
5. v-cloak: インスタンスの準備が終わると取り除かれる(CSS`[v-cloak]{display: none;}`みたいに書いて、テンプレートにMustacheが表示されるのを防いだり出来る)