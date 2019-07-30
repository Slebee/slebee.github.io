> HoperBank 项目为 P2P 对外 wap 端，提供用户注册到投资理财、充值提现等一系列操作功能，与 IOS 与安卓 app 端的 UI 与功能保持一致，wap 端与 app 端 UI 有细微的差别，不过功能保持一致。

#重构原因
实际上我们项目是已经有一个线上的了，不过这个项目没有使用 SPA，单纯的使用 Jquery、Ajax 构成，然而随着功能增加，页面逻辑也开始越写越多，到后面维护起来已经是相当的蛋疼...由于我们这个 wap 主要运行在微信端，且使用的数据、UI 与 ios 及安卓端一模一样，我决定使用 SPA 来重构这个项目。

#使用 React
使用 React 是我早已打算好的，除了个人喜欢 React 外，更加是为了用 React Native 开发手机 App 端做铺垫，wap 端 app 的代码和手机 App 端的代码共用率相当高，在编写 web 端的时候就考虑到的话可以在开发 RN 应用的时候节省大量时间。
wap 与手机端的逻辑及数据层面都是一样的，区别主要在 View 以及样式。

#数据
我们后端是 java，这里我这里是直接使用的 app 的接口,由于接口已经是现成的，可以直接通过连接测试环境接口开发。

#开发技术栈
React 是主要应用框架，redux 为数据层，使用 react-router 作为路由，使用 webpack 编译打包。
简要概括为:**react + redux + react-router + webpack + es6-7**
除了上述这些还包含了一些小工具

实际上这次的重构计划也是我个人的决定而已，重构跟着现有项目更新同步进行，一有空就继续重构，前前后后一个多月才终于赶上现有项目，最终替换掉了原版本。

线上项目部分截图：

![截图一](http://upload-images.jianshu.io/upload_images/5677873-a70a46c031c0ff8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![截图二](http://upload-images.jianshu.io/upload_images/5677873-0b0056d0246785b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
