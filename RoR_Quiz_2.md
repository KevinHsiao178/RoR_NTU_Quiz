1. 請用簡單的方式敘述以下每一行程式碼:
  ```ruby
  a = 1
  @a = 2
  @@a = 5
  user = User.new
  user.name
  user.name = "Joe"
  ```
Ans:
  `a = 1`是宣告一個變數a並且指定他的值為1
  `@a = 2`將instance variable @a設定為2
  `@@a = 5`將class varible @@a設定為5
  `user = User.new`以User為模板建造一個名字叫user的物件
	`user.name`user物件中name欄位的getting method
	`user.name = "Joe"`user物件中name欄位的setting method
2. 什麼是 module? 請寫一段程式碼說明一個 class 要如何使用一個 module 裡面的 method?  
Ans: module就像是一個工具箱，可以被class include來使用
	```ruby
	module Knowledge
	  def math
		  puts 'I know math!'
	  end
	end
	class Engineer
	  include Knowledge
	end
	#Main code
	bob = Engineer.new
	bob.math
	```
3. 請說明 class 和 instance variable 之間的差別  
Ans: instance variable對應到每一個被create出來的object，但是class variable只會有一個，對應到class
4. 如果今天我為一個叫 User 的 class 產生一個新物件的方式是:
  ```ruby
  User.new("Bob", "male", "Engineer")
  ```
請寫出 User class 的 initialize method  
Ans:
  ```ruby
	class User
	  attr_accessor :name, :gender, :job
	  def initialize(name, gender, job)
		  @name = name
		  @gender = gender
		  @job = job
	  end
	end
  ```
5. self 在： a) class 裡，method 外面 b) class 裡，instance method 裡 分別是指向什麼?  
Ans: a)class b)instance
6. attr_accessor 的功能是什麼  
Ans: ruby自幫我們寫getter與setter，也就是說可以直接使用`bob.name`與`bob.name = "Bob"`
7. 請說明 public 和 private method 之間的不同  
Ans: public method代表公開的，所有人都看得到；private method則是只有在本身處的class內才看得到，且不能被直接呼叫，只能透過class內的其他instance method呼叫
8. Ruby 是如何確保一個 module 的 method 會被 include 它的 class 使用到？ (提示：method lookup)  
Ans: Include的module會先被找到，因為使用.ancestors會發現它夾在bclass與parent class之間