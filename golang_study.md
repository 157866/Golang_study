# Golang

[golang官网

[[Go 语言之旅 (go-zh.org)](https://tour.go-zh.org/welcome/1)



[[Go语言标准库文档中文版 | Go语言中文网 | Golang中文社区 | Golang中国 (studygolang.com)](https://studygolang.com/pkgdoc)](https://golang.org/)

## GOLang 基础



### GOLang 文件目录

> goProject\src\go_code\project01
>
> main                                    project01 下面 和package同级
>
> package

![image-20230704130401049](..\golang_study\imgs\image-20230704130401049.png)



### 第一个程序

注意：P是大写和Java不一样

> 第一个程序

```go
package main
import "fmt"

func main(){
	fmt.Println("hello")
}
```

package main 爆红   原因我修改了全局配置 GOPATH 的路径和win中不一样

解决方法

​	- go env -w GO111MODULE=auto   在 $GOPATH/src 外层且根目录有 go.mod 文件时，开启模块支持；否者无模块支持。

​	- 或者使用去修改GOPATH路径



> 通过 go build  命令对go文件进行编译，生成.exe文件    可以通过加-o来自定义文件名称但是必须以.exe来当后缀必须在win中
>
> 也可以 通过 go run来运行 .go的代码

```

D:\goProject\src\go_code\project01\main>go build hello.go

D:\goProject\src\go_code\project01\main>dir
 驱动器 D 中的卷是 新加卷
 卷的序列号是 EA5E-5E33

 D:\goProject\src\go_code\project01\main 的目录

2023/07/04  13:52    <DIR>          .
2023/07/04  13:52    <DIR>          ..
2023/07/04  13:52         1,968,128 hello.exe             # 会生成一个.exe文件可执行的
2023/07/04  13:51                68 hello.go
               2 个文件      1,968,196 字节
               2 个目录  7,793,217,536 可用字节

D:\goProject\src\go_code\project01\main>hello.exe
hello

#自定义名称
D:\goProject\src\go_code\project01\main>go build -o myCode.exe hello.go

D:\goProject\src\go_code\project01\main>dir
 驱动器 D 中的卷是 新加卷
 卷的序列号是 EA5E-5E33

 D:\goProject\src\go_code\project01\main 的目录

2023/07/04  14:19    <DIR>          .
2023/07/04  14:19    <DIR>          ..
2023/07/04  13:52         1,968,128 hello.exe
2023/07/04  13:51                68 hello.go
2023/07/04  14:19         1,968,128 myCode.exe    #成功生成
               3 个文件      3,936,324 字节
               2 个目录  7,791,247,360 可用字节
```



### GO 执行流程分析

- 如果对源码编译后，在执行，Go的执行流程如下

  -  .go文件  通过go build 来编译 生成.exe或者可执行文件  运行   结果

- 如果我们是对源码直接 执行 go run 源码， GO的执行流程如下
  - .go文件 通过 go run 结构   会隐藏编译这个过程



- 这两种运行方式的区别

1. 如果我们先编译生成了可执行文件，那么我们可以将该可执行文件拷贝到没有go开发环境的机器上，仍然可以运行

2. 如果我们是直接go run go源代码， 那么如果要在另外一个机器上这么运行，也需要go开发环境，否则无法执行。

3. 在编译时，编译器会将程序运行依赖的库文件包含在可执行文件中，所以，可执行文件变大了很多。



### GO语言开发的注意事项

1. Go源文件以"go"为扩展名。
2. Go应用程序的执行入口是main()方法。
3.  Go语 言严格区分大小写。
4.  Go方法由一条条语句构成，每个语句后不需要分号(Go语言会在每行后自动加分号),这也体现出Golang的简洁性。
5.  Go编译器是一 行行进行编译的，因此我们一行就写一条语句，不能把多条语句写在同一个，否则报错
6.  go语言定义的变量或者import的包如果没有使用到，代码不能编译通过。
7. 大括号都是成对出现的，缺一不可。



### GO语言转译字符

| GO转义字符 |                       解释                        |
| :--------: | :-----------------------------------------------: |
|     \t     |            一个制表单位，实现对齐功能             |
|     \n     |                      换行符                       |
|    \\\     |                       一个\                       |
|    \\"     |                       一个"                       |
|     \r     | 一个回车 从当前行的最前面进行输出，覆盖掉以前内容 |





### VScode 格式整理

第一种方式

> 选择需要整理格式的代码 按shift+tab  全体向左移动 然后按tab进行首行缩进

```go
package main
import "fmt"

func main(){
    fmt.Println("hello")
    fmt.Println("hello")
    fmt.Println("hello")
    fmt.Println("hello")
}
```



第二种方式

  ​	使用gofmt -w 来进行格式化

```
D:\goProject\src\go_code\project01\main>gofmt -w hello.go
```



行长约定：

​			一行最长不超过80个字符，超过的请使用换行展示，





### 变量

> 变量是程序的基本组成单位



- 概念

  变量相当于内存中一个数据存储空间的表示，你可以把变量看做是-一个房间的门牌号，通过门牌号我们可以找到房间，同样的道理，通过变量名可以访问到变量(值)。

  

-   变量使用的基本步骤

    1.声明变量(有人也叫: 定义变量)
    2.赋值
    3.使用



- 案例

```go
package main

import "fmt"

func main(){
	// 定义一个i
	var i int 
	// 给i赋值
	i = 20
	// 打印出值
	fmt.Println(i)
}
```





1变量表示内存中的一个存储区域

2该区域有自己的名称 (变量名)和类型(数据类型)

3 Golang变量 使用的三种方式

1. 第一种:指定变量类型，声明后若不赋值，使用默认值

   ```
   package main
   import "fmt"
   func main(){
   // 第一种:指定变量类型，声明后若不赋值，使用默认值
   	var  i int
   	fmt.Println("i=", i)   // i = 0
   }
   ```

   

2. 第二种:根据值自行判定变量类型(类型推导)中

   ```
   	// 第二种:根据值自行判定变量类型(类型推导)中
   	var n = 10.1  //会根据你的值来推到这个类型
   	fmt.Println("n=", n)
   ```

   

3. 第三种:省略var, 注意:=左侧的变量不应该是已经声明过的，否则会导致编译错误

```
	// 第三种:省略var, 注意:=左侧的变量不应该是已经声明过的，否则会导致编译错误
	name := "wmt"   // 等价于 var name string = "wmt"
	fmt.Println("c=", name)    
```



4.多变量声明
   在编程中，有时我们需要一次性声明多个变量，Golang也提 供这样的语法

```go
package main
import "fmt"
func main(){
	//    在编程中，有时我们需要一次性声明多个变量，Golang也提 供这样的语法
	var a, b, c int
	fmt.Println(a, b, c)
    
    // 声明多种方式并赋值
	var name, age, sex = "王孟涛",  18, "男"
	fmt.Println(name, age, sex)
    
   // 第三种声明多种变量的方式
	cid, uid, tid := 1, 2, 3
	fmt.Println(cid, uid, tid)

}
```



5.全局变量

> 在main 方法上面声明全局变量

```go
package main
import "fmt"

//声明全局变量
var n1 = "n1"
var n2 = "n2"
//第二种方式
var (
	n3 ="n3"
	n4 ="n4"
)

func main(){
	// 全局变量 
	fmt.Println("n1=", n1,"n2=", n2,"n3=", n3,)
}
```



6. 该区域的数据值可以在同一类型范围内不断变化

7. 变量在同一个作用域内不能重名

8. 变量=变量名+值+数据类型，  这一点请大家注意。
9. Golang的变量如果没有赋初值，编译器会使用默认值,比如int默认值0 string默认值为空串





#### Go变量的数据类型

- 小tips
  - go中使用的是UTF-8的格式   一个汉字占3字节
  - 整型前面加u是无符号的整型可以存放更多

![image-20230706210653726](.\imgs\image-20230706210653726.png)



##### 整型



######  有符号的int

> 代表有符号的int类型  所以会比无符号的int少保存一些

```go
package main
import "fmt"
func main(){ 
	// 基础数据类型 int8  8代表8位=1字节 因为int代表是有符号的8位 第一位表示正数还是负数 0代表正数 1代表负数 因为从0开始所以要减一是127  范围是 -128~127
	var num1 int8
	var num2 int16 //有符号的int16
	var num3 int32 //有符号的int32
	var num4 int64 //有符号的int64
	num1 = -128
    fmt.Println(num1, num2, num3, num4)
}
```



###### 无符号的int

> 无符号的int就代表为正数

```go
	// 无符号类型uint8 8代表8位 1字节 第一位不代表字符所以8位都可以装所以是 0~255
	var num1 uint8   //uint16 uint32 uint64
	num1 = 255
	fmt.Println("num1=", num1) //输出 255
```



###### int其它数据类型的使用



![image-20230707084747212](.\imgs\image-20230707084747212.png)



###### 整型使用的细节

1. Golang各整数类型分:有符号和无符号，int uint的大小和系统有关。

2. Golang的整型默认声明为int型

   ```
   	// 如何查看一个数据的类型
   	var num int = 127
   	// %T  指的是type int的大小是根据你操作系统的大小来的如果你是32位操作系统 这个int的大小就是int32 如此类推
   	fmt.Printf("num 的类型是 %T", num)
   ```

   

3. 如何在程序查看某个变量的字节大小和数据类型(使用较多)

   ```go
   	var num int8 = 127	
   // 如何查看这个数据占用的字节数 %d是一个整数的占位符 unsafe.Sizeof的返回值是一个字节 不是位  需要导入一个unsafe的包
   	fmt.Printf("    num 的字节大小是 %d", unsafe.Sizeof(num))  //8
   ```

   

4. Golang程序中整型变量在使用时，遵守保小不保大的原则，即:在保证程序正确运行下，尽量使用占用空间小的数据类型。 [如:年龄]

   ```go
   	// byte 0~255
   	var age byte
   	age = 100
   	fmt.Print(age)
   ```

   

5. bit: 计算机中的最小存储单位。byte:计算机中基本存储单元。[二进制再详细说]1byte= 8 bit 



##### 浮点类型 

> 创建一个浮点类型



```go
package main

import (
	"fmt"
	"unsafe"
)

func main() {
	// 创建一个单精度
	var price float32 = 38.88
	//  输出price 的类型是 float32 price的所占的字节是 4
	fmt.Printf("price 的类型是 %T price的所占的字节是 %d", price, unsafe.Sizeof(price))
}

```









###### 浮点数分类

>  分为单精度和双精度

![image-20230707093801382](.\imgs\image-20230707093801382.png)

对上图说明：

- 关于浮点数在机器中存放的简单说明，浮点数= 符号位 + 指数位 + 尾数位        说明：浮点数都是有符号的

```go
	// 创建一个有符号的单精度和双精度
	var float1 float32 = -0.147
	var float2 float64 = -84884.154
	// 输出结果float1 = -0.147 float2 = -84884.154
	fmt.Println("float1 =", float1, "float2 =", float2)
```

- 尾数位可能丢失，造成精度损失，比如 -1247.000000000123

```go
	var float3 float32 = -1247.000000000123
	var float4 float64 = -1247.000000000123
	// 输出的结果为 float3 = -1247
	fmt.Println("float3 =", float3)
	// 输出结果float4 = -1247.000000000123
	fmt.Println("float4 =", float4)
```

  说明：

	 	1. 浮点型存数字可能会造成精度丢失
   	 	2. float64 要比 float32 要准确
   	 	3. 如果我们需要保存一个精度比较高的数，则应该选择用float64





###### float 的使用细节

1. Golang 浮点类型有固定的范围和字段长度，不受具体OS(操作系统)的影响，不像int类型如果操作系统为32位那么int类型的是4字节
2. Golang的浮点类型默认声明长度为float64类型
3. 浮点类型常量有两种表示形式
   1. 十进制数形式：如 5.12    .512   .512 是 0.512的简写 **必须要有小数点**
   2. 科学计数法形式： 如 5.1234e2 = 5.12 * 10的2次方   5.12E-2 = 5.12 / 10的2次方
4. 通常情况下，应使用float64 因为它比float32更精确



##### 字符类型

- 基本简绍

  Golang中**没有专门的字符类型**，如果要存储单个字符(字母)，一般使用byte来保存。字符串就是一串固定长度的字符连接起来的字符序列。Go的字符串是由单个字节连接起来的。也就是说对于传统的字符串是由字符组成的，**而Go的字符串不同，它是由字节组成**的。[官方将string归属到基本数据类型. https://tour.go-zh.org/basics/11 ]



###### 字符型的使用

> 如果保存的ASCII码中是数据可以直接使用byte来保存     

```go
package main

import "fmt"

func main() {
	//字符型的使用
	var c1 byte = 'a'
	var c2 byte = '1'
	//输出的结果是 以ASCII码输出 c1 =  97 c2=  49
	fmt.Println("c1 = ", c1, "c2= ", c2)
	// 输出： c1 =a c2 = 1  表示以char字符输出
	fmt.Printf("c1 =%c c2 = %c \n", c1, c2)

	// 汉字不能使用byte来保存
	//var c3 byte = "王" //untyped string constant
	var c3 int = '王' //必须是单引号
	// %c以字符输出   %d以对于的编码值输出
	// 输出：c3=王 c3 的对应的编码值为 29579
	fmt.Printf("c3=%c c3 的对应的编码值为 %d", c3, c3)
}

```



###### 字符类型使用细节

1. 字符常量是用单引号(")括起来的单个字符。例如: var c1byte= 'a' var c2 int='中' var c3 byte= '9'

2. Go中允许使用转义字符\'来将其后的字符转变为特殊字符型常量。例如: var c3 byte= '\n' // '\n'表示换行符

   ```go
   	// byte 转义字符   \n换行
   	var conversion byte = '\n'
   	// 输出 111111
   	//      2222
   	fmt.Printf("111111%c2222", conversion)
   ```

   

3. Go语言的字符使用UTF-8编码  **英文字母1个字节汉字3个字节**

4. 在Go中，字符的本质是一个整数，直接输出时，是该字符对应的UTF-8编码的码值。

5. 可以直接给某个变量赋一个数字，然后按格式化输出时%c会输出该数字对应的unicode字符

   ````go
   	// 1. 可以直接给某个变量赋一个数字，然后按格式化输出时%c会输出该数字对应的unicode字符
   	var c4 int = 247
   	// 输出： c4 =÷
   	fmt.Printf("\n c4 =%c", c4)
   ````

   

6. 字符类型是可以进行运算的，相当于一个整数，因为它都对应有Unicode码.

   ```go
   	// 2. 字符类型是可以进行运算的，相当于一个整数，因为它都对应有Unicode码.   ASCII 码 a=97
   	var c5 int = 'a' - 30
   	// 输出 67
   	println("c5=", c5)
   ```





###### 字符类型的讨论

1. 字符型存储到计算机中，需要将字符对应的码值(整数)找出来
   	存储:字符-->对应码值---> 进制->存储
   	读取:二进制-->码值---> 字符->读取
2. 字符 和码值的对应关系是通过字符编码表决定的(是规定好)
3.  Go语 言的编码都统一成了utf-8。非常的方便，很统一，再也没有编码乱码的困扰了



##### 布尔类型 bool



p43



### GoLang 指针



1. 基本数据类型，变量存的就是值，也叫值类型
   获取变量的地址，用&，比如:
   var num int,获取num的地址: &num
   指针类型，变量存的是-一个地址，这个地址指向的空间存的才是值
   比如: var ptr *int = &num
   获取指针类型所指向的值，使用: *，比如:
   var
   r *ptr int, 使用*ptr获取p指向的





#### 导包问题

sdk版本： 1.20版本

> 问题描述导包找不到路径

1.在dos命令中 修改 go env

```
C:\Users\34912>go env
set GO111MODULE=on  // 把修改成 off
```

​	修改 go env -w GO111MODULE=on

```
C:\Users\34912>go env set GO111MODULE=off  // 把修改成 off
```





