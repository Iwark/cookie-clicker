##  デフォルト値の設定
<br />
名前などのデフォルト値を設定する<br />
<br />
```ruby
# db/migrate/2014xxxxx.rbを編集(xxxxは人によって異なる！)
class CreateUsers < ActiveRecord::Migration
  def change
    create_table :users do |t|
      t.string :name, default: '名無しさん'
      t.integer :cookie, default: 0
      t.integer :grandma, default: 0
      t.integer :farm, default: 0

      t.timestamps
    end
  end
end
```