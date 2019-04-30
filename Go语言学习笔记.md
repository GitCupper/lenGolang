# <center>Go语言学习笔记</center>


## 前言

前两天忙里偷闲将第五版《Go学习笔记》上下册合并，预备交给出版社编辑。不经意扫了一眼更新记录，才发觉四年光阴悄然而过。不知从何时起，岁月流逝的速度越来越快，抓不得，留不住。

我很擅长坚持，不知是因为笨，还是性情迟钝的缘故。在给编辑写作者简介时，我努力回忆自己最近二十年的经历，好像除了些纷扰的人和事外，就是一段段在不同技术圈子里日夜探索的记忆，历久弥新。

现在带了些学生，每每交流时，总偷偷庆幸自己是个先行者，没有互联网的“黑暗时代”反而造就了踏实的基础，远不是现今乱花迷眼的境况。看着他们对于具体实现“懵懂无知”的表现，我对于写书这事就愈发虔诚，生怕误了人的光阴和热情。似乎《学习笔记》这个名字才是最好的诠释，立不得案头，权作闲书，稍能观感一二即可。

因喜爱C，故对Go关注得很早。观望良久，终究受不住诱惑，一头栽了进去。边学边记，于是有了最早的《学习笔记》。办因错漏过多，发到某论坛着实没砸出什么水花来。此后，对于宣传也谈了心思，再不原出去，只自己默默更新，或发到微博，给一些熟识尚惦记这事的人打个招呼。

某日，一编辑发来消息，询问我是否出版，才悄然知道这书原也是可印的，好像自己从没想过。犹豫再三，且将几本笔记从GitHub下架。只可惜，因某些理念不同，最终未能如愿，这一拖就是许多时日。

去年受老谢的邀请，前往上海参加Gopher China大会。期间多次被问及何时能有实体书出版，熄了许久的心思方又活过来。年中，重新写了书稿，年底几乎又重来一遍，心底对于出书总有些忐忑。走到圣诞节，才放了下册出来。幸好，并没有人出来指责我粗制滥造，方得心安。

我儿小乘还太小，于是我猴年我一个回老家过年。也许是在外面太久，对搬进城里的老家全然陌生，每日里除了陪父母吃饭外，其他时间都用来写上册书稿。偶尔透过窗看见远处的山影，才找回些幼时记忆。书写得意外顺利，即便网络不算通畅也未能影响到我。回京路上，我彻底写了主意，准备交付出版。

节后忙于培训一事，书稿校对稍稍拖后了些。边按章节调整，边请群里的伙伴们帮忙审校，所幸赶在戴上日期前完成。样稿交到编辑手里，虽尚有些收尾工作，但总算能放轻松些。这于我是个解脱，困于此的心思总算少了一大半。

依惯例，需在此感谢很多人。其中自然少不了对我多加鼓励的家中太上领导和惦记良久的网络众位大仙们。当然，最需感谢的是群里帮忙校对的小伙伴们，有溺水的鱼、大内总管、starchou、老虎、日下、小E、春婶、奋斗娃等等。

#### 读者定位
本书并不适合用作编程初学者入门，因内容和文体都太过简练了些。我厚脸推荐给有实际经验或正用Go工作的人群，可于路途中当闲书翻看几页。

#### 联系方式
鉴于能力有限，书中难免错漏。如您看到任何问题，请与我联系，以便更正。谢谢！
- 微博：weibo.com/qyuhen
- 邮件：qyuhen@hotmail.com
- 社区：qyuhen.bearychat.com

<p align="right">雨痕</p>
<p align="right">二〇一六年春</p>


## 目录

## 第1章  概述
对我而言，Go是一门很有意思的编程语言。虽算不得优雅，但也不浅薄。自C一脉相承，又吸收了些时髦的东西。最重要的是，它依旧简单。我喜欢简单，平日里也是竭尽所能将复杂的东西简单化。

有关Go的宣传语已经太多，优点或缺点都能罗列出长长的清单。我甚至不知道该如何做才能堆砌出本章内容，所以一直拖到全书的最后才去完成。

### 1.1 特征
我产不想，似乎也没资格为Go增添什么新的荣誉。在些仅从这几年的使用经验说说个人看法，一如书名《学习笔记》那样。

#### 语法简单
抛开语法样式不谈，单就类型和规则而言，Go与C99、C11相似之处颇多，这也是我能接受它被冠以“NextC”名号的重要原因。

即便我是个坚定的C拥趸，也不得不承认，它处于简单和复杂的两极。C简单到你每写下一行代码，都能在脑中想象出编译后的模样，指令如何执行，内存如何分配，等等。而C的复杂在于，它有太多隐晦而不着边际的规则，着实让人头疼。相比较而言，Go从零开始，没有历史包袱，在汲取众多经验教训后，可从头规划一个规则严谨、条理简单的世界。

人们习惯拿关键字和控制语句的数量为作为Go简单的例证，我倒觉着这并不合适。诚然，更小的语言规则有助于入门学习，这无可厚非。但更重要的在于，语言规则严谨，没有歧义，更没什么黑魔法变异用法。任何人写出的代码都基于一致，这才是简单的本质。放弃部分“灵活”和“自由”，换来更好的维护性，我觉得是值得的。

将“++”、“--”从运算符降级为语句，保留指针，但默认阻止指针运算。初时的不习惯，并不能掩盖它们带来的长期的好处。还有，将切片和字典作为内置类型，从运行时的层面进行优化，这也算是一种“简单”。

#### 并发模型
时至今日，并发编程已成为程序员的基本技能，在各个技术社区都能看到诸多与之相关的讨论主题。空间哪种方式是最佳并发编程体验，或许会一直争论下去。但Go却一反常态做了件极大胆的事，从根子上将一切都并发化，运行时用Goroutine运行所有的一切，包括main.main入口函数。

可以说，Goroutine是Go最显著的特征。它用类协程的方式来处理并发单元，却又在运行时层面做了更深度的优化处理。这使得语法上的并发编程变得极为容易，无须处理回调，无须关注执行绪切换，仅一个关键字，简单而自然。

搭配channel，实现CSP模型。将迸发单元间的数据耦合拆解开来，各司其职，这对年有纠结于内存共享，锁粒度的开发人员都是一个可期盼的解脱。若说有所不足，那就是应该有个更大的计划，将通信从进程内拓展到进程外，实现真正意义上的分布式。

#### 内存分配
将一切并发化固然是好，但带来的问题同样很多。如何实现高并发下的内存分配和管理就是个难题。好在Go选择了tcmalloc，它本就是为并发而设计的高性能内存分配组件。

可以说，内存分配器是运行时三大组件里变化最少的部分。刨去因配合垃圾回收器而修改的内容，内存分配器完整保留了tcmalloc的原始架构。使用cache为当前执行线程提供无锁分配，多个central在不同线程间平衡内存单元复用。在更高层次里，heap则管理着大块内存，用以切分成不同等级的利用内存块。快速分配和二级内存平衡机制，让内存分配器能优秀地完成高压力下的内存管理任务。

在最近几个版本中，编译器优化旧有成成效。它会竭力将对象分配在栈上，以降低垃圾回收压力，减少消耗，提升执行性能。可以说，除偶尔因性能问题而被迫彩对象池和自主内存管理外，我们基本无须参与内存管理操作。

#### 垃圾回收
垃圾回收一直是个难题，早年间，Java就因垃圾回收低效被嘲笑了许久，后来Sun连续收纳了好多人和技术才发展到今天。可即便如此，在Hadoop等大内存应用场景下，垃圾回收依旧捉襟见肘，步履维艰。

相比Java，Go面临的困难要更多。因指针的存在，所以回收内存不能做收缩处理。幸好，指针运算被阻止，否则要做到精确回收都难。

每次升级，垃圾回收器必然是核心组件里修改最多的部分。从并发清理，到降低STW时间，直到Go的1.5版本实现并发标记，逐步引入三色标记和写屏障等等，都是为了能让垃圾回收在不影响用户逻辑的情况下更好地工作。尽管有了努力，当前版本的垃圾回收算法也只能说堪用，离好用尚有不少距离。可对一个从R60一路跟踪源码走过来的程序员而言，我目睹了Go Team为此所付出的全部努力。我在此表达敬意，以及对未来某个飞跃的预期。

#### 静态链接
Go刚发布时，静态链接被当作优点宣传。只须编译后的一个可执行文件，无须附加任何东西就能部署。这似乎很不错，只是后来风气变了。连着几个版本，编译器都在完善动态库buildmode功能，场面一时变得有些尴尬。

暂不说未完工的buildmode模式，静态编译的好处显而易见。将运行时、依赖库直接打包到可执行文件内部，简单化了部署和发布操作，无须事先安装运行环境和下载诸多第三方库。这种简单方式对于编写系统软件有着极大好处，因为库依赖一直都是个麻烦。事实上，我们也能看到越来越多的工具采用Go开发，其中恐怕就有此等原因。

####标准库
学习编程语言，早已不是学一点语法规则那么简单。现在更习惯称称作选择Ecosystem（生态圈），而这其中标准库的作用和分量尤为明显。

功能完善、质量可靠的标准库为编程语言提供了充足动力。在不借助第三方扩展的情况下，就可完成大部分基础功能开发，这大大降低了学习和使用成本。最关键的是，标准库有升级和修复保障，还能从运行时获得深层次优化的便利，这是第三方库所不具备的。

Go标准库虽称不得完全覆盖，但也算极为丰富。其中值得称道的是net/http，仅须简单几条语句就能实现一个高性能Web Server，这从来都是宣传的亮点。更何况大批基于此的优秀第三方Framework更是将Go推到Web/Microservice开发标准之一的位置。

当然，优秀第三方资源也是语言生态圈的重要组成部分。近年来崛起的几门语言中，Go算是独树一帜，大批优秀作品频繁涌现，这也给我们学习Go提供了很好的参照。

#### 工具链
完整工具链对于日常开发极为重要。Go在些做得相当不错，无论是编译、格式化、错误检查、帮助文档，还是第三方包下载、更新都有对应工具。其功能未必完善，但起码算得上简单易用。

内置完整测试框架，其中包括单元测试、性能测试、代码覆盖率、数据竞争、以及用来高估的pprof，这些都是保障代码能正确而稳定运行的必备利器。

除此之外，还可通过环境变量输出运行时监控信息，尤其是垃圾回收和并发调试跟踪，可进一步帮助我们改进算法，获得更佳的运行期表现。

遗憾的是，发展6年的Go依然缺少一个真正意义上的调试器，对此我个人颇有怨念。另外，依赖包管理也是社区争论的焦点之一。

### 1.2 简介
本节简单预览一下语言功能，有个相对完整的印象更利于学习后续知识。
*** 
可依照第12章安装配置编译环境。
*** 
本书相关内容和示例运行环境：
- Mac OS X EI Capitan 10.11.4
- Ubuntu Server 14.04 x86_64
- GNU gcc 5.3 / gdb 7.7
- Go 1.6 amd64

#### 源文件
源码文件使用UTF-8编码，对Unicode支持良好。每个源文件都属于包的一部分，在文件头部用package声明所属包名称。
**test.go**
``` go
package main
func main() {
    println("hello, world!")
}
```
以“.go”作为文件扩展名，语句结束分号会被默认省略，支持C样式的注释，入口函数main没有参数，且必须放在main包中。

用import导入标准库或第三方包。
``` go
package main

import {
	"fmt"
}

func main() {
	fmt.Println("hello, world!")
}
```
*** 
请删除未使用的导入，否则编译器会将其当作错误。 
***
可直接运行，或编译为可执行文件。
```
$ go run main.go

hello, world
```
#### 变量
使用var定义变量，支持类型推断。基础数据类型划分清晰明确，有助于编写跨平台应用。编译器确保变量总是被初始化为零值，避免出现意外状况。
``` go
package main

func main() {
	var x int32
	var s = "hello, world!"

	println(x, s)
}
```
***
编译器将未使用的局部变量定义当作错误
***
#### 表达式
Go仅有三种流控制语句，与大多数语言相比，都可称得上简单。
##### if
``` go
func main() {
	x := 100

	if x > 0 {
		println("X")
	} else if x < 0 {
		println("-x")
	} else {
		println("0")
	}
}
```
##### switch
``` go
func main() {
	x := 100

	switch {
		case x > 0:
			println("x")
		case x < 0:
			println("-x")
		default:
			println("0")
	}
}
```
##### for
``` go
func main() {
	for i := 0; i < 5; i++ {
		println(i)
	}

	for i := 4; i >= 0; i-- {
		println(i)
	}
}
```
``` go
func main() {
	x := 0

	for x < 5 {               // 相当于 while (x < 5) { ... }
		println(x)
		x++
	}
}
```
``` go
func main() {
	x := 4

	for {                    // 相当于 while (true) { ... }
		println(x)
		x--

		if x < 0 {
			break
		}
	}
}
```
在迭代遍历时，for ... range 除元素外，还可返回索引。
``` go
func main() {
	x := []int{100, 101, 102}

	for i, n := range x {
		println(i, " : ", n)
	}
}
```
##### 输出：
```
0 : 100
1 : 101
2 : 102
```
#### 函数
函数可定义多个返回值，甚至对其命名。
``` go
package main

import {
	"errors"
	"fmt"
}

func div(a, b int) (int, error) {
	if b == 0 {
		return 0, errors.New("division by zero")
	}

	return a / b, nil
}

func main() {
	a, b := 10, 2                 // 定义多个变量
	c, err := div(a, b)           // 接收多返回值

	fmt.Println(c, err)
}
```
函数是第一类型，可作为参数或返回值
``` go
func test(x int) func() {			// 返回函数类型
	return func() {					// 匿名函数
		println(x)					// 闭包
	}
}

func main() {
	x := 100

	f := test(x)
	f()
}
```
用defer定义延迟调用，无论函数是否出错，它都确保结束前被调用。
``` go
package main

func test(a, b int) {
	defer println("dispose...")		// 常用来释放资源、解除锁定，或执行一些清理操作
	
	println(a / b)
}

func main() {
	test(10, 0)
}
```
##### 输出：
```
$ go run test.go

dispose...
panic: runtime error: integer divide by zero
```
#### 数据
切片（slice）可实现类似动态数组的功能。
``` go
package main

import (
	"fmt"
)

func main() {
	x := make([]int, 0, 5)				// 创建容量为 5 的切片

	for i := 0; i < 8; i++ {
		x = append(x, i)				// 追加数据。当超出容量限制时，自动分配更大的存储空间
	}

	fmt.Println(x)
}
```
##### 输出：
```
[0 1 2 3 4 5 6 7]
```
将字典（map）类型内置，可直接从运行时层面获得性能优化。
``` go
package main

import (
	"fmt"
)

func main() {
	m := make(map[string]int)			// 创建字典类型对象
	
	m["a"] = 1							// 添加或设置

	x, ok := m["b"]						// 使用 ok-idiom 获取值，可知道 key/value 是否存在

	delete(m, "a")						// 删除
}
```
***
所谓ok-idiom模式，是指在多返回值中用一个名为ok的布尔值来标示操作是否成功。因为很多操作默认返回零值，所以须额外说明。
***
结构体（struct）可匿名嵌入其他类型。
``` go
package main

import (
	"fmt"
)

type user struct {					// 结构体类型
	name string
	age byte
}

type manager struct {
	user							// 匿名嵌入其他类型
	title string
}

func main() {
	var m manager

	m.name = "Tom"					// 直接访问匿名字段的成员
	m.age = 29
	m.title = "CTO"

	fmt.Println(m)
}
```
##### 输出：
```
{(Tom 29) CTO}
```
#### 方法
可以为当前包内的任意类型定义方法。
``` go
package main

type X int

func (x *X) inc() {					// 名称前的参数称作 receiver，作用类似python self
	*x++
}

func main() {
	var x X
	x.inc()
	println(x)
}
```
还可直接调用匿名字段的方法，这种方式可实现与继承类似的功能。
``` go
package

import (
	"fmt"
)

type user struct {
	name string
	age byte
}

func (u user) ToString() string {
	return fmt.Sprintf("%+v", u)
}

type manager struct {
	user
	title string
}

func main() {
	var m manager
	m.name = "Tom"
	m.age = 29

	println(m.ToString())					// 调用 user.ToString()
}
```
#### 接口
接口采用了duck type方式，也就是说无须在实现类型上添加声明。
``` go
package main

import (
	"fmt"
)

type user struct {
	name string
	age byte
}

func (u user) Print() {
	fmt.Printf("%+v\n", u)
}

type Printer interface {				// 接口类型
	Print()
}

func main() {
	var u user
	u.name = "Tom"
	u.age = 29

	var p Printer = u					// 只要包含接口所需的全部方法，即表示实现了该接口
	p.Print()
}
```
***
另有空接口类型interface{}，用途类似OOP里的system.Object，可接收任意类型对象。
***
#### 并发
整个运行时完全并发化设计。凡你能看到的，几乎都在goroutine方式运行。这是一种比普通协程或线程更加高效的并发设计，能轻松创建和运行成千上万的并发任务。
``` go
package main

import (
	"fmt"
	"time"
)

func task(id int) {
	for i := 0; i < 5; i++ {
		fmt.Printf("%d: %d\n", id, i)
		time.Sleep(time.Second)
	}
}

func main() {
	go task(1)					// 创建 goroutine
	go task(2)

	time.Sleep(time.Second * 6)
}
```
```
1: 0
2: 0
1: 1
2: 1
1: 2
2: 2
2: 3
1: 3
2: 4
1: 4
```
通道（channel）与goroutine搭配，实现用通信代替内存共享的模型。
``` go
package main

// 消费者
func consumer(data chan int, done chan bool) {
	for x := range data {						// 接收数据，直到通道被关闭
		println("recv:", x)
	}

	done <- true								// 通知 main，消费结束
}

// 生产者
func producer(data chan int) {
	for i := 0; i < 4; i++ {
		data <- 1								// 发送数据
	}

	close(data)									// 生产结束，关闭通道
}

func main() {
	done := make(chan bool)						// 用于接收消费结束信号
	data := make(chan int)						// 数据管道

	go consumer(data, done)						// 启动消费者
	go producer(data)							// 启动生产者

	<-done										// 阻塞，走到消费者发回结束信号
}
```
##### 输出：
```
recv: 0
recv: 1
recv: 2
recv: 3
```


## 第2章 类型
### 2.1 变量
在数学概念中，变量（variable）表示没有固定值且可改变的数。但从计算机系统实现角度来看，变量是一段或多段用来存储数据的内存。
作为静态类型语言，Go变量总是有固定的数据类型，类型决定了变量内存的长度和存储格式。我们只能修改变量值，无法改变类型。
***
通过类型转换或指针操作，我们可用不同方式修改变量值，但这并不意味着改变了变量类型。
***
因为内存分配发生在运行期，所以在编码阶段我们用一个易于阅读的名字来表示这段内存。实际上，编译后的机器码从不使用变量名，而是直接通过内存地址来访问目标数据。保存在符号表中的变量名等信息可被删除，或用于输出更详细的错误信息。
### 定义
关键字var用于定义变量，和C不同，类型被放在变量名后。另外，运行时内存分配操作会确保变量自动初始化为二进制零值（zero value），避免出现不可预测行为。如显示提供初始化值，可省略变量类型，由编译器推断。
``` go
var x int					// 自动初始化为 0
var y = false				// 自动推断为 bool 类型
```
可一次定义多个变量，包括用不同初始值定义不同类型。
``` go
var x, y int				// 相同类型的多个变量
var a, s = 100, "abc"		// 不同类型初始化值
```
依照惯例，建议以组方式整理多行变量定义。
``` go
var (
	x, y int
	a, s = 100, "abc"
)
```
#### 简短模式
除var关键字外，还可使用更加简短的变量定义和初始化语法。
``` go
func main() {
	x := 100
	a, s := 1, "abc"
}
```
只是要注意，简短模式（short variable declaration）有些限制：
- 定义变量，同时显示初始化。
- 不能提供数据类型。
- 只能用在函数内部。

对于粗心的新手，这可能会造成意外错误。比如原本打算修改全局变量，结果变成重新定义同名局部变量。
``` go
var x = 100

func main() {
	println(&x, x)					// 全局变量

	x := "abc"						// 重新定义和初始化同名局部变量
	println(&x, x)
}
```
##### 输出：
```
0xae020					100			// 对比内存地址，可以看出是两个不同的变量
0xc820041f38			abc
```
***
简短定义在函数多返回值，以及if/for/switch等语句中定义局部变量非常方便。
***
简短模式并不总是重新定义变量，也可能是部分退化的赋值操作。
``` go
func main() {
	x := 100
	println(&x)

	x, y := 200, "abc"				// 注意：x退化为赋值操作，仅有y是变量定义

	println(&x, x)
	println(y)
}
```
##### 输出：
```
0xc820041f28						// 对比内存地址，可以看出是两个不同的变量
0xc820041f28			100
abc
```
退化赋值的前提条件是：最少有一个新变量被定义，且必须是同一作用域。
``` go
func main() {
	x := 100
	println(&x)

	x := 200						// 错误：no new variables on left side of :=
	println(&x, x)
}
```
``` go
func main() {
	x := 100
	println(&x)

	{
		x, y := 200, 300			// 不同作用域，全部是新变量定义
		println(&x, x, y)
	}
}
```
##### 输出：
```
0xc820041f30			100
0xc820041f38			200		300
```
在处理函数错误返回值时，退化赋值允许我们重复使用err变量，这是相当有益的。
``` go 
package main

import (
	"log"
	"os"
)

func main() {
	f, err := os.Open("/dev/random")
	...

	buf := make([]byte, 1024)
	n, err := f.Read(buf)			// err 退化赋值，n新定义
}
```
#### 多变量赋值
在进行多变量赋值操作时，首先计算出所有右值，然后再今次完成赋值操作。
``` go
func main() {
	x, y := 1, 2
	x, y = y+3, x+2					// 先计算出右值y+3、x+2，然后再对x、y变量赋值

	println(x, y)
}
```
输出：
```
$ go build && ./test

5 3

$ go tool objdump -s "main\.main" test

TEXT main.main(SB) test.go
	MOVQ $0x1, AX				// 先使用AX、CX寄存器完成表达式x+2、y+3操作
	MOVQ $0x2, CX
	MOVQ $0x3, CX
	MOVQ $0x2, AX
	MOVQ CX, 0x10(SP)			// 然后将计算结果分别写入x、y变量
	MOVQ AX, 0x8(SP)

	CALL runtime.printlock(SB)	// 依次printint(x)，printint(y)
	MOVQ 0x10(SP), BX
	MOVQ BX, 0(SP)
	CALL runtime.printint(SB)
	CALL runtime.printsp(SB)

	MOVQ 0x8(SP), BX
	MOVQ BX, 0(SP)
	CALL runtime.printint(SB)
	CALL runtime.println(SB)
	CALL runtime.printunlock(SB)
```
赋值操作，必须确保左右值类型相同。
#### 未使用错误
编译器将未使用局部变量当作错误。不要觉得麻烦，这有助于培养良好的编码习惯。
``` go
var x int					// 全局变量没问题

func main() {
	y := 10
}
```
##### 输出：
```
$ go build

./test.go: y declared and not used
```
### 2.2 命名
对变量、常量、函数、自定义类型进行命名，通常优先选用有实际含义，易于阅读和理解的字母或单词组合。
#### 命名建议
- 以字母或下划线开始，由多个字母、数字和下划线组合而成。
- 区分大小写。
- 使用驼峰（camel case）拼写格式。
- 局部变量优先使用短名。
- 不要使用保留关键字。
- 不建议使用与预定义常量、类型、内置函数相同的名字。
- 专有名词通常会全部大写，例如escapeHTML。

***
尽管Go支持用汉字等Unicode字符命名，但从编程习惯上来说，这并不是好选择。
***
``` go
func main() {
	var c int						// c 代替 count
	for i := 0; i < 10; i++ {		// i 代替 index
		c++
	}

	println(c)
}
```
符号名字首字母大小写决定了其作用域。首字母大写的为导出成员，可被包外引用，而小写则仅能在包内使用。相关细节，可参考后续章节。
#### 空标识符
和Python类似，Go也有个名为“_”的特殊成员（blank identifier）。通常作为忽略占位符使用，可作表达式左值，无法读取内容。
``` go
import "strconv"

func main() {
	x, _ := strconv.Atoi("12")				// 忽略Atoi的err返回值
	println(x)
}
```
空标识符可用来临时规避编译器对未使用变量和导入包的错误检查。但请注意，它是预置成员，不能重新定义。
### 2.3 常量
常量表示运行时恒定不可改变的值，通常是一些字面量。使用常量就可用一个易于阅读理解的标识符号来代替“魔法数字”，也使得在调整常量值时，无须修改所有引用代码。
常量值必须是编译期可确定的字符、字符串、数字或布尔值。可指定常量类型，或由编译器通过初始化值推断，不支持C/C++数字类型后缀。
``` go
const x, y int = 123, 0x22
const s = "hello, world!"
const c = '我'							// rune (unicode code point)

const (
	i, f = 1, 0.123						// int, float64(默认)
	b = false
)
```
可在函数 代码块中定义常量，不曾使用的常量不会引发编译错误。
``` go
func main() {
	const x = 123
	println(x)

	const y = 1.23						// 未使用，不会引发编译错误

	{
		const x = "abc"					// 在不同作用域定义同名常量
		println(x)
	}
}
```
##### 输出：
```
123
abc
```
如果显式指定类型，必须确保常量左右值类型一致，需要时可做显式转换。右值不能超出常量类型取值范围，否则会引发溢出错误。
```go
const (
	x, y int = 99, -999
	b byte = byte(x)					// x 被指定为int类型，须显式转换为byte类型
	n = unit8(y)						// 错误：constant -999 overflows unit8
)
```
常量值也可以是某些编译器能计算出结果的表达式，如unsafe.Sizeof、len、cap等。
``` go
import "unsafe"

const (
	ptrSize = unsafe.Sizeof(uintptr(0))
	strSize = len("hello, world!")
)
```
在常量组中如不指定类型和初始化值，则与上一行非空常量右值（表达式磨文本）相同。
``` go
import "fmt"

func main() {
	const (
		x uint16 = 120
		y							// 与上一行 x 类型、右值相同
		s = "abc"
		z							// 与 s 类型、右值相同
	)

	fmt.Printf("%T, %v\n", y, y)	// 输出类型和值
	fmt.Printf("%T, %v\n", z, z)
}
```
##### 输出：
```
uint16, 120
string, abc
```
#### 枚举
Go并没有明确意义上的enum定义，不过可借助iota标识符实现一组自增常量值来实现枚举类型。
``` go
const (
	x = iota		// 0
	y				// 1
	z				// 2
)

const (
	_ = itoa		// 0
	KB = 1 << (10 * iota)			// 1 << (10 * 1)
	MB								// 1 << (10 * 2)
	GB								// 1 << (10 * 3)
)
```
自增作用范围为常量组。可在多常量定义中使用多个iota，它们各自单独计数，只须确保组中每行常量的列数量相同即可。
``` go
const (
	_, _ = iota, iota * 10			// 0, 0 * 10
	a, b							// 1, 1 * 10
	c, d							// 2, 2 * 10
)
```
如中断iota自增，则必须显式恢复。且后续自增值按行序递增，而非 C enum那般按上一取值递增。
``` go
const (
	a = iota						// 0
	b								// 1
	c = 100							// 100
	d								// 100（与上一行常量右值表达式相同）
	e = iota						// 4（恢复iota自增，计数包括c、d）
	f								// 5
)
```
自增默认数据类型为int，可显式指定类型。
``` go
const (
	a = i							// int
	b float32 = iota				// float32
	c = iota						// int（如不显式指定 iota，则与 b 数据类型相同）
)
```
在实际编码中，建议用自定义类型实现用途明确的枚举类型。但这并不能将取值范围限定在预定义的枚举值内。
``` go
type color byte						// 自定义类型

const (
	black color = iota				// 指定常量类型
	red
	blue
)

func test(c color) {
	test(red)
	test(100)						// 100 并未超出 color/byte 类型取值范围

	x := 2
	test(x)							// 错误：cannot use x (type int) as type color in argument to test
}
```
#### 展开
常量除“只读”外，和变量究竟有什么不同？
``` go
var x = 0x100
const y = 0x200

func main() {
	println(&x, x)
	println(&y, y)					// 错误：cannot take the address of y
}
```
不同于变量在运行期分配 存储内存（非优化状态），常量通常会被编译器在预处理阶段直接展开，作为指令数据使用。
``` go
const y = 0x200

func main() {
	println(y)
}
```
##### 输出：
```
$ go build && go tool objdump -s "main\.main" test

TEXT main.main(SB) test.go
	MOVQ $0x200, 0(SP)				// 将常量值作为指令数据展开
	CALL runtime.printint(SB)
```
数字常量不会分配存储空间，无须像变量那样通过内存寻址来取值，因此无法获取地址。
***
鉴于Go当前对动态库的支持还不完善，是否存在“常量陷阱”问题，尚有待观察。
***
提到常量展开，我们还须回头看看常量的两种状态对编译器的影响。
``` go
const x = 100						// 无类型声明的常量
const y byte = x					// 直接展开 x，相当于const y byte = 100

const a int = 100					// 显式指定常量类型，编译器会做强类型检查
const b byte = a					// 错误：cannot use a (type int) as type byte in const initializer
```
### 2.4 基本类型
清晰完备的预定义基础类型，使得开发跨平台应用时无须过多考虑符号和长度差异。
| 类型  | 长度 | 默认值  | 说明 |
| :-------- | --------:| --: | :-- |
| bool  | 1 |  false   ||
| byte  | 1 |  0  | uint8 |
| int, unit | 4, 8 | 0 | 默认整数类型，依据目标平台，32或64位 |
| int8, uint8 | 1 | 0 | -128 ~ 127， 0 ~ 255 |
| int16, uint16 | 2 | 0 | -32,768 ~ 32,767, 0 ~ 65,535 |
| int32, uint32 | 4 | 0 | -21亿 ~ 21亿，0 ~ 42亿 |
| int64, uint64 | 8 | 0 |  |
| float32 | 4 | 0.0 |  |
| float64 | 8 | 0.0 | 默认浮点数类型 |
| complex64 | 8 |  |  |
| complex128 | 16 |  |  |
| rune | 4 | 0 | Unicode Code Point, int32 |
| uintptr | 4, 8 | 0 | 足以存储指针的uint |
| string |  | "" | 字符串，默认值为空字符串，而非NULL |
| array |  |  | 数组 |
| struct |  |  | 结构体 |
| function |  | nil | 函数 |
| interface |  | nil | 接口 |
| map |  | nil | 字典，引用类型 |
| slice |  | nil | 切片，引用类型 |
| channel |  | nil | 通道，引用类型 |
支持八进制，十六进制以及科学记数法。标准库math定义了各数字类型的取值范围。
``` go
import (
	"fmt"
	"math"
)

func main() {
	a, b, c := 100, 0144, 0x64

	fmt.Println(a, b, c)
	fmt.Printf("0b%b, %#o, %#x\n", a, a, a)

	fmt.Println(math.MinInt8, math.MaxInt8)
}
```
##### 输出：
```
100 100 100
0b1100100, 0144, 0x64

-128 127
```
标准库strconv可在不同进制（字符串）间转换。
``` go
import "strconv"

func main() {
	a, _ := strconv.ParseInt("1100100", 2, 32)
	b, _ := strconv.ParseInt("0144", 8, 32)
	c, _ := strconv.ParseInt("64", 16, 32)
	println(a, b, c)

	println("0b" + strconv.FormatInt(a, 2))
	println("0" + strconv.FormatInt(a, 8))
	println("0x" + strconv.FormatInt(a, 16))
}
```
##### 输出：
```
100 100 100
0b1100100
0144
0x64
```
使用浮点数时，须注意小数位的有效精度，相关细节可参考IEE-754标准。
``` go
func main() {
	var a float32 = 1.1234567899		// 注意：默认浮点类型是float64
	var b float32 = 1.12345678
	var c float32 = 1.123456781

	println(a, b, c)
	println(a == b, a == c)
	fmt.Printf("%v %v, %v\n", a, b, c)
}
```
##### 输出：
```
+1.1234567e+000 +1.1234567e+000 +1.1234567e+000
true true
1.1234568 1.1234568 1.1234568
```
#### 别名
在官方的语言规范中，专门提到两个别名。
``` go
byte		alias for unit8
rune		alias for int32
```
别名类型无须转换，可直接赋值。
``` go
func test(x byte) {
	println(x)
}

func main() {
	var a byte = 0x11
	var b uint8 = a
	var c uint8 = a + b

	test(c)
}
```
但这并不表示，拥有相同底层结构的就属于别名。就算在64位平台上int和int64结构完全一致，也分属不同类型，须显式转换。
``` go
func add(x, y int) int {
	return x + y
}

func main() {
	var x int = 100
	var y int64 = x			// 错误：cannot use x (type int) as type int64 in assignment

	add(x, y)				// 错误：cannot use y (type int64) as type int in argument to add
}
```
### 2.5 引用类型
所谓引用类型（reference type）特指slice、map、channel这三种预定义类型。
相比数字、数组等类型，引用类型拥有更复杂的存储结构。除分配内存外，它们还须初始化一系列属性，诸如指针、长度，甚至包括哈希分布、数据队列等。
内置函数new按指定类型长度分配零值内存，返回指针，并不关心类型内部构造和初始化方式。而引用类型则必须使用make函数创建，编译器会将make转换为目标类型专用的创建函数（或指令），以确保完成全部内存分配和相关属性初始化。
``` go
func mkslice() []int {
	s := make([]int, 0, 10)
	s = append(s, 100)
	return s
}

func mkmap() map[string]int {
	m := make(map[string]int)
	m["a"] = 1
	return m
}

func main() {
	m := mkmap()
	println(m["a"])

	s := mkslice()
	println(s[0])
}
```
##### 输出：
```
$ go build -gcflags "-l"				// 禁用函数内联

$ go tool objdump -s "main\.mk" test

TEXT main.mkslice(SB) test.go
	CALL runtime.makeslice(SB)

TEXT main.mkmap(SB) test.go
	CALL runtime.makemap(SB)
```
***
除new/make函数外，也可使用初始化表达式，编译器生成的指令基本相同。
***
当然，new函数也可为引用类型分配内存，但这是不完整创建。以字典（map）为例，它仅分配了字典类型本身（实际就是个指针包装）所需内存，并没有分配键值存储内存，也没有初始化散列桶等内部属性，因此它无法正常工作。
``` go
import "fmt"

func main() {
	p := new(map[string]int)		// 函数 new 返回指针
	m := *p
	m["a"] = 1						// panic: assignment to entry in nil map （运行期错误）
	fmt.Println(m)
}
```
### 2.6 类型转换
隐式转换造成的问题远大于它带来的好处。
除常量、别名类型以及未命名类型外，Go强制要求使用类型转换。加上不支持操作符重载，所以我们总是能确定语句及表达式的明确含义。
``` go
a := 10
b := byte(a)
c := a + int(b)						// 混合类型表达式必须确保类型一致
```
同样不能将非bool类型结果当作true/false使用。
``` go
func main() {
	x := 100

	var b bool = x		// 错误：cannot use x (type int) as type bool in assignment
	
	if x {				// 错误：non-bool x (type int) used as if condition
	}
}
```
#### 语法歧义
如果转换的目标是指针、单向通道或没有返回值的函数类型，那么必须使用括号，以避免造成语法分解错误。
``` go
func main() {
	x := 100
	p := *int(&x)		//错误：cannot convert &x (type *int) to type int
						// invalid indirect of int(&x) (type int)

	println(p)
}
```
正确的做法是用括号，让编译器将*int解析为指针类型。
``` go
(*int)(p)				--> 如果没有括号 -->		*(int(p))
(<-chan int)(c)									<-(chan int(c))
(func())(x)										func() x

func()int(x)			--> 有返回值的函数类型可省略括号，但依然建议使用。
(func()int)(x)				使用括号后，更易阅读
```
### 2.7 自定义类型
使用关键字type定义用户自定义类型，包括基于现有基础类型创建，或者是结构体、函数类型等。
``` go
type flags byte

const (
	read flages = 1 << iota
	write
	exec
)

func main() {
	f := read | exec
	fmt.Printf("%b\n", f)			// 输出二进制标记位
}
```
##### 输出：
```
101
```
和var、const类似，多个type定义可合并成组，可在函数或代码块内定义局部类型。
``` go
func main() {
	type (							// 组
		user struct {				// 结构体
			name string
			age uint8
		}

		event func(string) bool		// 函数类型
	)

	u := user{"Tom", 20}
	fmt.Println(u)

	var f event = func(s string) bool {
		println(s)
		return s != ""
	}

	f("abc")
}
```
即使指定了基础类型，也只表明它们有相同底层数据结构，两者间不存在任何关系，属完全不同的两种类型。除操作符外，自定义类型不会继承基础类型的其他信息（包括方法）。不能视作别名，不能隐式转换，不能直接用于比较表达式。
``` go
func main() {
	type data int
	var d data = 10

	var x int = d					// 错误：cannot use d (type data) as type int in assignment
	println(x)

	println(d == x)					// 错误：invalid operation: d == x (mismatched types data and int)
}
```
#### 未命名类型
与有明确标识符的bool、int、string等类型相比，数组、切片、字典、通道等类型与具体元素类型或长度等属性有关，故称作未命名类型（unnamed type）。当然，可用type为其提供具体名称，将其改变为命名类型（named type）。
具有相同声明的未命名类型被视作同一类型。
- 具有相同基类型的指针。
- 具有相同元素类型和长度的数组（array）。
- 具有相同元素类型的切片（slice）。
- 具有相同键值类型的字典（map）。
- 具有相同字段序列（字段名、字段类型、标签，以及字段顺序）的结构体（struct）。
- 具有相同签名（参数和返回值列表，不包括参数名）的函数（func）。
- 具有相同方法集（方法名、方法签名，不包括顺序）的接口（intrerface）。
***
相关类型会在后续章节做详细说明，此处无须了解更多细节。
***
容易被忽视的是struct tag，它也属于类型组成部分，而不仅仅是元数据描述。
``` go
func main() {
	var a struct {					// 匿名结构类型
		x int 'x'
		s string 's'
	}

	var b struct {
		x int
		s string
	}

	b = a							// 错误：cannot use a type
									// 		struct { x int "x"; s string "s" } as type
									//		struct { x int; s string } in assignment
	fmt.Println(b)
}
```
同样，函数的参数顺序也属签名组成部分。
``` go
func main() {
	var a func(int, string)
	var b func(string int)

	b = a			// 错误：cannot use a (type func(int, string)) as type
					//      func(string, int) in assignment
	b("s", 1)
}
```
未命名类型转换规则：
- 所属类型相同。
- 基础类型相同，且其中一个是未命名类型。
- 数据类型相同，将双向通道赋值给单向通道，且其中一个为未命名类型。
- 对象实现了目标接口。
``` go
func main() {
	type data [2]int
	var d data = [2]int{1, 2}		// 基础类型相同，右值为未命名类型

	fmt.Println(d)

	a := make(chan int, 2)
	var b chan <- int = a			// 双向通道转换为单向通道，其中b为未命名类型

	b <- 2
}
```

## 第三章 表达式
### 3.1 保留字
Go语言仅25个保留关键字（keyword），这是最常见的宣传语，虽不是主流语言中最少的，但也确实体现了Go语法规则的简洁性。保留关键字不能用作常量、变量、函数名、以及结构字段等标识符。
``` go
break			default			func			interface			select
case			defer			go				map					struct
chan			else			goto			package				switch
const			fallthrough		if				range				type
continue		for				import			return				var
```
***
相比在更新版本中不停添加新语言功能，我更喜欢简单的语言设计。某些功能可能通过类库扩展，或其他非侵入方式实现，完全没必要为了“方便”让语言变得臃肿。过于丰富的功能特征会随着时间的推移抬升门槛，还会让代码变得日趋”魔幻”，降低一致性和可维护性。
***
### 3.2 运算符
很久以前，流传“程序=算法+数据”这样的说法。
算法是什么？通俗点说主是“解决问题的过程”。小到加法指令，大到成千上万台服务器组成的分布式计算集群，抛去抽象概念和宏观架构，最终都由最基础的机器指令过程去处理不同层次存储设备里的数据。
学习语言和设计架构不同，我们所关心的就是微观层次，诸如语法规则所映射的机器指令，以及数据存储位置和格式等等。其中，运算符和表达式用来串联数据和指令，算是最基础的算法。
***
另有一句话：“硬件的方向是物理，软件的结局是数据。”
***
全部运算符及分隔符列表：
``` go
+		&		+=		&=		&&		==		!=		(		)
-		|		-=		|=		||		<		<=		[		]
*		^		*=		^=		<-		>		>=		{		}
/		<<		/=		<<=		++		=		:=		,		;
%		>>		%=		>>=		--		!		...		.		:
		&^				&^=
```
没有乘幂和绝对值运算符，对应的是标准库math里的Pow、Abs函数实现。
#### 优先级
一元运算符优先级最高，二元则分成五个级别，从高往低分别是：
``` go
highest		*	/	%	<<	>>	&	&^
			+	-	|	^
			==	!=	<	<=	>	>=
			&&
lowest		||
```
相同优先级的二元运算符，从左往右依次计算。
#### 二元运算符
除位移操作外，操作数类型必须相同。如果其中一个是无显式类型声明的常量，那么该常量操作数会自动转型。
``` go
func main() {
	const v = 20					// 无显式类型声明的常量
	
	var a byte = 10
	b := v + a						// v 自动转换为 byte/uint8 类型
	fmt.Printf("%T, %v\n", b, b)

	const c float32 = 1.2
	d := c + v						// v 自动转换为float32类型
	fmt.Printf("%T, %v\n", d, d)
}
```
##### 输出：
```
uint8, 30
float32, 21.2
```
位移右操作数必须是无符号整数，或可以转换的无显式类型常量。
``` go
func main() {
	b := 23				// b 是符号 int 类型变量
	x := 1 << b			// 无效操作：1 << b (shift count type int, must be unsigned integer)
	println(x)
}
```
如果是非常量位移表达式，那么会优先将无显式类型的常量左操作数转型。
``` go
func main() {
	a := 1.0 << 3					// 常量表达式（包括常量展开）
	fmt.Printf("%T, %v\n", a, a)	// int, 8

	var s uint = 3
	b := 1.0 << s					// 无效操作： 1 << s (shift of type float64)
	fmt.Printf("%T, %v\n", b, b)	// 因为 b 没有提供类型，那么编译器通过1.0推断，
									// 显然无法对浮点数做位移操作

	var c int32 = 1.0 << s			// 自动将 1.0 转换为 int32 类型
	fmt.Printf("%T, %v\n", c, c)	// int32, 8
}
```
#### 位运算符
二进制位运算符比较特别的就是“bit clear”，在其他语言里很少见到。
``` go
AND				按位与：都为 1			a & b	0101 & 0011 = 0001
OR				按位或：至少一个 1			a | b	0101 | 0011 = 0111
XOR				按位异或：只有一个 1		a ^ b	0101 ^ 0011 = 0110
NOT				按位取反 （一元）			^a		^0111 = 1000
AND NOT			按位清除 （bit clear）	a &^ b	0110 &^ 1011 = 0101
LEFT SHIFT		位左移					a << 2	0001 << 3 = 1000
RIGHT SHIFT		位右移					a >> 2	1010 >> 2 = 0010
```
位清除（AND NOT）和位异或（XOR）是不同的。它将左右操作数对应二进制位都为1的重围为0（有些类似位图），以达到一次清除多个标记位的目的。
``` go
const (
	read	byte = 1 << iota
	write
	exec
	freeze
)

func main() {
	a := read | write | freeze
	b := read | freeze | exec
	c := a &^ b					// 相当于 a ^ read ^ freeze，但不包括 exec

	fmt.Printf("%04b &^ %04b = %04b\n", a, b, c)
}
```
##### 输出：
```
1011 &^ 1101 = 0010
```
#### 自增
自增、自减不再是运算符。只能作为独立语句，不能用于表达式。
``` go
func main() {
	a := 1
	++a						// 语法错误： unexpected ++ （不能前置）
	
	if (a++) > 1 {			// 语法错误：unexpected ++,expecting (语句不能作为表达式使用)
	}

	p := &a
	*p++					// 相当于 （*p）++
	println(a)
}
```
***
表达式通常是求值代码，可作为右值或参数使用。而语句完成一个行为，比如if、for代码块。表达式可作为语句用，但语句却不能当作表达式。
***
#### 指针
不能将内存地址与指针混为一谈。
内存地址是内存中每个字节单元的唯一编号，而指针则是一个实体。指针会分配内存空间，相当于一个专门用来保存地址的整型变量。
```
				p := &x                x := 100
----------------+--------+------\\-----+-------+-------
  memory ...    | 0x1200 |    ....     |  100  |  ....
----------------+--------+------\\-----+-------+-------
  address       0x800                  0x1200
```
- 取地址运算符“&”用于获取对象地址。
- 指针运算符“*”用于间接引用目标对象。
- 二级指针**T，如包含包名则写成*package.T。
并非所有对象都能进行取地址操作，但变量总是能正确返回（addressable）。指针运算符为左值时，我们可更新目标对象状态；而为右值时则是为了获取目标状态。
``` go
func main() {
	x := 10
	
	var p *int = &x			// 获取地址，保存到指针变量
	*p += 20				// 用指针间接引用，并更新对象

	println(p, *p)			// 输出指针所存储的地址，以及目标对象
}
```
##### 输出：
```
  0xc82003df30  30
```
``` go
func main() {
	m := map[string]int{ "a": 1}
	println(&m["a"])			// 错误：cannot take the address of m["a"]
}
```
指针类型支持相待运算符，但不能做加减法运算和类型转换。如果两个指针指向同一地址，或都为nil，那么它们相等。
``` go
func main() {
	x := 10
	p := &x

	P++							// 无效操作：p++ (non-numeric type *int)
	var p2 *int = p + 1			// 无效操作：p + 1 (mismatched types *int and int)

	p2 = &x
	println(p == p2)
}
```
***
可通过unsafe.Pointer将指针转换为uintptr后进行加减法运算，但可能会造成非法访问。
Pointer类似C语言中的 void* 万能指针，可用来转换指针类型。它能安全持有对象或对象成员，但uintptr不行。后者仅是一种特殊整型，并不引用目标对象，无法阻止垃圾回收器回收对象内存。
***
指针没有专门指向成员的“->”运算符，统一使用 “.” 选择表达式。
``` go
func main() {
	a := struct {
		x int
	}{}

	a.x = 100

	p := &a
	p.x += 100				// 相当于 p -> x += 100

	println(p.x)
}
```
零长度（zero-size）对象的地址是否相等和具体的实现版本有关，不过肯定不等于nil。
``` go
func main() {
	var a, b struct{}

	println(&a, &b)
	println(&a == &b, &a == nil)
}
```
##### 输出：
```
 0xc820041f2f  0xc820041f2f
 true  false
```
***
即便长度为0，可该对象依然是“合法存在”的，拥有合法内存地址，这与nil语义完全不同。
在runtime/malloc.go里有个zerobase全局变量，所有通过mallocgc分配的零长度对象都使用该地址。不过上例中，对象a、b在栈上分配，并未调用mallocgc函数。
***
### 3.3 初始化
对复合类型（数组、切片、字典、结构体）变量初始化时，有一些语法限制。
- 初始化表达式必须含类型标签。
- 左花括号必须在类型尾部，不能另起一行。
- 多个成员初始值以逗号分隔。
- 允许多行，但每行须以逗号或右花括号结束。
正确示例：
``` go
type data struct {
	x int
	s string
}

var a data = data{1, "abc"}

b := data {
	1,
	"abc",
}

c := []int {
	1,
	2
}

d := []int {1, 2
	3, 4,
	5
}
```
错误示例：
``` go
var d data = {1, "abc"}		// 语法错误：unexpected (缺类型标签)

d := data
	{						// 语法错误：unexpected semicolon or newline (左花括号不能另起一行)
	1,
	"abc"
	}

d := data {
	1,
	"abc"					// 语法错误：need trailing comma before newline(须以逗号或右花括号结束)
}
```
### 3.4 流控制
Go精简（合并）了流控制语句，虽然某些时候不够便捷，但够用。
#### if ... else ...
条件表达式值必须是布尔类型，可省略括号，且左花括号不能另起一行。
``` go
func main() {
	x := 3

	if x > 5 {
		println("a")
	} else if x < 5 && x > 0 {
		println("b")
	} else {
		println("z")
	}
}
```
比较特别的是对初始化语句的支持，可定义块局部变量或执行初始化函数。
``` go
func main() {
	x := 10

	if xinit(); x == 0 {				// 优先执行xinit函数
		println("a")
	}

	if a, b := x+1, x+10; a < b {		// 定义一个或多个局部变量（也可以是函数返回值）
		println(a)
	} else {
		println(b)
	}
}
```
***
局部变量的有效范围包含整个 if/else 块。
***
对于编程初学者，可能会因条件匹配顺序不当而写出死代码（dead code）。
``` go
func main() {
	x := 8

	if x > 5 {							// 优先判断，条件表达式结果为 true
		println("a")
	} else if x > 7 {					// dead code
		println("b")
	}
}
```
##### 输出：
```
 a
```
***
死代码是指永远不会被执行的代码，可使用专门的工具，或用代码覆盖率（code coverage）测试进行检查。某些比较智能的编译器也可主动清除死代码（dead code elimination, DCE）。
***
尽可能减少代码块嵌套，让正常逻辑处于相同层次。
``` go
import (
	"errors"
	"log"
)

func check(x int) error {
	if x <= 0 {
		return errors.New("x <= 0")
	}

	return nil
}

func main() {
	x := 10

	if err := check(x); err == nil {
		x++
		println(x)
	} else {
		log.Fatalln(err)
	}
}
```
该示例中，if块显然承担了两种逻辑：错误处理和后续正常操作。基于重构原则，我们应该保持代码块功能的单一性。
``` go
func main() {
	x := 10

	if err := check(x); err != nil {
		log.Fatalln(err)
	}

	x++
	println(x)
}
```
如此，if块仅完成条件检查和错误处理，相关正常逻辑保持在同一层次。当有人试图通过阅读这段代码来获知逻辑流程时，完全可忽略if块细节。同时，单一功能可提升代码可维护性，更利于拆分重构。
当然，如须在多个条件块中使用局部变量，那么只能保留原层次，或直接使用外部变量。
``` go
import (
	"log"
	"strconv"
)

func main() {
	s := "9"

	n, err := strconv.ParseInt(s, 10, 64)		// 使用外部变量

	if err != nil {
		log.Fatalln(err)
	} else if n < 0 || n > 10 {					// 也可考虑拆分成另一个独立 if 块
		log.Fatalln("invalid number")
	}

	println(n)									// 避免 if 局部变量将该逻辑放到 else 块
}
```
对于某些过于复杂的组合条件，建议将其重构为函数。
``` go
import (
	"log"
	"strconv"
)

func main() {
	s := "9"

	if n, err := strconv.ParseInt(s, 10, 64); err != nil || n < 0 || n > 10 || n%2 != 0 {
		log.Fatalln("invalid number")
	}

	println("ok")
}
```
函数调用虽然有一些性能损失，可却让主流程变得更加清爽。况且，条件语句独立之后，更易于测试，同样会改善代码可维护性。
``` go
import (
	"errors"
	"log"
	"strconv"
)

func check(s string) error {
	n, err := strconv.ParseInt(s, 10, 64)
	if err != nil | n < 0 || n > 10 || n%2 != 0 {
		return errors.New("invalid number")
	}

	return nil
}

func main() {
	s := "9"
	
	if err := check(s); err != nil {
		log.Fatalln(err)
	}

	println("ok")
}
```
将流程和局部细节分离是很常见的做法，不同的变化因素被分隔在各自独立单元（函数或模块）内，可避免修改时造成关联错误，减少患“肥胖症”的函数数量。当然，代码单元测试也是主要原因之一。另一方面，该示例中的函数check仅被 if 块调用，也可将其作为局部函数，以避免扩大作用域，只是对测试的友好度会差一些。
***
当前编译器只能说够用，须优化的地方太多，其中内联处理做得也差强人意，所以代码维护性和性能平衡需要投入更多心力。
语言方面，最遗憾的是没有条件运算符“a > b ? a : b”。有没有 lambda 无所谓，但没有这个却少了份优雅。加上一大堆 err != nil 判断语句，对于有完美主义倾向的代码洁癖患者来说是种折磨。
***
#### switch
与 if 类似，switch语句也用于选择执行，但具体使用场景会有所不同。
``` go
func main() {
	a, b, c, x := 1, 2, 3, 2

	switch x {						// 将 x 与 case 条件匹配
	case a, b:						// 多个匹配条件命中其一即可（OR），变量
		println("a | b")
	case c:							// 单个匹配条件
		println("c")
	case 4:							// 常量
		println("d")
	default:
		println("z")
	}
}
```
##### 输出：
```
 a | b
```
***
条件表达式支持非常量值，这要比C更加灵活。相比 if 表达式，switch值列表要更加简洁。
编译器对 if、switch 生成的机器指令可能完全相同，所谓谁性能更好须看具体情况，不能作为主观判断条件。
***
switch同样支持初始化语句，按从上到下、从左到右顺序匹配 case 执行。只有全部匹配失败时，才会执行 default 块。
``` go
func main() {
	switch x := 5; x {
		default:				// 编译器确保不会先执行 default 块
			x += 100
			println(x)
		case 5:
			x += 50
			println(x)
	}
}
```
##### 输出：
```
 55
```
***
考虑到 default 作用类似 else，建议将其放置在 switch 末尾。
***
相邻的空 case 不构成多条件匹配。
``` go
switch x {
	case a:						// 单条件，内容为空。隐式“case a: break;”
	case b:
		println("b")
}
```
不能出现重复的 case 常量值。
``` go
func main() {
	switch x := 5; x {
	case 5:
		println("a")
	case 6, 5:					// 错误：duplicate case 5 in switch
		println("b")
	}
}
```
无须显式执行break语句，case 执行完毕后自动中断。如须贯通后续 case （源码顺序），须执行 fallthrough，但不再匹配后续条件表达式。
``` go
func main() {
	switch x := 5; x {
		default:
			println(x)
		case 5:
			x += 10
			println(x)

			fallthrough			// 继续执行一下 case，但不再匹配条件表达式
		
		case 6:
			x += 20
			println(x)

			// fallthrough		// 如果在此继续 fallthrough，不会执行 default，完全按源码顺序
								// 导致“cannot fallthrough final case in switch” 错误
	}
}
```
##### 输出：
```
  15
  35
```
注意，fallthrough 必须放在 case 块结尾，可使用 break 语句阻止。
``` go
func main() {
	switch x := 5; x {
	case 5:
		x += 10
		println(x)

		if x >= 15 {
			break			// 终止，不再执行后续语句
		}

		fallthrough			// 必须是 case 块的最后一条语句
	case 6:
		x += 20
		println(x)
	}
}
```
##### 输出：
```
 15
```
某些时候，switch 还被用来替换 if 语句。被省略的 switch 条件表达式默认值为 true，继而与 case 比较表达式结果匹配。
``` go
func main() {
	switch x := 5; {		// 相当于“switch x := 5; true { ... }”
	case x > 5:
		println("a")
	case x > 0 && x <= 5:	// 不能写成“case x > 0, x <= 5”，因为多条件是 OR 关系
		println("b")
	default:
		println("z")
	}
}
```
##### 输出：
```
 b
```
***
  switch 语句也可用于接口类型匹配，详见后续章节。
***
#### for
仅有 for 一种循环语句，但常用方式都能支持。
``` go
for i := 0; i < 3; i++ {		// 初始化表达式支持函数调用或定义局部变量
}
```
``` go
for x < 10 {				// 类似 “while x < 10 {}”或“for ; x < 10; {}”
	x++
}
```
``` go
for {						// 类似 “while true {}”或“for true {}”
	break
}
```
初始化语句仅被执行一次。条件表达式中如有函数调用，须确认是否会重复执行。可能会被编译器优化掉，也可能是动态结果须每次执行确认。
``` go
func count() int {
	print("count.")
	return 3
}

func main() {
	for i, c := 0, count(); i < c; i++ {	// 初始化语句的 count 函数仅执行一次
		println("a", i)
	}

	c := 0
	for c < count() {						// 条件表达式中的 count 重复执行
		println("b", c)
		c++
	}
}
```
##### 输出：
```
count.a 0
a 1
a 2

count.b 0
count.b 1
count.b 2
```
***
	规避方式就是在初始化表达式中定义局部变量保存 count 结果。
***
允许返回单值，或用“_”忽略。
``` go
func main() {
	data := [3]string{"a", "b", "c"}

	for i := range data {			// 只返回 1st value
		println(i, data[i])
	}

	for _, s := range data {		// 忽略 1st value
		parintln(s)
	}

	for range data {				// 仅迭代，不返回。可用来执行清空channel等操作
	}
}
```
无论普通 for 循环，还是 range 迭代，其定义的局部变量都会重复使用。
``` go
func main() {
	data := [3]string{"a", "b", "c"}

	for i, s := range data {
		println(&i, &s)
	}
}
```
##### 输出：
```
  0xc8200efe98  0xc82003fec8
  0xc8200efe98  0xc82003fec8
  0xc8200efe98  0xc82003fec8
```
***
  这对闭包存在一些影响，相关详情，请阅读后续章节。
***
注意，range会复制目标数据。爱直接影响的是数组，可改用数组指针或切片类型。
``` go
func main() {
	data := [3]int{10, 20, 30}

	for i, x := range data {		// 从 data 复制品取值
		if i == 0 {
			data[0] += 100
			data[1] += 200
			data[2] += 300
		}

		fmt.Printf("x: %d, data: %d\n", x, data[i])
	}

	for i, x := range data[:] {		// 仅复制 slice，不包括底层 array
		if i == 0 {
			data[0] += 100
			data[1] += 200
			data[2] += 300
		}

		fmt.Printf("x: %d, data: %d\n", x, data[i])
	}
}
```
##### 输出：
```
  x: 10, data: 110
  x: 20, data: 220				// range 返回的依旧是复制值
  x: 30, data: 330

  x: 110, data: 210				// 当 i == 0 修改 data 时，x 已经取值，所以是 110
  x: 420, data: 420				// 复制的仅是 slice 自身，底层 array 依旧是原对象
  x: 630, data: 630
```
如果 range 目标表达式是函数调用，也仅被执行一次。
``` go
func data() []int {
	println("origin data.")
	return []int{10, 20, 30}
}

func main() {
	for i, x := range data() {
		println(i, x)
	}
}
```
##### 输出：
```
  origin data.
  0 10
  1 20
  2 30
```
建议嵌套循环不要超过2层，否则会难以维护。必要时可剥离，重构为函数。
#### goto, continue, break
对于 goto 的讨伐由来已久，仿佛它是“笨蛋”标签一般。可事实上，能在很多场合见到它的身影，就边Go源码里都有很多。
``` go
  $ cd go/src
  $ grep -r -n "goto" *
```
***
    单就Go 1.6的源码统计结果，goto语句就超出1000条有余。很惊讶，不是吗？虽然某些设计可用来消除 goto 语句，但在性能优先的场合，它能发挥积极作用。
***
使用 goto 前，须先定义标签。标签区分大小写，且未使用的标签会引发编译错误。
``` go
func main() {
start:								// 错误：label start defined and not used
	for i := 0; i < 3; i++ {
		println(i)

		if i > 1 {
			goto exit
		}
	}
	exit:
		println("exit.")
}
```
不能跳转到其他函数，或内层代码块内。
``` go
func test() {
test:
	println("test")
	println("test exit.")
}

func main() {
	for i := 0; i < 3; i++ {
	loop:
		println(i)
	}

	goto test			// 错误： label test not defined
	goto loop			// 错误： goto loop jumps into block
}
```
和 goto 定点跳转不同，break、continue 用于中断代码块执行。
- break：用于switch、for、select 语句，终止整个语句块执行。
- continue：仅用于 for 循环，终止后续逻辑，立即进入下一轮循环。
``` go
func main() {
	for i := 0; i < 10; i++ {
		if i%2 == 0 {
			continue			// 立即进入下一轮循环
		}

		if i > 5 {
			break				// 立即终止整个 for 循环
		}

		println(i)
	}
}
```
##### 输出：
```
  1
  3
  5
```
配合标签，break 和 continue 可在多层嵌套中指定目标层级。
``` go
func main() {
outer:
	for x := 0; x < 5; x++ {
		for y := 0; y < 10; y++ {
			if y > 2 {
				println()
				continue outer
			}

			if x > 2 {
				break outer
			}

			print(x, ":", y, " ")
		}
	}
}
```
##### 输出：
```
  0:0 0:1 0:2
  1:0 1:1 1:2
  2:0 2:1 2:2
```
## 第4章 函数
### 4.1 定义
函数是结构化编程的最小模块单元。它将复杂的算法过程分解为若干较小任务，隐藏相关细节，使得程序结构更加清晰，易于维护。函数被设计成相对独立，通过接收输入参数完成一段算法指令，输出或存储相关结果。因此，函数还是代码复用和测试的基本单元。
关键字 func 用于定义函数。Go 中的函数有些不太方便的限制，但也借鉴了动态语言的某些优点。
- 无须前置声明。
- 不支持命名嵌套定义（nested）。
- 不支持同名函数重载（overload）。
- 不支持默认参数。
- 支持不定长变参。
- 支持多返回值。
- 支持命名返回值。
- 支持匿名函数和闭包。

和前面曾说过的一样，左花括号不能另起一行。
``` go
func test()
{						// 错误：syntax error: unexpected semicolon or newline before {
}

func test(x int) {		// 错误：test redeclared in this block
}

func main() {
	func add(x, y int) int {	// 错误：syntax error: unexpected add, expecting {
		return x + y
	}
}
```
函数属于第一类对象，具备相同签名（参数及返回值列表）的视作同一类型。
``` go
func hello() {
	println("hello, world!")
}

func exec(f func()) {
	f()
}

func main() {
	f := hello
	exec(f)
}
```
***
    第一类对象（first-class object）指可在运行期创建，可用作函数参数或返回值，可存入变量的实体。最常见的用法就是匿名函数。
***
从阅读和代码维护的角度来说，使用命名类更加方便。
``` go
// 定义函数类型
type FormatFunc func(string, ...interface{}) (string, error)

// 如不使用命名类型，这个参数签名会长到没法看
func format(f FormatFunc, s string, a ..interface{}) (string, error) {
	return f(s, a...)
}
```
函数只能判断其是否为nil，不支持其他比较操作。
``` go
func a() {}
func b() {}

func main() {
	println(a == nil)
	println(a == b)				// 无效操作： a == b (func can only be compared to nil)
}
```
从函数返回局部变量指针是安全的，编译器会通过逃逸分析（escape analysis）来决定是否在堆上分配内存。
``` go
func test() *int {
	a := 0x100
	return &a
}

func main() {
	var a *int = test()
	println(a, *a)
}
```
##### 输出：
```
$ go build -gcflags "-l -m"			// 禁用函数内联，输出优化信息

moved to heap: a
&a escapes to heap


$ go tool objdump -s "main\.main" test		// 反汇编确认

TEXT main.main(SB) test.go
	CALL main.test(SB)

$ ./test
0xc820074000 256
```
函数内联（inline）对内存分配有一定的影响。如果上例中允许内联，那么就会直接在栈上分配内存。
```
$ go build -gcflags "-m"				// 默认优化方式，允许内联

inlining call to test
main &a does not escape

$ go tool objdump -s "main\.main" test
TEXT main.main(SB) test.go
	MOVQ $0x100, 0x10(SP)
	LEAQ 0x10(SP), BX
	MOVQ BX, 0x18(SP)
	MOVQ 0x18(SP), BX
	MOVQ BX, 0(SP)
	CALL rentime.printpointer(SB)
```
当前编译器未实现尾递归优化（tail-call optimization）。尽管Go执行栈的上限是GB规模，轻易不会出现堆栈溢出（stack overflow）错误，但依然需要注意拷贝栈的复制成本。
***
    内存管理相关内容，请阅读本书下郑“源码剖析”
***
#### 建议命名规则
在避免冲突的情况下，函数 命名要本着精简短小、望文知意的原则。
- 通常是动词和介词加上名词，例如scanWords。
- 避免不必要的缩写，printError要比printErr更好一些。
- 避免使用类型关键字，比如buildUserStruct看上去会很别扭。
- 避免歧义，不能有多种用途的解释造成误解。
- 避免只能通过大小写区分的同名函数。
- 避免与内置函数同名，这会导致误用。
- 避免使用数字，除非是特定专有名词，例如UTF8。
- 避免添加作用域提示前缀。
- 统一使用camel / pascal case拼写风格。
- 使用相同术语，保持一致性。
- 使用习惯用语，比如init表示初始化，is / has 返回布尔值结果。
- 使用反义词组命名行为相反的函数，比如 get / set 、min / max 等。
***
    函数和方法的命名规则稍有些不同。方法通过选择符调用，且具备状态上下文，可使用更简短的动词命名。
***
### 4.2 参数
Go对参数的处理偏向保守，不支持有默认值的可选参数，不支持命名实参。调用时，必须按签名顺序传递指定类型和数量的实参，就算以“_”命名的参数也不能忽略。
在参数列表中，相邻的同类型参数可合并。
``` go
func test(x, y int, s string, _ bool) *int {
	return nil
}

func main() {
	test(1, 2, "abc")		// 错误：not enough arguments in call to test
}
```
参数可视作函数局部变量，因此不能在相同层次定义同名变量。
``` go
func add (x, y int) int {
	x := 100				// 错误：no new variables on left side of :=
	var y int				// 错误： y redeclared in this block
	return x + y
}
```
***
    形参是指函数定义中的参数，实参则是函数调用时所传递的参数。形参类似函数局部变量，而实参则是函数外部对象，可以是常量、变量、表达式或函数等。
***
不管是指针、引用类型，还是其他类型参数，都是值拷贝传递（pass-by-value）。区别无非是拷贝目标对象，还是拷贝指针而已。在函数调用前，会为形参和返回值分配内存空间，并将实参拷贝开形参内存。
``` go
func test(x *int) {
	fmt.Printf("pointer: %p, target: %v\n", &x, x)		// 输出形参 x 的地址
}

func main() {
	a := 0x100
	p := &a
	fmt.Printf("pointer: %p, target: %v\n", &p, p)		// 输出实参 p 的地址

	test(p)
}
```
##### 输出：
```
  pointer: 0xc82002c020, target: 0xc82000a298
  pointer: 0xc82002c030, target: 0xc82000a298
```

***
从输出结果可以看，尽管实参和形参都指向同一目标，但传递指针时依然被复制。
***
表面上看， 指针参数的性能要更好一些，但实际上得具体分析。被复制的指针会延长目标对象生命周期，还可能会导致它被分配到堆上，那么其性能消耗就得加上堆内存分配和垃圾回收的成本。
其实在栈上复制小对象只须很少的指令即可完成，远比运行时进行堆内存分配要快得多。另外，并发编程也提倡尽可能使用不变对象（只读或复制），这可消除数据同步等麻烦。当然，如果复制成本很高，或需要修改原对象状态，自然使用指针更好。
下面是一个指针参数导致实参变量被分配到堆上的简单示例。可对比传值参数的汇编代码，从中可看出具体的差别。
``` go
func test(p *int) {
	go func() {					// 延长 p 生命周期
		println(p)
	}()
}

func main() {
	x := 100
	p := &x
	test(p)
}
```
##### 输出：
```
$ go build -gcflags "-m"					// 输出编译器优化策略

moved to heap: x
&x escapes to heap							// 逃逸

$ go tool objdump -s "main\.main" test

TEXT main.main(SB) test.go
	CALL runtime.newobject(SB)				// 在堆上为 x 分配内存
	CALL main.test(SB)
```
要实现传出参数（out），通常建议使用返回值。当然，也可继续用二级指针。
``` go
func test(p **int) {
	x := 100
	*p = &x
}

func main() {
	var p *int
	test(&p)
	println(*p)
}
```
##### 输出：
```
  100
```
如果函数参数过多，建议将其重构为一个复合结构类型，也算是变相实现可选参数和命名实参功能。
``` go
type serverOption struct {
	address			string
	port 			int
	path			string
	timeout			time.Duration
	log				*log.Logger
}

func newOption() *serverOption {
	return &serverOption {						// 默认参数
		address:	"0.0.0.0",
		port:		8080,
		path:		"/var/test",
		timeout:	time.Second * 5,
		log:		nil,
	}
}

func server(option *serverOption) {}

func main() {
	opt := newOption()
	opt.port = 8085								// 命名参数设置

	server(opt)
}
```
***
  将过多的参数独立成 option struct，既便于扩展参数集，也方便通过 newOption 函数设置默认配置。这也是代码复用的一种方式，避免多处调用时烦琐的参数配置。
***
#### 变参
变参本质上就是一个切片。只能接收一到多个同类型参数，且必须放在列表尾部。
``` go
func test(s string, a ...int) {
	fmt.Printf("%T, %v", a, a)			// 显示类型和值
}

func main() {
	test("abc", 1, 2, 3, 4)
}
```
##### 输出：
```
[] int, [1 2 3 4]
```
将切片作为变参时，须进行展开操作。如果是数组，先将其转换为切片。
``` go
func test(a ...int) {
	fmt.Println(a)
}

func main() {
	a := [3]int{10, 20, 30}
	test(a[:]...)						// 转换为 slice 后展开
}
```
既然变参是切片，那么参数复制的仅是切片自身，并不包括底层数组，也因此可修改原数据。如果需要，可用内置函数copy复制底层数据。
``` go
func test(a ...int) {
	for i := range a {
		a[i] += 100
	}
}

func main() {
	a := []int{10, 20, 30}
	test(a...)
	fmt.Println(a)
}
```
##### 输出：
```
  [110 120 130]
```
### 4.3 返回值
有返回值的函数，必须有明确的 return 终止语句。
``` go
func test(x int) int {
	if x > 0 {
		return 1
	} else if x < 0 {
		return -1
	}
}							// 错误：missing return at end of function
```
除非有 panic，或者无 break 的死循环，则无须 return 终止语句。
``` go
func test(x int) int {
	for {
		break
	}
}							// 错误：missing return at end of function
```
借鉴自动态语言的多返回值模式，函数得以返回更多状态，尤其是 error 模式。
``` go
import "errors"

func div(x, y int) (int, error) {		// 多返回值列表必须使用括号
	if y == 0 {
		return 0, errors.New("dividsion by zero")
	}
	return x / y, nil
}
```
稍有不便的是没有元组（tuple）类型，也不能用数组、切片接收，但可用 “_” 忽略掉不想要的返回值。多返回值可用作其他函数调用实参，或当作结果直接返回。
``` go
func div(x, y int) (int, error) {
	if y == 0 {
		return 0, errors.New("division by zero")
	}

	return x / y, nil
}

func log(x int, err error) {
	fmt.Println(x, err)
}

func test() (int, error) {
	return div(5, 0)				// 多返回值用作 return 结果
}

func main() {
	log(test())						// 多返回值用作实参
}
```
#### 命名返回值
对返回值命名和简短变量定义一样，优缺点共存。
``` go
func paging(sql string, index int) (count int, pages int, err error) {
}
```
从这个简单的示例可看出，命名返回值让函数声明更加清晰，同时也会改善帮助文档和代码编辑器提示。
命名返回值和参数一样，可当作函数局部变量使用，最后由 return 隐式返回。
``` go
func div(x, y int) (z int, err error) {
	if y == 0 {
		err = errors.New("division by zero")
		return
	}
	z = x / y
	return						// 相当于“return z, err”
}
```
这些特殊的“局部变量”会被不同层级的同名变量遮蔽。好在编译器能检查到此类状况，只要改为显式 return 返回即可。
``` go
func add(x, y int) (z int) {
	{
		z := x + y			// 新定义的同名局部变量，同名遮蔽
		return				// 错误：z is shadowed during return （改成"return z"即可）
	}

	return
}
```
除遮蔽外，我们还必须对全部返回值命名，否则编译器会搞不清状况。
``` go
func test() (int, s string, e error) {
	return 0, "",nil			// 错误：cannot use 0 (type int) as type string in return argument
}
```
***
  显然编译器在处理 return 语句的时候，会跳过未命名返回值，无法准确匹配。
***
如果返回值类型能明确表明其含义，就尽量不要对其命名。
``` go
func NewUser() (*User, error)
```
### 4.4 匿名函数
匿名函数是指没有定义名字符号的函数。
除没有名字外，匿名函数和普通函数完全相同。最大区别是，我们可在函数内部定义匿名函数，形成类假嵌套效果。匿名函数可直接调用，保存到变量，作为参数或返回值。
直接执行：
``` go
func main() {
	func(s sting) {
		println(s)
	}("Hello, world!")
}
```
赋值给变量：
``` go
func main() {
	add := func(x, y int) int {
		return x + y
	}

	println(add(1, 2))
}
```
作为参数：
``` go
func test(f func()) {
	f()
}

func main() {
	test(func() {
		println("hello, world!")
	})
}
```
作为返回值：
``` go
func test() func(int, int) int {
	return func(x, y int) int {
		return x + y
	}
}

func main() {
	add := test()
	println(add(1, 2))
}
```
***
  将匿名函数赋值给变量，与为普通函数提供名字标识符有着根本的区别。当然，编译器会为匿名函数生成一个“随机”符号名。
***
普通函数和匿名函数都可作为结构体字段，或经通道传递。
``` go
func testStruct() {
	type calc struct {					// 定义结构体类型
		mul func(x, y int) int			// 函数类型字段
	}

	x := calc{
		mul: func(x, y int) int {
			return x * y
		},
	}

	println(x.mul(2, 3))
}

func testChannel() {
	c := make(chan func(int, int) int, 2)

	c <- func(x, y int) int {
		return x + y
	}

	println((<-c)(1, 2))
}
```
不曾使用的匿名函数会被编译器当作错误。
``` go
func main() {
	func(s string) {		// 错误：func literal evaluated but not used
		println(s)
	}						// 此处并未调用
}
```
除闭包因素外，匿名函数也是一种常见重构手段。可将大函数分解成多个相对独立的匿名函数块，然后用相对简洁的调用完成逻辑流程，以实现框架和细节分离。
相比语句块，匿名函数的作用域被隔离（不使用闭包），不会引发外部污染，更加灵活。没有定义顺序限制，必要时可抽离，便于实现干净、清晰的代码层次。
#### 闭包
闭包（closure）是在其词法上下文中引用了自由变量的函数，或者说是函数和其引用的环境的组合体。这种说明太学术范儿了，很难理解，我们先看一个例子。
``` go
func test(x int) func() {
	return func() {
		println(x)
	}
}

func main() {
	f := test(123)
	f()
}
```
##### 输出：
```
  123
```
就这段代码而言，test返回的匿名函数会引用上下文环境变量x。当该函数在main中执行时，它依然可正确读取x的值，这种现象就称为闭包。
闭包是如何实现的？匿名函数被返回后，为何还能读取环境变量值？修改一下代码再看。
``` go
package main

func test(x int) func() {
	println(&x)

	return func() {
		println(&x, x)
	}
}

func main() {
	f := test(0x100)
	f()
}
```
##### 输出：
```
  0x82000a100
  0xc82000a100 256
```
通过输出指针，我们注意到闭包直接引用了环境变量。分析汇编代码，你会看到返回的不仅仅是匿名函数，还包括所引用的环境变量指针。所以说，闭包是函数和引用环境的组合体更加确切。
***
  本质上返回的一个funcval结构，可在runtime/runtime2.go中找到相关定义。
***
```
$ go build -gcflags "-N -l"		# 禁用内联和代码优化

$ gdb test

(gdb) b 6						# 设置断点后，执行
(gdb) b 13
(gdb) r

(gdb) info locals				# 进入 test 函数，获取环境变量 x 地址
&x = 0x82000a130

(gdb) c							# 继续执行，回到 main 函数

(gdb) disas
Dump of assembler code for function main.main:
   0x000000000000213f <+15>:	sub		rsp, 0x18
   0x0000000000002143 <+19>:	mov		QWORD PTR [rsp], 0x100
   0x000000000000214b <+27>:	call	0x2040 <main.test>
   0x0000000000002150 <+32>:	mov		rbx, QWORD PTR [rsp+0x8]    # test 返回值
   0x0000000000002155 <+37>:	mov		QWORD PTR [rsp+0x10],rbx
=> 0x000000000000215a <+42>:	mov		rbx,QWORD PTR [rsp+0x10]
   0x000000000000215f <+47>:	mov		rbx,rbx                     # 保存到 rdx 寄存器
   0x0000000000002162 <+50>:	mov		rbx,QWORD PTR [rdx]
   0x0000000000002165 <+53>:	call	rbx
   0x0000000000002167 <+55>:	add		rsp,0x18
   0x000000000000216b <+59>:	ret

(gdb) x/2xg $rbx				# 包含匿名函数和环境变量地址
0xc82000a140:	0x0000000000002180  0x000000c82000a130

(gdb) s							# 继续，进入匿名函数
Breakpoint 1, main.test.func1

(gdb) disas
Dump of assembler code for function main.test.func1:
	0x000000000000218f <+15>:	sub		rsp,0x18
	0x0000000000002193 <+19>:	mov		rbx,QWORD PTR [rdx+0x8]		# 经 rdx 读取环境变量地址
	0x0000000000002197 <+23>:	mov		QWORD PTR [rsp+0x10],rbx
	0x000000000000219c <+28>:	mov		rbx,QWORD PTR [rsp+0x10]
	0x00000000000021a1 <+33>:	mov		QWORD PTR [rsp+0x8],rbx
	0x00000000000021a6 <+38>:	call	0x23ac0 <runtime.printlock>
	0x00000000000021ab <+43>:	mov		rbx,QWORD PTR [rsp+0x8]
	0x00000000000021b0 <+48>:	mov		QWORD PTR [rsp],rbx
	0x00000000000021b4 <+52>:	call	0x244a0 <runtime.printpointer>

(gdb) x/1xg $rdx+0x8
0xc82000a148:	0x0000000c82000a130
```
正因为闭包通过指针引用环境变量，那么可能会导致其生命周期延长，甚至被分配到堆内存。另外，还有所谓“延迟求值”的特性。
``` go
func test() []func() {
	var s []func()

	for i := 0; i < 2; i++ {
		s = append(s, func() {			// 将多个匿名函数添加到列表
			println(&i, i)
		})
	}

	return s							// 返回匿名函数列表
}

func main() {
	for _, f := range test() {			// 迭代执行所有匿名函数
		f()
	}
}
```
##### 输出：
```
  0x82000a078  2
  0x82000a078  2
```
对这个输出结果不必惊讶。很简单，for循环复用局部变量 i，那么每次添加的匿名函数引用的自然是同一变量。添加操作仅仅是将匿名函数放入列表，并未执行。因此，当main执行这些函数时，它们读取的是环境变量 i 最后一次循环时的值。不是 2，还能是什么？
解决方法就是每次用不同的环境变量或传参复制，让各自闭包环境各不相同。
``` go
func test() []func() {
	var s []func()

	for i := 0; i < 2; i++ {				// x 每次循环都重新定义
		x := i
		s = append(s, func() {
			println(&x, x)
		})
	}
	return s
}
```
##### 输出：
```
 0xc820006e000  0
 0xc820006e008  1
```
多个匿名函数引用同一环境变量，也会让事情变得更加复杂。任何的修改行为都会影响其他函数取值，在并发模式下可能需要做同步处理。
``` go
func test(x int) (func(), func()) {			// 返回两个匿名函数
	return func() {
		println(x)
		x += 10								// 修改环境变量
	}, func() {
		println(x)							// 显示环境变量
	}
}

func main() {
	a, b := test(100)
	a()
	b()
}
```
##### 输出：
```
 100
 110
```
闭包让我们不用传递参数就可读取或修改环境状态，当然也要为此付出额外代价。对于性能要求较高的场合，须慎重使用。

### 4.5 延迟调用
语句`defer`向当前函数注册稍后执行的函数调用。这些调用被称作延迟调用，因为它们走到当前函数执行结束前才被执行，常用于资源释放、解除锁定，以及错误处理等操作。
``` go
 func main() {
	 f, err := os.Open("./main.go")
	 if err != nil {
		 log.Fatalln(err)
	 }

	defer f.Close()					// 仅注册，直到main退出前才执行

	... do something ...
 }
```
注意，延迟调用注册的是调用，必须提供执行所需参数（哪怕为空）。参数值在注册时被复制并缓存起来。如对状态敏感，可改用指针或闭包。
























(第86页)
