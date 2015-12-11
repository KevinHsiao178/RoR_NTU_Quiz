1. 請解釋 `database.yml`, `routes.rb`, 和 `Gemifle` 分別是什麼？ 他們分別在一個 Rails 專案裡的什麼位置？ 他們為什麼對一個 Rails 專案如此重要？  
**Ans:  
`database.yml`在Config內,是紀錄設定Database的地方，分別在開發、測試、推上雲端時  
`routes.rb`在Config內,設定此Rails專案的路由  
`Gemifle`在根目錄內，記錄所有此Rails專案會用到的gem，可以紀錄使用那些library，另外當Rails版本異動時，也可以輕易地用bundle install來取得需要的gem**

2. MVC 架構裡的 M, V, 和 C 分別代表什麼？  
**Ans: Model(分別對應到不同的Table，放商業邏輯的地方), View, Controller(處理前端的request)  
(Rule: Skinny controller, fat model)**

3. 請解釋 CRUD 是哪四個字的縮寫？  
**Ans:Create, Read, Update, Delete**

4. 請問在 routes.rb 裡面加入以下程式碼會產生出哪一些 url？ (提示：在 browser 輸入`http://localhost:3000/rails/info/routes`)
	```ruby
	resources :users
	```
**Ans:可以對資料庫進行CRUD的動作**

5. 請解釋 model 檔案和 migration 檔案的差別  
**Ans:model是對應到資料庫的資料表；而migration是紀錄資料庫內table, column...等等的任何變動**

6. 若今天發現一個 migration 檔寫錯，請問我應該用什麼指令回復到上一個版本的 migration?  
**Ans:可以用`rake db:rollback`但是不建議這麼做；最保險的作法是再create一個migration file進行修復，這樣會免去可能造成co-worker麻煩的機會**

7. 假設今天
 - 我要在資料庫裡產出一個叫 group 的資料表
 - 裡面包括的欄位名稱和相對應的資料型別是： name (string), description (text), members (integer)
 - 請寫出一個能產生出以上需求的 migration檔  
**Ans:**`rails g migration CreateGroups name:string, description:text, members:integer`

8. 請解釋什麼是 ActiveRecord?  
**Ans:用Ruby語法進行對資料庫的操作(一般需要用SQL語法才能做到的事), ActiveRecord會自動翻譯成SQL語言,他就是Rails的ORM**
