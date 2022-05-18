# Quasar - Learn



dddd

## Quasar 体验局

![image-20220518141705980](md-imgs/Quasar-Learn.assets/image-20220518141705980.png)

https://docs.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2

```powershell
PS C:\Users\NERO\Desktop\Quasar-learn> Get-ExecutionPolicy
Restricted
PS C:\Users\NERO\Desktop\Quasar-learn> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine       Undefined
```

配置

https://blog.csdn.net/weixin_37493499/article/details/108930327

![image-20220518142012358](md-imgs/Quasar-Learn.assets/image-20220518142012358.png)

不可行

![image-20220518142058537](md-imgs/Quasar-Learn.assets/image-20220518142058537.png)

<img src="md-imgs/Quasar-Learn.assets/image-20220518142158672.png" alt="image-20220518142158672" style="zoom:70%;" />

![image-20220518142338966](md-imgs/Quasar-Learn.assets/image-20220518142338966.png)

估计是公司机子有权限，那就把策略范围设置到当前用户上

![image-20220518142459479](md-imgs/Quasar-Learn.assets/image-20220518142459479.png)

再试一下

![image-20220518142635631](md-imgs/Quasar-Learn.assets/image-20220518142635631.png)

可以了，不过命令变了

```powershell
npm init quasar
```



![image-20220518143557568](md-imgs/Quasar-Learn.assets/image-20220518143557568.png)

生成如下项目文件夹

![image-20220518143727538](md-imgs/Quasar-Learn.assets/image-20220518143727538.png)

![image-20220518144239952](md-imgs/Quasar-Learn.assets/image-20220518144239952.png)

记得创建项目后，cd 进去（同时VSCode打开的根路径要是项目根路径），不然不在项目根路径下，很多 config 识别不到的

测试启动默认quasar样例：

```shell
quasar dev
```

<img src="md-imgs/Quasar-Learn.assets/image-20220518144805994.png" alt="image-20220518144805994" style="zoom:50%;" />



## Quasar 项目结构 （旧版本）

```powershell
├── public/                  # 纯静态资源（直接复制）
├── src/
│   ├── assets/              # 动态资源（由webpack处理）
│   ├── components/          # 用于页面和布局的.vue组件
│   ├── css/                 # CSS/Stylus/Sass/...文件
|   |   ├── app.styl
|   │   └── quasar.variables.styl # 供您调整的Quasar Stylus变量
│   ├── layouts/             # 布局 .vue 文件
│   ├── pages/               # 页面 .vue 文件
│   ├── boot/                # 启动文件 (应用初始化代码) 
│   ├── router/              # Vue路由
|   |   ├── index.js         # Vue路由定义
|   │   └── routes.js        # App路由定义
│   ├── store/               # Vuex Store
|   |   ├── index.js         # Vuex Store 定义
|   │   ├── <folder>         # Vuex Store 模块...
|   │   └── <folder>         # Vuex Store 模块...
│   ├── App.vue              # APP的根Vue组件
│   └── index.template.html  # index.html模板
├── src-ssr/                 # SSR特定代码(就像生产环境的Node网页服务器)
├── src-pwa/                 # PWA特定代码（如Service Worker）
├── src-cordova/             # Cordova生成的文件夹用于创建移动APP
├── src-electron/            # Electron特定代码（如"main"线程)
├── src-bex/                 # BEX（浏览器扩展）特定代码（如"main"线程)
├── dist/                    # 生产版本代码，用于部署
│   ├── spa/                 # 构建SPA的例子
│   ├── ssr/                 # 构建SSR的例子
│   ├── electron/            # 构建Electron的例子
│   └── ....
├── quasar.conf.js           # Quasar App配置文件
├── babel.config.js          # Babeljs配置
├── .editorconfig            # editor配置
├── .eslintignore            # ESlint忽略路径
├── .eslintrc.js             # ESlint配置
├── .postcssrc.js            # PostCSS配置
├── .stylintrc               # Stylus lint配置
├── .gitignore               # GIT忽略路径
├── package.json             # npm脚本和依赖项
└── README.md                # 您的网站/应用程序的自述文件
```

> 参考：[quasar 参考文档 ](https://www.cnblogs.com/q1104460935/p/15663108.html) 





## 安装 Quasar

npm i -g @quasar/cli



# Ref

+ [quasar 简介](https://blog.csdn.net/BDawn/article/details/102477936)
+ [quasar 参考文档 ](https://www.cnblogs.com/q1104460935/p/15663108.html) 👍
+ [quasar-cli项目创建](https://blog.csdn.net/web_monkey888/article/details/119803934) 👍
+ [quasar使用记录-安装配置](https://zhuanlan.zhihu.com/p/363921765)
+ https://www.yuque.com/fictiony/cs6lwq/nzrxtl

