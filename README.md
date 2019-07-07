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