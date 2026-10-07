# 数独

ブラウザで遊べる数独ゲームです。解が一つに決まる問題を毎回自動で生成します。

**プレイ:** https://mika-zhong.github.io/sudoku/

## 機能

- 難易度 3 段階(やさしい / ふつう / むずかしい)
- メモ(候補数字)、消す、戻す、ヒント
- 同じ行・列・ブロックと同じ数字のハイライト、ルール違反の赤表示
- タイムとミス回数の記録
- Google ログインとオンラインランキング(Firebase Authentication / Cloud Firestore)
- スマホ対応、ライト / ダークテーマ対応

## 操作(キーボード)

| キー | 動作 |
| --- | --- |
| 1〜9 | 数字を入力 |
| 矢印キー | マスを移動 |
| Delete / Backspace | 消去 |
| N | メモモード切替 |
| Ctrl+Z | 戻す |

## ローカルで遊ぶ

`index.html` をブラウザで開くだけでゲームは動きます。ビルドは不要です。
Google ログインは `file://` では動かないため、ローカルで試すときは簡易サーバーを使ってください(例: `npx serve .`)。

## Firebase の設定

Firebase プロジェクト `sudoku-e66c5` を使います。

1. **Authentication** → ログイン方法 → **Google** を有効にする
2. **Authentication** → 設定 → 承認済みドメイン に `mika-zhong.github.io` を追加する
3. **Firestore Database** を作成する
4. **Firestore Database** → ルール に [`firestore.rules`](firestore.rules) の内容を貼り付けて公開する

記録は `rankings/{easy|normal|hard}/scores` に保存されます。ヒントを使ったゲームは登録されません。
