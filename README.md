# 中村駿吾さん ご栄転 デジタル色紙

法人インストラクターへのご栄転を祝う、コマンドで読む色紙です。
外部通信ゼロ、画像も埋め込み済みの HTML 1枚。GitHub Pages でもローカルでも同じように動きます。

公開URL: https://rtsuyuki.github.io/congrats-nakamura/

---

## 1. 公開・更新のしかた

1. リポジトリで **`+` → Upload files**
2. `index.html`（と `README.md`）をドラッグ
3. 下の **Commit changes**

同じ名前で上げれば上書きされます。反映まで1〜2分。
確認するときはキャッシュを避けるため `?v=2` のように末尾を変えてください。

Pages の設定は **Settings → Pages** → Source: `Deploy from a branch` → Branch: `main` / `/ (root)`。
`deploy` が Timeout で落ちたときは **Re-run jobs**。繰り返すなら Source を `GitHub Actions` に切り替えます。

`<meta name="robots" content="noindex, nofollow">` を入れてあるので検索結果には出ません。

---

## 2. 中身の直しかた

`index.html` の冒頭の `DATA` だけ触ります。

```js
const DATA = {
  name:    "中村 駿吾",
  eyebrow: "CONGRATULATIONS / 2026.08",
  tenure:  "研修生 → 人財開発課 → 法人インストラクター",
  seal:    "祝",
  org:     "インターネット・アカデミー株式会社",
  facts:   [ "...", ... ],          // /about に出る記録
  messages:[ { id:"tsuyuki", who:"露木 諒", body:"..." }, ... ],
};
```

- `id` … 半角英字。内部用
- `who` … 画面に出る差出人名
- `body` … 本文。改行は `\n`

所属や関係性は表示しません。差出人名と本文だけです。
人数を増減しても、件数の表示は自動で追従します。

イラストは `PORTRAIT` に base64 で埋め込んであります。差し替えるときはこの文字列ごと入れ替えます。

---

## 3. コマンド

| コマンド | 動作 |
|---|---|
| `/messages` | 全員の一覧（タップで開く。既読が出る） |
| `/all` | ぜんぶ通しで読む |
| `/show` | 1通ずつ全画面。スワイプ／← → で移動、Esc で終了 |
| `/show auto` | 9秒ずつ自動でめくる（プロジェクタ用） |
| `/about` | 本人についての記録 |
| `/clear` | 画面を消す |
| `/help` | 一覧 |

名前を入力してもその人の手紙が開きます。入力欄の上のボタンからも同じ操作ができます。

---

## 4. 当日の運用

プロジェクタに映すときは、**URL ではなくローカルの `index.html` を開いてください。**
会場の Wi-Fi に依存しません。ダブルクリックするだけで動きます。
自動送りが要るときだけ `/show auto`、読み上げながら進めるなら `/show`。
