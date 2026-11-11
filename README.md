# AI が 1 枚の HTML で作った 3D の解説ページ (エアコン・量子コンピューター)

同じ指示を 1 回だけ、7 つの AI モデルに出して、Three.js の 3D の解説ページを HTML ファイル 1 枚で作らせた結果です。

- エアコン: 家庭用エアコンの室内機と室外機を実物と同じ作りの 3D 模型にし、圧縮機の中の動き・ファンの回転・冷媒の流れ・冷房と暖房の切り替えを見せる
- 量子コンピューター: 希釈冷凍機の 3D 模型と、2 量子ビットの「H ゲート → CNOT ゲート → 測定」をブロッホ球で順に見せる

ブラウザで見る: https://satsuki-c6s.github.io/ai-3d-explainers/

測定と記事 (5 モデルの回): さつきの note「Claude Fable 5.2 と GPT-6 Astra に『エアコンの中身』を 3D で説明させた」 https://note.com/happy_hound3166/n/nf0fba18a933b

作った日: 2026 年 11 月 10 日

## 作品

| ファイル | モデル |
|---|---|
| aircon-fable52.html / quantum-fable52.html | Claude Fable 5.2 |
| aircon-astra.html / quantum-astra.html | GPT-6 Astra |
| aircon-opus55.html / quantum-opus55.html | Claude Opus 5.5 |
| aircon-fable51.html / quantum-fable51.html | Claude Fable 5.1 |
| aircon-grok.html / quantum-grok.html | Grok 4.7 |
| aircon-argon.html / quantum-argon.html | Gemini 4 Argon (11 日に追加) |
| aircon-carbon.html / quantum-carbon.html | Gemini 4 Carbon (11 日に追加・分けて書く指示つき) |

- エアコンは URL の後ろに `?mode=heat` を付けると暖房で始まります (何も付けなければ冷房)
- 各 `.gif` は同じ作品の録画です
- HTML は、モデルが最後に書いた `index.html` のままです。書き換えていません。Three.js は各ページが jsDelivr から読み込みます

## 作らせ方

- 道具: Hermes Agent v0.23.0。記憶も設定も無いまっさらな環境と空のフォルダーを毎回用意
- 使えるツールは端末とファイル操作だけ。思考の深さは全モデル high。時間の上限は 30 分
- 人が出す指示は 1 回だけ。追加の指示ややり直しはしていない
- モデルはブラウザーの道具を持たない (自分の出力を画面で見ずに作っている)
- 依頼文: `prompt-aircon.txt`・`prompt-quantum.txt`

## 採点 (各モデル 1 回・順位は付けない)

| モデル | 合計 /35 | エアコン /19 | 量子 /16 | 2 課題の時間 | 2 課題の原価 |
|---|---|---|---|---|---|
| Claude Fable 5.2 | 35 | 19 | 16 | 59 分 | 3,134 円 |
| GPT-6 Astra | 35 | 19 | 16 | 49 分 | 1,284 円 |
| Claude Opus 5.5 | 34 | 18 | 16 | 58 分 | 1,484 円 |
| Claude Fable 5.1 | 33 | 18 | 15 | 44 分 | 2,218 円 |
| Grok 4.7 | 29 | 16 | 13 | 37 分 | 432 円 |
| Gemini 4 Argon (11 日に追加) | 35 | 19 | 16 | 38 分 | 281 円 |
| Gemini 4 Carbon (11 日に追加・分けて書く指示つき) | 34 | 19 | 15 | 43 分 | 375 円 |

- 1 課題の点 = 機械の確認 3 点 (例外なしで開く・3D が描画される・操作なしで動いている) + 中身の項目 (エアコン 16・量子 13)
- 中身の項目は 3 つの AI モデル (Claude Fable 5.2・GPT-6.1 Sol・Gemini 4 Argon) が、作者名を伏せた画面の写真とソースで合否を付け、2 つ以上の合格で 1 点
- 採点表は走らせる前に固定しました (`RUBRIC.md`)
- 原価は、API に直結したモデルはトークン数 × 各社の公式単価、Grok 4.7 は中継の記録の値 (1 ドル 165 円)
- 各モデル・各課題 1 回だけの結果です。同じモデルでも、もう一度走らせれば別の画面が出ます。この表で順位は言えません

## 知っておいてほしい偏り

- 課題と採点表を作り、実測を回したのは Claude Fable 5.2 です。採点表の「正しい答え」も Fable 5.2 が書きました
- 審査は写真とソースで行い、動きそのものは見ていません。人の目の採点は入れていません
- Claude と GPT は各社の API に直結、Grok は中継と OpenRouter 経由で、経路がそろっていません
- Gemini の 2 つは、ほかの 5 つの翌日 (11 月 11 日) に同じ課題・同じ道具で走らせて足しました。Hermes Agent は 5 つのときが v0.23.0、Gemini のときが v0.23.1 です
- Gemini 4 Carbon は、同じ指示のままではページ全体を 1 回で書こうとして途中で打ち切られ、2 課題とも完走できませんでした。載せているのは「大きなファイルを 1 回で書かず、骨組みを書いてから部品ごとに足す (1 回 200 行以内)」という 3 行を足した回の結果です (`prompt-aircon-split.txt`・`prompt-quantum-split.txt`)。Gemini 4 Argon は同じ指示のままの回の結果です
- 審査した 3 つのモデルのうち 2 つ (Claude Fable 5.2・Gemini 4 Argon) は、比べるモデル自身です

## ライセンス

このリポジトリのファイルは MIT ライセンスです (`LICENSE`)。Three.js は MIT ライセンスで、jsDelivr から読み込みます。
