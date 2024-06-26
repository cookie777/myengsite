# Myengsite
 * Hugo blog of my daily routine note


# Hugo command
```bash
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo server --bind=0.0.0.0 -w --disableFastRender -D
docker run --rm --name hugo -v %cd%:/home/ -it -p 1313:1313 japer/hugo hugo new posts/toefl-activity-school.md
docker run --rm --name hugo -v $(pwd):/home/ -it -p 1313:1313 japer/hugo hugo new posts/activity-log-sample.md
```
docker run --rm --name hugo -v $(pwd):/home/ -it -p 1313:1313 japer/hugo hugo
docker run --rm --name hugo -v $(pwd):/home/ -it -p 1313:1313 japer/hugo hugo server --bind=0.0.0.0 -w --disableFastRender -D
# Customized history
ここにはTIPSより具体的にやった内容だけ記述
## Initalized
 * hydeを使用
 * .gitを削除（二重管理をふせぐため）

## Modified fonts
### main font
 * add webfont in head_fonts.html
  ```html
    <link href="https://fonts.googleapis.com/css?family=Lato:400,700|Noto+Sans+JP:400,700" rel="stylesheet">
  ```

 * changed font_family in hyde.css (2 places)
```css
font-family: 'Lato', 'Noto Sans JP', '游ゴシック Medium', '游ゴシック体', 'Yu Gothic Medium', YuGothic, 'ヒラギノ角ゴ ProN', 'Hiragino Kaku Gothic ProN', 'メイリオ', Meiryo, 'ＭＳ Ｐゴシック', 'MS PGothic', sans-serif;
```
### discripsion font
`pool.css` font-size: 1.0rem;

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

### ogp設定
config.tomlに以下を追加
```toml
[params]
ogp_thumb = "images/ogp_thumb.jpg" #thumb用の画像
```

head.html系などテーマのmetaを記述している部分に以下を追加
```html
  {{ if .IsHome -}}
  <meta property="og:url" content="{{.Site.BaseURL}}" />
  <meta property="og:type" content="website" />
  <meta property="og:title" content="{{ .Title }}" />
  <meta property="og:description" content="{{ .Site.Params.description }}" />
  <meta property="og:site_name" content="{{ .Site.Title }}" />
  <meta property="og:image" content="{{ .Site.BaseURL }}{{ .Site.Params.ogp_thumb }}" />
  {{- else -}}
  <meta property="og:url" content="{{ .Permalink }}" />
  <meta property="og:type" content="article" />
  <meta property="og:title" content="{{ .Title }}" />
  <meta property="og:description" content="{{ .Site.Params.description }}" />
  <meta property="og:site_name" content="{{ .Site.Title }}" />
  <meta property="og:image" content="{{ .Site.BaseURL }}{{ .Site.Params.ogp_thumb }}" />
  {{- end }}
```
### ogp:twitter 設定
* head.html系などテーマのmetaを記述している部分に以下を追加
* 注意点： 画像のurlは絶対パスにすること
  <meta name="twitter:card" value="summary_large_image"/>
  <meta name="twitter:site" value="{{ .Site.Params.twitter_auther }}" />
  <meta name="twitter:creator" value="{{ .Site.Params.twitter_auther }}" />
  <meta name="twitter:title" value="{{ .Title }}"/>
  <meta name="twitter:description" value="{{ .Site.Params.description }}"/>
  <meta name="twitter:image" value="{{ .Site.BaseURL }}{{ .Site.Params.ogp_thumb }}" />

## shortcode
### youtube
```html
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/{{ index .Params 0 }}?start={{ index .Params 1 }}" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border:0;" allowfullscreen title="YouTube Video"></iframe>
</div>
```


## Modified basic setting
* change default.md 
  > title: "My activity as for TOEFL;  {{ dateFormat "1/2/2006" .Date }}"
* summary size 
https://hugo.nakaken88.com/master/summaries/
```yml
hasCJKLanguage = true # 日本語で単語カウントが認識される
summaryLength = 20
```
