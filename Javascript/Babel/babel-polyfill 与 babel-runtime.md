## babel-polyfill
babel 虽然可以转换各种 ES2015 语法及 jsx，但浏览器未提供原生支持的许多功能还是需要 polyfill，比如 Promise。

我们只要在代码中引入 babel-polyfill 就可以模拟出一个 ES2015 的环境，用法如下：

安装 babel-polyfill

npm install babel-polyfill --save
在入口文件中引用：

import babel-polyfill

## babel-runtime
与 babel-polyfill 一样，babel-runtime 的作用也是模拟 ES2015 环境。只不过，babel-polyfill 是针对全局环境的，引入它，我们的浏览器就好像具备了规范里定义的完整的特性 – 虽然原生并未实现。

babel-runtime 更像是分散的 polyfill 模块，我们可以在自己的模块里单独引入，比如 require(‘babel-runtime/core-js/promise’) ，它们不会在全局环境添加未实现的方法，只是，这样手动引用每个 polyfill 会非常低效。我们借助 Runtime transform 插件来自动化处理这一切。

至于要用 babel-polyfill 还是 babel-runtime，则需要根据具体需求。举个例子，如果一个库里引用了 babel-polyfill，别人的库也引用了 babel-polyfill，我们很可能会跑两个 babel-polyfill 实例，这里，使用 babel-runtime 会更合适。

webpack 中定义 babel-loader#

在 webpack.config.js 里这样定义：

module: {
  loaders:  [
    {
      test: /\.js/,
      loader: 'babel?presets[]=es2015,presets[]=react,plugins[]=transform-runtime'
    }
  ]
}

## babel-register
babel-register 是放在 node 里使用的。它的作用是替代 node 的 require 命令，与 node 自身的 require 不同，它可以加载 es2015、jsx 等类型文件。

用法如下：

require('babel-register')({presets: ['es2015', 'react']})
require('./app')
这样我们在 app 文件中就可以使用 es2015 与 jsx 语法了。

#这个没有写完，先记录上，有时间排版