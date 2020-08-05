#### 验证密码
密码长度 6-12 位，由数字、小写字符和大写字母组成，但必须至少包括 2 种字符。

#### 实例
```javascript
console.log( regex.test("1234567") ); // false 全是数字
console.log( regex.test("abcdef") ); // false 全是小写字母
console.log( regex.test("ABCDEFGH") ); // false 全是大写字母 
console.log( regex.test("ab23C") ); // false 不足6位 
console.log( regex.test("ABCDEF234") ); // true 大写字母和数字 
console.log( regex.test("abcdEF234") ); // true 三者都有
```
#### 分析方法一：

##### 一、密码长度 6-12 位，由数字、小写字符和大写字母组成

```javascript
var regex = /^[0-9A-Za-z]{6,12}$/;
``` 
##### 二、至少包括 2 种字符
数字与小写字母、数字与大写字母、小写字母与大写字母
```javascript
var regex = /((?=.*[0-9])(?=.*[a-z])|(?=.*[0-9])(?=.*[A-Z])|(?=.*[a-z])(?=.*[A-Z]))/;
``` 
##### 两者结合
```javascript
var regex = /((?=.*[0-9])(?=.*[a-z])|(?=.*[0-9])(?=.*[A-Z])|(?=.*[a-z])(?=.*[A-Z]))^[0-9A-Za-z]{6,12}$/;
``` 

#### 分析方法二：

用排除法

##### 一、密码长度 6-12 位，由数字、小写字符和大写字母组成

```javascript
var regex = /^[0-9A-Za-z]{6,12}$/;
``` 

#### 至少包括 2 种字符
不能全部都是数字，也不能全部都是小写字母，也不能全部都是大写字母.

```javascript
var regex = /(?!^[0-9]{6,12}$)(?!^[a-z]{6,12}$)(?!^[A-Z]{6,12}$)/;
```

##### 两者结合
```javascript
var regex = /(?!^[0-9]{6,12}$)(?!^[a-z]{6,12}$)(?!^[A-Z]{6,12}$)^[0-9A-Za-z]{6,12}$/;
``` 