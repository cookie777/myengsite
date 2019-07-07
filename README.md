# myengsite
 * Website for improving my English writing
 * using hugo


## テーマの改造
 * hydeを使用
 * .gitを削除（二重管理をふせぐため）
 * 日本語のフォントをきれいに魅せるためhyde.cssを修正

全体のフォント
```css
html {
  /* font-family: "PT Sans", Helvetica, Arial, sans-serif; */
  font-family: "PT Sans", Helvetica, Arial, sans-serif, 'Hiragino Kaku Gothic Pro','ヒラギノ角ゴ Pro W3','メイリオ',Meiryo,'ＭＳ Ｐゴシック',sans-serif;
}
```
タイトルのフォント(サイドバーの見出し)
```css
/* About section */
.sidebar-about h1 {
  color: #fff;
  margin-top: 0;
  /* font-family: "Abril Fatface", serif; */
  font-family: "PT Sans", Helvetica, Arial, sans-serif, 'Hiragino Kaku Gothic Pro','ヒラギノ角ゴ Pro W3','メイリオ',Meiryo,'ＭＳ Ｐゴシック',sans-serif;
  font-size: 3.25rem;
}
```

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