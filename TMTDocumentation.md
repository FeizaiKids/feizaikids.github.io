#### Project Structure

```
tmt-refine
│  .gitignore
│  babel.config.js
│  package-lock.json
│  package.json
│  README.md
│  vue.config.js  //代理设置，项目配置等
│  
├─dist  //项目输出目录 npm run build 
│          
├─public
│      favicon.ico
│      index.html
│      
└─src
    │  App.vue  //项目入口文件
    │  main.js  //项目入口脚本
    │  routers.js //项目路由配置，路由跳转拦截
    │  
    ├─api
    │      api.js //API 封装
    │      request.js //axios 后台交互设置 交互拦截
    │      
    ├─assets  //样式，字体，图片资源
    │  │  
    │  ├─css
    │  │      
    │  ├─fonts
    │  │      
    │  ├─img
    │  │      
    │  └─js
    │          common.js //公共方法
    │          
    ├─plugins
    │      element.js
    │      
    ├─store //vuex 全局状态管理（user id/ token）
    │      actions.js
    │      getters.js
    │      mutations.js
    │      state.js
    │      store.js
    │      
    └─views //页面布局
        ├─home  //主页面
        │  │  HomePage.vue
        │  │  
        │  └─components //主页面子组件
        │      │  HeadView.vue  //标题栏组件
        │      │  MainView.vue  //主页面组件 （所有的subpages的页面作为此页面的子组件）
        │      │  NavigationView.vue  //左侧导航栏页面
        │      │  
        │      └─data
        │              menu.js
        │              
        ├─login //登陆页面
        │      LoginInfo.vue
        │      SelfLogin.vue
        │      SelfLogin_ElementUI.vue
        │      
        └─subpages  //功能模块
            ├─employee
            │      EmployeeManagement.vue
            │      
            ├─overtime
            │      OvertimeApplication.vue
            │      OvertimeStatus.vue
            │      OvertimeStatusManager.vue
            │      
            ├─project
            │      ProjectManagement.vue
            │      
            ├─test
            │      test.vue
            │      
            ├─timesheet
            │      TimesheetSubmit.vue
            │      
            ├─util
            │      DeleteDialog.vue
            │      inlineEdit.js
            │      
            └─welcome
                    WelcomePage.vue
                    WelcomePage_ElementUI.vue
                    
```
