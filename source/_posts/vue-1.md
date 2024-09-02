---
layout: text
title: vue入门教程
date: 2023-09-15 23:53:17
tags: 
	- 精选 
	- vue
cover: img\posts\picture\vue.png
description: vue入门教程
recommend: true
---

 <img src= "..\img\posts\picture\vue.png" alt="vue" style="zoom:33%;" />

## 一、Vue简介

### 1.1 简介

```
Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式的js框架，发布于 2014 年 2 月。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库（如：vue-router，vue-resource，vuex）或既有项目整合。
```

### 1.2 MVVM 模式的实现者——双向数据绑定模式

```
Model：模型层，在这里表示 JavaScript 对象
View：视图层，在这里表示 DOM（HTML 操作的元素）
ViewModel：连接视图和数据的中间件，Vue.js 就是 MVVM 中的 ViewModel 层的实现者
```

![1](img\posts\picture\1.png)

```
在 MVVM 架构中，是不允许 数据 和 视图 直接通信的，只能通过 ViewModel 来通信，而 ViewModel 就是定义了一个Observer 观察者

ViewModel 能够观察到数据的变化，并对视图下对应的内容进行更新
ViewModel 能够监听到视图的变化，并能够通知数据发生改变
```

至此，我们就明白了，Vue.js 就是一个 MVVM 的实现者，他的核心就是实现了 DOM 监听 与 数据绑定

### 1.3 其它 MVVM 实现者

```
AngularJS
简单介绍一下，AngularJS诞生于2009年，由Misko Hevery 等人创建，后为Google所收购。是一款优秀的前端JS框架，已经被用于Google的多款产品当中。AngularJS有着诸多特性，最为核心的是：MVVM、模块化、自动化双向数据绑定、语义化标签、依赖注入等等。
ReactJS
React引入了虚拟DOM（Virtual DOM）的机制：在浏览器端用Javascript实现了一套DOM API。基于React进行开发时所有的DOM构造都是通过虚拟DOM进行，每当数据变化时，React都会重新构建整个DOM树，然后React将当前整个DOM树和上一次的DOM树进行对比，得到DOM结构的区别，然后仅仅将需要变化的部分进行实际的浏览器DOM更新。
微信小程序
微信小程序的视图层和数据层就是通过MVVM进行绑定的。
```

### 1.4 为什么要使用 Vue.js

```
轻量级，体积小是一个重要指标。Vue.js 压缩后有只有 20多kb （Angular 压缩后 56kb+，React 压缩后 44kb+）
移动优先。更适合移动端，比如移动端的 Touch 事件
易上手，学习曲线平稳，文档齐全
吸取了 Angular（模块化）和 React（虚拟 DOM）的长处，并拥有自己独特的功能，如：计算属性
开源，社区活跃度高
```

### 1.5 Vue.js 的两大核心要素

#### 1.5.1 数据驱动

![2](img\posts\picture\2.png)

​	当你把一个普通的 JavaScript 对象传给 Vue 实例的 data 选项，Vue 将遍历此对象所有的属性，并使用 Object.defineProperty 把这些属性全部转为 getter/setter。Object.defineProperty 是 ES5 中一个无法 shim 的特性，这也就是为什么 Vue 不支持 IE8 以及更低版本浏览器。
这些 getter/setter 对用户来说是不可见的，但是在内部它们让 Vue 追踪依赖，在属性被访问和修改时通知变化。这里需要注意的问题是浏览器控制台在打印数据对象时 getter/setter 的格式化并不同，所以你可能需要安装 vue-devtools 来获取更加友好的检查接口。
每个组件实例都有相应的 watcher 实例对象，它会在组件渲染的过程中把属性记录为依赖，之后当依赖项的 setter 被调用时，会通知 watcher 重新计算，从而致使它关联的组件得以更新。

#### 1.5.2 组件化

```
页面上每个独立的可交互的区域视为一个组件
每个组件对应一个工程目录，组件所需的各种资源在这个目录下就近维护
页面不过是组件的容器，组件可以嵌套自由组合（复用）形成完整的页面
```

## 二、Vue的初体验

### 2.1 在页面引入vue的js文件即可。

```
注意：cdn是一种加速策略，能够快速的提供js文件
```

```js
<script src="https://cdn.bootcss.com/vue/2.5.17-beta.0/vue.min.js"></script>
```

### 2.2 在页面中绑定vue元素

```js
创建一个div，id是app
<div id="app"></div>
```

#### 2.3 创建vue对象，设计对象的内容

其中该vue对象，绑定了页面中id是app的那个div

```js
<script>
		new Vue({
			el:"#app",
			data:{
				title:"hello vue!",
                args1:"hi!",
                age:18,
                flag:true
			}
		});
</script>
```

el: element的简称，也就是Vue实例挂载的元素节点，值可以是 CSS 选择符，或实际 HTML 元素，或返回 HTML 元素的函数。

data: 用于提供数据的对象，里面存放键值对数据。

### 2.4 在页面的元素中使用插值表达式来使用vue对象中的内容

```js
<div id="app">
	{{ title }}
</div>
```

## 三、 插值表达式

插值表达式的作用是在View中获得Model中的内容
Model中的内容如下：

```js
new Vue({
		el:"#app",
		data:{
			title:"hello world!"
		},
		methods:{
			sayHello:function(){
				return "hello vue";
			}
		}
	});
```

### 3.1 简单使用插值表达式获取数据

```js
<div id="app">
	{{title}}
</div>
```

此时，页面上将会显示"Hello world!"]

### 3.2 在插值表达式中获取数组中的内容

```js
<div id="app">
	{{[1,2,3,4][2]}}
</div>
```

此时，页面上会显示“3”，也就是数组中的第三个元素被获取。

### 3.3 使用插值表达式获取对象中的属性

```js
<div id="app">
	{{ {"name":"xiaoyu","age":20}.age }}
</div>
```

此时，页面上会显示“20”，也就是对象中age属性的值。

### 3.4 使用插值表达式调用Vue中的方法

```js
<div id="app">
		{{ sayHello()}}
</div>
```

## 四、Vue对象总结

​	Vue.js通过加载js，实现对页面的快速渲染。vue封装的js该如何使用？ 就必须了解MVVM双向数据绑定模式。Vue将视图层和数据层分离，通过MVVM建立视图层和数据层的连接。其中，插值表达式是一种连接方式，可以通过插值表达式以多种方式，快速的从数据层获取数据并展示在视图层上。数据层Vue对象，也是由很多部分组成，比如之前介绍的el，data，methods等，以及之后要介绍的mount，computed等。

## 五、Vue的分支 v-if

### 5.1 v-if

Vue中的分支语句v-if非常好理解，逻辑跟Java中的if-else相同。v-if语句块包含以下内容：

- v-if

- v-else

- v-else-if

接下来以一个简单例子即可理解：

```html
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<div id="app">
			<p v-if="flag">
				今天天气很舒服！
			</p>
			<p v-else-if="rich">
				今天天气很燥热！晚上要去放松一下！
			</p>
			<p v-else="rich">
				晚上只能自嗨！
			</p>
		</div>
		
	</body>
	<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
	<script>
		
		new Vue({
			
			el:'#app',
			data:{
				flag:false,
				rich:false
			},
			methods:{
				
			}
		});
		
		
	</script>
</html>
```

从这个例子可以看出，vue对象中的data提供了分支的条件。根据条件，如果是true，则v-if的内容就会显示，反之不显示。

### 5.2 v-show

v-if和v-show之间有着看似相同的效果，但优化上却有区别。先看下面这个例子：

```html
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		
			<p v-show="rich">
				有钱！
			</p>
			<p v-if="rich">
				有钱！
			</p>
			<button type="button" @click="rich=!rich">今晚彩票开奖</button>
		</div>
		
	</body>
	<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
	<script>
		
		new Vue({
			
			el:'#app',
			data:{
				flag:false,
				rich:false
			},
			methods:{
				
			}
		});
		
		
	</script>
</html>
```

​	通过点击“今晚彩票开奖”按钮，能切换rich的值，此时发现，v-if和v-show的显示状态都会来回切换。看起来是一样的，但通过查看控制台代码发现，**v-show实际会将p标签的css样式的display属性设为none来达到隐藏的效果**。

​	而**v-if是直接在页面上添加和删除p标签来达到效果，因此v-show在反复切换的应用场景下，效率比v-if更高**。

## 六、Vue的循环 v-for

Vue中的循环关键字并没有Java的那么多，只有v-for，但用法上有多种。接下来我们来逐一介绍。

### 6.1 普通的for循环

```html
<body>
<div id="app">
    <ul>
        <li v-for="a in args">{{a}}</li>
    </ul>
</div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
    new Vue({
        el:'#app',
        data:{
            args:[1,2,3,4,5,6]
        }
    });
</script>
```

在这个例子中，数据源提供了一个数组。视图层通过v-for来循环输出多个li标签，非常简单。

### 6.2 带着索引的for

```html
<body>
<div id="app">
    <ul>
        <li v-for=" (a,i)  in  args" :key='i'>{{i}}{{a}}</li>
    </ul>
</div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
    new Vue({
        el:'#app',
        data:{
            args:[1,2,3,4,5,6]
        }
    });
</script>
```

此时的i就是每次循环的循环变量 ，从0开始一直到元素个数-1

### 6.3 遍历一个对象中的信息： v、k、i

```html
<body>
<div id="app">
    <ul>
        <li v-for="(v,k,i) in student">{{i+1}}--{{k}}--{{v}}</li>
    </ul>
</div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
    new Vue({
    	el:'#app',
    	data:{
       	 	student:{
            	username:'小鱼',
				age:20,
				girl:'如花'
        	}
    	}
	});
</script>
```

v、k、i 这几个字符可以自己定义，分别表示每次循环内容的值、键、序号。

- v: 循环中每条数据的值  小鱼、20、如花

- k: 循环中每天数据的键  username、age、girl

- i: 循环的序号，从0开始

### 6.4 遍历一个对象数组：嵌套的for循环

```html
<body>
<div id="app">
    <ul>
        <li v-for=" student in students">
        	<span v-for="(v,k,i) in student">{{i+1}}--{{k}}--{{v}}</span>
    	</li>
    </ul>
</div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
    new Vue({
    	el:'#app',
    	data:{
       	 	students:[
            	{
                	name:'xiaoming',
                	age:20
            	},
            	{
                	name:'xiaowang',
                	age:21
            	}
        	]
    	}
	});
</script>
```

​	可以清楚的看到，此时数据源是一个student数组，通过两层v-for循环，外层遍历数组中的每个student对象，内层v-for遍历每个对象的v、k、i。
页面效果如下：

![3](img\posts\picture\3.png)

## 七、Vue的属性绑定

Vue提供了多个关键字，能快速的将数据对象中的值绑定在视图层中。

### 7.1 v-model

通过v-model将标签的value值与vue对象中的data属性值进行绑定。

```html
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div id="app">
			<input type="text" v-model="title">
			{{title}}
		</div>
	</body>
	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	<script type="text/javascript">
		new Vue({
			el:'#app',
			data:{
				title:"hello vue"
			}
			
		})
	</script>
</html>
```

此时input标签中加入了“v-model='title'”，表示input的value值与vue对象中的title属性绑定，当在input输入框中输入内容会实时修改title的值。于是{{title}}插值表达式能实时输出input输入框内的值。

### 7.2 v-bind

我们知道插值表达式是不能写在html的标签的属性内的，那如果一定要用vue中的属性作为html标签的属性的内容，就可以通过v-bind进行属性绑定。

```html
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div id="app">
			<a v-bind:href="link"></a>
		</div>
	</body>
	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	<script type="text/javascript">
		new Vue({
			el:'#app',
			data:{
				link:'http://www.baidu.com'
			}
		})
	</script>
</html>
```

这样，a标签内的href属性就可以使用vue对象中的属性值。
注意： v-bind也可以简写，使用冒号“:”来代替。

```html
<a v-bind:href='link'></a>  ==>  <a :href='link'>
```

## 八、Vue的事件绑定

关于事件，要把握好三个步骤：设参、传参和接参。

```html
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div id="app">
			sum={{sum}}<br/>
			{{sum>10?'总数大于10':'总数不大于10'}}<br/>
			<button type="button" @click="increase(2)">增加</button>
		</div>
	</body>
	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	<script type="text/javascript">
		new Vue({
			el:'#app',
			data:{
				sum:0
			},
			methods:{
				increase:function(s){
					this.sum+=s
				}
			}
		})
	</script>
</html>
```

从这里例子中：

- 设参：

  ```html
  <html>
  	<head>
  		<meta charset="utf-8" />
  		<title></title>
  	</head>
  	<body>
  		<div id="app">
  			sum={{sum}}<br/>
  			{{sum>10?'总数大于10':'总数不大于10'}}<br/>
  			<button type="button" @click="increase(2)">增加</button>
  		</div>
  	</body>
  	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  	<script type="text/javascript">
  		new Vue({
  			el:'#app',
  			data:{
  				sum:0
  			},
  			methods:{
  				increase:function(s){
  					this.sum+=s
  				}
  			}
  		})
  	</script>
  </html>
  ```

  

- 传参：

- ```html
  increase:function(s)
  ```

- 接参：

  ```
  this.sum+=s
  ```

接下来我们来看一下VUE中如何进行事件绑定。

### 8.1 v-on

通过配合具体的事件名，来绑定vue中定义的函数

```html
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div id="app">
			<input type="text" v-on:click="changeMajor"  />
		</div>
	</body>
	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	<script type="text/javascript">
		new Vue({
    		el:'#app',
    		data:{
        		major:'java'
    		},
    		methods:{
        		sayHi:function(){
            		alert("HELLO VUE!");
        		},
        		changeMajor:function(){
            		console.log("change Title")
        		}
    		}
	</script>
</html>
```

此时，该按钮，在点击时将会调用Vue对象中定义的changeMajor方法。
注意： v-on也可以简写，使用"@"替代。

```html
<input type="text" @click="changeMajor"  />
```

### 8.2 事件修饰符

可以使用Vue中定义好的事件修饰符，快速达到效果。查看以下例子：

```html
<html>
	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<body>
		<div id="app">
			<p @mousemove="mm">
				x:{{x}}
				y:{{y}}
				<span @mousemove.stop>鼠标移动到此即停止</span>
			</p>
		</div>
	</body>
	<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
	<script type="text/javascript">
		new Vue({
			el:'#app',
			data:{
				x:0,
				y:0
			},
			methods:{
				mm:function(event){
					this.x = event.clientX;
					this.y = event.clientY;
				},
				stopm:function(event){
					event.stopPropagation();
				}	
			}
		})
	</script>
</html>
```

当鼠标经过P标签区域内时，区域内就会显示X和Y轴的坐标，如果经过P标签内的Span标签内时，此时会调用事件属性mousemove.stop预定的效果，鼠标移动的效果将会被取消，X和Y不再显示信息。

### 8.3计算属性：computed

#### 8.3.1 什么是计算属性

计算属性的重点突出在 属性 两个字上（属性是名词），首先它是个 属性 其次这个属性有 计算 的能力（计算是动词），这里的 计算 就是个函数；简单点说，它就是一个能够将计算结果缓存起来的属性（将行为转化成了静态的属性），仅此而已；

#### 8.3.2 计算属性与方法的区别

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>布局篇 计算属性</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js"></script>
</head>
<body>
<div id="vue">
    <p>调用当前时间的方法：{{currentTime1()}}</p>
    <p>当前时间的计算属性：{{currentTime2}}</p>
</div>
<script type="text/javascript">
    var vm = new Vue({
        el: '#vue',
        data: {
            message: 'Hello Vue'
        },
        methods: {
            currentTime1: function () {
                return Date.now();
            }
        },
        computed: {
            currentTime2: function () {
                this.message;
                return Date.now();
            }
        }
    });
</script>
</body>
</html>
```

说明

- methods：定义方法，调用方法使用 currentTime1()，需要带括号

- computed：定义计算属性，调用属性使用 currentTime2，不需要带括号；this.message 是为了能够让 currentTime2 观察到数据变化而变化
- 注意：methods 和 computed 里不能重名

#### 8.3.3 测试效果

仔细看图中说明，观察其中的差异

![4](img\posts\picture\4.png)

#### 8.3.4 结论

调用方法时，每次都需要进行计算，既然有计算过程则必定产生系统开销，那如果这个结果是不经常变化的呢？此时就可以考虑将这个结果缓存起来，采用计算属性可以很方便的做到这一点；计算属性的主要特性就是为了将不经常变化的计算结果进行缓存，以节约我们的系统开销

## 九、Vue的组件化

### 9.1 什么是“组件化”

Vue的组件化设计思想借鉴了Java的面向对象思想。Java认为万物皆对象，在Vue中，万物皆组件。
也就是说，在实际的vue项目中，以及使用了Vue框架的项目中，Vue的对象都会以组件的形式出现，能被反复使用。
要想实现组件化，需要在页面中注册组件：关于注册的方式有两种，分别是全局注册和本地注册。

#### 9.1.1 组件的全局注册

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件的全局注册</title>
</head>
<body>
    <div id="app">
        <model1></model1>
        <model1></model1>
        <model1></model1>
    </div>
        <hr/>
    <div id="app1">
        <model1></model1>
        <model1></model1>
        <model1></model1>
    </div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
	//通过Vue.component实现组件的全局注册，全局注册后的组件可以被重复使用。
    Vue.component("model1",{
        template:"<div><h1>{{title}}</h1><button type='button' @click='btnfn'>点我</button></div>",
        data:function(){
            return {
                title:"hello vue"
            }
        },
        methods:{
            btnfn:function(){
                alert("hello !!!");
            }
        }
    });
    new Vue({
        el:'#app'
    })
    new Vue({
        el:'#app1'
    })
</script>
</html>
```

#### 9.1.2 组件的本地注册

vue的全局注册，也就意味着在页面的任意一个被vue绑定过的div中，都可以使用全局注册了的vue组件。
但是，如果是对vue组件进行本地注册，那么在其他被vue绑定的div中，不能使用该组件。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>vue组件的本地(局部)注册</title>
</head>
<body>
    <div id="app">
        <model11></model11>
    </div>
	<hr/>
    <!--在这里使用组件model11会报错-->
    <div id="app1">
        <model11></model11>
    </div>
</body>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.js"></script>
<script>
    new Vue({
        el:'#app',
        components:{
            "model11":{
                template:"<div><h1>{{title}}</h1><button type='button' @click='btnfn'>点我</button></div>",
                data:function(){
                    return {
                        title:"hello vue"
                    }
                },
                methods:{
                    btnfn:function(){
                        alert("hello !!!");
                    }
                }
            }
        }
    })
    new Vue({
        el:'#app1'
    })
</script>
```

#### 9.1.3 小结

这是一个完整的Vue组件。该组件包含了三个部分：template（html视图层内容）、script（Model层）、style（CSS样式）。这样封装好的组件可以被复用，也可以作为其他组件的组成部分而被封装——Java的面向对象再次体现。

特点1： template标签内，必须有且只能有一个根标签。
特点2： componet中注册的组件中的data，必须是已函数的形式。
如下：

```
data:function(){
     return {
           title:"hello vue"
     }
 }
```

### 9.2 组件的生命周期

Vue中的组件也是有生命周期的。一个Vue组件会经历：初始化、创建、绑定、更新、销毁等阶段，不同的阶段，都会有相应的生命周期钩子函数被调用。注意生命周期跟methods方法同级！

```html
<html>
	<head>
		<meta charset="UTF-8">
		<title>生命周期</title>
	</head>
	<body>
		<div id="app1">
			{{title}}
			<button type="button" @click="changeTitle">change title</button>
			<button type="button" @click="destroy">destroy</button>
		</div>
	</body>
	<script src="https://cdn.bootcss.com/vue/2.5.17-beta.0/vue.min.js"></script>
	<script>
		new Vue({
			el:"#app1",
			data:{
				title:"this is title"
			},
			methods:{
				changeTitle:function(){
					this.title= "new title";
				},
				destroy:function(){
					this.$destroy();
				}
			},
			beforeCreate(){
				console.log("beforeCreate")
			},
			created(){
				console.log("created")
			},
			beforeMount(){
				console.log("beforeMount")
			},
			mounted(){
				console.log("mounted")
			},
			beforeUpdate(){
				console.log("beforeUpdate")
			},
			updated(){
				console.log("updated")
			},
			beforeDestroy(){
				console.log("beforeDestory")
			},
			destroyed(){
				console.log("destory")
			}
		})
	</script>
</html>
```

组件的生命周期钩子

<img src="..\img\posts\picture\5.png" alt="5" style="zoom: 300%;" />

## 十、使用Vue-Cli搭建Vue项目

### 10.1 什么是vue-cli

cli: Command Line 命令行工具，vue-cli就是vue的命令行工具，也称之为脚手架，使用vue-cli提供的各种命令可以拉取、创建、运行我们需要使用到的框架，比如webpack、Element UI、Element Admin等等。那么要想使用vue-cli命令，需要先安装node.js。

### 10.2 node.js的介绍及安装

node.js的介绍:node.js提供了前端程序的运行环境，可以把node.js理解成是运行前端程序的服务器。

node.js的安装:从官网下载安装即可：http://nodejs.cn/download/

测试node.js是否安装成功： 在DOS窗口中输入“node -v” 查看版本，如果看到版本，就表示安装成功。

### 10.3 使用node.js安装vue-cli

使用如下命令安装vue-cli

```
npm install vue-cli -g
```

- npm： 使用node.js的命令

- install： 安装

- vue-cli： 要安装的vue-cli

- -g： 全局安装

  如果使用npm官方镜像速度比较慢，可以使用淘宝镜像来安装：

  ```
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  ```

  

之后使用npm命令时就可以替换成cnpm

### 10.4 使用vue-cli下载项目骨架搭建我们的项目

就像maven一样，vue为我们提供了一些官方项目骨架。使用vue list命令可以列出当前官方提供的骨架，可以使用这些骨架来快速搭建出项目。

```
vue list
```

### 10.5 创建项目目录并打开

```
mkdir e:/my-vue-project
cd e:/my-vue-project
```

### 10.6 使用Webpack骨架快速创建项目

在my-vue-project目录中使用以下命令下载项目骨架

```
vue init webpack my-project1
```

- webpack: 骨架名称

- my-project1: 项目名称

  

进入到my-project1文件夹内后，使用以下命令来运行项目。

```
npm run dev
```

项目目录及各目录介绍如下：

![6](img\posts\picture\6.png)

### 10.7 webpack项目的几个常用命令

- npm install
  在运行和调试项目前，一般都需要先执行该命令，目的是安装项目运行所需要的环境。

- npm run dev
  以调试的方式运行项目

- npm run build
  生成用于项目部署所需的最小资源，生成的内容存放在build文件夹内。

