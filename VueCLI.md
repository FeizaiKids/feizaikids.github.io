##### install node.js
https://nodejs.org/en/download/

```
node --version
npm -v
```

##### cnpm
optional to use.
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
////
npm config set registry https://registry.npm.taobao.org
```

##### install vue cli
```
npm i -g @vue/cli @vue/cli-service-global //cli-service-global: zero-configuration
```
##### save App.vue in a folder
```
<template>
    <h1>Hello World</h1>
</template>
```

##### start server 0 configuration
switch to the folder
```
vue serve -o
```

##### create project
```
vue create hello-world -d
cd hello-world
npm run serve
npm run lint
npm run build
cd dist
npx http-server
```

##### trouble shooting

```
//set up proxy
npm config set proxy http://z003anxy:Siemens2020@140.231.192.162:8080
npm config set https-proxy http://z003anxy:Siemens2020@140.231.192.162:8080

//set up vue proxy if necessary
vue config
useTaobaoRegistry true/false
C:\Users\z0038jwk\.vuerc
```

##### install required plugin
```
npm i vue-router -D
npm i axios -D
vue add element
```

##### vuex
```
//optional
npm install vuex --save

vuex数据持久话插件，将state里面的数据保存到localstorage
npm install vuex-persistedstate --save
```

##### Promise
Promise有三种状态
pending:等待中，或者进行中，表示还没有得到结果
resolved:已经完成，表示得到了我们想要的结果，可以继续往下执行
rejected:也表示得到结果，但是由于结果并非我们所愿，因此拒绝执(用catch捕获异常)

这三种状态不受外界影响，而且状态只能从pending改变为resolved或者rejected，并且不可逆(顾名思义承诺的后的东西怎么又能返回呢)。在Promise对象的构造函数中，将一个函数作为第一个参数。而这个函数，就是用来处理Promise的状态变化

这里要注意，不管是then或者catch返回的都是一个新的Promise实例！而每个Promise实例都有最原始的Pending（进行中）到Resolve（已完成），或者Pending（进行中）到Reject（已失败）的过程

```
Promise.resolve('foo')
//equals
new Promise(resolve => resolve('foo'))

Promise.reject('foo')
//equals
new Promise(reject => reject('foo'))
```

##### Interceptor
```
// Add a request interceptor
axios.interceptors.request.use(function (config) {
    // Do something before request is sent
    return config;
  }, function (error) {
    // Do something with request error
    return Promise.reject(error);
  });
 
// Add a response interceptor
axios.interceptors.response.use(function (response) {
    // Any status code that lie within the range of 2xx cause this function to trigger
    // Do something with response data
    return response;
  }, function (error) {
    // Any status codes that falls outside the range of 2xx cause this function to trigger
    // Do something with response error
    return Promise.reject(error);
  });
```
