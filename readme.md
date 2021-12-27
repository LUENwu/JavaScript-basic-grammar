# JavaScript 语法基础入门级

## 1. 什么是表达式和语句?
* 表达式一般有值,如 1 + 2 叫做表达式（expression），指一个为了得到返回值的计算式.
* 语句一般会改变环境(声明,赋值),主要是进行某个操作,一般不需要返回值.
* 语句以分号结尾，一个分号就表示一个语句结束。多个语句可以写在一行内.
```
add(1,2) 表达式的值为函数的返回值,函数才有返回值.
console.log 这个表达式的值为函数本身.
console.log (3) 返回的依旧是函数本身, 3 只是打印在控制台的数字.
```
## 2. 标识符的规则
> 标识符是用来识别各种值的合法名称,最常见的标识符就是变量名与函数名.
1. 命名规则:
* 第一个字母可以是<font color =red size=3 face="黑体"> Unicode </font>字母(英文字母以及其他语言的字母),美元符号<font color =red> ($) </font>和下划线<font color =red> ( _ )</font>.
* 第二个字母及后面的,除了<font color =red size=3 face="黑体"> Unicode </font>字母(英文字母以及其他语言的字母),美元符号<font color =red size=3 face="黑体"> ($) </font>和下划线<font color =red> ( _ )</font>.还可以用数字 <font color=red size=3 face="黑体"> 0-9 </font>.
* JavaScript 有一些保留字，不能用作标识符：arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。

## 3. 条件语句 
> JavaScript 提供if结构和switch结构，完成条件判断，即只有满足预设的条件，才会执行相应的语句。  
  
###  if...else 结构
* if 结构先判断一个表达式的布尔值，然后根据布尔值的真伪，执行不同的语句。所谓布尔值，指的是 JavaScript 的两个特殊值，true表示“真”，false表示“伪”。
* 布尔值经由一个条件表达式产生的,必须房子括号内,表示求值.true则执行if里的语句,false则执行else里语句.
```
if (表达式/布尔值) {
             语句;
} else {
        语句;
}
 

if (m === 3) {
  // 满足条件时，执行的语句
} else {
  // 不满足条件时，执行的语句
}
```
JavaScript 还有一个三元运算符（即该运算符需要三个运算子）? : ，也可以用于逻辑判断。
```
(1 % 2 === 1) ? 奇数 : 偶数;

(条件) ? 表达式1 : 表达式2;
```


上面代码中，如果“条件”为true，则返回“表达式1”的值，否则返回“表达式2”的值。
## 循环语句 while for 语句:
> 循环语句用于重复执行某个操作，它有多种形式
   * While语句包括一个循环条件表达式和一段代码块，只要条件为真，就不断循环执行代码块。
```
while (条件) {
  语句;
}

var i = 1
while (i < 10) {
  console.log('i 当前为：' + i);
  i = i + 1;
}
上面的代码将循环10次，直到i等于10为止

```
* for语句是循环命令的另一种形式，可以指定循环的起点、终点和终止条件。它的格式如下。
```
for (初始化表达式; 条件; 递增表达式) {
  循环体;
}

for(var i = 1; i<10;i++){
  console.log(i)
}
```

1. 初始化表达式（initialize）：确定循环变量的初始值，只在循环开始时执行一次。
2. 条件表达式（test）：每轮循环开始时，都要执行这个条件表达式，只有值为真，才继续进行循环。
3. 递增表达式（increment）：每轮循环的最后一个操作，通常用来递增循环变量。

## 4. break 语句和 continue 语句
* break语句和continue语句都具有跳转作用，可以让代码不按既有的顺序执行。

* break语句用于跳出代码块或循环。
  
* 如果存在多重循环，不带参数的break语句和continue语句都只针对最内层循环。

```
var i = 0;

while(i < 10) {
  console.log('i 当前为：' + i);
  i++;
  if (i === 8) break;
}
上面代码只会执行8次循环，一旦i等于8，就会跳出循环。
```
```
for(var i = 0; i<10;i++){
  if (i % 2 === 0) continue;
  console.log(i)
}
上面代码只有在i为奇数时，才会输出i的值。如果i为偶数，则直接进入下一轮循环。
```
## 标签（label）
* JavaScript 语言允许，语句的前面有标签（label），相当于定位符，用于跳转到程序的任意位置，

* 标签可以是任意的标识符，但不能是保留字，语句部分可以是任意语句。

* 标签通常与break语句和continue语句配合使用，跳出特定的循环。
```
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) break top;
      console.log('i=' + i + ', j=' + j);
    }
  }
// i=0, j=0
// i=0, j=1
// i=0, j=2
// i=1, j=0

上面代码为一个双重循环区块，break命令后面加上了top标签（注意，top不用加引号），满足条件时，直接跳出双层循环。如果break语句后面不使用标签，则只能跳出内层循环，进入下一次的外层循环。
```
```
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) continue top;
      console.log('i=' + i + ', j=' + j);
    }
  }
// i=0, j=0
// i=0, j=1
// i=0, j=2
// i=1, j=0
// i=2, j=0
// i=2, j=1
// i=2, j=2
上面代码中，continue命令后面有一个标签名，满足条件时，会跳过当前循环，直接进入下一轮外层循环。如果continue语句后面不使用标签，则只能进入下一轮的内层循环。
```
资料来自 https://wangdoc.com/javascript/index.html


