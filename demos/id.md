#### 匹配id
```javascript
  <div id="container" class="main"></div>
```
分析:
使用惰性匹配: //ice 回溯
```javascript
var regex = /id="[^"]*"/
var string = '<div id="container" class="main"></div>'; console.log(string.match(regex)[0]);
// => id="container"
```