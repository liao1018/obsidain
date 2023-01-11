#cs #front-end #html

# Tips
## HTML 限制無法縮放
```html
<meta 
	  name="viewport" 
	  content="width=device-width,  initial-scale=1.0, maximum-scale=1.0, user-scalable=0"
>
```

# input maxlength
	透過 maxlength 限制 input text 字數。
```html
<form action="/action_page.php">  
  <label for="username">Username:</label>  
  <input type="text" id="username" name="username" maxlength="10"><br><br>  
  <input type="submit" value="Submit">  
</form>
```