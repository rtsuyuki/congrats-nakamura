# 中村駿吾さん ご栄転 デジタル色紙

部署異動（法人インストラクターへ栄転）のお祝いに贈る、コマンドで読む色紙です。
外部通信ゼロ。HTML 1枚だけの静的サイトなので、GitHub Pages でもローカルでも同じように動きます。

---

## 1. GitHub Pages で公開する

1. リポジトリに `index.html` をアップロード（**Add file → Upload files**）
2. **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` / `/ (root)` → Save
3. 1〜2分でビルドが終わり、URL が開けるようになります

```
https://rtsuyuki.github.io/congrats-nakamura/
```

更新するときは、同じ名前で `index.html` を再アップロードするだけで上書きされます。
反映まで1〜2分かかります。

`<meta name="robots" content="noindex, nofollow">` を入れてあるので、検索結果には出ません。

---

## 2. メッセージの差し替え

`index.html` の冒頭にある `DATA` を書き換えます。

```js
const DATA = {
  name:    "中村 駿吾",
  tenure:  "研修生 → 人財開発課 → 法人インストラクター",
  messages: [
    { id:"tsuyuki", who:"露木 諒", body:"..." },
  ],
};
```

- `id` … `/read tsuyuki` で呼ぶときの名前。半角英字
- `who` … 画面に出る差出人名
- `body` … 本文。改行は `\n`

所属や関係性は画面に出しません。差出人名と本文だけです。

---

## 3. コマンド一覧

| コマンド | 動作 |
|---|---|
| `/messages` | 全員の一覧 |
| `/read 石本` | ひとりぶんを開く |
| `/all` | ぜんぶ通しで読む |
| `/show` | 全画面で1件ずつ流す（← 当日はこれ） |
| `/about` | 本人についての記録 |
| `/clear` | 画面を消す |
| `/help` | 一覧 |

名前だけ入力しても、その人のメッセージが開きます。
`/show` 中は ← → で移動、`Esc` で終了。

---

## 4. 当日の運用

プロジェクタに映すときは、**URL ではなくローカルの `index.html` を開いてください。**
会場の Wi-Fi に依存せずに済みます。ファイルをダブルクリックするだけで動きます。
