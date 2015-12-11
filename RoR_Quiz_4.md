1. 請說明 rails g scaffold xxx 功能的壞處為何？  
**Ans:**  
 - No data validations
 - No authentication
 - No tests
 - No style or layout
 - No real understanding

2. 若今天需要為 Project 和 Issue 這兩個 Model 建立一對多的關係，請寫出實作上所需要的 migratiion 和 model 檔案  
**Ans: **
	```ruby
	class Project < ActiveRecord::Base
		has_many :issues
	end
	```
	```ruby
	class CreateProjects < ActiveRecord::Migration
		def change
			create_table :projects do |t|
				t.string :title
				t.timestamps null: false
			end

			create_table :issues do |t|
				t.belongs_to :projects, index: true
				t.timestamps null: false
			end
		end
	end
```
3. 若今天我有以下 model 檔：
	```ruby
	class User < ActiveRecord::Base
		has_many :groups_users
		has_many :groups, through: :groups_users
	end
	```
請寫出和這個 model 檔相關連的 model 檔，以及這些 model 檔所需要的資料庫欄位  
**Ans:**
	```ruby
	class Group < ActiveRecord::Base
		has_many :groups_users
		has_many :users, through: :groups_users
	end
	
	class Participation < ActiveRecord::Base
		belongs_to :group
		belongs_to :user
	end
	```
	**User欄位：{id: integer, name: string}
	Group欄位：{id: integer, name: string}
	Participation欄位：{id: integer, user_id: integer, group_id: integer}**
	
4. 延續第3題，如果需要讓一個叫 "Bob" 的使用者產生一個名字叫做 "Rails is Fun" 的社團，應該如何在 rails console 裡實作出來？  
**Ans:**
```ruby
#在User table內創建一筆資料
> user = User.new(name: 'Bob')
> user.save
#查詢此筆資料的id
> user = User.where(name: 'Bob')
#在Group table內創建一筆資料
> group = Group.new('Fails is Fun')
> group.save
#查詢此筆資料的id
> group = Group.where(name: 'Fails is Fun')
#在Participation table內創建一筆資料(假設兩個的id都是1)
> par = Participation.new(user_id: 1, group_id: 1)
> par.save
```

5. 延續第4題，請寫一段程式碼確保使用者在建立新社團時社團名字不可以是空白，而且不能超過50個字  
**Ans:**
	```ruby
	class Group < ActiveRecord::Base
		validates :name, presence: true, length:{maxinum: 50}
	end
	```

6. 請列出兩種方法檢查在 routes.rb 裡面設定的路由  
**Ans:**  
 - Rails console下執行`rake routes`
 - 直接在browser輸入`localhost:3000/rails/info/routes`

7. 請列出在一個 rails 專案裡使用 bootstrap 套件的步驟  
**Ans:**  
 - Gemfile加入`gem 'bootstrap-sass'`後執行`bundle install`
 - 用`bundle show bootstrap`檢查
 - 在app/assets/javascripts/application.js內加入`//=require bootstrap`(在require_tree之前)
 - 在app/assets/stylesheets/application.css內加入`@import bootstrap;`並且修改副檔名為.scss

8. 請說明在 .erb 檔案裡 <%= %> 與 <% %> 這兩種 tag 的差別  
**Ans: 有等號的才會顯示在browser**