##  見た目の作成
<br />

```html
<!-- app/views/welcome/index.html.erbを次のように編集しよう -->

<div class="left">
  <strong>
    <input type=text id="name" value="">
  </strong>のクッキークリッカー！
  <br />
  <br />
  <%= image_tag("cookie.png", id: "cookie_button") %>
  <br /><br />
  クッキー: <strong><span id="cookie"></span></strong>
  <br />
</div>
<div class="middle">
  <ul>
    <li>おばあさん: <strong><span id="grandma">0</span></strong></li>
    <li>工場: <strong><span id="farm">0</span></strong></li>
  </ul>
  <button id="buy_grandma">おばあさんを購入(100枚)</button>
  <button id="buy_farm">工場を購入(1000枚)</button>
</div>
<div class="right">
</div>
```
