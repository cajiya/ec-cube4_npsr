# EC-CUBE4.x用 新着情報一覧／詳細ページ生成プラグイン

EC-CUBEデフォルトの「新着情報」の、一覧／詳細URLを生成する。

## 生成されるURL

`{$your_site_address}/news` // 新着情報一覧ページ

`{$your_site_address}/news/{$news_id}` // 新着情報詳細ページ

# インストール方法

```
cd app/Plugin;
git clone https://github.com/cajiya/ec-cube4_news-pages.git;
mv ec-cube4_news-pages NewsPages;
cd ../../;
php bin/console eccube:plugin:install --code="NewsPages"
```

# 開発作業時の注意事項

通常、ファイルの編集時のキャッシュクリアは
```
php bin/console cache:clear --no-warmup 
```
で問題ない。
だが、TwigファイルはPlugin有効化時に、
`app/template/`に編集用ファイルを生成しているので、
これらのファイルも削除をする必要がある。

直接削除を行っても問題ないが、Pluginの無効化(disable)時に、
`app/template/`内のファイルを削除する処理をしているので、以下コマンドの実行でも削除可能。

```
php bin/console eccube:plugin:disable --code="NewsPages"
php bin/console eccube:plugin:enable --code="NewsPages"
```
