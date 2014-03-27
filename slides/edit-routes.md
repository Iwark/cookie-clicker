##  ルーティングの設定
<br />
作ったコントローラのアクションへのルートを設定する<br />
<br />

```ruby
# config/routes.rbを以下のように編集する

CookieClicker::Application.routes.draw do
  get "users/get_status"
  post "users/update_status"
  get "welcome/index"
  root 'welcome#index'
end
```