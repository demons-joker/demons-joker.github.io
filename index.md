

# NODE

## [nodejs安装](https://nodejs.org/zh-cn/)

```js
1.安装时Add to PATH添加node安装路径到环境变量

2.假如路径D:\nodejs\

3.在安装路径下创建两个文件夹【node_global】及【node_cache】同【node_modules】平级

4.创建完两个空文件夹之后，打开cmd命令窗口，输入
	npm config set prefix "D:\nodejs\node_global"
	npm config set cache "D:\nodejs\node_cache"

5.修改环境变量：
	在【系统变量】下新建【NODE_PATH】，输入【D:\nodejs\node_modules】
    将【用户变量】下的【Path】里面的npm后缀的路径修改为【D:\nodejs\node_global】
```



# NPM

## npm包介绍



```
在npm引用的依赖的时候，会在项目的根目录生成node_modules文件夹和package.json文件。
依赖文件包存放在node_modules中，package.json记录的是开发环境和生产环境的依赖名字。这样有利于在某个包丢失的时候，可以针对哪个环境下进行恢复。
```



## 包管理



```
安装包的时候，做一个分类管理：

开发环境 npm 包名 -D —> devDependencies 开发和测试环境中依赖的包，项目上线之后不需要
生产环境 npm 包名 -S —> dependencies 项目正常运行依赖的包，项目上线后会使用到的包
具体安装环境自行判断
```



#### npm install -S

```
 即--save（保存）
包名会被注册在package.json的dependencies里面，在生产环境下这个包的依赖依然存在 如 vue ,react 等
```



#### npm install -D

```
即--dev（生产）
包名会被注册在package.json的devDependencies里面，仅在开发环境下存在的包用-D，如babel，sass-loader， gulp ，babel，webpack 一般都是辅助工具
```



#### npm uninstall 

```
npm uninstall jquery --save   //----删除dependencies  [项目依赖包]  中的jquery  【npm uninstall *】快速删除所有包
```

```
npm uninstall jquery --save-dev   //-----删除devDependencies  [开发依赖包]  中的jquery
```







# VUE3.X



![image-20201211165528106](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201211165528106.png)



| vue2.x                                    | vue3.x                                      |
| ----------------------------------------- | ------------------------------------------- |
| beforeCreate(组件创建之前)                | setup(组件创建之前)                         |
| created(组件创建完成)                     | setup(组件创建完成)                         |
| beforeMount(组件挂载之前)                 | onBeforeMount(组件挂载之前)                 |
| mounted(组件挂载完成)                     | onMounted(组件挂载完成)                     |
| beforeUpdate(数据更新，虚拟DOM打补丁之前) | onBeforeUpdate(数据更新，虚拟DOM打补丁之前) |
| updated(数据更新，虚拟DOM渲染完成)        | onUpdated(数据更新，虚拟DOM渲染完成)        |
| beforeDestroy(组件销毁之前)               | onBeforeUnmount(组件销毁之前)               |
| destroyed(组件销毁之后)                   | onUnmounted(组件销毁之后)                   |



## vue.config.js**配置**



### **publicPath**

```
Type: string

Default: '/'

 部署应用包时的基本 URL， 用法和 webpack 本身的 output.publicPath 一致。

这个值也可以被设置为空字符串 ('') 或是相对路径 ('./')，这样所有的资源都会被链接为相对路径，这样打出来的包可以被部署在任意路径。
```



### **outputDir**

```
Type: string

Default: 'dist'

输出文件目录，当运行 vue-cli-service build 时生成的生产环境构建文件的目录。注意目标目录在构建之前会被清除 (构建时传入 --no-clean 可关闭该行为)。
```



### **assetsDir**

```
Type: string

Default: ''

放置生成的静态资源 (js、css、img、fonts) 的目录。
```



### **indexPath**

```
Type: string

Default: 'index.html'

指定生成的 index.html 的输出路径 (相对于 outputDir)。也可以是一个绝对路径。
```



### **filenameHashing**

```
Type: boolean

Default: true

默认情况下，生成的静态资源在它们的文件名中包含了 hash 以便更好的控制缓存。然而，这也要求 index 的 HTML 是被 Vue CLI 自动生成的。如果你无法使用 Vue CLI

生成的 index HTML，你可以通过将这个选项设为 false 来关闭文件名哈希。
```



### **pages**

```
Type: Object

Default: undefined

在 multi-page（多页）模式下构建应用。每个“page”应该有一个对应的 JavaScript 入口文件。

其值应该是一个对象，对象的 key 是入口的名字，value 是：一个指定了 entry, template, filename, title 和 chunks 的对象 (除了 entry 之外都是可选

的)；或一个指定其 entry 的字符串
```



### **lintOnSave**

```
Type: boolean | 'error'

Default: true

是否在保存的时候使用 `eslint-loader` 进行检查。 有效的值：`ture` | `false` | `"error"`  当设置为 `"error"` 时，检查出的错误会触发编译失败。
```



### **runtimeCompiler**

```
Type: boolean

Default: false

是否使用包含运行时编译器的 Vue 构建版本。设置为 true 后你就可以在 Vue 组件中使用 template 选项了，但是这会让你的应用额外增加 10kb 左右。
```



### **transpileDependencies**

```
Type: Array<string | RegExp>

Default: []

默认情况下 babel-loader 会忽略所有 node_modules 中的文件。如果你想要通过 Babel 显式转译一个依赖，可以在这个选项中列出来。
```



### **productionSourceMap**

```
Type: boolean

Default: true

如果你不需要生产环境的 source map，可以将其设置为 false 以加速生产环境构建。（生产环境必须手动设置false）
```



### **crossorigin**

```
Type: string

Default: undefined

设置生成的 HTML 中 <link rel="stylesheet"> 和 <script> 标签的 crossorigin 属性。
```



### **integrity**

> ```
> Type: boolean
> 
> Default: false
> 
> 在生成的 HTML 中的 <link rel="stylesheet"> 和 <script> 标签上启用 Subresource Integrity (SRI)。如果你构建后的文件是部署在 CDN 上的，启用该选
> 
> 项可以提供额外的安全性。
> ```



## **devServer**配置

> ```js
> Type: Object
> 
> 所有 webpack-dev-server 的选项都支持。注意：
> 
> 有些值像 host、port 和 https 可能会被命令行参数覆写。
> 
> 有些值像 publicPath 和 historyApiFallback 不应该被修改，因为它们需要和开发服务器的 publicPath 同步以保障正常的工作。
> 
> 此处只列出项目中普遍用到的配置，完整文档请查看 https://www.webpackjs.com/
> ```



### **devServer.open**

```html
Type: string | Object 

Default: false

告诉 dev-server 在服务器启动后打开浏览器。 将其设置为 true 以打开默认浏览器。
```



### **devServer.host**

```js
Type: string

Default: 'localhost'

指定要使用的 host。如果你希望服务器可从外部访问，请按以下方式进行配置：

module.exports = {
  //...
  devServer: {
    host: '0.0.0.0'
  }
};

通过命令行使用 webpack serve --host 0.0.0.0
```



### **devServer.hot**

```
Type: boolean

启用 webpack 的 Hot Module Replacement 功能(热部署)
```



### **devServer.overlay**

```js
Type: object

{ 
    errors : false, 
	warnings: = true 
}

出现编译器错误或警告时，在浏览器中显示全屏覆盖。 如果只想显示编译器错误
```





### **devServer.port**

```
Type: string | number

Default: 8080

指定端口号以侦听请求

通过命令行使用 webpack serve --port 8080
```



### **devServer.proxy**

```js
Type: string | Object

如果你的前端应用和后端 API 服务器没有运行在同一个主机上，你需要在开发环境下将 API 请求代理到 API 服务器。这个问题可以通过 vue.config.js 中

的 devServer.proxy 选项来配置。

proxy: {
    //现在，对 /api/users 的请求会将请求代理到 http://localhost:3000/api/users
	"/api": {
        target: "http://localhost:3000", //代理目标服务地址+端口
        /* 允许跨域 */
        changeOrigin: true,
        ws: true,
		secure: false, //默认情况下，将不接受在 HTTPS 上运行且证书无效的后端服务器。 如果需要，可以这样修改配置
        pathRewrite: { //如果不希望传递/api，则需要重写路径
          "^/api": ""
        }
	}
}

```





## **vue-cli Webpack相关配置**

> ```
> 以下为cli内置的webpack配置：
> 1.vueCli自带Hot-Module-Replacement（模块热重载）不需要后期添加
> 2.为更好的缓存而做的自动的 vendor chunk splitting（Code splitting）。它的 chunk manifest 会内联在 HTML 里
> ```



### **configureWebpack**

```
Type: Object | Function

如果这个值是一个对象，则会通过 webpack-merge 合并到最终的配置中。

如果这个值是一个函数，则会接收被解析的配置作为参数。该函数及可以修改配置并不返回任何东西，也可以返回一个被克隆或合并过的配置版本。
```



### **chainWebpack**

```
Type: Function

是一个函数，会接收一个基于 webpack-chain 的 ChainableConfig 实例。允许对内部的 webpack 配置进行更细粒度的修改。
```





## vue-cli-service



### vue-cli-service serve

```
用法：vue-cli-service serve [options] [entry]

options：

  --open    在服务器启动时打开浏览器
  --copy    在服务器启动时将 URL 复制到剪切版
  --mode    指定环境模式 (默认值：development)
  --host    指定 host (默认值：0.0.0.0)
  --port    指定 port (默认值：8080)
  --https   使用 https (默认值：false)
  
命令行参数 [entry] 将被指定为唯一入口，而非额外的追加入口。尝试使用 [entry] 覆盖 config.pages 中的 entry 将可能引发错误
```



### vue-cli-service build

```
用法：vue-cli-service build [options] [entry|pattern]

options：

  --mode        指定环境模式 (默认值：production)
  --dest        指定输出目录 (默认值：dist)
  --modern      面向现代浏览器带自动回退地构建应用
  --target      app | lib | wc | wc-async (默认值：app)
  --name        库或 Web Components 模式下的名字 (默认值：package.json 中的 "name" 字段或入口文件名)
  --no-clean    在构建项目之前不清除目标目录
  --report      生成 report.html 以帮助分析包内容
  --report-json 生成 report.json 以帮助分析包内容
  --watch       监听文件变化
  
  
  
--modern 使用现代模式构建应用，为现代浏览器交付原生支持的 ES2015 代码，并生成一个兼容老浏览器的包用来自动回退。

--target 允许你将项目中的任何组件以一个库或 Web Components 组件的方式进行构建。更多细节请查阅构建目标。

--report 和 --report-json 会根据构建统计生成报告，它会帮助你分析包中包含的模块们的大小。
  
```



### vue-cli-service inspect

```
用法：vue-cli-service inspect [options] [...paths]

options：

  --mode    指定环境模式 (默认值：development)

审查 Vue CLI 项目的 webpack config
```







## **Css相关配置**



### **css.modules**

```
Type: boolean

Default: false

默认情况下，只有 *.module.[ext] 结尾的文件才会被视作 CSS Modules 模块。设置为 true 后你就可以去掉文件名中的 .module 并将所有的 *.

(css|scss|sass|less|styl(us)?) 文件视为 CSS Modules 模块。
```



### **css.extract**

```
Type: boolean | Object

Default: 生产环境下是 true，开发环境下是 false

是否将组件中的 CSS 提取至一个独立的 CSS 文件中 (而不是动态注入到 JavaScript 中的 inline 代码)。
```



### **css.sourceMap**

```
Type: boolean

Default: false

是否为 CSS 开启 source map。设置为 true 之后可能会影响构建的性能。
```



### **css.loaderOptions**

```
Type: Object

Default: {}

向 CSS 相关的 loader 传递选项。支持的 loader 有：css-loader，postcss-loader，sass-loader，less-loader，stylus-loader
```



# JavaScript



## Promise 对象

```js
1、对象的状态不受外界影响。Promise 对象代表一个异步操作，有三种状态：

    pending: 初始状态，不是成功或失败状态。
    
    fulfilled: 意味着操作成功完成。
    
    rejected: 意味着操作失败。
    
    只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。这也是 Promise 这个名字的由来，它的英语意思就是「承诺」，表示其他手段无法改变。

2、一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise 对象的状态改变，只有两种可能：从 Pending 变为 Resolved 和从 Pending 变为 Rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果。就算改变已经发生了，你再对 Promise 对象添加回调函数，也会立即得到这个结果。这与事件（Event）完全不同，事件的特点是，如果你错过了它，再去监听，是得不到结果的。

var promise = new Promise(function(resolve, reject) {
    // 异步处理
    // 处理结束后、调用resolve 或 reject
});

```







### Promise.prototype.then方法：链式操作

```js
Promise.prototype.then 方法返回的是一个新的 Promise 对象，因此可以采用链式写法。

getJSON("/posts.json").then(function(json) {
  return json.post;
}).then(function(post) {
  // proceed
});

上面的代码使用 then 方法，依次指定了两个回调函数。第一个回调函数完成以后，会将返回结果作为参数，传入第二个回调函数。

如果前一个回调函数返回的是Promise对象，这时后一个回调函数就会等待该Promise对象有了运行结果，才会进一步调用。

getJSON("/post/1.json").then(function(post) {
  return getJSON(post.commentURL);
}).then(function(comments) {
  // 对comments进行处理
});

这种设计使得嵌套的异步操作，可以被很容易得改写，从回调函数的"横向发展"改为"向下发展"。

```



### Promise.prototype.catch方法：捕捉错误

```js
Promise.prototype.catch 方法是 Promise.prototype.then(null, rejection) 的别名，用于指定发生错误时的回调函数。

getJSON("/posts.json").then(function(posts) {
  // some code
}).catch(function(error) {
  // 处理前一个回调函数运行时发生的错误
  console.log('发生错误！', error);
});

Promise 对象的错误具有"冒泡"性质，会一直向后传递，直到被捕获为止。也就是说，错误总是会被下一个 catch 语句捕获。

getJSON("/post/1.json").then(function(post) {
  return getJSON(post.commentURL);
}).then(function(comments) {
  // some code
}).catch(function(error) {
  // 处理前两个回调函数的错误
});
```



### Promise.all方法

```js
Promise.all 方法用于将多个 Promise 实例，包装成一个新的 Promise 实例

var p = Promise.all([p1,p2,p3]);

上面代码中，Promise.all 方法接受一个数组作为参数，p1、p2、p3 都是 Promise 对象的实例。（Promise.all 方法的参数不一定是数组，但是必须具有 iterator 接口，且返回的每个成员都是 Promise 实例。）

p 的状态由 p1、p2、p3 决定，分成两种情况。

（1）只有p1、p2、p3的状态都变成fulfilled，p的状态才会变成fulfilled，此时p1、p2、p3的返回值组成一个数组，传递给p的回调函数。
（2）只要p1、p2、p3之中有一个被rejected，p的状态就变成rejected，此时第一个被reject的实例的返回值，会传递给p的回调函数。

// 生成一个Promise对象的数组
var promises = [2, 3, 5, 7, 11, 13].map(function(id){
  return getJSON("/post/" + id + ".json");
});
 
Promise.all(promises).then(function(posts) {
  // ...  
}).catch(function(reason){
  // ...
});

```

### Promise.race方法

```js
Promise.race 方法同样是将多个 Promise 实例，包装成一个新的 Promise 实例。

var p = Promise.race([p1,p2,p3]);

上面代码中，只要p1、p2、p3之中有一个实例率先改变状态，p的状态就跟着改变。那个率先改变的Promise实例的返回值，就传递给p的返回值。

如果Promise.all方法和Promise.race方法的参数，不是Promise实例，就会先调用下面讲到的Promise.resolve方法，将参数转为Promise实例，再进一步处理。

```



### Promise.resolve 方法

```js
有时需要将现有对象转为Promise对象，Promise.resolve方法就起到这个作用。

var jsPromise = Promise.resolve($.ajax('/whatever.json'));

上面代码将 jQuery 生成 deferred 对象，转为一个新的 ES6 的 Promise 对象。

如果 Promise.resolve 方法的参数，不是具有 then 方法的对象（又称 thenable 对象），则返回一个新的 Promise 对象，且它的状态为fulfilled。

var p = Promise.resolve('Hello');
 
p.then(function (s){
  console.log(s)
});
// Hello

上面代码生成一个新的Promise对象的实例p，它的状态为fulfilled，所以回调函数会立即执行，Promise.resolve方法的参数就是回调函数的参数。

如果Promise.resolve方法的参数是一个Promise对象的实例，则会被原封不动地返回。

```

### Promise.reject 方法

```js
Promise.reject(reason)方法也会返回一个新的Promise实例，该实例的状态为rejected。Promise.reject方法的参数reason，会被传递给实例的回调函数。

var p = Promise.reject('出错了');
 
p.then(null, function (s){
  console.log(s)
});
// 出错了

上面代码生成一个Promise对象的实例，状态为rejected，回调函数会立即执行。
```











# TypeScript

## **tsconfig.json**



```js
{
  "compilerOptions": {
        "target": "esnext", 
        "module": "esnext", 
        "strict": true,
        "jsx": "preserve", 
        "importHelpers": true,
        "moduleResolution": "node",
        "experimentalDecorators": true,
        "esModuleInterop": true,
        "noUnusedLocals": true,
		"noImplicitAny":true,
        "allowSyntheticDefaultImports": true,
        "suppressImplicitAnyIndexErrors": true,
        "strictPropertyInitialization": false,
        "sourceMap": true,
        "baseUrl": ".",
        "types": ["webpack-env", "jest"],
        "paths": {
            "@/*": ["src/*"]
        },
        "lib": ["esnext", "dom", "dom.iterable", "scripthost"]
    },
    "include": [
        "src/**/*.js",
        "src/**/*.ts",
        "src/**/*.tsx",
        "src/**/*.vue",
        "tests/**/*.ts",
        "tests/**/*.tsx"
    ],
    "exclude": [
        "node_modules"
    ]
}
```



## **tsconfig.json完整配置项列表**



| 配置项                                    | **类型**                                                     | **默认值**          | 描述                                                         |
| :---------------------------------------- | ------------------------------------------------------------ | ------------------- | ------------------------------------------------------------ |
| incremental                               | boolean                                                      | false               | 启动增量编译                                                 |
| tsBuildInfoFile                           | string                                                       | .tsbuildinfo        | 指定文件去存储增量编译信息                                   |
| target                                    | string                                                       | ES3                 | 指定ECMAScript目标版本 "ES3"（默认）， "ES5"， "ES6"/ "ES2015"， "ES2016"， "ES2017"或 "ESNext"。 |
| module                                    | string                                                       |                     | 指定使用什么模块代码生成："None"， "CommonJS"， "AMD"， "System"， "UMD"， "ES6"或 "ES2015"。只有 "AMD"和 "System" --outFile一起使用。"ES6"和 "ES2015"可使用在目标输出为 "ES5"或更低的情况下。 |
| lib                                       | array                                                        |                     | 编译过程中需要引入的库文件的列表。可能的值为：ES5、ES6、ES2015、ES7、ES2016、ES2017、ES2018、ESNext、DOM、DOM.Iterable、WebWorker、ScriptHost、ES2015.Core、ES2015.Collection、ES2015.Generator、ES2015.Iterable、ES2015.Promise、ES2015.Proxy、ES2015.Reflect、ES2015.Symbol、ES2015.Symbol.WellKnown、ES2016.Array.Include、ES2017.object、ES2017.Intl、ES2017.SharedMemory、ES2017.String、ES2017.TypedArrays、ES2018.Intl、ES2018.Promise、ES2018.RegExp、ESNext.AsyncIterable、ESNext.Array、ESNext.Intl、ESNext.Symbol 注意：如果--lib没有指定默认注入的库的列表。默认注入的库为：针对于--target ES5：DOM，ES5，ScriptHost、针对于--target ES6：DOM，ES6，DOM.Iterable，ScriptHost |
| allowJs                                   | boolean                                                      | false               | 允许编译javascript文件                                       |
| checkJs                                   | boolean                                                      | false               | 在 .js文件中报告错误                                         |
| jsx                                       |                                                              |                     | 在 .tsx文件里支持JSX："React","react-native"或 "Preserve"    |
| declaration                               | boolean                                                      | false               | 生成相应的 .d.ts文件                                         |
| declarationMap                            | boolean                                                      | false               | 为每个相应的“ .d.ts”文件生成一个sourcemap文件                |
| declarationDir                            | [string, null]                                               |                     | 为生成的声明文件指定输出目录。需要TypeScript 2.0或更高版本。 |
| sourceMap                                 | boolean                                                      | false               | 生成相应的 .map文件                                          |
| outFile                                   | string                                                       |                     | 将输出文件合并为一个文件                                     |
| outDir                                    | string                                                       |                     | 重定向输出目录                                               |
| rootDir                                   | string                                                       |                     | 用来控制输出的目录结构                                       |
| composite                                 | boolean                                                      | true                | 启用项目编译                                                 |
| removeComments                            | boolean                                                      | false               | 删除所有注释，除了以 /!*开头的版权信息                       |
| noEmit                                    | boolean                                                      | false               | 不生成输出文件                                               |
| noEmitHelpers                             | boolean                                                      | false               | 不要在编译输出中生成自定义助手函数，比如__extends。要求TypeScript 1.5或更高版本。 |
| noEmitOnError                             | boolean                                                      | false               | 如果报告了任何类型检查错误，则不要发出输出。要求TypeScript 1.4或更高版本。 |
| importHelpers                             | boolean                                                      | false               | 从 tslib 导入辅助工具函数（比如 __extends， __rest等）       |
| importsNotUsedAsValues                    | "remove",                 "preserve",                 "error" | remove              | 这个标志控制导入的工作方式。当设置为' remove '时，只会删除引用类型的导入。当设置为“保存”时，导入不会被删除。当设置为' error '时，可以被' import type '替换的导入将导致编译器错误。要求TypeScript版本3.8或更高版本。 |
| downlevelIteration                        | boolean                                                      | false               | 当针对“ ES5”或“ ES3”时，在“ for-of”，传播和解构中为可迭代项提供全面支持 |
| isolatedModules                           | boolean                                                      | false               | 将每个文件作为单独的模块（与“ts.transpileModule”类似）       |
| strict                                    | boolean                                                      | false               | 启用所有严格类型检查选项                                     |
| noImplicitAny                             | boolean                                                      |                     | 在表达式和声明上有隐含的 any类型时报错                       |
| strictNullChecks                          | boolean                                                      | false               | 在严格的 null检查模式下， null和 undefined值不包含在任何类型里，只允许用它们自己和 any来赋值（有个例外， undefined可以赋值到 void） |
| strictFunctionTypes                       | boolean                                                      | false               | 启动对函数类型的检查                                         |
| strictBindCallApply                       | boolean                                                      | false               | 在函数上启动"bind","call"和"apply"                           |
| strictPropertyInitialization              | boolean                                                      | false               | 确保类的非undefined属性已经在构造函数里初始化。若要令此选项生效，需要同时启用--strictNullChecks |
| noImplicitThis                            | boolean                                                      |                     | 当 this表达式的值为 any类型的时候，生成一个错误              |
| alwaysStrict                              | boolean                                                      |                     | 以严格模式解析并为每个源文件生成 "use strict"语句            |
| noUnusedLocals                            | boolean                                                      | false               | 若有未使用的局部变量则抛错                                   |
| noUnusedParameters                        | boolean                                                      | false               | 若有未使用的参数则抛错                                       |
| noImplicitReturns                         | boolean                                                      | false               | 不是函数的所有返回路径都有返回值时报错                       |
| noFallthroughCasesInSwitch                | boolean                                                      | false               | 不允许switch的case语句贯穿                                   |
| moduleResolution                          | string                                                       |                     | 如何解析模块:'node' (Node.js) or 'classic' (TypeScript pre-1.6) |
| baseUrl                                   | string                                                       |                     | 解析文档目录                                                 |
| paths                                     | object                                                       |                     | 模块名到基于 baseUrl的路径映射的列表                         |
| rootDirs                                  | array                                                        |                     | 用来控制输出的目录结构                                       |
| typeRoots                                 | array                                                        |                     | 要包含的类型声明文件路径列表                                 |
| types                                     | array                                                        |                     | 要包含的类型声明文件名列表                                   |
| allowSyntheticDefaultImports              | boolean                                                      |                     | 允许从没有设置默认导出的模块中默认导入。这并不影响代码的输出，仅为了类型检查 |
| esModuleInterop                           | boolean                                                      | false               | 通过所有导入创建名称空间对象，启用CommonJS和ES模块之间的相互操作 |
| keyofStringsOnly                          | boolean                                                      | false               | 解析'keyof'为字符串值的属性名(没有数字或符号)。不建议使用此设置。要求TypeScript 2.9或更高版本。 |
| allowUmdGlobalAccess                      | boolean                                                      | false               | 允许从模块访问UMD全局变量                                    |
| sourceRoot                                | string                                                       |                     | 指定TypeScript源文件的路径，以便调试器定位。当TypeScript文件的位置是在运行时指定时使用此标记。路径信息会被加到 sourceMap里 |
| mapRoot                                   |                                                              |                     | 为调试器指定指定sourcemap文件的路径，而不是使用生成时的路径。当 .map文件是在运行时指定的，并不同于 js文件的地址时使用这个标记。指定的路径会嵌入到 sourceMap里告诉调试器到哪里去找它们。 |
| inlineSourceMap                           | boolean                                                      | false               | 生成单个sourcemaps文件，而不是将每sourcemaps生成不同的文件   |
| inlineSources                             | boolean                                                      | false               | 将代码与sourcemaps生成到一个文件中，要求同时设置了 --inlineSourceMap或 --sourceMap属性 |
| experimentalDecorators                    | boolean                                                      |                     | 启用装饰器                                                   |
| emitDecoratorMetadata                     | boolean                                                      |                     | 给源码里的装饰器声明加上设计类型元数据                       |
| skipLibCheck                              | boolean                                                      | false               | 忽略所有的声明文件（ *.d.ts）的类型检查                      |
| skipDefaultLibCheck                       | boolean                                                      | false               | 使用“skipLibCheck”代替。跳过默认库声明文件的类型检查。       |
| forceConsistentCasingInFileNames          | boolean                                                      | false               | 禁止对同一个文件使用大小写不一致的引用                       |
| generateCpuProfile                        | string                                                       | profile.cpuprofile  | 在编译器运行期间发出一个v8 CPI配置文件，这可以提供对缓慢构建的洞察。要求TypeScript 3.7或更高版本。 |
| charset                                   | string                                                       |                     | 输入文件的字符集。不建议使用此设置。                         |
| diagnostics                               | boolean                                                      |                     | 显示诊断信息。不赞成使用此设置。见“extendedDiagnostics.”     |
| disableReferencedProjectLoad              | boolean                                                      |                     | 建议IDE动态加载引用的复合项目，而不是立即全部加载它们。要求TypeScript 4.0或更高版本。 |
| emitBOM                                   | boolean                                                      | false               | 在输出文件的开头发出UTF-8字节的顺序标记(BOM)。               |
| emitDeclarationOnly                       | boolean                                                      | false               | 只有发出的.d。ts的声明文件。要求TypeScript 2.8或更高版本。   |
| reactNamespace                            | string                                                       | React               | 指定对象调用createElement和__spread时，目标'react' JSX发出。 |
| jsxFactory                                | string                                                       | React.createElement | 指定当目标react JSX发出时要使用的JSX工厂函数，例如:"React.createElement"或“h”。要求TypeScript 2.1或更高版本。 |
| jsxFragmentFactory                        | string                                                       | React.Fragment      | 当目标react JSX发出时，指定JSX片段引用来使用片段。例如：”React.Fragment“或者”Fragment“。要求TypeScript 4.0或更高版本。 |
| jsxImportSource                           | string                                                       | react               |                                                              |
| listFiles                                 | boolean                                                      | false               | 打印编译部分文件的名称。                                     |
| newLine                                   | string                                                       |                     | 指定发送文件时使用的行序列的末尾:'crlf' (Windows)或'lf' (Unix)。要求TypeScript 1.5或更高版本 |
| noLib                                     | boolean                                                      | false               | 不要包含默认库文件(lib.d.ts)。                               |
| noResolve                                 | boolean                                                      | false               | 不要在编译文件列表中添加三重斜杠引用或模块导入目标。         |
| noStrictGenericChecks                     | boolean                                                      | false               | 在函数类型中禁用严格的泛型签名检查。需要TypeScript 2.4或更高版本。 |
| preserveConstEnums                        | boolean                                                      | false               | 不要在生成的代码中删除const枚举声明                          |
| preserveSymlinks                          | boolean                                                      | false               | 不把符号链接解析为其真实路径；将符号链接文件视为真正的文件   |
| preserveWatchOutput                       | boolean                                                      |                     | 保持过时的控制台输出在watch模式，而不是清除屏幕。            |
| pretty                                    | boolean                                                      | true                | 使用颜色和上下文设置错误和信息的风格(实验)。                 |
| suppressExcessPropertyErrors              | boolean                                                      | false               | 禁止对对象字面量进行过多的属性检查。建议使用@ts-ignore注释而不是启用此设置。 |
| suppressImplicitAnyIndexErrors            | boolean                                                      | false               | 阻止`--noImplicitAny`对缺少索引签名的索引对象报错            |
| stripInternal                             | boolean                                                      |                     | 设置为true，则遇到@internal注解时，不会触发代码定义。        |
| watch                                     | boolean                                                      |                     | 监听文件变更                                                 |
| fallbackPolling                           |                                                              |                     | 指定系统用完或不支持本机文件监视器时要使用的轮询策略。要求TypeScript版本3.8或更高版本 |
| watchDirectory                            |                                                              |                     | 指定在缺乏递归文件监视功能的系统下监视目录的策略。要求TypeScript版本3.8或更高版本。 |
| watchFile                                 |                                                              |                     | 指定监视单个文件的策略。要求TypeScript版本3.8或更高版本。    |
| allowUnusedLabels                         | boolean                                                      |                     | 不要在未使用的标签上报告错误。要求TypeScript版本1.8或更高版本。 |
| noUncheckedIndexedAccess                  | boolean                                                      |                     | 向类型中未声明的字段添加“undefined”。要求TypeScript 4.1或更高版本。 |
| allowUnreachableCode                      | boolean                                                      |                     | 不要报告无法到达的代码的错误。要求TypeScript版本1.8或更高版本。 |
| plugins                                   | array                                                        |                     | 要加载的TypeScript语言服务器插件列表。需要TypeScript版本2.3或更高版本。 |
| traceResolution                           | boolean                                                      | false               | 启用名称解析过程的跟踪。需要TypeScript 2.0或更高版本。       |
| noErrorTruncation                         | boolean                                                      | false               | 不要截断错误消息。不建议使用此设置。                         |
| noImplicitUseStrict                       | boolean                                                      | false               | 当设置为true时，编译输出时不会调用'use strict'指令（也就是不生成use strict） |
| listEmittedFiles                          | boolean                                                      | false               | 启用列出所有发出的文件。需要TypeScript 2.0或更高版本。       |
| disableSizeLimit                          | boolean                                                      | false               | 禁用JavaScript项目的大小限制。要求TypeScript 2.0或更高版本。 |
| maxNodeModuleJsDepth                      | number                                                       | 0                   | 搜索node_modules和加载JavaScript文件的最大依赖深度。只适用于——allowJs。 |
| useDefineForClassFields                   | boolean                                                      | false               | 发出ECMAScript标准类字段。要求TypeScript 3.7或更高版本。     |
| resolveJsonModule                         | boolean                                                      | false               | 包括模块导入.json的扩展。要求TypeScript 2.9或更高版本。      |
| assumeChangesOnlyAffectDirectDependencies | boolean                                                      |                     | 在--incremental’和--watch中设置recompiles，假设文件内的变化只会直接影响依赖于它的文件。要求TypeScript版本3.8或更高版本 |
| extendedDiagnostics                       | boolean                                                      | false               | 显示详细的诊断信息。                                         |
| listFilesOnly                             | boolean                                                      |                     | 打印作为编译一部分的文件的名称，然后停止处理。               |
| disableSourceOfProjectReferenceRedirect   | boolean                                                      |                     | 禁用源文件，而不是引用项目的声明文件。要求TypeScript 3.7或更高版本。 |
| disableSolutionSearching                  | boolean                                                      |                     | 禁用此项目的解决方案搜索。要求TypeScript版本3.8或更高版本。  |







# [NGINX](https://nginx.org/download/)



## linux安装

```json
linux版本：CentOS7 64位

在安装nginx前首先要确认系统中安装了gcc、pcre-devel、zlib-devel、openssl-devel

1、rpm包安装的，可以用 rpm -qa 看到，如果要查找某软件包是否安装，用 rpm -qa | grep "软件或者包的名字"

2、以deb包安装的，可以用 dpkg -l 看到。如果是查找指定软件包，用 dpkg -l | grep "软件或者包的名字"

3、yum方法安装的，可以用 yum list installed 查找，如果是查找指定包，用 yum list installed | grep "软件名或者包名"

安装命令：
yum -y install gcc pcre-devel zlib-devel openssl openssl-devel

确定安装以上软件包过后：

##移动到【/usr/local/】创建文件夹
	mkdir nginx

## 下载稳定版
	wget http://nginx.org/download/nginx-1.8.1.tar.gz 

## 解压
	tar -zxvf nginx-1.8.1.tar.gz 

##进入nginx目录
	cd nginx-1.8.1
	
## 配置
	./configure --prefix=/usr/local/nginx

# make
	make //确定make成功之后再make install
	make install

# cd到刚才配置的安装目录/usr/loca/nginx/sbin
	./nginx -t //测试
	./nginx //默认配置启动
	./nginx -c /usr/local/nginx/conf/nginx.conf //带配置文件启动
	./nginx -s reload //重启
	./nginx -s stop //快速停止
	./nginx -s quit //正常停止

服务器配置：
1.查询服务器防火墙端口是否打开
	firewall-cmd --query-port=80/tcp //nginx默认监听80，如果需要监听其他端口需要自行配置

2.打开80端口(如果80端口没打开)                                                                                                                                                                                                                
	firewall-cmd --add-port=80/tcp --permanent //开启80端口， --permanent#永久生效，没有此参数重启后失效
	systemctl restart firewalld //重启防火墙

3.配置自启动脚本（见nginx自启动脚本）

	#把脚本保存为nginx文件放入/etc/init.d/nginx 然后可以通过
    /etc/init.d/nginx start 命令启动nginx
    /etc/init.d/nginx stop 命令停止nginx
    /etc/init.d/nginx restart 命令重启nginx

4.配置nginx开机自启动

	#(a+x ==> all user can execute  所有用户可执行)
	chmod a+x /etc/init.d/nginx

	#将nginx服务加入chkconfig管理列表
	chkconfig --add ningx  
    
	#加完这个之后，就可以使用service对nginx进行启动，重启等操作了。
    service nginx start
    service nginx stop
    service nginx restart

	#最后设置开机自动启动
	chkconfig nginx on
                     

#查看启动的nginx
ps -ef|grep nginx

```



nginx自启动脚本：**注意修改PATH和NAME字段, 匹配自己的安装路径**

```json
#! /bin/sh
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: starts the nginx web server

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="nginx daemon"
NAME=nginx
DAEMON=/usr/local/nginx/sbin/$NAME
CONFIGFILE=/usr/local/nginx/conf/$NAME.conf
PIDFILE=/usr/local/nginx/logs/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

set -e
[ -x "$DAEMON" ] || exit 0

do_start() {
 $DAEMON -c $CONFIGFILE || echo -n "nginx already running"
}

do_stop() {
 kill -INT `cat $PIDFILE` || echo -n "nginx not running"
}

do_reload() {
 kill -HUP `cat $PIDFILE` || echo -n "nginx can't reload"
}

case "$1" in
 start)
 echo -n "Starting $DESC: $NAME"
 do_start
 echo "."
 ;;
 stop)
 echo -n "Stopping $DESC: $NAME"
 do_stop
 echo "."
 ;;
 reload|graceful)
 echo -n "Reloading $DESC configuration..."
 do_reload
 echo "."
 ;;
 restart)
 echo -n "Restarting $DESC: $NAME"
 do_stop
 do_start
 echo "."
 ;;
 *)
 echo "Usage: $SCRIPTNAME {start|stop|reload|restart}" >&2
 exit 3
 ;;
esac

exit 0

```



## 常用配置项



| **nginx内置变量**     | **变量描述**（假定请求地址为: https://www.nginx.cn/doc/general/overview.html?test=123） |
| --------------------- | ------------------------------------------------------------ |
| $arg_name             | 请求中的的参数名，即“?”后面的arg_name=arg_value形式的arg_name ==> test |
| $args和$query_string  | 请求中的参数值 ==> 123                                       |
| $binary_remote_addr   | 客户端地址的二进制形式, 固定长度为4个字节                    |
| $body_bytes_sent      | 传输给客户端的字节数，响应头不计算在内                       |
| $bytes_sent           | 传输给客户端的字节数                                         |
| $connection           | TCP连接的序列号                                              |
| $connection_requests  | TCP连接当前的请求数量                                        |
| $content_length       | Content-Length 请求头字段                                    |
| $content_type         | Content-Type 请求头字段                                      |
| $cookie_name          | cookie名称                                                   |
| $document_root        | 当前请求的文档根目录或别名。即：root/alias的设置             |
| $document_uri 和 $uri | 请求中的当前URI，不带请求参数  ==>/doc/general/overview.html |
| $host                 | 优先级如下：HTTP请求行的主机名>”HOST”请求头字段>符合请求的服务器名 ==> www.nginx.cn |
| $hostname             | 主机名                                                       |
| $http_name            | 匹配任意请求头字段； 变量名中的后半部分“name”可以替换成任意请求头字段，如在配置文件中需要获取http请求头：“Accept-Language”，那么将“－”替换为下划线，大写字母替换为小写，形如：$http_accept_language即可。                                                      $http_cookie    $http_post     $http_referer   $http_user_agent  *#获取请求来源的IP地址* $http_x_forwarded_for |
| $https                | 如果开启了SSL安全模式，值为“on”，否则为空字符串。            |
| $is_args              | 如果请求中有参数，值为“?”，否则为空字符串。                  |
| $limit_rate           | 用于设置响应的速度限制，详见 [limit_rate](http://nginx.org/en/docs/http/ngx_http_core_module.html#limit_rate)。 |
| $msec                 | 当前的Unix时间戳                                             |
| $nginx_version        | nginx版本                                                    |
| $pid                  | 工作进程的PID                                                |
| $pipe                 | 如果请求来自管道通信，值为“p”，否则为“.”                     |
| $proxy_protocol_addr  | 获取代理访问服务器的客户端地址，如果是直接访问，该值为空字符串 |
| $realpath_root        | 当前请求的文档根目录或别名的真实路径，会将所有符号连接转换为真实路径。 |
| $remote_addr          | 客户端地址（如果有上级代理应该是上一级代理的IP）             |
| $remote_port          | 客户端端口                                                   |
| $remote_user          | 用于HTTP基础认证服务的用户名                                 |
| $request              | 代表客户端的请求地址                                         |
| $request_body         | 客户端的请求主体                                             |
| $request_body_file    | 将客户端请求主体保存在临时文件中                             |
| $request_completion   | 如果请求成功，值为”OK”，如果请求未完成或者请求不是一个范围请求的最后一部分，则为空。 |
| $request_filename     | 当前连接请求的文件路径，由root或alias指令与URI请求生成。     |
| $request_length       | 请求的长度 (包括请求的地址, http请求头和请求主体)            |
| $request_method       | HTTP请求方法，通常为“GET”或“POST”                            |
| $request_time         | 处理客户端请求使用的时间，从读取客户端的第一个字节开始计时   |
| $request_uri          | 这个变量等于包含一些客户端请求参数的原始URI，不包含主机名 ==> /doc/general/overview.html?test=123 |
| $scheme               | 请求使用的Web协议, “http” 或 “https“                         |
| $sent_http_name       | 服务器端地址，需要注意的是：为了避免访问linux系统内核，应将ip地址提前设置在配置文件中 |
| $server_name          | 服务器名例如：www.nginx.cn                                   |
| $server_port          | 服务器端口                                                   |
| $server_protocol      | 服务器的HTTP版本, 通常为 “HTTP/1.0” 或 “HTTP/1.1”            |
| $status               | HTTP响应代码                                                 |
| $time_local           | 服务器时间                                                   |



```json
########### 每个指令必须有分号结束。#################
#user administrator administrators;  #配置用户或者组，默认为nobody nobody。
#worker_processes 2;  #允许生成的进程数，默认为1
#pid /nginx/pid/nginx.pid;   #指定nginx进程运行文件存放地址
error_log log/error.log debug;  #制定日志路径，级别。这个设置可以放入全局块，http块，server块，级别以此为：debug|info|notice|warn|error|crit|alert|emerg
events {
    accept_mutex on;   #设置网路连接序列化，防止惊群现象发生，默认为on
    multi_accept on;  #设置一个进程是否同时接受多个网络连接，默认为off
    #use epoll;      #事件驱动模型，select|poll|kqueue|epoll|resig|/dev/poll|eventport
    worker_connections  1024;    #最大连接数，默认为512
}
http {
    include       mime.types;   #文件扩展名与文件类型映射表
    default_type  application/octet-stream; #默认文件类型，默认为text/plain
    #access_log off; #取消服务日志    
    log_format myFormat '$remote_addr–$remote_user [$time_local] $request $status $body_bytes_sent $http_referer $http_user_agent $http_x_forwarded_for'; #自定义格式
    access_log log/access.log myFormat;  #combined为日志格式的默认值
    sendfile on;   #允许sendfile方式传输文件，默认为off，可以在http块，server块，location块。
    sendfile_max_chunk 100k;  #每个进程每次调用传输数量不能大于设定的值，默认为0，即不设上限。
    keepalive_timeout 65;  #连接超时时间，默认为75s，可以在http，server，location块。

    upstream mysvr {   
      server 127.0.0.1:7878;
      server 192.168.10.121:3333 backup;  #热备
    }
    error_page 404 https://www.baidu.com; #错误页
    server {
        keepalive_requests 120; #单连接请求上限次数。
        listen       4545;   #监听端口
        server_name  127.0.0.1;   #监听地址       
        location  ~*^.+$ {       #请求的url过滤，正则匹配，~为区分大小写，~*为不区分大小写。
           #root path;  #根目录
           #index vv.txt;  #设置默认页
           proxy_pass  http://mysvr;  #请求转向mysvr 定义的服务器列表
           deny 127.0.0.1;  #拒绝的ip
           allow 172.18.5.54; #允许的ip           
        } 
    }
}
```





## 反向代理

```js
include       mime.types;   #文件扩展名与文件类型映射表

default_type  application/octet-stream; #默认文件类型，默认为text/plain
#access_log off; #取消服务日志    

log_format myFormat ' $remote_addr–$remote_user [$time_local] $request $status $body_bytes_sent $http_referer $http_user_agent $http_x_forwarded_for'; #自定义格式

access_log log/access.log myFormat;  #combined为日志格式的默认值

sendfile on;   #允许sendfile方式传输文件，默认为off，可以在http块，server块，location块。

sendfile_max_chunk 100k;  #每个进程每次调用传输数量不能大于设定的值，默认为0，即不设上限。

keepalive_timeout 65;  #连接超时时间，默认为75s，可以在http，server，location块。

proxy_connect_timeout 1;   #nginx服务器与被代理的服务器建立连接的超时时间，默认60秒

proxy_read_timeout 1; #nginx服务器想被代理服务器组发出read请求后，等待响应的超时间，默认为60秒。

proxy_send_timeout 1; #nginx服务器想被代理服务器组发出write请求后，等待响应的超时间，默认为60秒。

proxy_http_version 1.0 ; #Nginx服务器提供代理服务的http协议版本1.0，1.1，默认设置为1.0版本。

#proxy_method get;    #支持客户端的请求方法。post/get；

proxy_ignore_client_abort on;  #客户端断网时，nginx服务器是否终端对被代理服务器的请求。默认为off。

proxy_ignore_headers "Expires" "Set-Cookie";  #Nginx服务器不处理设置的http相应投中的头域，这里空格隔开可以设置多个。

proxy_intercept_errors on;    #如果被代理服务器返回的状态码为400或者大于400，设置的error_page配置起作用。默认为off。

proxy_headers_hash_max_size 1024; #存放http报文头的哈希表容量上限，默认为512个字符。

proxy_headers_hash_bucket_size 128; #nginx服务器申请存放http报文头的哈希表容量大小。默认为64个字符。

proxy_next_upstream timeout;  #反向代理upstream中设置的服务器组，出现故障时，被代理服务器返回的状态值。error|timeout|invalid_header|http_500|http_502|http_503|http_504|http_404|off

#proxy_ssl_session_reuse on; 默认为on，如果我们在错误日志中发现“SSL3_GET_FINSHED:digest check failed”的情况时，可以将该指令设置为off。

/*--------*/
#设定查看Nginx状态的地址
location /nginxstatus{
    stub_status on;
    access_log on;
    auth_basic "nginxstatus";
    auth_basic_user_file htpasswd;
    #htpasswd文件的内容可以用apache提供的htpasswd工具来产生。
}

location /normal {
    index  index.html index.htm index.jsp;
    proxy_pass  http://xxx.xxx.xxx.xx:xxxx/xxxx;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $host:$server_port;
}
```





## Server names

```json
服务器名称是使用server_name指令定义的，并确定哪个服务器块用于给定的请求。

server {
    listen       80;
    server_name  example.org  www.example.org; // 确切名称
    ...
}

server {
    listen       80;
    server_name  *.example.org; // 通配符
    ...
}

server {
    listen       80;
    server_name  mail.*; // 通配符
    ...
}

server {
    listen       80;
    server_name  ~^(?<user>.+)\.example\.net$; // 正则
    ...
}

#默认
server {
    listen       80;
    #_它只是无数无效域名中的一个，它们与任何真实名称都不会相交。其他无效的名称，如“ --”和“ !@#”等也可以使用。
    server_name _;
    ...
}

#缺省端口与default_server
server {
    #80 为缺省端口
    listen       80;
    #8080 default_server代表默认端口 
    listen       8080  default_server;
    server_name  example.net;
    ...
}

#URL存在跨站漏洞http host头攻击漏洞解决方案
server {
   listen 8888 default;
   server_name _;
   location / {
        return 403;
   }
}
添加一个默认 server，当 host 头被修改匹配不到 server 时会跳到该默认 server，该默认 server 直接返回 403 错误。

除了这种做法，也可以在目标 server 添加检测规则。比如下面的 if 判断配置。

复制代码
server {
  server_name  192.168.0.171;
  listen       8888;
  if ($http_Host !~*^192.168.0.171:8888$){
    return 403;
  }
  include /etc/nginx/default.d/*.conf;
  location / {
    root /www/dvwa;
    index index.php index.html index.htm;
  }
}
```



## 域名重定向

```json

server {
    listen       80;
    server_name  example.org;
    #返回301(重定向),然后重定向到[http://www.example.org$request_uri]  $request_uri为去除$host(域名)外的其他部分
    return       301 http://www.example.org$request_uri;  
}

server {
    listen       80;
    server_name  www.example.org;
    ...
}

#example.org的请求会被重定向到 www.example.org

例如：
http://example.org/index.html ==> http://www.example.org/index.html

```



## HTTPS



```json
#单个https服务
server {
    #HTTPS的默认端口是443
    listen 443 ssl;
    #填写绑定证书的域名
    server_name www.yuming.com; //假如绑定的域名www.yuming.com
    #证书文件名称 （申请的证书文件和密钥文件，放在/usr/local/nginx/conf/下面）
    ssl_certificate  1_www.yuming.com_bundle.crt; 
    #私钥文件名称
    ssl_certificate_key 2_www.yuming.com.key; 
    ssl_session_timeout 5m;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    location / {
       #网站主页路径。此路径仅供参考，具体请您按照实际目录操作。  
    	root html;
    	index index.html index.htm;
    }
	#HTTPS的默认端口是443 如果有接口反向代理需要将接口代理到443端口下
    location /user { 
        proxy_pass http://127.0.0.1:7001;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Via "nginx";
        client_max_body_size  102400m;
    } 
    location /public {
        proxy_pass  http://127.0.0.1:7001/public;
        proxy_set_header Host      $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```


```json
#http级别共享单个内存副本的多https服务
http {
    
    ssl_certificate     common.crt;
    ssl_certificate_key common.key;
    
    server {
        listen          443 ssl;
        server_name     www.example.com;
        ...
    }

    server {
        listen          443 ssl;
        server_name     www.example.org;
        ...
    }
	...
}

#注：理论可行没试过0.0
```



## GZIP

nginx_gzip压缩提升网站的传输速度（配置项作用域 http, server, location）

| 配置项            | 默认值                | 作用                                                         |
| ----------------- | --------------------- | ------------------------------------------------------------ |
| gzip              | gzip off              | 开启或者关闭gzip模块                                         |
| gzip_buffers      | gzip_buffers 4 4k     | 设置系统获取几个单位的缓存用于存储gzip的压缩结果数据流。例如 4 4k 代表以4k为单位，按照原始数据大小以4k为单位的4倍申请内存 |
| gzip_comp_level   | gzip_comp_level 1     | gzip压缩比，1 压缩比最小处理速度最快，9 压缩比最大但处理最慢（传输快但比较消耗cpu）。 |
| gzip_min_length   | gzip_min_length 0     | 设置允许压缩的页面最小字节数，页面字节数从header头中的Content-Length中进行获取。默认值是0，不管页面多大都压缩。建议设置成大于1k的字节数，小于1k可能会越压越大，即: gzip_min_length 1024 |
| gzip_http_version | gzip_http_version 1.1 | 识别http的协议版本。由于早期的一些浏览器或者http客户端，可能不支持gzip自解压，用户就会看到乱码，所以做一些判断还是有必要的。现在基本不用设置保持默认值就行 |
| gzip_proxied      | gzip_proxied off      | Nginx作为反向代理的时候启用，开启或者关闭后端服务器返回的结果，匹配的前提是后端服务器必须要返回包含"Via"的 header头。                                                                                                                                                    off-关闭所有的代理结果数据的压缩                                                                                                                                  expired-启用压缩，如果header头中包含 "Expires" 头信息                                                                                           no-cache-启用压缩，如果header头中包含 "Cache-Control:no-cache" 头信息                                                         no-store-启用压缩，如果header头中包含 "Cache-Control:no-store" 头信息                                                          private-启用压缩，如果header头中包含 "Cache-Control:private" 头信息                                                                no_last_modified-启用压缩,如果header头中不包含 "Last-Modified" 头信息                                                              no_etag-启用压缩 ,如果header头中不包含 "ETag" 头信息                                                                                           auth-启用压缩 , 如果header头中包含 "Authorization" 头信息                                                                                    any-无条件启用压缩 |
| gzip_types        | gzip_types text/html  | 匹配MIME类型进行压缩，（无论是否指定）"text/html"类型总是会被压缩的。注意：如果作为http server来使用，主配置文件中要包含文件类型配置文件 : http { 	include       conf/mime.types; 	...... }                                如果你希望压缩常规的文件类型，可以写成这个样子:                                                                                                     gzip_types       text/plain application/x-javascript text/css text/html application/xml; |
| gzip_vary         | gzip_vary off         | 是否在http header中添加Vary: Accept-Encoding，建议开启       |

```
    gzip on;
    gzip_buffers 32 4K;
    gzip_comp_level 1;
    gzip_min_length 1024;
    gzip_types application/javascript text/css text/xml;
    gzip_disable "MSIE [1-6]\."; 
    gzip_vary on;
```



## TCP优化

```js
http {
	#sendfile 配置可以提高 Nginx 静态资源托管效率。sendfile 是一个系统调用，直接在内核空间完成文件发送，不需要先 read 再 write，没有上下文切换开销。
    sendfile           on;
    #TCP_NOPUSH 是 FreeBSD 的一个 socket 选项，对应 Linux 的 TCP_CORK，Nginx 里统一用 tcp_nopush 来控制它，并且只有在启用了 sendfile 之后才生效。启用它之后，数据包会累计到一定大小之后才会发送，减小了额外开销，提高网络效率。
    tcp_nopush         on;
    #TCP_NODELAY 也是一个 socket 选项，启用后会禁用 Nagle 算法，尽快发送数据，某些情况下可以节约 200ms（Nagle 算法原理是：在发出去的数据还未被确认之前，新生成的小数据先存起来，凑满一个 MSS 或者等到收到确认后再发送）。Nginx 只会针对处于 keep-alive 状态的 TCP 连接才会启用 tcp_nodelay
    tcp_nodelay        on;
	#指定服务端为每个 TCP 连接最多可以保持多长时间。Nginx 的默认值是 75 秒，有些浏览器最多只保持 60 秒
    keepalive_timeout  60;
    ... ...
}
```





# GIT



![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015120901.png)





> ```
> Workspace：工作区
> 
> Index / Stage：暂存区
> 
> Repository：仓库区（或本地仓库）
> 
> Remote：远程仓库
> ```



### 一、新建代码库

```js
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]
```



### 二、配置

```js
Git的设置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```



### 三、增加/删除文件

```js
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```



### 四、代码提交

```js

# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```



### 五、分支

```js

# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```



### 六、标签

```js

# 列出所有tag
$ git tag

# 新建一个tag在当前commit
$ git tag [tag]

# 新建一个tag在指定commit
$ git tag [tag] [commit]

# 删除本地tag
$ git tag -d [tag]

# 删除远程tag
$ git push origin :refs/tags/[tagName]

# 查看tag信息
$ git show [tag]

# 提交指定tag
$ git push [remote] [tag]

# 提交所有tag
$ git push [remote] --tags

# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]
```



### 七、查看信息

```js

# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
```



### 八、远程同步

```js

# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all

#仓库迁移
git clone --mirror https://github.com/xxxxxxx/oldProject.git
cd oldProject.git
git remote set-url –-push origin https://github.com/xxxxxxx/newProject.git
git push –-mirror
```



### 九、撤销

```js
# 恢复暂存区的指定文件到工作区
$ git checkout [file]

# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

# 恢复暂存区的所有文件到工作区
$ git checkout .

# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

# 重置当前分支的HEAD为指定commit，保留暂存区和工作区
$ git reset --soft [commit]

# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]

# 暂时将未提交的变化移除，稍后再移入
$ git stash //存入堆栈暂存区
$ git stash list //查看所有的暂存
$ git stash pop //取出上一次暂存的内容
$ git stash clear //清除所有暂存区内容
```



### 十、其他

```js

# 生成一个可供发布的压缩包
$ git archive

# 强化版的merge，清晰的git提交历史
$ git rebase

```





## git子模块



```js
创建子仓库方法：

1.新建或者clone主仓库到本地
$ git clone http://git@127.0.0.1/main.git

2.在远程仓库创建一个新的仓库用作子仓库使用
http://git@127.0.0.1/child.git

3.进入主仓库添加子仓库 
#otherName非必填，填了会作为主仓库文件夹的名称
$ git submodule add http://git@127.0.0.1/child.git otherName

添加成功后，在父仓库根目录增加了.gitmodule文件。


#克隆一个包含子仓库的仓库目录，并不会clone下子仓库的文件，只是会克隆下.gitmodule描述文件，需要进一步克隆子仓库文件。
// 初始化本地配置文件
$ git submodule init
// 检出父仓库列出的commit
$ git submodule update

#子仓库如何更新提交代码，cd到子仓库所在文件夹，将子仓库看作一个单独的仓库操作

#删除子模块 name子模块名称
$ git submodule deinit name
$ git rm -r --cached name
```







# OTHER



## 三斜线指令

支持 6 种指令：

    1.描述文件间依赖：/// <reference path="./myFile.ts" />，引用当前目录下的myFile.ts 
    
    2.描述（类型）声明依赖：/// <reference types="node" />，引用@types/node/index.d.ts类型声明，对应--types选项
    
    3.显式引用内置（类型）库文件：/// <reference lib="es2015" />或/// <reference lib="es2017.string" />，引用内置（类型）库lib.es2015.d.ts或lib.es2017.string.d.ts，对应--lib编译选项
    
    4.禁用默认库：/// <reference no-default-lib="true"/>，编译过程中不加载默认库，对应--noLib编译选项，同时标记当前文件为默认库（以致于--skipDefaultLibCheck选项能够跳过检查该文件）
    
    5.指定当前模块的 AMD 模块名：///<amd-module name="NamedModule"/>，指定 AMD 模块名为NamedModule
    
    6.指定 AMD 模块依赖（已废弃）：/// <amd-dependency path="legacy/moduleA" name="moduleA"/>，依赖legacy/moduleA，并指定引入模块名为moduleA（name属性可选）



## 前端LocalStorage实现单点登录

```js
实现单点登录的关键在于，如何让 Session ID（或 Token）在多个域中共享。

父域 Cookie 确实是一种不错的解决方案，但是不支持跨域。那么有没有什么奇淫技巧能够让 Cookie 跨域传递呢？

很遗憾，浏览器对 Cookie 的跨域限制越来越严格。Chrome 浏览器还给 Cookie 新增了一个 SameSite 属性，此举几乎禁止了一切跨域请求的 Cookie 传递（超链接除外），并且只有当使用 HTTPs 协议时，才有可能被允许在 AJAX 跨域请求中接受服务器传来的 Cookie。

不过，在前后端分离的情况下，完全可以不使用 Cookie，我们可以选择将 Session ID （或 Token ）保存到浏览器的 LocalStorage 中，让前端在每次向后端发送请求时，主动将 LocalStorage 的数据传递给服务端。这些都是由前端来控制的，后端需要做的仅仅是在用户登录成功后，将 Session ID （或 Token ）放在响应体中传递给前端。

在这样的场景下，单点登录完全可以在前端实现。前端拿到 Session ID （或 Token ）后，除了将它写入自己的 LocalStorage 中之外，还可以通过特殊手段将它写入多个其他域下的 LocalStorage 中。


// 获取 token
var token = result.data.token;

// 动态创建一个不可见的iframe，在iframe中加载一个跨域HTML
var iframe = document.createElement("iframe");
iframe.src = "http://app1.com/localstorage.html";
document.body.append(iframe);
// 使用postMessage()方法将token传递给iframe
setTimeout(function () {
    iframe.contentWindow.postMessage(token, "http://app1.com");
}, 4000);
setTimeout(function () {
    iframe.remove();
}, 6000);

// 在这个iframe所加载的HTML中绑定一个事件监听器，当事件被触发时，把接收到的token数据写入localStorage
window.addEventListener('message', function (event) {
    localStorage.setItem('token', event.data)
}, false);

前端通过 iframe+postMessage() 方式，将同一份 Token 写入到了多个域下的 LocalStorage 中，前端每次在向后端发送请求之前，都会主动从 LocalStorage 中读取 Token 并在请求中携带，这样就实现了同一份 Token 被多个域所共享。
```



# CSS3

## calc, support, media

```
@support主要是用于检测浏览器是否支持CSS的某个属性，其实就是条件判断，如果支持某个属性，你可以写一套样式，如果不支持某个属性，你也可以提供另外一套样式作为替补。

calc() 函数用于动态计算长度值。 calc()函数支持 "+", "-", "*", "/" 运算；

@media 查询，你可以针对不同的媒体类型定义不同的样式。
```



## css水平垂直居中的写法

```
水平居中

行内元素: text-align: center
块级元素: margin: 0 auto
position:absolute +left:50%+ transform:translateX(-50%)
display:flex + justify-content: center
垂直居中

设置line-height 等于height
position：absolute +top:50%+ transform:translateY(-50%)
display:flex + align-items: center
display:table+display:table-cell + vertical-align: middle;

```



## 1rem、1em、1vh、1px

```
rem
rem是全部的长度都相对于根元素<html>元素。通常做法是给html元素设置一个字体大小，然后其他元素的长度单位就为rem。

em
子元素字体大小的em是相对于父元素字体大小
元素的width/height/padding/margin用em的话是相对于该元素的font-size
vw/vh
全称是 Viewport Width 和 Viewport Height，视窗的宽度和高度，相当于 屏幕宽度和高度的 1%，不过，处理宽度的时候%单位更合适，处理高度的 话 vh 单位更好。

px
px像素（Pixel）。相对长度单位。像素px是相对于显示器屏幕分辨率而言的。

一般电脑的分辨率有{1920*1024}等不同的分辨率

1920*1024 前者是屏幕宽度总共有1920个像素,后者则是高度为1024个像素
```



## 0.5px的直线

```
考查的是css3的transform
height: 1px;
transform: scale(0.5);
```



## 盒模型

```
盒模型的组成，由里向外content,padding,border,margin.

在IE盒子模型中，width表示content+padding+border这三个部分的宽度

在标准的盒子模型中，width指content部分的宽度

box-sizing的使用
box-sizing: content-box 是W3C盒子模型
box-sizing: border-box 是IE盒子模型
box-sizing的默认属性是content-box
```



## 三角形

```css
 .a{
            width: 0;
            height: 0;
            border-width: 100px;
            border-style: solid;
            border-color: transparent #0099CC transparent transparent;
            transform: rotate(90deg); /*顺时针旋转90°*/
 }

<div class="a"></div>
```



## 清除浮动原理

```
#清除浮动简单，但这题要引出的是BFC，BFC也是必考的基础知识点
1.::after  clear: both
2.创建父级 BFC(overflow:hidden)
3.父级设置高度
#BFC （块级格式化上下文），是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。
触发条件:
1.根元素
2.position: absolute/fixed
3.display: inline-block / table
4.float 元素
5.ovevflow !== visible
规则:
1.属于同一个 BFC 的两个相邻 Box 垂直排列
2.属于同一个 BFC 的两个相邻 Box 的 margin 会发生重叠
3.BFC 的区域不会与 float 的元素区域重叠
4.计算 BFC 的高度时，浮动子元素也参与计算
5.文字层不会被浮动层覆盖，环绕于周围
```



# html



## <label>标签的用法

```
label标签主要是方便鼠标点击使用，扩大可点击的范围，增强用户操作体验
```



## 遍历A节点的父节点下的所有子节点

```js
<script>
    var b=document.getElementById("a").parentNode.children;
    console.log(b)
</script>
```



# js



## 用js递归的方式写1到100求和？

```js
#递归我们经常用到，vue在实现双向绑定进行数据检验的时候用的也是递归，但要我们面试的时候手写一个递归，如果对递归的概念理解不透彻，可能还是会有一些问题。

function add(num1,num2){
	var num = num1+num2;
        if(num2+1>100){
	 return num;
	}else{
	  return add(num,num2+1)
        }
 }
var sum =add(1,2);      
```



## 页面渲染html的过程

```
浏览器渲染页面的一般过程：

1.浏览器解析html源码，然后创建一个 DOM树。并行请求 css/image/js在DOM树中，每一个HTML标签都有一个对应的节点，并且每一个文本也都会有一个对应的文本节点。DOM树的根节点就是 documentElement，对应的是html标签。

2.浏览器解析CSS代码，计算出最终的样式数据。构建CSSOM树。对CSS代码中非法的语法它会直接忽略掉。解析CSS的时候会按照如下顺序来定义优先级：浏览器默认设置 < 用户设置 < 外链样式 < 内联样式 < html中的style。

3.DOM Tree + CSSOM --> 渲染树（rendering tree）。渲染树和DOM树有点像，但是是有区别的。

DOM树完全和html标签一一对应，但是渲染树会忽略掉不需要渲染的元素，比如head、display:none的元素等。而且一大段文本中的每一个行在渲染树中都是独立的一个节点。渲染树中的每一个节点都存储有对应的css属性。

4.一旦渲染树创建好了，浏览器就可以根据渲染树直接把页面绘制到屏幕上。

以上四个步骤并不是一次性顺序完成的。如果DOM或者CSSOM被修改，以上过程会被重复执行。实际上，CSS和JavaScript往往会多次修改DOM或者CSSOM。
```



## CORS

```
CORS是一种新标准，支持同源通信，也支持跨域通信。fetch是实现CORS通信的
```



## 如何中断ajax请求

```
一种是设置超时时间让ajax自动断开，另一种是手动停止ajax请求，其核心是调用XML对象的abort方法，ajax.abort()


#XMLHttpRequest.abort()
如果该请求已被发出，XMLHttpRequest.abort() 方法将终止该请求。当一个请求被终止，它的  readyState 将被置为 XMLHttpRequest.UNSENT (0)，并且请求的 status 置为 0。
```



## 事件代理

```js
#事件委托是指将事件绑定到目标元素的父元素上，利用冒泡机制触发该事件
ulEl.addEventListener('click', function(e){
    var target = event.target || event.srcElement;
    if(!!target && target.nodeName.toUpperCase() === "LI"){
        console.log(target.innerHTML);
    }
}, false);
```



## target、currentTarget的区别

```
currentTarget当前所绑定事件的元素

target当前被点击的元素
```



## 宏任务和微任务

```
宏任务：当前调用栈中执行的任务称为宏任务。（主代码快，定时器等等）。
微任务： 当前（此次事件循环中）宏任务执行完，在下一个宏任务开始之前需要执行的任务为微任务。（可以理解为回调事件，promise.then，proness.nextTick等等）。
宏任务中的事件放在callback queue中，由事件触发线程维护；微任务的事件放在微任务队列中，由js引擎线程维护。
```



## 继承的几种方式及优缺点

```
1.借用构造函数继承，使用call或apply方法，将父对象的构造函数绑定在子对象上
2.原型继承，将子对象的prototype指向父对象的一个实例
3.组合继承

原型链继承的缺点:
字面量重写原型会中断关系，使用引用类型的原型，并且子类型还无法给超类型传递参数。

借用构造函数（类式继承）：
借用构造函数虽然解决了刚才两种问题，但没有原型，则复用无从谈起。

组合式继承:
组合式继承是比较常用的一种继承方法，其背后的思路是使用原型链实现对原型属性和方法的继承，而通过借用构造函数来实现对实例属性的继承。这样，既通过在原型上定义方法实现了函数复用，又保证每个实例都有它自己的属性
```



## 闭包

```
闭包的实质是因为函数嵌套而形成的作用域链

闭包的定义即：函数 A 内部有一个函数 B，函数 B 可以访问到函数 A 中的变量，那么函数 B 就是闭包
```



## export和export default的区别

```js
export default  xxx
import xxx from './'

export xxx
import {xxx} from './'
```



## 会话cookie,持久cookie

```
cookie是服务器返回的，指定了expire time（有效期）的是持久cookie,没有指定的是会话cookie
```



## 数组去重

```js
js:
var arr=['12','32','89','12','12','78','12','32'];
    // 最简单数组去重法
    function unique1(array){
        var n = []; //一个新的临时数组
        for(var i = 0; i < array.length; i++){ //遍历当前数组
            if (n.indexOf(array[i]) == -1)
                n.push(array[i]);
        }
        return n;
    }
    arr=unique1(arr);
    // 速度最快， 占空间最多（空间换时间）
    function unique2(array){
        var n = {}, r = [], type;
        for (var i = 0; i < array.length; i++) {
            type = typeof array[i];
            if (!n[array[i]]) {
                n[array[i]] = [type];
                r.push(array[i]);
            } else if (n[array[i]].indexOf(type) < 0) {
                n[array[i]].push(type);
                r.push(array[i]);
            }
        }
        return r;
    }
    //数组下标判断法
    function unique3(array){
        var n = [array[0]]; //结果数组
        for(var i = 1; i < array.length; i++) { //从第二项开始遍历
            if (array.indexOf(array[i]) == i) 
                n.push(array[i]);
        }
        return n;
    }
    
es6:
1.const arr=[...new Set(arr)];

2.function dedupe(array) {
  return Array.from(new Set(array));       //Array.from()能把set结构转换为数组
}

```



## get、post的区别

```
1.get传参方式是通过地址栏URL传递，是可以直接看到get传递的参数，post传参方式参数URL不可见，get把请求的数据在URL后通过？连接，通过&进行参数分割。psot将参数存放在HTTP的包体内

2.get传递数据是通过URL进行传递，对传递的数据长度是受到URL大小的限制，URL最大长度是2048个字符。post没有长度限制

3.get后退不会有影响，post后退会重新进行提交

4.get请求可以被缓存，post不可以被缓存

5.get请求只URL编码，post支持多种编码方式

6.get请求的记录会留在历史记录中，post请求不会留在历史记录

7.get只支持ASCII字符，post没有字符类型限制
```



## http的响应码及含义

```
1xx(临时响应)

100: 请求者应当继续提出请求。

101(切换协议) 请求者已要求服务器切换协议，服务器已确认并准备进行切换。

2xx(成功)

200：正确的请求返回正确的结果

201：表示资源被正确的创建。比如说，我们 POST 用户名、密码正确创建了一个用户就可以返回 201。

202：请求是正确的，但是结果正在处理中，这时候客户端可以通过轮询等机制继续请求。

3xx(已重定向)

300：请求成功，但结果有多种选择。

301：请求成功，但是资源被永久转移。

303：使用 GET 来访问新的地址来获取资源。

304：请求的资源并没有被修改过

4xx(请求错误)

400：请求出现错误，比如请求头不对等。

401：没有提供认证信息。请求的时候没有带上 Token 等。

402：为以后需要所保留的状态码。

403：请求的资源不允许访问。就是说没有权限。

404：请求的内容不存在。

5xx(服务器错误)

500：服务器错误。

501：请求还没有被实现。
```

