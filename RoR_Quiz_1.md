1. 請說明 Fixnum (整數) 和 Float (浮點數) 之間的差異  
**Ans: 使用在除法上會有差異，Fixnum無法被整除**

2. 今天有兩個字串：
  ```ruby
  str1 = "Hallo Welt!"
  str2 = "NTU Rails 261!"
  ```
請說明以下兩個印出字串的方式的不同處：
  ```ruby
  puts str1 + str2
  puts "#{str1}#{str2}"
  ```
**Ans: str1 + str2會造成記憶體的浪費(電腦會要先開一個記憶體儲存str1 + str2)**

3. 請解釋 array 和 hash 的不同處  
**Ans: Array是排序的，每個值都有對應的index；Hash是一對一對的，並且用key對應**

4. 請寫一段 code 從 [1, "a string", 3.14, [1,2,3,4]] 這個陣列找出所有非字串的值  
**Ans: Arr.reject{|x| x.class == String}**

5. 請列出兩種產出亂數的方法  
**Ans: rand(1..9) or (1..9).to_a.shuffle.last**

6. 請把 lesson1 程式碼裡的 calculator.rb 裡面的使用者輸入兩個數字的方式改寫成 method，並要有防止使用者亂輸入值的功能  
**Ans: 先從String增加一個方法，使Ruby可以判斷string是否為float:**
  ```ruby
  class String
	  def is_number?
		true if Float(self).rescue false
	  end
  end
  ```
**然後再加入**
	```ruby
	def user_input
	  begin
	    puts "please enter the first number:"
	    num1 = gets.chomp
	  end until num1.is_number? == true
	  Float(num1)
	end
	```

7. 以下這段程式碼：
	```ruby
	  ((1 > 3)&&(true == true))||(!!!false)
	```
  會執行出什麼結果？ 請試試不用 irb 算出結果  
**Ans: True**

8. 請問 binding.pry 是什麼？ 要如何使用它？  
**Ans: Debug用的，在code上方require “pry”，接下來只要在想要看程式執行狀況的地方加入binding.pry；接下來執行程式，程式跑到這個地方的時候就會進入debug的模式**

9. 下面的一段程式碼，請嘗試用其他方法把 if...else...end 簡化成一行
	```ruby
	var = 5
	if var >= 5
		return "var is greater than or equal to 5"
	else
		return "var is less than 5"
	end
	```
**Ans:**
	```ruby
	return var>=5 ?  “var is greater than or equal to 5” : ” var is less than 5”
	```
