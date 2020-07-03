##### install node.js
https://nodejs.org/en/download/

```
node --version
npm -v
```

##### cnpm
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
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
