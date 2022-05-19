# Quasar - Learn



dddd

## Quasar 初体验

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

```shell
# 全局安装 脚手架
npm i -g @quasar/cli
```

## 创建 Quasar 项目

```
npm init quasar
# 以下为旧版本命令，已弃用
# -------------------
```

![image-20220519093148480](md-imgs/Quasar-Learn.assets/image-20220519093148480.png)

之后就是一些项目配置选项了

![image-20220519093301384](md-imgs/Quasar-Learn.assets/image-20220519093301384.png)

```
? What would you like to build? » - Use arrow-keys. Return to submit.
>   App with Quasar CLI, let's go! - spa/pwa/ssr/bex/electron/capacitor/cordova 👈 创建此些类型项，见下文介绍
>   AppExtension (AE) for Quasar CLI - Quasar CLI AE 👈 开发 Quasar CLI 插件（扩展应用）
>   Quasar UI kit - Vue component and/or directive 👈 开发 Vue组件或指令
```

### Quasar 支持创建的几种类型的web应用

Quasar的理念是：**一站式所有平台**，即一次性编写代码，并同时将其部署为网站，移动应用程序和应用程序。 一个适用于所有代码的代码库，可通过Quasar Web复用组件，会帮助您在创纪录的时间内开发应用程序。

- **SPA（Single-Page Application，单页应用程序/网站）**

  > <u>A **Single-Page Application (SPA)** is a web application or web site that interacts with the user by ***dynamically rewriting the current page rather than loading entire new pages from a server***.</u> This approach avoids interruption of the user experience between successive pages, making the application ***behave more like a desktop application***.
  >
  > ——[Quasar - What is SPA](https://quasar.dev/quasar-cli-vite/developing-spa/introduction#introduction)
  >
  > 
  >
  > **单页Web应用（single page web application，SPA）**，就是只有一张Web页面的应用。单页应用程序 (SPA) 是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。  浏览器一开始会加载必需的HTML、CSS和JavaScript，所有的操作都在这张页面上完成，都由JavaScript来控制。因此，对单页应用来说模块化的开发和设计显得相当重要。
  >
  > —— https://baike.baidu.com/item/SPA/17536313

- **PWA（Progressive Web App, 渐进式Web应用）**

  > <u>A **Progressive Web App (PWA)** is a web app that uses modern web capabilities to deliver an ***app-like experience*** to users.</u> These apps meet certain requirements (see below), are deployed to web servers and accessible through URLs (on HTTPS protocol).
  >
  > This can work in conjunction with Cordova to provide a multiple deploy targets for all your users. Quasar CLI allows you to deploy your app as a PWA as well as a Mobile app and take advantage of both channels.
  >
  > ——[Quasar - What is a PWA](https://quasar.dev/quasar-cli-vite/developing-pwa/introduction#introduction)
  >
  > 
  >
  > PWA（Progressive Web Apps，渐进式 Web 应用）运用现代的 Web API 以及传统的渐进式增强策略来创建跨平台 Web 应用程序。这些应用无处不在、功能丰富，使其具有与原生应用相同的用户体验优势。这组文档和指南告诉您有关 PWA 的所有信息。
  >
  > —— [MDN - 渐进式 Web 应用（PWA）](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps) 👈 关于PWA的所有概念都在这里
  >
  > 
  >
  > PWA 不是只使用一种技术创建的。**它代表了构建 Web 应用程序的新理念**，涉及一些特定的模式，API 和其他功能。**一眼是看不出来一个 Web App 是不是 PWA 的。**如果应用程序满足某些要求，或者实现了一组特定的功能，例如离线工作、可安装、易于同步、可以发送推送通知等，我们就可以将其视为 PWA。
  >
  > 辨别一个 Web 应用是否是 PWA 有一些关键原则。一个 PWA 应该具有以下特点：
  >
  > - [可发现（Discoverable）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#discoverable), 可以通过搜索引擎发现。
  > - [可安装（Installable）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#installable), 可以出现在设备的主屏幕。
  > - [可链接（Linkable）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#linkable), 可以简单地通过 URL 分享。 
  > - [独立于网络（Network independent）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#network_independent), 可以在离线状态或者是在网速很差的情况下运行。
  > - [渐进式（Progressive）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#progressive), 在老版本的浏览器仍旧可以使用，在新版本的浏览器上可以使用全部功能。
  > - [可重入（Re-engageable）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#re-engageable), 无论何时有新的内容，都可以发送通知。
  > - [响应式（Responsive）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#responsive), 在任何具有屏幕和浏览器的设备上可以正常使用——包括手机、平板电脑、笔记本、电视、冰箱等。
  > - [安全（Safe）](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Introduction#Advantages_of_web_applications#safe), 在用户、应用和服务器之间的连接是安全的，第三方无法访问你的敏感数据。
  >
  > ——[渐进式 Web 应用介绍](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/Introduction)
  >
  > <a name="ssr"></a>
  >
  > **渲染网站主要有两种方法 - 在服务器上或在客户端上。**它们都有其优点和缺点，你可以适当地混合使用这两种方法
  >
  > - **服务器端渲染（Server-Side Rendering, SSR）**的意思是在服务器上渲染网页，因此首次加载会更快，但是在不同页面之间导航都需要下载新的HTML内容。它的跨浏览器兼容性良好，但代价是页间加载时间延长，也就是总体感知上的性能降低：每加载一个页面，都需要一个服务器请求往返的时间。
  > - **客户端渲染（Client-Side Rendering, CSR）**允许在导航到不同页面时几乎立即在浏览器中更新网站，但在开始时需要更多的初始下载和客户端上的额外渲染。 首次访问时网站速度较慢，但后续访问速度要快得多。
  >
  > 将 SSR 与 CSR 混用可以获得最佳效果：您可以在服务器上渲染网站，缓存其内容，然后在客户端需要时更新渲染。因为使用了 SSR，第一页加载很快；因为客户端可以仅使用已更改的部分重新渲染页面，所以页面之间的导航也是平滑的。
  >
  > ——[PWA 结构](https://developer.mozilla.org/zh-CN/docs/Web/Progressive_web_apps/App_structure)

- **SSR(Server-Side Rendering, 服务器端渲染)**

  > ==Quasar and Vue.js are frameworks for building **client-side** applications==. By default, Quasar Vue components produce and manipulate DOM in the browser as output. <u>However, it is **also possible to render the same components into HTML strings on the server**, send them directly to the browser, and finally “hydrate” the static markup into a fully interactive app on the client.</u>
  >
  > A **server-rendered Quasar app** can also be considered `isomorphic` or `universal`, in the sense that the majority of **your app’s code runs on both the server and the client.**
  >
  > ——[What is SSR](https://quasar.dev/quasar-cli-vite/developing-ssr/introduction#introduction)
  >
  > 
  >
  > - SSR（服务器端渲染应用程序）（+可选的PWA客户端接管）
  >
  > **服务器端渲染（SSR）**的意思是在服务器上渲染网页，因此首次加载会更快，但是在不同页面之间导航都需要下载新的HTML内容。它的跨浏览器兼容性良好，但代价是页间加载时间延长，也就是总体感知上的性能降低：每加载一个页面，都需要一个服务器请求往返的时间。
  >
  > 与之对应的就是 **客户端渲染（CSR）**，回顾 <a href="#ssr">这里</a>

- **BEX（Browser Extension，浏览器扩展）**

  > <u>A **Browser Extension (BEX)** is an application that runs in the browsers context and is used to customize the web browser in some way.</u>
  >
  > They are built on web technologies such as HTML, JavaScript, and CSS and will aim to fulfill a single purpose. A single BEX can be built in any way the user deems fit but must contribute towards fulfilling that single purpose.
  >
  > Here a few things a BEX can do:
  >
  > - Override page content
  > - Add to (or alter) the browser’s interface
  > - Intercept page requests
  > - Be a full featured app that runs in the browser.
  > - Interact with and alter the development tools of the browser.
  >
  > We’ve all used Browser Extensions in some capacity. Quasar BEX allows you to do anything a browser extension allows but with the simplicity Quasar offers in all other modes.
  >
  > —— [Quasar - What is a Browser Extension](https://quasar.dev/quasar-cli-vite/developing-browser-extensions/introduction)
  >
  > 
  >
  > 扩展或者说是附加组件，拥有可以修改、增强浏览器的能力。
  >
  > ——[MDN - 浏览器扩展](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions)
  >
  > 可以参考这篇文章：[用Vue实现一个谷歌浏览器搜索扩展](https://zhuanlan.zhihu.com/p/355864607) 👈 用了Quasar

- **Electron应用（桌面应用程序）**

  > [Electron](https://electronjs.org/) (formerly known as Atom Shell) is an open-source framework created by Cheng Zhao, and now developed by GitHub. <u>**It allows for the development of ==desktop GUI applications==** using front and back end components originally developed for web applications: **Node.js runtime for the backend** and **Chromium for the frontend**.</u> Electron is the main GUI framework behind several notable open-source projects including GitHub’s Atom and Microsoft’s Visual Studio Code source code editors, the Tidal music streaming service desktop application and the Light Table IDE, in addition to the freeware desktop client for the Discord chat service.
  >
  > Each Electron app has two threads: one is the main thread (dealing with the App window and bootup), and one is the renderer thread (which is basically your UI web code). There is also a preload script to bridge the two “worlds”.
  >
  > ——[Quasar - What is Electron](https://quasar.dev/quasar-cli-vite/developing-electron-apps/introduction)
  >
  > 
  >
  > VS Code 就是用 Electron 开发的哦~

- **移动APP**

  > Quasar offers two solutions for creating mobile apps:
  >
  > - **Capacitor** was created by Ionic Framework as a more modern replacement for Cordova. It supports most, but not all, Cordova plugins as well as Capacitor-specific plugins.
  > - **Cordova** is a mobile application development framework originally created by Nitobi. Adobe Systems purchased Nitobi in 2011, rebranded it as PhoneGap, and later released an open source version of the software called Apache Cordova.

  - **借助 Capacitor 开发**

    > [Capacitor](https://capacitorjs.com/) is a **cross-platform native runtime for *deploying web applications to mobile***. It is maintained by [Ionic](https://ionic.io/) and designed as a modern successor to Cordova. It supports most, but not all Cordova plugins, as well as Capacitor-specific plugins (called APIs). It exposes native device APIs in the form of JavaScript modules.
    >
    > ——[Quasar - What is Capacitor](https://quasar.dev/quasar-cli-vite/developing-capacitor-apps/introduction#introduction)

  - **借助 Cordova 开发**

    > Apache **Cordova is a *mobile application* development framework** originally created by Nitobi. Adobe Systems purchased Nitobi in 2011, rebranded it as PhoneGap, and later released an open source version of the software called Apache Cordova.
    >
    > [Apache Cordova](https://cordova.apache.org/) enables software programmers to build applications for mobile devices using CSS3, HTML5, and JavaScript instead of relying on platform-specific APIs like those in Android, iOS, or Windows Phone. It enables wrapping up of CSS, HTML, and JavaScript code depending upon the platform of the device. It extends the features of HTML and JavaScript to work with the device. The resulting applications are hybrid, meaning that they are neither truly native mobile application (because all layout rendering is done via Web views instead of the platform’s native UI framework) nor purely Web-based (because they are not just Web apps, but are packaged as apps for distribution and have access to native device APIs).
    >
    > You can hook into the native device APIs by using [Cordova Plugins](https://quasar.dev/quasar-cli-vite/developing-cordova-apps/cordova-plugins).
    >
    > ——[Quasar - What is Cordova](https://quasar.dev/quasar-cli-vite/developing-cordova-apps/introduction)

  



# Ref

+ [quasar 简介](https://blog.csdn.net/BDawn/article/details/102477936)
+ [quasar 参考文档 ](https://www.cnblogs.com/q1104460935/p/15663108.html) 👍
+ [quasar-cli项目创建](https://blog.csdn.net/web_monkey888/article/details/119803934) 👍
+ [quasar使用记录-安装配置](https://zhuanlan.zhihu.com/p/363921765)
+ https://www.yuque.com/fictiony/cs6lwq/nzrxtl

