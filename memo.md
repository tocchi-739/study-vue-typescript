# memo

- scoped

  scoped を指定すると、そのファイルに指定した style は他のファイルに適用されない

```
<style scoped>
</style>
```

- v-vind

定義した変数を HTML 内で使える

```
<a v-bind:href="url">bought at...</a>
```

- v-on

定義した関数を HTML 内で使える

```
<button v-on:click="buy">buy</button>
```

- ref

リアクティブにする方法１

再レンダリングさせることができる（厳密には違うかもしれないが、、）

ref に代入する場合は　変数名.value とする必要がある（ref はオブジェクトである）

```

import { ref } from "vue";

let item1 = ref({ name: "Desk", price: 300 });

const input = (e: any) => {
  item1.value.name = e.target.value;
};
```

- reactive

リアクティブにする方法２

オブジェクト全体をリアクティブにしたい場合

```
import { reactive } from "vue";


const item1 = reactive({ name: "Desk", price: 300 });

const input = (e: any) => {
  item1.name = e.target.value;
};

```

- v-model

input をすっきり描くことができる

関数を定義せずに、input の値を取得することができる

- computed

変数の値を条件に応じて分岐させたい場合などに使用

computed を使わなくても表現できるが、パフォーマンス的には computed を使った方が良い（推奨されている）

```
import { computed } from "vue";

const priceLabel = computed(() => {
  if (item1.price > budget) {
    return "予算オーバー";
  } else {
    return item1.price + "円";
  }
});
```

- v-if

条件付きで html 要素をレンダリングすることができる

似たものに v-show がある

```ツイートが0以下の場合のみpタグを表示
<p v-if="tweets.length <= 0">No tweets have been added.</p>
```

- コンポーネント間のデータの受け渡し
  - 親から子
    Props（defineProps）
  - 子から親
    Emit（defineEmits）
