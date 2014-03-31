##  トークンの設定

<br>
ログインに使うトークンは、ユーザーの作成時に<br>
自動的に設定するようにする。<br>
<br>

```ruby
# app/models/user.rbを次のように編集する

class User < ActiveRecord::Base
  before_create :set_token

  def set_token
    self.token = Digest::SHA1.hexdigest("#{id}#{rand.to_s}")[0..15]
  end
end
```