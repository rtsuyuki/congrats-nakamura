# 中村駿吾さん ご栄転 デジタル色紙

部署異動のお祝いに贈る、コマンドで読む色紙です。
外部通信ゼロ。HTML 2枚だけの静的サイトなので、GitHub Pages でもローカルでも同じように動きます。

| ファイル | 誰が開くか | 中身 |
|---|---|---|
| `index.html` | 中村さん | 完成した色紙。コマンドで読む |
| `sign.html` | 書き手5名 | メッセージを書いてコピー用の1行を出す |

---

## 1. GitHub Pages で公開する

1. GitHub で新しいリポジトリを作る（**Public**。Free プランでは Private だと Pages が使えません）
2. `index.html` `sign.html` `README.md` をアップロード
   - Web からなら **Add file → Upload files** にドラッグするだけ
3. **Settings → Pages** を開く
   - Source: `Deploy from a branch`
   - Branch: `main` / `/ (root)` → **Save**
4. 1〜2分待つと URL が発行されます

```
https://<ユーザー名>.github.io/<リポジトリ名>/          ← 中村さん用
https://<ユーザー名>.github.io/<リポジトリ名>/sign.html  ← 書き手用
```

### コマンドで済ませる場合

```bash
git init
git add .
git commit -m "congrats board"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/<リポジトリ名>.git
git push -u origin main
```

push 後に Settings → Pages で上記の設定をします。

なお両ファイルに `<meta name="robots" content="noindex, nofollow">` を入れてあるので、
検索エンジンの結果には出ません。URL を知っている人だけが開く形になります。

---

## 2. メッセージの差し替え

`index.html` の冒頭にある `DATA` を書き換えます。

```js
const DATA = {
  name:    "中村 駿吾",
  tenure:  "研修生 → 人財開発課 → ◯◯部",   // ← 異動先を入れる
  messages: [
    { id:"komatsu", who:"小松", role:"...", body:"..." },
  ],
};
```

`sign.html` で各自が `/done` すると、この形式の1行がコピーできる状態で出ます。
届いた5行を `messages: [` の中に貼り替えれば完成です。

書き手側の下書きは `sign.html` の `ROSTER` にあります。

---

## 3. コマンド一覧

### index.html（中村さん）

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

### sign.html（書き手）

| コマンド | 動作 |
|---|---|
| `/done` | 確定してコピー用の1行を出す |
| `/clear` | 全部消して白紙から書く |
| `/undo` | 末尾の1行を消す |
| `/reset` | 最初の下書きに戻す |
| `/preview` | ここまでを表示 |

---

## 4. 当日の運用

プロジェクタに映すときは、**URL ではなくローカルの `index.html` を開いてください。**
会場の Wi-Fi に依存せずに済みます。ファイルをダブルクリックするだけで動きます。
