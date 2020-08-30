一、JS表达式
1、语法结构
优先级：
Member（a.b|a[b]|foo`string`|suoer.b|super['b']|new.target|new Foo()）
New(new Foo)
Call(foo()|super()|foo()['b']|foo().b|foo()`abc`)
Left Handside & Right Handside
Unary(delete|void foo()|typeof a|+ a|- a|!a|await a)单目运算符
Exponental(右结合运算符)2*2*2
Multiplicative(*/%)
Additive(+-)
Shift(<< >> >>>)
Relationship(< > <= >= instanceof in)
Equality(== != === !==)
Bitwise(&^|)
Logical(&& ||)
Conditional(? :) 具有短路原则和C语言不一致
标准类型：
Reference（标准中的类型而不是语言中的类型）=> Object.delete Object.assign

2、类型转换

|           | Number         | String            | Boolean  | Undefined | Null | Object | Symbol |
| --------- | -------------- | ----------------- | -------- | --------- | ---- | ------ | ------ |
| Number    | -              |                   | 0 false  | X         | X    | Boxing | X      |
| String    |                | -                 | "" false | X         | X    | Boxing | X      |
| Boolean   | true 1 false 0 | 'true' 'false'    | -        | X         | X    | Boxing | X      |
| undefined | NaN            | 'undefined'       | false    | -         | X    | X      | X      |
| Null      | 0              | 'null'            | false    | X         | -    | X      | X      |
| Object    | valueOf        | valueOf/tosString | true     | X         | X    | -      | X      |
| Symbol    | X              | X                 | X        | X         | X    | Boxing | -      |

3、拆箱Unboxing
Symbol.toPrimitive的优先级最高，否则转number 会先调用valueOf，string运算先调用toString
4、装箱Boxing

| 类型      | 对象                      | 值           |
| ------- | ----------------------- | ----------- |
| Number  | new Number(1)           | 1           |
| String  | new String("a")         | "a"         |
| Boolean | new Boolean(true)       | true        |
| Symbol  | new Object(Symbol("a")) | Symbol("a") |

二、JS语句
Completion Record（语句完成状态记录）

	[[type]]:normal, break, continue, return, or throw
	[[value]]: 基本类型
	[[target]]: label
简单语句：
ExpressionStatement
EmptyStatement：空
DebuggerStatement：调试
ThrowStatement:抛出异常
ContinueStatement：结束单次循环
BreakStatement：结束整个循环
	[[type]]:break continue
	[[value]]:- -
	[[target]]:label
	带label的break可以跳出多层循环:break
ReturnStatement：返回
复合语句：
BlockStatement
	[[type]]:normal
	[[value]]:- -
	[[target]]:- -
IfStatement
SwitchStatement(js中不建议写，和ifelse一样)
IterationStatement
	while()
	do while();
	for(; ;)
	for( in )
	for( of )
	for await (of)
WithStatement
LabelledStatement
TryStatement（用的不是block声明）
声明：
FunctionDeclaration
GeneratorDeclaration
AsyncFunctionDeclaration
AsyncGeneratorDeclaration
VariableStatement
ClassDeclaration
LexicalDeclaration
预处理：
function的声明不论在哪都会当做第一行处理，var的声明会放在第一行处理但是赋值还是原来的地方
const和let声明位置生效
注：所有的声明都是有预处理机制

三、Js结构化
1、宏任务和微任务
Js执行粒度（运行时）：
宏任务
微任务（Promise）
函数调用（Execution Context）
语句/声明（Completion Record）
表达式（Reference）
直接量/变量/this......

事件循环：

函数调用：入栈出栈