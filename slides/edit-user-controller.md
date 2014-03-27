##  ユーザコントローラの編集
<br />

```ruby
# app/controllers/users_controller.rbを次のように編集しよう

class UsersController < ApplicationController

  def get_status
    render json: @user
  end

  def update_status
    @user.update(user_params)
    render json: @user
  end

  private
    def user_params
      params.require(:user).permit(:name, :cookie, :grandma, :farm)
    end
end
```
