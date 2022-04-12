# Vue 3.0 笔记

## 一 .Vue介绍

Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。

传统的网站开发一般采用HTML+CSS+JS作为技术架构，而vue立足于其上，以模板语法为基础，以数据绑定和组件化开发为核心，极大的简化了开发流程。
使用vue技术栈，可以在几分钟内搭建出一个完整的前端项目。

现在，很多项目采用这样的架构，后台只负责数据的存储和组装，而前端负责业务逻辑层和视图层的全部工作。

Vue 是利用模版语法来渲染页面的，这也称做声明式渲染。Vue 好上手的重要原因也是因为这个，因为它符合了前端开发者的习惯。

Vue 将 HTML、CSS、JS 全部整合在同一个文件 .vue 中，以组件化应用构建的方式来组织代码，从语法特性上鼓励 “高内聚、低耦合” 的设计理念，让代码组织变得更加合理，提升了可读性与逻辑性。

1). 一位华裔前Google工程师(尤雨溪)开发的前端js库
2). 作用: 动态构建用户界面
3). 特点:
* 遵循MVVM模式
* 编码简洁, 体积小, 运行效率高, 移动/PC端开发
* 它本身只关注UI, 可以轻松引入vue插件和其它第三库开发项目
4). 与其它框架的关联:
* 借鉴angular的模板和数据绑定技术
* 借鉴react的组件化和虚拟DOM技术
5). vue包含一系列的扩展插件(库):
* vue-cli: vue脚手架-（帮我们下载依赖）
* vue-resource(axios): ajax请求
* vue-router: 路由
* vuex: 状态管理
* element-plus: 基于vue的组件库

MVVM框架

![MVVM](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204122036884.png)vue是MVVM框架；

1. M: Model数据层；
2. V: View视图层；
3. VM: 视图数据连接层

## 二. 创建应用基本介绍

### 基本使用：

1. 引入vue.js;
2. 创建Vue实例对象, 指定选项(配置)对象
3. 在页面模板中使用{{}}或vue指令

案例:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="utf-8">
    <title></title>

    <body>
        <div id="app">
            {{message}}{{hh}}
        </div>
        <script src="https://unpkg.com/vue@next"></script>

        <script>
            const app = {
                data() {
                    return {
                        hh: 'vue',
                        message: 'Hello'
                    }
                }
            }
            const APP = Vue.createApp(app).mount("#app");
        </script>
    </body>

</html>
```

使用Vue的过程就是定义MVVM各个组成部分的过程的过程。

1. **定义View**
2. **定义Model**
3. **创建一个Vue实例或"ViewModel"，它用于连接View和Model**

在创建Vue实例时，需要传入一个**选项对象**，选项对象可以包含数据、挂载元素、方法、模生命周期钩子等等。

data return 的message **指向model**

const  APP = Vue.createApp(app)   **创建app vue实例**

mount("#app")    **指向 view**

### 双向绑定 :



```html
<div id="app">
	<p>{{ message }}</p>
	<input type="text" v-model="message"/>
</div>
```

将message绑定到文本框，当更改文本框的值时

## 三.安装与创建运行项目

Vue.js 设计的初衷就包括可以被渐进式地采用。这意味着它可以根据需求以多种方式集成到一个项目中。

将 Vue.js 添加到项目中主要有四种方式：

1. 在页面上以 [CDN 包](https://v3.cn.vuejs.org/guide/installation.html#cdn)的形式导入。
2. 下载 JavaScript 文件并[自行托管](https://v3.cn.vuejs.org/guide/installation.html#下载并自托管)。
3. 使用 [npm](https://v3.cn.vuejs.org/guide/installation.html#npm) 安装它。
4. 使用官方的 [CLI](https://v3.cn.vuejs.org/guide/installation.html#命令行工具-cli) 来构建一个项目，它为现代前端工作流程提供了功能齐备的构建设置 (例如，热重载、保存时的提示等等)

###  CDN

对于制作原型或学习，你可以这样使用最新版本：

```html
<script src="https://unpkg.com/vue@next"></script>
```

### npm

在用 Vue 构建大型应用时推荐使用 npm 安装[[1\]](https://v3.cn.vuejs.org/guide/installation.html#footnote-1) 。npm 能很好地和诸如 [webpack](https://webpack.js.org/) 或 [Rollup](https://rollupjs.org/) 模块打包器配合使用。

```bash
# 最新稳定版
$ npm install vue@next
```

### vuecli

```bash
yarn global add @vue/cli
# 或
npm install -g @vue/cli
```

运行以下命令来创建一个新项目：

```bash
vue create hello-world
```

运行、发布

```bash
# 运行 （可以监控文件修改，自动刷新客户端）
npm run serve

# 打包发布。（默认发布到dist目录下）
npm run build
```

## 四. 指令介绍

面用到的`v-model`是Vue.js常用的一个指令，那么指令是什么呢？

**Vue.js的指令是以v-开头的，它们作用于HTML元素，指令提供了一些特殊的特性，将指令绑定在元素上时，指令会为绑定的目标元素添加一些特殊的行为，我们可以将指令看作特殊的HTML特性（attribute）。**

Vue.js提供了一些常用的内置指令，接下来我将介绍以下几个内置指令：

- v-if指令
- v-show指令
- v-else指令
- v-for指令
- v-bind指令
- v-on指令

Vue.js具有良好的扩展性，我们也可以开发一些自定义的指令，后面的文章会介绍自定义指令。

### v-if  v-else指令

`v-if`是条件渲染指令，它根据表达式的真假来删除和插入元素，它的基本语法如下：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        <h1 v-if="awesome">Vue is awesome!</h1>
        <h1 v-else>Oh no 😢</h1>
        <button @click="ck">
            click
        </button>
        <div v-if="type === 'A'">
            A
        </div>
        <div v-else-if="type === 'B'">
            B
        </div>
        <div v-else-if="type === 'C'">
            C
        </div>
        <div v-else>
            Not A/B/C
        </div>
        <!-- 另一个用于条件性展示元素的选项是 v-show 指令。用法大致一样： -->

        <h1 v-show="ok">Hello!</h1>
        <!-- 不同的是带有 v-show 的元素始终会被渲染并保留在 DOM 中。v-show 只是简单地切换元素的 display CSS property。
        注意，v-show 不支持 <template> 元素，也不支持 v-else。-->


    </div>


    <script src="https://unpkg.com/vue@next"></script>
    <script>
        let root = {
            data() {
                return {
                    awesome: false,
                    type: "D"

                }
            },
            methods: {
                ck() {
                    this.awesome = !this.awesome
                }
            }
        };
        const app = Vue.createApp(root);
        const vm = app.mount("#app");
    </script>
</body>

</html>
```

![image-20220412204951629](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204122049740.png)

v-else:前一兄弟元素必须有 `v-if` 或 `v-else-if`

### v-show指令

`v-show`也是条件渲染指令，和v-if指令不同的是，使用`v-show`指令的元素始终会被渲染到HTML，它只是简单地为元素设置CSS的style属性。

![image-20220412205109289](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204122051434.png)

### v-for指令

`v-for`指令基于一个数组渲染一个列表，它和JavaScript的遍历语法相似：

```html
v-for="item in items"
```

items是一个数组，item是当前被遍历的数组元素。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <div id="app">
        <li v-for="(value, name) in myObject">
            {{ name }}: {{ value }}
        </li>

    </div>
    <script src="https://unpkg.com/vue@next"></script>
    <script>
        let root = {
            data() {
                return {
                    myObject: {
                        title: 'How to do lists in Vue',
                        author: 'Jane Doe',
                        publishedAt: '2016-04-10'
                    }

                }
            }
        };
        const app = Vue.createApp(root);
        const vm = app.mount("#app");
    </script>
</body>

</html>
```

![image-20220412205637646](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204122056770.png)

`v-for`遍历myObject对象的title、author和publishedAt。

### v-bind指令

**缩写**：`:`

动态地绑定一个或多个 attribute

在绑定 `class` 或 `style` attribute 时，支持其它类型的值，如数组或对象。可以通过下面的教程链接查看详情。

在绑定 prop 时，prop 必须在子组件中声明。可以用修饰符指定不同的绑定类型。

没有参数时，可以绑定到一个包含键值对的对象。注意此时 `class` 和 `style` 绑定不支持数组和对象。



```html
<!-- 绑定 attribute -->
<img v-bind:src="imageSrc" />

<!-- 动态 attribute 名 -->
<button v-bind:[key]="value"></button>

<!-- 缩写 -->
<img :src="imageSrc" />

<!-- 动态 attribute 名缩写 -->
<button :[key]="value"></button>

<!-- 内联字符串拼接 -->
<img :src="'/path/to/images/' + fileName" />

<!-- class 绑定 -->
<div :class="{ red: isRed }"></div>
<div :class="[classA, classB]"></div>
<div :class="[classA, { classB: isB, classC: isC }]"></div>

<!-- style 绑定 -->
<div :style="{ fontSize: size + 'px' }"></div>
<div :style="[styleObjectA, styleObjectB]"></div>

<!-- 绑定一个全是 attribute 的对象 -->
<div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>

<!-- prop 绑定。"prop" 必须在 my-component 声明 -->
<my-component :prop="someThing"></my-component>

<!-- 将父组件的 props 一起传给子组件 -->
<child-component v-bind="$props"></child-component>

<!-- XLink -->
<svg><a :xlink:special="foo"></a></svg>
```

### v-on指令

**缩写**：`@`

`v-on`指令用于给监听DOM事件，它的用语法和v-bind是类似的，例如监听<a>元素的点击事件：

```html
<a v-on:click="doSomething">
```

```html
<!-- 方法处理器 -->
<button v-on:click="doThis"></button>

<!-- 动态事件 -->
<button v-on:[event]="doThis"></button>

<!-- 内联语句 -->
<button v-on:click="doThat('hello', $event)"></button>

<!-- 缩写 -->
<button @click="doThis"></button>

<!-- 动态事件缩写 -->
<button @[event]="doThis"></button>

<!-- 停止冒泡 -->
<button @click.stop="doThis"></button>

<!-- 阻止默认行为 -->
<button @click.prevent="doThis"></button>

<!-- 阻止默认行为，没有表达式 -->
<form @submit.prevent></form>

<!-- 串联修饰符 -->
<button @click.stop.prevent="doThis"></button>

<!-- 键修饰符，键别名 -->
<input @keyup.enter="onEnter" />

<!-- 点击回调只会触发一次 -->
<button v-on:click.once="doThis"></button>

<!-- 对象语法 -->
<button v-on="{ mousedown: doThis, mouseup: doThat }"></button>
```



## 五.应用与组件

### 创建一个应用实例

每个 Vue 应用都是通过用 `createApp` 函数创建一个新的**应用实例**开始的：

```js
const app = Vue.createApp({
  /* 选项 */
})
```

```js
const app = Vue.createApp({})
app.component('SearchInput', SearchInputComponent)
app.directive('focus', FocusDirective)
app.use(LocalePlugin)
```

### 根组件

传递给 `createApp` 的选项用于配置**根组件**。当我们**挂载**应用时，该组件被用作渲染的起点。

一个应用需要被挂载到一个 DOM 元素中。例如，如果你想把一个 Vue 应用挂载到 `<div id="app"></div>`，应该传入 `#app`：

```js
const RootComponent = { 
  /* 选项 */ 
}
const app = Vue.createApp(RootComponent)
const vm = app.mount('#app')
```

### 组件实例 property(属性)

在前面的指南中，我们认识了 `data` property。在 `data` 中定义的 property 是通过组件实例暴露的：

```js
const app = Vue.createApp({
  data() {
    return { count: 4 }
  }
})

const vm = app.mount('#app')

console.log(vm.count) // => 4
```

还有各种其他的组件选项，可以将用户定义的 property 添加到组件实例中，例如 `methods`，`props`，`computed`，`inject` 和 `setup`。我们将在后面的指南中深入讨论它们。组件实例的所有 property，无论如何定义，都可以在组件的模板中访问。

### 生命周期钩子

每个组件在被创建时都要经过一系列的初始化过程——例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。同时在这个过程中也会运行一些叫做**生命周期钩子**的函数，这给了用户在不同阶段添加自己的代码的机会。

比如 [created](https://v3.cn.vuejs.org/api/options-lifecycle-hooks.html#created) 钩子可以用来在一个实例被创建之后执行代码：

```js
Vue.createApp({
  data() {
    return { count: 1}
  },
  created() {
    // `this` 指向 vm 实例
    console.log('count is: ' + this.count) // => "count is: 1"
  }
})
```

也有一些其它的钩子，在实例生命周期的不同阶段被调用，如 mounted(页面初始化)、updated(更新)和 unmounted。生命周期钩子的 `this` 上下文指向调用它的当前活动实例。

![实例的生命周期](https://v3.cn.vuejs.org/images/lifecycle.svg)

created: html加载完成之前执行。执行顺序：父组件-子组件；
mounted: html加载完成后执行。执行顺序：子组件-父组件；
methods：事件方法执行；
watch：watch是去监听一个值的变化，然后执行相对应的函数；
computed：computed是计算属性，也就是依赖其它的属性计算所得出最后的值；

## 六.Data Property 和方法

### Data Property

组件的 `data` 选项是一个函数。Vue 会在创建新组件实例的过程中调用此函数。它应该返回一个对象，然后 Vue 会通过响应性系统将其包裹起来，并以 `$data` 的形式存储在组件实例中。为方便起见，该对象的任何顶级 property 也会直接通过组件实例暴露出来：

```js
const app = Vue.createApp({
  data() {
    return { count: 4 }
  }
})

const vm = app.mount('#app')

console.log(vm.$data.count) // => 4
console.log(vm.count)       // => 4

// 修改 vm.count 的值也会更新 $data.count
vm.count = 5
console.log(vm.$data.count) // => 5

// 反之亦然
vm.$data.count = 6
console.log(vm.count) // => 6
```

perty 仅在实例首次创建时被添加，所以你需要确保它们都在 `data` 函数返回的对象中。必要时，要对尚未提供所需值的 property 使用 `null`、`undefined` 或其他占位的值。方法

我们用 `methods` 选项向组件实例添加方法，它应该是一个包含所需方法的对象：

```js
const app = Vue.createApp({
  data() {
    return { count: 4 }
  },
  methods: {
    increment() {
      // `this` 指向该组件实例
      this.count++
    }
  }
})

const vm = app.mount('#app')

console.log(vm.count) // => 4

vm.increment()

console.log(vm.count) // => 5
```

Vue 自动为 `methods` 绑定 `this`，以便于它始终指向组件实例。这将确保方法在用作事件监听或回调时保持正确的 `this` 指向。在定义 `methods` 时应避免使用箭头函数，因为这会阻止 Vue 绑定恰当的 `this` 指向。

### computed计算属性

对于任何包含响应式数据的复杂逻辑，你都应该使用**计算属性**

基本例子

```html
<div id="computed-basics">
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</div>
```

```js
Vue.createApp({
  data() {
    return {
      author: {
        name: 'John Doe',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  computed: {
    // 计算属性的 getter
    publishedBooksMessage() {
      // `this` 指向 vm 实例
      return this.author.books.length > 0 ? 'Yes' : 'No'
    }
  }
}).mount('#computed-basics')
```

我们可以将同样的函数定义为一个方法，而不是一个计算属性。从最终结果来说，这两种实现方式确实是完全相同的。然而，不同的是**计算属性将基于它们的响应依赖关系缓存**。计算属性只会在相关响应式依赖发生改变时重新求值。这就意味着只要 `author.books` 还没有发生改变，多次访问 `publishedBookMessage` 时计算属性会立即返回之前的计算结果，而不必再次执行函数。

### watch侦听器

虽然计算属性在大多数情况下更合适，但有时也需要一个自定义的侦听器。这就是为什么 Vue 通过 `watch` 选项提供了一个更通用的方法来响应数据的变化。当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。

例如：

```html
<div id="watch-example">
  <p>
    Ask a yes/no question:
    <input v-model="question" />
  </p>
  <p>{{ answer }}</p>
</div>
```

```html
<!-- 因为 AJAX 库和通用工具的生态已经相当丰富，Vue 核心代码没有重复 -->
<!-- 提供这些功能以保持精简。这也可以让你自由选择自己更熟悉的工具。 -->
<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script>
  const watchExampleVM = Vue.createApp({
    data() {
      return {
        question: '',
        answer: 'Questions usually contain a question mark. ;-)'
      }
    },
    watch: {
      // 每当 question 发生变化时，该函数将会执行
      question(newQuestion, oldQuestion) {
        if (newQuestion.indexOf('?') > -1) {
          this.getAnswer()
        }
      }
    },
    methods: {
      getAnswer() {
        this.answer = 'Thinking...'
        axios
          .get('https://yesno.wtf/api')
          .then(response => {
            this.answer = response.data.answer
          })
          .catch(error => {
            this.answer = 'Error! Could not reach the API. ' + error
          })
      }
    }
  }).mount('#watch-example')
</script>
```

### 计算属性 vs 侦听器

Vue 提供了一种更通用的方式来观察和响应当前活动的实例上的数据变动：**侦听属性**。当你有一些数据需要随着其它数据变动而变动时，`watch` 很容易被滥用——特别是如果你之前使用过 AngularJS。然而，通常更好的做法是使用计算属性而不是命令式的 `watch` 回调。细想一下这个例子：

```html
<div id="demo">{{ fullName }}</div>
```

1

```js
const vm = Vue.createApp({
  data() {
    return {
      firstName: 'Foo',
      lastName: 'Bar',
      fullName: 'Foo Bar'
    }
  },
  watch: {
    firstName(val) {
      this.fullName = val + ' ' + this.lastName
    },
    lastName(val) {
      this.fullName = this.firstName + ' ' + val
    }
  }
}).mount('#demo')
```

上面代码是命令式且重复的。将它与计算属性的版本进行比较：

```js
const vm = Vue.createApp({
  data() {
    return {
      firstName: 'Foo',
      lastName: 'Bar'
    }
  },
  computed: {
    fullName() {
      return this.firstName + ' ' + this.lastName
    }
  }
}).mount('#demo')
```

好很多了，不是吗？

## 七.组合式api

组合式 API：一组低侵入式的、函数式的 API，使得我们能够更灵活地「组合」组件的逻辑

### setup

`setup` 函数是一个新的组件选项。作为在组件内使用 Composition API 的入口点。

- **调用时机**

  创建组件实例，然后初始化 `props` ，紧接着就调用`setup` 函数。从生命周期钩子的视角来看，它会在 `beforeCreate` 钩子之前被调用

- **模板中使用**

  如果 `setup` 返回一个对象，则对象的属性将会被合并到组件模板的渲染上下文：

  ```html
  <template>
    <div>{{ count }} {{ object.foo }}</div>
  </template>
  
  <script>
    import { ref, reactive } from 'vue'
  
    export default {
      setup() {
        const count = ref(0)
        const object = reactive({ foo: 'bar' })
  
        // 暴露给模板
        return {
          count,
          object,
        }
      },
    }
  </script>
  ```

  

  ### `computed`

  传入一个 getter 函数，返回一个默认不可手动修改的 ref 对象。
  
  ```js
  const count = ref(1)
  const plusOne = computed(() => count.value + 1)
  
  console.log(plusOne.value) // 2
  
  plusOne.value++ // 错误！
  ```
  
  或者传入一个拥有 `get` 和 `set` 函数的对象，创建一个可手动修改的计算状态。
  
  ```js
  const count = ref(1)
  const plusOne = computed({
    get: () => count.value + 1,
    set: (val) => {
      count.value = val - 1
    },
  })
  
  plusOne.value = 1
  console.log(count.value) // 
  ```
  
  ### `watch`
  
  `watch` API 完全等效于 2.x `this.$watch` （以及 `watch` 中相应的选项）。`watch` 需要侦听特定的数据源，并在回调函数中执行副作用。默认情况是懒执行的，也就是说仅在侦听的源变更时才执行回调。
  
  - 对比 `watchEffect`，`watch` 允许我们：
  
    - 懒执行副作用；
    - 更明确哪些状态的改变会触发侦听器重新运行副作用；
    - 访问侦听状态变化前后的值。
  
  - **侦听单个数据源**
  
    侦听器的数据源可以是一个拥有返回值的 getter 函数，也可以是 ref：
  
    ```js
    // 侦听一个 getter
    const state = reactive({ count: 0 })
    watch(
      () => state.count,
      (count, prevCount) => {
        /* ... */
      }
    )
    
    // 直接侦听一个 ref
    const count = ref(0)
    watch(count, (count, prevCount) => {
      /* ... */
    })
    ```
  
  - **侦听多个数据源**
  
    `watcher` 也可以使用数组来同时侦听多个源：
  
    ```js
    watch([fooRef, barRef], ([foo, bar], [prevFoo, prevBar]) => {
      /* ... */
    })
    ```
  
  

### ref 函数

  在 Vue 3.0 中，我们可以通过一个新的 `ref` 函数使任何响应式变量在任何地方起作用，如下所示：

  注意 `setup` 返回的 ref 在模板中会自动解开，不需要写 `.value`,setup 内部外部要。

```html
<p>{{t1}}</p>
<p>{{t2.value}}</p>
```

```js
 setup() {
    const t1 = ref(10);
    const t2 = reactive({ value: 30 });
    console.log("里面"+t1.value);
    console.log("里面"+t2.value);
    return {t1,t2};
  },
  mounted(){
    console.log("外面"+this.t1);
    console.log(this.t2.value);
  },
  
```

  `ref` 接收参数并将其包裹在一个带有 `value` property 的对象中返回，然后可以使用该 property 访问或更改响应式变量的值：

  ```js
  import { ref } from 'vue'
  
  const counter = ref(0)
  
  console.log(counter) // { value: 0 }
  console.log(counter.value) // 0
  
  counter.value++
  console.log(counter.value) // 1
  ```

  将值封装在一个对象中，看似没有必要，但为了保持 JavaScript 中不同数据类型的行为统一，这是必须的。这是因为在 JavaScript 中，`Number` 或 `String` 等基本类型是通过值而非引用传递的：

  ![按引用传递与按值传递](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204122210588.gif)

  在任何值周围都有一个封装对象，这样我们就可以在整个应用中安全地传递它，而不必担心在某个地方失去它的响应性。

  const 失效

  换句话说，`ref` 为我们的值创建了一个**响应式引用**。在整个组合式 API 中会经常使用**引用**的概念。

```js
const userForm = ref({
  size: 3,
  page: 0,
  userName: "",
  nickName: "",
  sclass: "",
  phonenumber: "",
  professional: "",
  email: "",
  delFlag: "0",
});

const tableData = ref([]);
const total = ref(0);
```

ref 创建响应式数据
使用ref可以创建一个包含响应式数据的引用对象（reference对象，简称ref对象），可以是基本类型、也可以是对象。

```
// 创建
const xxx = ref(value)

// 使用
xxx.value

// 在模板中

<div>{{xxx}}</div>



```

reactive 创建响应式数据
定义一个对象类型的响应式数据，内部基于ES6的Proxy实现，通过代理对象操作源对象内部数据进行操作

```
// 创建
const xxx = reactive({
    xxx: ''
})

// 使用
xxx.xxx

```

ref 和 reactive 本质我们可以简单的理解为ref是对reactive的二次包装, ref定义的数据访问的时候要多一个.value

### 生命周期函数

你可以通过在生命周期钩子前面加上 “on” 来访问组件的生命周期钩子。

下表包含如何在 [setup ()](https://v3.cn.vuejs.org/guide/composition-api-setup.html) 内部调用生命周期钩子：

| 选项式 API        | Hook inside `setup` |
| ----------------- | ------------------- |
| `beforeCreate`    | Not needed*         |
| `created`         | Not needed*         |
| `beforeMount`     | `onBeforeMount`     |
| `mounted`         | `onMounted`         |
| `beforeUpdate`    | `onBeforeUpdate`    |
| `updated`         | `onUpdated`         |
| `beforeUnmount`   | `onBeforeUnmount`   |
| `unmounted`       | `onUnmounted`       |
| `errorCaptured`   | `onErrorCaptured`   |
| `renderTracked`   | `onRenderTracked`   |
| `renderTriggered` | `onRenderTriggered` |
| `activated`       | `onActivated`       |
| `deactivated`     | `onDeactivated`     |

TIP

因为 `setup` 是围绕 `beforeCreate` 和 `created` 生命周期钩子运行的，所以不需要显式地定义它们。换句话说，在这些钩子中编写的任何代码都应该直接在 `setup` 函数中编写。

这些函数接受一个回调函数，当钩子被组件调用时将会被执行:

```js

export default {
  setup() {
    // mounted
    onMounted(() => {
      console.log('Component is mounted!')
    })
  }
}
```

```js
onMounted(() => {
  getList();
  loading.value = false;
});
```

## 八.路由

###  创建路由器

router/index.js

```
new VueRouter({
        routes: [
          { // 一般路由
            path: '/about',
            component: about
          },
          { // 自动跳转路由
            path: '/', 
            redirect: '/about'
          }
        ]
      })

```

### 注册路由器

 main.js       

```
 import router from './router'
       	new Vue({
       		router
       	})
```

### 使用路由组件标签

```vue
<p>
    <!--使用 router-link 组件进行导航 -->
    <!--通过传递 `to` 来指定链接 -->
    <!--`<router-link>` 将呈现一个带有正确 `href` 属性的 `<a>` 标签-->
<router-link to="/">GHome</router-link>
<router-link to="/about">About</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
```

### 动态路由匹配

很多时候，我们需要将给定匹配模式的路由映射到同一个组件。例如，我们可能有一个 `User` 组件，它应该对所有用户进行渲染，但用户 ID 不同。在 Vue Router 中，我们可以在路径中使用一个动态字段来实现，我们称之为 *路径参数* ：

```
const User = {
  template: '<div>User</div>',
}

// 这些都会传递给 `createRouter`
const routes = [
  // 动态字段以冒号开始
  { path: '/users/:id', component: User },
]
```

现在像 `/users/johnny` 和 `/users/jolyne` 这样的 URL 都会映射到同一个路由。

*路径参数* 用冒号 `:` 表示。当一个路由被匹配时，它的 *params* 的值将在每个组件中以 `this.$route.params` 的形式暴露出来。因此，我们可以通过更新 `User` 的模板来呈现当前的用户 ID：

```
const User = {
  template: '<div>User {{ $route.params.id }}</div>',
}
```

你可以在同一个路由中设置有多个 *路径参数*，它们会映射到 `$route.params` 上的相应字段。例如：

| 匹配模式                       | 匹配路径                 | $route.params                            |
| ------------------------------ | ------------------------ | ---------------------------------------- |
| /users/:username               | /users/eduardo           | `{ username: 'eduardo' }`                |
| /users/:username/posts/:postId | /users/eduardo/posts/123 | `{ username: 'eduardo', postId: '123' }` |

除了 `$route.params` 之外，`$route` 对象还公开了其他有用的信息，如 `$route.query`（如果 URL 中存在参数）、`$route.hash` 等。你可以在 [API 参考](https://router.vuejs.org/zh/api/#routelocationnormalized)中查看完整的细节。

### 嵌套路由



```
// 导入用来创建路由和确定路由模式的两个方法
import {
    createRouter,
    createWebHistory
} from 'vue-router'

/**
 * 定义路由信息
 * 
 */
const routes = [{
    name: 'login',
    path: '/login',
    component: () =>
        import ('@/components/login'),

}, {
    name: 'main',
    path: '/main',
    component: () =>
        import ('@/components/main'),
    children: [{
            name: 'user',
            path: '/user',
            component: () =>
                import ('@/components/user'),
        },
        {
            name: 'system',
            path: '/system',
            component: () =>
                import ('@/components/system'),
        },
        {
            name: 'question',
            path: '/question',
            component: () =>
                import ('@/components/question'),
        },
        {
            name: 'teacher',
            path: '/teacher',
            component: () =>
                import ('@/components/teacher/index.vue'),
        },
    ]

}]

// 创建路由实例并传递 `routes` 配置
// 我们在这里使用 html5 的路由模式，url中不带有#，部署项目的时候需要注意。
const router = createRouter({
    history: createWebHistory(),
    routes,
})


// 全局的路由守卫
router.beforeEach(() => {
    // console.log(to)
    // console.log(from)
    return true
})

// 讲路由实例导出
export default router;
```

### 编程式导航

除了使用 `<router-link>` 创建 a 标签来定义导航链接，我们还可以借助 router 的实例方法，通过编写代码来实现。

**注意：在 Vue 实例中，你可以通过 `$router` 访问路由实例。因此你可以调用 `this.$router.push`。**

想要导航到不同的 URL，可以使用 `router.push` 方法。这个方法会向 history 栈添加一个新的记录，所以，当用户点击浏览器后退按钮时，会回到之前的 URL。

当你点击 `<router-link>` 时，内部会调用这个方法，所以点击 `<router-link :to="...">` 相当于调用 `router.push(...)` ：

| 声明式                    | 编程式             |
| ------------------------- | ------------------ |
| `<router-link :to="...">` | `router.push(...)` |

该方法的参数可以是一个字符串路径，或者一个描述地址的对象。例如：

```js
// 字符串路径
router.push('/users/eduardo')

// 带有路径的对象
router.push({ path: '/users/eduardo' })

// 命名的路由，并加上参数，让路由建立 url
router.push({ name: 'user', params: { username: 'eduardo' } })

// 带查询参数，结果是 /register?plan=private
router.push({ path: '/register', query: { plan: 'private' } })

// 带 hash，结果是 /about#team
router.push({ path: '/about', hash: '#team' })
```

**注意**：如果提供了 `path`，`params` 会被忽略，上述例子中的 `query` 并不属于这种情况。取而代之的是下面例子的做法，你需要提供路由的 `name` 或手写完整的带有参数的 `path` ：

```js
const username = 'eduardo'
// 我们可以手动建立 url，但我们必须自己处理编码
router.push(`/user/${username}`) // -> /user/eduardo
// 同样
router.push({ path: `/user/${username}` }) // -> /user/eduardo
// 如果可能的话，使用 `name` 和 `params` 从自动 URL 编码中获益
router.push({ name: 'user', params: { username } }) // -> /user/eduardo
// `params` 不能与 `path` 一起使用
router.push({ path: '/user', params: { username } }) // -> /user
```

由于属性 `to` 与 `router.push` 接受的对象种类相同，所以两者的规则完全相同

### 组合式 API

在 `setup` 中访问路由和当前路由

因为我们在 `setup` 里面没有访问 `this`，所以我们不能再直接访问 `this.$router` 或 `this.$route`。作为替代，我们使用 `useRouter` 函数：

```js
import { useRouter, useRoute } from 'vue-router'

export default {
  setup() {
    const router = useRouter()
    const route = useRoute()

    function pushWithQuery(query) {
      router.push({
        name: 'search',
        query: {
          ...route.query,
        },
      })
    }
  },
}
```