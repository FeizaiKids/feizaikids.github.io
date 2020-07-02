##### hello world
```
<!DOCTYPE html>
<head>
    <title></title>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        {{ message }}
    </div>
    <script type="text/javascript">
        var app = new Vue({
            el: '#app',
            data: {
                message: 'Hello Vue!'
            }
        })
    </script>
</body>
</html>
```

##### 指令
v-bind
```
    <div id="app-2">
        <span v-bind:title="message">
            鼠标悬停几秒钟查看此处动态绑定的提示信息！
        </span>
    </div>
    <script type="text/javascript">
        var app2 = new Vue({
            el: '#app-2',
            data: {
                message: '页面加载于 ' + new Date().toLocaleString()
            }
        })
    </script>
```

v-if
```
//插入/移除 <p> 元素。
    <div id="app-3">
        <p v-if="seen">现在你看到我了</p>
    </div>
    <script type="text/javascript">
        var app3 = new Vue({
            el: '#app-3',
            data: {
                seen: true
            }
        })
    </script>
```

v-for
```
    <div id="app-4">
        <ol>
            <li v-for="todo in todos">
                {{ todo.text }}
            </li>
        </ol>
    </div>
    <script type="text/javascript">
        var app4 = new Vue({
            el: '#app-4',
            data: {
                todos: [
                    { text: '学习 JavaScript' },
                    { text: '学习 Vue' },
                    { text: '整个牛项目' }
                ]
            }
        })
    </script>
    
    //app4.todos.push({ text: '新项目' })
```

v-on 事件监听器
```
    <div id="app-5">
        <p>{{ message }}</p>
        <button v-on:click="reverseMessage">反转消息</button>
    </div>
    <script type="text/javascript">
        var app5 = new Vue({
            el: '#app-5',
            data: {
                message: 'Hello Vue.js!'
            },
            methods: {
                reverseMessage: function () {
                    this.message = this.message.split('').reverse().join('')
                }
            }
        })
    </script>
```

v-model 双向绑定
```
     <div id="app-6">
        <p>{{ message }}</p>
        <input v-model="message">
    </div>
    <script type="text/javascript">
        var app6 = new Vue({
            el: '#app-6',
            data: {
                message: 'Hello Vue!'
            }
        })
    </script>
```

v-once 执行一次性地插值
```
<span v-once>这个将不会改变: {{ msg }}</span>
```

v-html
```
    <div id="example">
        <p>Using mustaches: {{ rawHtml }}</p>
        <p>Using v-html directive: <span v-html="rawHtml"></span></p>
    </div>

    <script type="text/javascript">

        var vm = new Vue({
            el: '#example',
            data: { rawHtml: '<span style="color: red">This should be red.</span>' }
        })
    </script>
```

##### component 组件
```
    <div id="app-7">
        <ol>
            <!--
            现在我们为每个 todo-item 提供 todo 对象
            todo 对象是变量，即其内容可以是动态的。
            我们也需要为每个组件提供一个“key”，稍后再
            作详细解释。
          -->
            <todo-item v-for="item in groceryList" v-bind:todo="item" v-bind:key="item.id"></todo-item>
        </ol>
    </div>

    <script type="text/javascript">
        // Vue.component('todo-item', {
        //     template: '<li>这是个待办项</li>'
        // })

        Vue.component('todo-item', {
            // todo-item 组件现在接受一个
            // "prop"，类似于一个自定义 attribute。
            // 这个 prop 名为 todo。
            props: ['todo'],
            template: '<li>{{ todo.text }}</li>'
        })        

        var app7 = new Vue({
            el: '#app-7',
            data: {
                groceryList: [
                    { id: 0, text: '蔬菜' },
                    { id: 1, text: '奶酪' },
                    { id: 2, text: '随便其它什么人吃的东西' }
                ]
            }
        })
    </script>
```

```
<div id="app">
  <app-nav></app-nav>
  <app-view>
    <app-sidebar></app-sidebar>
    <app-content></app-content>
  </app-view>
</div>
```

##### 一些方法
```
    <div id="example">
        <p>{{ a }}</p>
        <!-- 这里的 `foo` 不会更新！ -->
        <button v-on:click="foo = 'baz'">Change it</button>
    </div>

    <script type="text/javascript">
        var data = { a: 1 }
        var vm = new Vue({
            el: '#example',
            data: data
        })

        vm.$data === data // => true
        vm.$el === document.getElementById('example') // => true

        // $watch 是一个实例方法
        vm.$watch('a', function (newValue, oldValue) {
            console.log("changed...")
        })
    </script>
```
```
var obj = {
  foo: 'bar'
}
//阻止修改现有的 property，也意味着响应系统无法再追踪变化。
Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
```

##### JavaScript表达式
```
{{ number + 1 }}

{{ ok ? 'YES' : 'NO' }}

{{ message.split('').reverse().join('') }}

<div v-bind:id="'list-' + id"></div>
```

##### 动态参数（2.6.0 新增
```
//避免使用大写字符来命名键名
<a v-bind:[attributeName]="url"> ... </a>
<a v-on:[eventName]="doSomething"> ... </a>
```

##### 缩写
```
<!-- 完整语法 -->
<a v-bind:href="url">...</a>
<!-- 缩写 -->
<a :href="url">...</a>
<!-- 动态参数的缩写 (2.6.0+) -->
<a :[key]="url"> ... </a>

<!-- 完整语法 -->
<a v-on:click="doSomething">...</a>
<!-- 缩写 -->
<a @click="doSomething">...</a>
<!-- 动态参数的缩写 (2.6.0+) -->
<a @[event]="doSomething"> ... </a>
```

##### 计算属性缓存 vs 方法
```
    <div id="example">
        <p>Original message: "{{ message }}"</p>
        <p>Computed reversed message: "{{ reversedMessage }}"</p>
    </div>

    <script type="text/javascript">
        var vm = new Vue({
            el: '#example',
            data: {
                message: 'Hello'
            },
            computed: {
                // 计算属性的 getter
                reversedMessage: function () {
                    // `this` 指向 vm 实例
                    return this.message.split('').reverse().join('')
                }
            }
        })
    </script>
```
```
    <div id="example">
        <p>Original message: "{{ message }}"</p>
        <p>Reversed message: "{{ reversedMessage() }}"</p>
    </div>

    <script type="text/javascript">
        var vm = new Vue({
            el: '#example',
            data: {
                message: 'Hello'
            },
            methods: {
                reversedMessage: function () {
                    return this.message.split('').reverse().join('')
                }
            }
        })
    </script>
```
不同的是计算属性是基于它们的响应式依赖进行缓存的。
只在相关响应式依赖发生改变时它们才会重新求值。
这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。
我们为什么需要缓存？假设我们有一个性能开销比较大的计算属性 A，它需要遍历一个巨大的数组并做大量的计算。
然后我们可能有其他的计算属性依赖于 A。如果没有缓存，我们将不可避免的多次执行 A 的 getter！如果你不希望有缓存，请用方法来替代。

##### 计算属性 vs 侦听属性
```
//命令式且重复的:
    <div id="demo">{{ fullName }}</div>
    <script type="text/javascript">
        var vm = new Vue({
            el: '#demo',
            data: {
                firstName: 'Foo',
                lastName: 'Bar',
                fullName: 'Foo Bar'
            },
            watch: {
                firstName: function (val) {
                    this.fullName = val + ' ' + this.lastName
                },
                lastName: function (val) {
                    this.fullName = this.firstName + ' ' + val
                }
            }
        })
    </script>
```
```
//好得多了，不是吗？
    <div id="demo">{{ fullName }}</div>
    <script type="text/javascript">
        var vm = new Vue({
            el: '#demo',
            data: {
                firstName: 'Foo',
                lastName: 'Bar'
            },
            computed: {
                fullName: function () {
                    return this.firstName + ' ' + this.lastName
                }
            }
        })
    </script>
```

##### 计算属性默认只有 getter，不过在需要时你也可以提供一个 setter
```
// ...
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
// ...

//vm.fullName = 'John Doe'
```

##### 侦听/ajax
```
    <div id="watch-example">
        <p>
            Ask a yes/no question:
            <input v-model="question">
        </p>
        <p>{{ answer }}</p>
    </div>

    
    <script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/lodash@4.13.1/lodash.min.js"></script>
    <script>
        var watchExampleVM = new Vue({
            el: '#watch-example',
            data: {
                question: '',
                answer: 'I cannot give you an answer until you ask a question!'
            },
            watch: {
                // 如果 `question` 发生改变，这个函数就会运行
                question: function (newQuestion, oldQuestion) {
                    this.answer = 'Waiting for you to stop typing...'
                    this.debouncedGetAnswer()
                }
            },
            created: function () {
                // `_.debounce` 是一个通过 Lodash 限制操作频率的函数。
                // 在这个例子中，我们希望限制访问 yesno.wtf/api 的频率
                // AJAX 请求直到用户输入完毕才会发出。想要了解更多关于
                // `_.debounce` 函数 (及其近亲 `_.throttle`) 的知识，
                // 请参考：https://lodash.com/docs#debounce
                this.debouncedGetAnswer = _.debounce(this.getAnswer, 500)
            },
            methods: {
                getAnswer: function () {
                    if (this.question.indexOf('?') === -1) {
                        this.answer = 'Questions usually contain a question mark. ;-)'
                        return
                    }
                    this.answer = 'Thinking...'
                    var vm = this
                    axios.get('https://yesno.wtf/api')
                        .then(function (response) {
                            vm.answer = _.capitalize(response.data.answer)
                        })
                        .catch(function (error) {
                            vm.answer = 'Error! Could not reach the API. ' + error
                        })
                }
            }
        })
    </script>
```

##### class & style bind
```
<div v-bind:class="{ active: isActive }"></div>
//上面的语法表示 active 这个 class 存在与否将取决于数据 property isActive 的 truthiness。
////////////////////
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>
data: {
  isActive: true,
  hasError: false
}
/////////////////////////////
<div v-bind:class="classObject"></div>
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
//////////////////////////////
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
//////////////////////////
<div v-bind:class="[activeClass, errorClass]"></div>
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
/////////////////////////////
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
/////////////////////////////
<div v-bind:class="[{ active: isActive }, errorClass]"></div>
```

