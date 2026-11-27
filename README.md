# 確率統計 — 原理から統計的推論へ

大学公開講義資料を参考に独自構成した、確率論・統計学の日本語学習教材です。

## 閲覧
GitHub Pages 公開後は、サイトのトップページから全22章、演習、解答、参考文献を閲覧できます。

## ファイル構成
- `index.html`: 学習サイト本体。Markdownを読み込み、数式をMathJaxで表示します。
- `style.css`: サイトのレイアウトと表示設定。
- `probability_statistics_v2.md`: 増補第2版の統合Markdown原稿（ダウンロード用）。
- `content/part-01.md`〜`content/part-06.md`: サイト表示用に分割した同じ本文。
- `.nojekyll`: GitHub PagesのJekyll処理を無効化します。

## GitHub Pages
1. Settings → Pages を開く。
2. Build and deployment の Source を **Deploy from a branch** にする。
3. Branch を **main**、Folder を **/(root)** に設定して Save。
4. デプロイ完了後、Settings → Pages に表示されるURLを開く。

## 注意
- 公開リポジトリ・公開サイトです。個人情報、非公開データ、企業から提供された研究データは含めないでください。
- 数式表示には MathJax、Markdown表示には markdown-it のCDNを利用します。
- 教材の記述・数値例は独自構成です。参考資料の原文を転載するものではありません。
