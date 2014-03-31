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
    @user ||= User.find_by(token: cookies.permanent[:token]) if cookies.permanent[:token].present?
    if @user.nil?
      @user = User.create!
      cookies.permanent[:token] = @user.token
    end
  end
end

```
