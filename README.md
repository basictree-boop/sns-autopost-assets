# sns-autopost-assets

`basictree-boop/sns-autopost`（Private）が投稿に使う画像の置き場。

## なぜ別リポジトリで、なぜPublicなのか

Threads の API は画像を**公開URLでしか受け取らない**（認証が必要なURLは拒否される）。
本体の `sns-autopost` は Private なので `raw.githubusercontent.com` から取得できない。
そのため画像だけをここに置き、raw URL を Threads に渡している。

Threads は投稿時に画像を自分側へ複製するので、URLが必要なのは投稿の瞬間だけ。

## 置いてよいもの / いけないもの

置いてよいのは**情景写真だけ**。人物・文字・ロゴが写っていないものに限る。

置かない:

- 投稿本文、アフィリエイトリンク、商品情報
- 家族の写真、実名、住所が分かるもの
- 認証情報（このリポジトリはPublic。誰でも読める）

## 中身

```
rakuten/
  pool/        投稿画像プール。ジャンル・季節のタグは本体側の
               channels/rakuten/data/image_pool.yaml が持つ
```

画像の登録は手で置かず、本体リポジトリの
`python -m rakuten.tools.add_pool_image` から行う（マニフェストと同時に更新するため）。
