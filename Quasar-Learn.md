# Quasar - Learn

整理我学习Quasar的笔记，网上大多文章都是旧版本的Quasar，有很多命令（如 `quasar init` ）已经弃用了，并且目录结构也有些许不一样（配置文件从 `quasar.conf.js` 变成了 `quasar.config.js` 等）。最新版本的英文文档，我一开始点进去他就直接介绍组件、api，一脸懵逼，不是特别友好。因此，本文档梳理了各种搜集到的文章，主要结合官方英文文档，重新排版一份我自己的入门学习笔记。

请直接从 <a href="#start"> 安装 Quasar</a> 这节开始阅读，前面几节踩坑记录。

**Presented By R.G.**

**Begin on 2022.05.18**

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

可以了，不过命令变了（我一开始看到的都是旧版本的资料）

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

> 如果你是初学者，你需要关心的是`/quasar.config.js`（Quasar App配置文件）、`/src/router`、`/src/layouts`、`/src/pages`和可选的`/src/assets`。

```powershell
.
├── public/                  # 纯静态资源（直接复制）
├── src/
│   ├── assets/              # 动态资源（由webpack处理）
│   ├── components/          # 用于页面和布局的.vue组件
│   ├── css/                 # CSS/Stylus/Sass/...文件【里面具体是啥，看你选哪个css预处理器】
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

> 参考：[quasar 参考文档 ](https://www.cnblogs.com/q1104460935/p/15663108.html) 【旧版本了，新版本请看后文】

<a name="start"></a>

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
quasar init <folder-name>
quasar create <folder-name>
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

#### ※ SPA（Single-Page Application，单页应用程序/网站）

> <u>A **Single-Page Application (SPA)** is a web application or web site that interacts with the user by ***dynamically rewriting the current page rather than loading entire new pages from a server***.</u> This approach avoids interruption of the user experience between successive pages, making the application ***behave more like a desktop application***.
>
> ——[Quasar - What is SPA](https://quasar.dev/quasar-cli-vite/developing-spa/introduction#introduction)
>
> 
>
> **单页Web应用（single page web application，SPA）**，就是只有一张Web页面的应用。单页应用程序 (SPA) 是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。  浏览器一开始会加载必需的HTML、CSS和JavaScript，所有的操作都在这张页面上完成，都由JavaScript来控制。因此，对单页应用来说模块化的开发和设计显得相当重要。
>
> —— https://baike.baidu.com/item/SPA/17536313

#### PWA（Progressive Web App, 渐进式Web应用）

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

#### ※ SSR(Server-Side Rendering, 服务器端渲染)

> ==Quasar and Vue.js are frameworks for building **client-side** applications==. By default, Quasar Vue components produce and manipulate DOM in the browser as output. <u>However, it is **also possible to render the same components into HTML strings on the server**, send them directly to the browser, and finally “hydrate” the static markup into a fully interactive app on the client.</u>
>
> A **server-rendered Quasar app** can also be considered `isomorphic` or `universal`, in the sense that the majority of **your app’s code runs on both the server and the client.**
>
> ——[Quasar - What is SSR](https://quasar.dev/quasar-cli-vite/developing-ssr/introduction#introduction)
>
> 
>
> - SSR（服务器端渲染应用程序）（+可选的PWA客户端接管）
>
> **服务器端渲染（SSR）**的意思是在服务器上渲染网页，因此首次加载会更快，但是在不同页面之间导航都需要下载新的HTML内容。它的跨浏览器兼容性良好，但代价是页间加载时间延长，也就是总体感知上的性能降低：每加载一个页面，都需要一个服务器请求往返的时间。
>
> 与之对应的就是 **客户端渲染（CSR）**，回顾 <a href="#ssr">这里</a>

#### BEX（Browser Extension，浏览器扩展）

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

#### Electron应用（桌面应用程序）

> [Electron](https://electronjs.org/) (formerly known as Atom Shell) is an open-source framework created by Cheng Zhao, and now developed by GitHub. <u>**It allows for the development of ==desktop GUI applications==** using front and back end components originally developed for web applications: **Node.js runtime for the backend** and **Chromium for the frontend**.</u> Electron is the main GUI framework behind several notable open-source projects including GitHub’s Atom and Microsoft’s Visual Studio Code source code editors, the Tidal music streaming service desktop application and the Light Table IDE, in addition to the freeware desktop client for the Discord chat service.
>
> Each Electron app has two threads: one is the main thread (dealing with the App window and bootup), and one is the renderer thread (which is basically your UI web code). There is also a preload script to bridge the two “worlds”.
>
> ——[Quasar - What is Electron](https://quasar.dev/quasar-cli-vite/developing-electron-apps/introduction)
>
> 
>
> VS Code 就是用 Electron 开发的哦~

#### 移动APP

> Quasar offers two solutions for creating mobile apps:
>
> - **Capacitor** was created by Ionic Framework as a more modern replacement for Cordova. It supports most, but not all, Cordova plugins as well as Capacitor-specific plugins.
> - **Cordova** is a mobile application development framework originally created by Nitobi. Adobe Systems purchased Nitobi in 2011, rebranded it as PhoneGap, and later released an open source version of the software called Apache Cordova.

##### 借助 Capacitor 开发移动应用

> [Capacitor](https://capacitorjs.com/) is a **cross-platform native runtime for *deploying web applications to mobile***. It is maintained by [Ionic](https://ionic.io/) and designed as a modern successor to Cordova. It supports most, but not all Cordova plugins, as well as Capacitor-specific plugins (called APIs). It exposes native device APIs in the form of JavaScript modules.
>
> ——[Quasar - What is Capacitor](https://quasar.dev/quasar-cli-vite/developing-capacitor-apps/introduction#introduction)

##### 借助 Cordova 开发移动应用

> Apache **Cordova is a *mobile application* development framework** originally created by Nitobi. Adobe Systems purchased Nitobi in 2011, rebranded it as PhoneGap, and later released an open source version of the software called Apache Cordova.
>
> [Apache Cordova](https://cordova.apache.org/) enables software programmers to build applications for mobile devices using CSS3, HTML5, and JavaScript instead of relying on platform-specific APIs like those in Android, iOS, or Windows Phone. It enables wrapping up of CSS, HTML, and JavaScript code depending upon the platform of the device. It extends the features of HTML and JavaScript to work with the device. The resulting applications are hybrid, meaning that they are neither truly native mobile application (because all layout rendering is done via Web views instead of the platform’s native UI framework) nor purely Web-based (because they are not just Web apps, but are packaged as apps for distribution and have access to native device APIs).
>
> You can hook into the native device APIs by using [Cordova Plugins](https://quasar.dev/quasar-cli-vite/developing-cordova-apps/cordova-plugins).
>
> ——[Quasar - What is Cordova](https://quasar.dev/quasar-cli-vite/developing-cordova-apps/introduction)



## Quasar 项目结构（最新版本）

> 如果你是初学者，你需要关心的是`/quasar.config.js`（Quasar App配置文件）、`/src/router`、`/src/layouts`、`/src/pages`和可选的`/src/assets`。

```
.
├── public/                  # pure static assets (directly copied)
├── src/
│   ├── assets/              # dynamic assets (processed by webpack)
│   ├── components/          # .vue components used in pages & layouts
│   ├── css/                 # CSS/Sass/... files for your app
|   |   ├── app.sass
|   │   └── quasar.variables.sass # Quasar Sass variables for you to tweak
│   ├── layouts/             # layout .vue files
│   ├── pages/               # page .vue files
│   ├── boot/                # boot files (app initialization code)
│   ├── router/              # Vue Router
|   |   ├── index.js         # Vue Router definition
|   │   └── routes.js        # App Routes definitions
│   ├── stores/              # Pinia Stores (if not using Vuex)
|   |   ├── index.js         # Pinia initialization
|   │   ├── <store>          # Pinia stores...
|   │   └── <store>...
│   ├── store/               # Vuex Store (if not using Pinia)
|   |   ├── index.js         # Vuex Store definition
|   │   ├── <folder>         # Vuex Store Module...
|   │   └── <folder>         # Vuex Store Module...
│   ├── App.vue              # root Vue component of your App
│   └── index.template.html  # Template for index.html
├── src-ssr/                 # SSR specific code (like production Node webserver)
├── src-pwa/                 # PWA specific code (like Service Worker)
├── src-cordova/             # Cordova generated folder used to create Mobile Apps
├── src-electron/            # Electron specific code (like "main" thread)
├── src-bex/                 # BEX (browser extension) specific code (like "main" thread)
├── dist/                    # where production builds go
│   ├── spa/                 # example when building SPA
│   ├── ssr/                 # example when building SSR
│   ├── electron/            # example when building Electron
│   └── ....
├── quasar.config.js           # Quasar App Config file
├── babel.config.js          # Babeljs config
├── .editorconfig            # editor config
├── .eslintignore            # ESlint ignore paths
├── .eslintrc.js             # ESlint config
├── .postcssrc.js            # PostCSS config
├── .gitignore               # GIT ignore paths
├── package.json             # npm scripts and dependencies
└── README.md                # readme for your website/App
```





## Quasar CLI 基础命令

### help 帮助命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar help


 .d88888b.
d88P" "Y88b
888     888
888     888 888  888  8888b.  .d8888b   8888b.  888d888
888     888 888  888     "88b 88K          "88b 888P"
888 Y8b 888 888  888 .d888888 "Y8888b. .d888888 888
Y88b.Y8b88P Y88b 888 888  888      X88 888  888 888
 "Y888888"   "Y88888 "Y888888  88888P' "Y888888 888
       Y8b

  Running @quasar/cli v1.3.2
  Running @quasar/app-webpack v3.5.1

  Example usage
    $ quasar <command> <options>

  Help for a command
    $ quasar <command> --help
    $ quasar <command> -h

  Options
    --version, -v Print Quasar App CLI version

  Commands
    dev, d        Start a dev server for your App
    build, b      Build your app for production
    clean, c      Clean all build artifacts
    new, n        Quickly scaffold page/layout/component/... vue file
    mode, m       Add/remove Quasar Modes for your App
    inspect       Inspect generated Webpack config
    ext, e        Manage Quasar App Extensions
    run, r        Run specific command provided by an installed
                    Quasar App Extension
    describe      Describe a Quasar API (component)
    test, t       Run @quasar/testing App Extension command
                    - requires @quasar/testing App Extension to be installed
                    - this is an alias command for convenience purposes
    info, i       Display info about your machine and your App
    help, h       Displays this message

  If the specified command is not found, then "quasar run"
  will be executed with the provided arguments.

  Commands supplied by @quasar/cli global installation:

    upgrade       Check (and optionally) upgrade Quasar packages
                    from a Quasar project folder
    serve         Create an ad-hoc server on App's distributables

```

### info 信息展示命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar info -h

  Description
    Displays information about your machine and your Quasar App.

  Usage
    $ quasar info

  Options
    --help, -h     Displays this message
```

### dev 开发服务器运行命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar dev -h

  Description
    Starts the app in development mode (hot-code reloading, error
    reporting, etc)

  Usage
    $ quasar dev
    $ quasar dev -p <port number>

    $ quasar dev -m ssr

    # alias for "quasar dev -m cordova -T ios"
    $ quasar dev -m ios

    # alias for "quasar dev -m cordova -T android"
    $ quasar dev -m android

    # passing extra parameters and/or options to
    # underlying "cordova" or "electron" executables:
    $ quasar dev -m ios -- some params --and options --here
    $ quasar dev -m electron -- --no-sandbox --disable-setuid-sandbox
    # when on Windows and using Powershell:
    $ quasar dev -m ios '--' some params --and options --here
    $ quasar dev -m electron '--' --no-sandbox --disable-setuid-sandbox

  Options
    --mode, -m       App mode [spa|ssr|pwa|cordova|capacitor|electron|bex] (default: spa)
    --port, -p       A port number on which to start the application
    --hostname, -H   A hostname to use for serving the application
    --help, -h       Displays this message

    Only for Cordova mode:
    --target, -T     (required) App target
                        [android|ios]
    --emulator, -e   (optional) Emulator name
                        Examples: iPhone-7, iPhone-X
                        iPhone-X,com.apple.CoreSimulator.SimRuntime.iOS-12-2
    --ide, -i        Open IDE (Android Studio / XCode) instead of letting Cordova
                        booting up the emulator, in which case the "--emulator"
                        param will have no effect

    --devtools, -d   Open remote Vue Devtools

    Only for Capacitor mode:
    --target, -T     (required) App target
                        [android|ios]
```

> Quasar开发服务器允许您通过编译和维护内存代码来开发您的应用程序。 一个Web服务器将为您的应用程序提供热备功能。 运行内存可以在更改代码时提供更快的重建速度。
>
> > Hot Reload不仅仅是在代码更改时刷新浏览器。 它会跳过刷新并在运行中更新您的代码，同时保持您的应用程序的状态（如您的Vue的模型数据）。 请注意，有些情况下这是不可能的，所以dev的网络服务器只会刷新你的浏览器。 （一定要确保一次只运行一个Quasar CLI实例，否则Hot-Reload和其他内容将会中断！）
>
> 根据您要开发的内容，您可以使用“quasar dev”命令启动开发服务器，如下所示：
>
> ```shell
> # Developing a SPA
> $ quasar dev
> # ...or
> $ quasar dev -m spa
> 
> # Developing a PWA
> $ quasar dev -m pwa
> 
> # Developing a Mobile App (through Cordova)
> $ quasar dev -m cordova -T [android|ios]
> 
> # Developing an Electron App
> $ quasar dev -m electron
> ```
>
> 但是，有两个主题可用：Material Design（’mat’）和iOS（’ios’）。 为了指定一个特定的主题，在上面的命令中添加’-t’参数：
>
> ```shell
> # Material Design
> $ quasar dev -t mat
> 
> # iOS theme
> $ quasar dev -t ios
> ```
>
> 如果您想更改为您的应用程序提供服务的主机名或端口，您有3个选项：
>
> - 编辑 ‘/quasar.conf.js’:
>
>   ```shell
>   devServer: {
>     host: '...',
>     port: ...
>   }
>   ```
>
> - 通过’-H’（主机名）和’-p’（端口）命令选项。
>
> - 如果这是一次性事情，请将主机名和/或端口指定为环境变量：
>
>   ```shell
>   $ PORT=3000 quasar dev
>   $ HOSTNAME=1.1.1.14 quasar dev
>   ```
>
> 如果似乎有热重载的问题，您可以尝试两个修补程序：
>
> - 更改项目文件夹的权限
>
>   ```shell
>   sudo chown -R username: .
>   ```
>
> - 或者以root权限运行开发服务器
>
>   ```shell
>   sudo quasar dev
>   ```
>
> —— [上古版本的quasar中文文档](http://v0-16.quasarchs.com/guide/quasar-cli.html)

### build 构建命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar build -h

  Description
    Builds distributables of your app.

  Usage
    $ quasar build
    $ quasar build -p <port number>

    $ quasar build -m ssr

    # alias for "quasar build -m cordova -T ios"
    $ quasar build -m ios

    # alias for "quasar build -m cordova -T android"
    $ quasar build -m android

    # passing extra parameters and/or options to
    # underlying "cordova" executable:
    $ quasar build -m ios -- some params --and options --here
    # when on Windows and using Powershell:
    $ quasar build -m ios '--' some params --and options --here

  Options
    --mode, -m      App mode [spa|ssr|pwa|cordova|capacitor|electron|bex] (default: spa)  
    --target, -T    App target
                      - Cordova (default: all installed)
                        [android|ios]
                      - Capacitor
                        [android|ios]
                      - Electron with default "electron-packager" bundler (default: yours)
                        [darwin|win32|linux|mas|all]
                      - Electron with "electron-builder" bundler (default: yours)
                        [darwin|mac|win32|win|linux|all]
    --publish, -P   Also trigger publishing hooks (if any are specified)
                      - Has special meaning when building with Electron mode and using    
                        electron-builder as bundler
    --debug, -d     Build for debugging purposes
    --skip-pkg, -s  Build only UI (skips creating Cordova/Capacitor/Electron executables)
                      - Cordova (it only fills in /src/cordova/www folder with the UI code)
                      - Capacitor (it only fills in /src/capacitor/www folder with the UI code)
                      - Electron (it only creates the /dist/electron/UnPackaged folder)
    --help, -h      Displays this message

    ONLY for Cordova and Capacitor mode:
    --ide, -i       Open IDE (Android Studio / XCode) instead of finalizing with a
                    terminal/console-only build

    ONLY for Electron mode:
    --bundler, -b   Bundler (electron-packager or electron-builder)
                      [packager|builder]
    --arch, -A      App architecture (default: yours)
                      - with default "electron-packager" bundler:
                          [ia32|x64|armv7l|arm64|mips64el|all]
                      - with "electron-builder" bundler:
                          [ia32|x64|armv7l|arm64|all]

    ONLY for electron-builder (when using "publish" parameter):
    --publish, -P  Publish options [onTag|onTagOrDraft|always|never]
                     - see https://www.electron.build/configuration/publish

```

> Quasar CLI可以将所有东西封装在一起，并优化您的应用程序进行生产。 它可以缩减源代码，提取供应商组件，利用浏览器缓存等等。
>
> ```shell
> # build for production
> $ quasar build
> 
> # build for production with specific theme
> $ quasar build -t mat
> $ quasar build -t ios
> $ quasar build -m pwa -t mat
> ```

### clean 清理构建命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar clean -h

  Description
    Cleans all build artifacts
  Usage
    $ quasar clean
  Options
    --help, -h     Displays this message

```

### mode 模式控制命令

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar mode -h

  Description
    Add/Remove support for PWA / BEX / Cordova / Capacitor / Electron modes.   

  Usage
    $ quasar mode [add|remove] [pwa|ssr|bex|cordova|capacitor|electron] [--yes]

    # determine what modes are currently installed:
    $ quasar mode

  Options
    --yes, -y     Skips the "Are you sure?" question
                  when removing a Quasar mode
    --help, -h    Displays this message

```

> 当您使用主入门套件时，您可以构建SPA（单页网站/应用程序），PWA（Progressive Web App），Mobile App（通过Cordova）和/或Electron Apps。当您开发PWA，Cordova或Electron时，需要安装这些模式。如果您发出“quasar dev”或“quasar build”，它们将自动安装。
>
> 这些模式将在您的项目中添加一个“src- *”文件夹，其中包含非常具体的代码：
>
> | 文件夹       | 模式     | 说明                                                         |
> | :----------- | :------- | :----------------------------------------------------------- |
> | src-pwa      | pwa      | 包含您可以调整的Service Worker文件。                         |
> | src-cordova  | cordova  | 是一个Cordova项目文件夹，将使用您的’src’作为内容。从此文件夹中调整Cordova配置，添加/删除平台，启动画面，Cordova插件等。不要触摸“src-cordova/www”文件夹，因为它会在每个版本中被覆盖。 |
> | src-electron | electron | 具有主电子线程的代码。渲染器线程将成为’src’中的应用程序。    |
>
> 如果由于某种原因您决定不需要某种模式，则可以将其删除。**这将永久删除**相应的“src-*”文件夹。
>
> ```shell
> $ quasar mode --remove pwa
> ```

### serve

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar serve -h

  Description
    Start a HTTP(S) server on a folder.

  Usage
    $ quasar serve [path]
    $ quasar serve . # serve current folder

    If you serve a SSR folder built with the CLI then
    control is yielded to /index.js and params have no effect.

  Options
    --port, -p              Port to use (default: 4000)
    --hostname, -H          Address to use (default: 0.0.0.0)
    --gzip, -g              Compress content (default: true)
    --silent, -s            Suppress log message
    --colors                Log messages with colors (default: true)
    --open, -o              Open browser window after starting
    --cache, -c <number>    Cache time (max-age) in seconds;
                            Does not apply to /service-worker.js
                            (default: 86400 - 24 hours)
    --micro, -m <seconds>   Use micro-cache (default: 1 second)

    --history               Use history api fallback;
                              All requests fallback to /index.html,
                              unless using "--index" parameter
    --index, -i <file>      History mode (only!) index url path
                              (default: index.html)

    --https                 Enable HTTPS
    --cert, -C [path]       Path to SSL cert file (Optional)
    --key, -K [path]        Path to SSL key file (Optional)
    --proxy <file.js>       Proxy specific requests defined in file;
                            File must export Array ({ path, rule })
                            See example below. "rule" is defined at:
                            https://github.com/chimurai/http-proxy-middleware
    --cors                  Enable CORS for all requests
    --help, -h              Displays this message

  Proxy file example
    module.exports = [
      {
        path: '/api',
        rule: { target: 'http://www.example.org' }
      }
    ]
    --> will be transformed into app.use(path, httpProxyMiddleware(rule))
```

> 构建SPA或PWA时，可分发的文件夹可由任何静态网络服务器提供服务。 为了测试它（假设您没有特定的publicPath或者没有使用Vue Router“history”模式），您可以使用“http-server”npm软件包。
>
> 或者你可以建立你自己的服务器。 这里有些例子：
>
> ```shell
> // when using default Vue Router "hash" mode
> const
>   express = require('express'),
>   serveStatic = require('serve-static'),
>   port = process.env.PORT || 5000
> 
> const app = express()
> 
> app.use(serveStatic(...path-to-dist...))
> app.listen(port)
> ```
>
> 
>
> ```shell
> // when using Vue Router "history" mode
> const
>   express = require('express'),
>   serveStatic = require('serve-static'),
>   history = require('connect-history-api-fallback'),
>   port = process.env.PORT || 5000
> 
> const app = express()
> 
> app.use(history())
> app.use(serveStatic(...path-to-dist...))
> app.listen(port)
> ```
>
> 如果您需要重写URL的URL，或者只需要代理您的API请求，那么您可以使用“http-proxy-middleware”软件包：
>
> ```shell
> // add this to one of the two previous examples:
> const proxy = require('http-proxy-middleware')
> 
> // ...
> app.use('/api', proxy({
>   '/api': {
>     target: `http://my-api.com:5050`,
>     pathRewrite: {"^/api" : ""}
>   }
> }))
> 
> // then app.listen(...)
> ```
>
> 
>
> Finally, run one of these files:
>
> ```shell
> $ node my-server.js
> ```
>
> 摘自 [上古版本的quasar文档 - serve (提供静态内容文件夹)](http://v0-16.quasarchs.com/guide/quasar-cli.html#serve-提供静态内容文件夹)，注意可能有些代码已经过时

### new

```shell
PS C:\Users\NERO\Desktop\Quasar-learn\source\Q-demo-1> quasar new -h

  Description
    Quickly scaffold a page/layout/component/store module.

  Usage
    $ quasar new <p|page> [-f <option>] <page_file_name>
    $ quasar new <l|layout> [-f <option>] <layout_file_name>
    $ quasar new <c|component> [-f <option>] <component_file_name>
    $ quasar new <b|boot> [-f ts] <boot_name>
    $ quasar new <s|store> [-f ts] <store_module_name>
    $ quasar new ssrmiddleware <middleware_name>

    # Examples:

    # Create src/pages/MyNewPage.vue:
    $ quasar new p MyNewPage

    # Create src/pages/MyNewPage.vue and src/pages/OtherPage.vue:
    $ quasar new p MyNewPage OtherPage

    # Create src/layouts/shop/Checkout.vue
    $ quasar new layout shop/Checkout.vue

    # Create src/layouts/shop/Checkout.vue with TypeScript options API      
    $ quasar new layout -f ts-options shop/Checkout.vue

    # Create a store with TypeScript support
    $ quasar new store -f ts myStore

  Options
    --help, -h            Displays this message

    --format -f <option>  (optional) Use a supported format for the template
                          Option can be:
                             * ts-options - TS options API
                             * ts-composition - TS composition API
                             * ts-class - [DEPRECATED] TS class style syntax
                             * ts - use for TS boot file and store modules only
```

这个命令不要用，自己新建文件，然后自己写内容就好，new命令只是帮你快速创建文件（里面会有默认的模板内容）

> 这个命令只是一个辅助工具，以便快速搭建page/layout/component/vuex store模块。 你不需要使用它，但可以帮助你，当你不知道如何开始。

### 其他

其他命令，自行用 `quasar <command> -h` 查阅



# Ref

+ [Quasar 最新版v2.7.0 英文文档](https://quasar.dev/quasar-cli-webpack/quasar-config-js) 【主要看这个文档】
  + 看了半天，终于知道从哪里看了，从 `Quasar CLI(With Webpack)` 这部分看起
  + 一开始我是看上古版本的中文文档，然后对比最新英文文档，才发现从👆这节看比较合适
  + 上古版本文档：http://v0-16.quasarchs.com/，他有个 1min 入门，点进去
+ [quasar 简介](https://blog.csdn.net/BDawn/article/details/102477936)
+ [quasar 参考文档 ](https://www.cnblogs.com/q1104460935/p/15663108.html) 👍【老旧版本】
+ [quasar-cli项目创建](https://blog.csdn.net/web_monkey888/article/details/119803934) 👍 【老旧版本】
+ [quasar使用记录-安装配置](https://zhuanlan.zhihu.com/p/363921765)
+ https://www.yuque.com/fictiony/cs6lwq/nzrxtl

