先从目录结构说起，事实上良好的目录结构对项目的拓展性有着很大的帮助。

![目录结构](http://upload-images.jianshu.io/upload_images/5677873-511a972ac349fa66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个是我这个 wap App 的目录结构，中间有过一次较大的变化，都是由于前期没有做好规划造成的，这里也只是一个参考。

#actions 文件夹
该文件夹包含了所有触发数据变更的 action 文件；
#components 文件夹
该文件夹包含了一些公用的 React 组件，如按钮、Tab；
#containers 文件夹
这里我放了 js 入口以及根据环境选择加载文件的 Root.js，这里还放置了一些开发工具组件如 DevTool.js。当然，一些全局共用的页面我也放在这里，比如 404；
#less 文件夹
没什么好说，放的全是 less 文件。
#reducer 文件夹
所有的 reducers 处理函数按大模块分成几个文件放这了;

#routes 文件夹
里面放的是所有页面文件夹，涵盖了页面组件、页面路由信息，大致如下结构

![routes目录](http://upload-images.jianshu.io/upload_images/5677873-49523ee645cbd86d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

每个模块文件夹都有 index.js，里面包含了该模块的路由配置。
这里我采取拆分这么多文件模块而不是统一配置页面路由的原因是为了后面的**按需加载**。

这个目录就是比较关键的部分，该目录下所有的文件夹 index 文件都包含了该目录的路由信息；
使用这种目录结构我们可以无限往下延伸，便于拓展，同时也方便共同开发时的合并

#static 文件夹

![static](http://upload-images.jianshu.io/upload_images/5677873-8e2492aee759e359.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个文件夹我放了一些静态文件如图片、公用 lib，以及执行打包生成后的文件都会在这里；
基本就是打包完之后我就把这个 static 文件夹上传即可。
#store 文件夹
就是 store 嘛，我这里也是准备了 configureStore.dev.js 和 configureStore.prod.js 两个文件来针对开发环境和生产环境。

<pre>
if (process.env.NODE_ENV === 'prod') {
  module.exports = require('./configureStore.prod')
} else {
  module.exports = require('./configureStore.dev')
}
</pre>

**process.env.NODE_ENV** 环境变量我是在 npm script 执行的时候设置的，
比如:

<pre>"bundle-test": "set NODE_ENV=prod&&webpack --config webpack.bundle.test.config.js -p --progress --colors"</pre>

另外提一下，当时我在写 NODE_ENV=prod&&webpack 这里的时候给 prod&&webpack 中间加了空格，结果怎么都设置不了 ENV，折腾了半天才发现。。。

最后就是 index.html 了，这个也就是文件入口部分了。

#结尾
大体上和大部分的 react 应用目录结构区别并不大，主要是 routes 文件夹这里，早期的时候我用了单个 routes.js 把整个应用的路由写在里面，然而最后因为写按需加载的时候发现这样做比较好区分，就改成了现在这个样子，拆了之后也不会像单个文件那么多看的眼花嘛。。。
