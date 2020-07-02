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
