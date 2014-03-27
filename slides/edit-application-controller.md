##  ログインの仕組み

<br />

アクセスと同時にログイン / ユーザ作成を<br />
自動的に行うようにする。

<br />
```ruby
# app/controllers/application_controller.rbを次のように編集しよう

class ApplicationController < ActionController::Base
  protect_from_forgery with: :exception
  before_action :login_user

  private
  def login_user
    @user ||= User.find(session[:user_id]) if session[:user_id].present?
    if @user.nil?
      @user = User.create!
      session[:user_id] = @user.id
    end
  end
end

```
