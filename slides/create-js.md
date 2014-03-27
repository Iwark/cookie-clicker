##  動きを作ろう！

<br />

```javascript
// app/assets/javascripts/application.jsに追記しよう

$(function(){
  name = "名無しさん"; //名前
  cookie = 0;        //クッキーの数
  grandma = 0;       //おばあちゃんの数
  farm = 0;          //工場の数
  count = 0;         //起動してからの時間(0.1秒単位)
  power = 0;         //0.1秒に増えるクッキーの数

  //データベースからユーザーのデータを取得
  $.ajax({
    url: "users/get_status",
    type: "GET",
    data: null,
    dataType: "json",
    success: function(data) {
      name = data["name"];
      cookie = data["cookie"];
      grandma = data["grandma"];
      farm = data["farm"];
      $('#name').val(name);
    },
    error: function(data) {
      alert("エラー。リロードしてください。");
    }
  });

  //クッキーを押した時の処理
  $('#cookie_button').click(function(){
    $("#cookie_button").animate({"margin-left": "+=5px", "opacity": "-=0.1"}, "fast",function(){
      $("#cookie_button").animate({"margin-left": "-=5px", "opacity": "+=0.1"}, "fast");
    });
    cookie += power;
  });

  //時間ごとにクッキーが増える処理。
  setInterval(function(){
    $('#cookie').text(cookie);
    $('#grandma').text(grandma);
    $('#farm').text(farm);
    if(count%50 == 0){
      sendData();
    }
    power = 1 + grandma + farm*11;
    cookie += power;
    count += 1;
  },100);

  //「おばあちゃん」の購入
  $('#buy_grandma').click(function(){
    if(cookie <= 100){
      alert("クッキーが足りません");
      return;
    }
    cookie -= 100;
    grandma += 1;
    sendData();
  });
  //「工場」の購入
  $('#buy_farm').click(function(){
    if(cookie <= 1000){
      alert("クッキーが足りません");
      return;
    }
    cookie -= 1000;
    farm += 1;
    sendData();
  });

  //サーバーにデータを送信する
  function sendData(){
    $.ajax({
      url: "users/update_status",
      type: "PATCH",
      data: {
        user: {
          name: $('#name').val(),
          cookie: cookie,
          grandma: grandma,
          farm: farm
        }
      },
      dataType: "html",
      success: function(data) {
      },
      error: function(data) {
        alert("エラー。リロードしてください。");
      }
    });
  }

});
```

