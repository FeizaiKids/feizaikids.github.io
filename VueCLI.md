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
