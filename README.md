# リー群を体感する

リー群(Lie group)をインタラクティブな可視化で学ぶ静的 Web ページです。
依存ライブラリなしの単一 `public/index.html` で構成され(黒背景・モノクロのシンプルなデザイン)、
Cloudflare Workers の静的アセット機能でデプロイします。

## 内容

1. **SO(2)** — 回転行列をスライダーで動かし、合成が角度の足し算になることを確認
2. **リー環と指数写像** — 接線(リー環)が円周(リー群)に巻き付く様子と、行列指数関数の級数の収束
3. **SO(3) の非可換性** — 回転の順序で結果が変わることを立方体のアニメーションで比較(自由回転も可)
4. **SU(2) と二重被覆** — 360° 回しても戻らない SU(2) の元を 0°→720° で追う

## ローカルで見る

```sh
# Wrangler のローカル開発サーバー(本番と同じ配信挙動)
npx wrangler dev
# または任意の静的サーバーで public/ を配信
python3 -m http.server -d public
```

## Cloudflare Workers へのデプロイ

設定は `wrangler.jsonc` にあります。Worker スクリプトは不要で、`public/` を
静的アセットとして配信する「アセットのみの Worker」構成です。

### 方法 1: Wrangler CLI で直接デプロイ

```sh
npx wrangler login   # 初回のみ
npx wrangler deploy
```

`https://lie-group.<アカウント名>.workers.dev` に公開されます。

### 方法 2: Git 連携(Workers Builds)

1. [Cloudflare ダッシュボード](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Workers** → **Import a repository**
2. このリポジトリを選択
3. ビルドコマンドは空のまま、デプロイコマンドに `npx wrangler deploy` を指定
4. **Save and Deploy**

以後、main に push するたびに自動でデプロイされます。
