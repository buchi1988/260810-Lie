# リー群を体感する

リー群(Lie group)をインタラクティブな可視化で学ぶ静的 Web ページです。
依存ライブラリなしの単一 `index.html` で構成されています(黒背景・モノクロのシンプルなデザイン)。

## 内容

1. **SO(2)** — 回転行列をスライダーで動かし、合成が角度の足し算になることを確認
2. **リー環と指数写像** — 接線(リー環)が円周(リー群)に巻き付く様子と、行列指数関数の級数の収束
3. **SO(3) の非可換性** — 回転の順序で結果が変わることを立方体のアニメーションで比較(自由回転も可)
4. **SU(2) と二重被覆** — 360° 回しても戻らない SU(2) の元を 0°→720° で追う

## ローカルで見る

```sh
# 任意の静的サーバーで OK
npx serve .
# または
python3 -m http.server
```

## Cloudflare へのデプロイ

### 方法 1: Cloudflare Pages(Git 連携)

1. [Cloudflare ダッシュボード](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
2. このリポジトリを選択
3. ビルド設定はすべて空のままで OK(フレームワークなし・ビルドコマンドなし・出力ディレクトリ `/`)
4. **Save and Deploy**

以後、ブランチに push するたびに自動でデプロイされます。

### 方法 2: Wrangler CLI で直接デプロイ

```sh
npx wrangler pages deploy . --project-name=lie-group
```
