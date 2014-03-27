##  ランキングの追加
<br />

```html
<!-- app/views/welcome/index.html.erbの次の部分を編集しよう -->

<div class="right">
  <% @users.each do |user| %>
    <%= user.name %> : <%= user.cookie %>枚 <br />
  <% end %>
</div>
```
```ruby
# app/controllers/welcome_controller.rbを次のように編集しよう

class WelcomeController < ApplicationController

  def index
    @users = User.all.order('cookie DESC')
  end

end
```