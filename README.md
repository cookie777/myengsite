# Myengsite
 * Website for improving my English writing
 * using hugo


# Hugo command
```bash
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo rver --bind=0.0.0.0 -w --disableFastRender -D
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo w posts/prectice-04.md
```

# Customized history

## Initalized
 * hydeを使用
 * .gitを削除（二重管理をふせぐため）

## Modified fonts
 * add webfont in head_fonts.html
  ```html
    <link href="https://fonts.googleapis.com/css?family=Lato:400,700|Noto+Sans+JP:400,700" rel="stylesheet">
  ```

 * changed font_family in hyde.css (2 places)
```css
font-family: 'Lato', 'Noto Sans JP', '游ゴシック Medium', '游ゴシック体', 'Yu Gothic Medium', YuGothic, 'ヒラギノ角ゴ ProN', 'Hiragino Kaku Gothic ProN', 'メイリオ', Meiryo, 'ＭＳ Ｐゴシック', 'MS PGothic', sans-serif;
```

## [Add SNS share buttons](http://hugocodex.org/add-ons/share-buttons/)
 * Step 1. Download the file share-buttons.html 
 * Step 2. Save the file in the ‘layouts/partials’ directory of your project 
 * Step 3. Add the following line to your layout on the place where you want the share buttons to appear:
```hugo
{{ partial "share-buttons.html" . }}
```
 * This time, I added in `single.html`
 * Disable(comment out) all buttons except twitter in `single.html`

## SEO関係

### 著者、サイト説明、キーワード追加

config.tomlに以下を追加
```toml
[params]
author = "著者"
keywords = ["ここに キーワード","追加"]
description = "説明"
```
head.html系などテーマのmetaを記述している部分に以下を追加
```html
  <meta name="author" content="{{.Site.Params.Author }}">
  <meta name="description" content="{{ .Site.Params.description }}">
  <meta name="keywords" content="{{ delimit .Site.Params.Keywords ", " }}" >
```