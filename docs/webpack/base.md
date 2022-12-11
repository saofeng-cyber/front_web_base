# 配置详情

## Webpack

[webpack5参考文档](http://xxpromise.gitee.io/webpack5-docs/)

## Eslint

可组装的 JavaScript 和 JSX 检查工具。

这句话意思就是：它是用来检测 js 和 jsx 语法的工具，可以配置各项功能

我们使用 Eslint，关键是写 Eslint 配置文件，里面写上各种 rules 规则，将来运行 Eslint 时就会以写的规则对代码进行检查

### 配置文件(Eslint)

> 配置文件由很多种写法：

- `.eslintrc.*` :新建文件，位于项目根目录
  - `.eslintrc`
  - `.eslintrc.js`
  - `.eslintrc.json`

!> 区别在于配置格式不一样

- `package.json` 中 `eslintConfig`：不需要创建文件，在原有文件基础上写

### 具体配置(Eslint)

我们以 `.eslintrc.js` 配置文件为例：

```js
module.exports = {
  // 解析选项
  parserOptions: {},
  // 具体检查规则
  rules: {},
  // 继承其他规则
  extends: [],
  // ...
  // 其他规则详见：https://eslint.bootcss.com/docs/user-guide/configuring
};
```

1 parserOptions 解析选项

```js
parserOptions: {
  ecmaVersion: 6, // ES 语法版本
  sourceType: "module", // ES 模块化
  ecmaFeatures: { // ES 其他特性
    jsx: true // 如果是 React 项目，就需要开启 jsx 语法
  }
}
```

2 rules 具体规则

- `"off"` 或 `0` - 关闭规则
- `"warn"` 或 `1` - 开启规则，使用警告级别的错误：`warn` (不会导致程序退出)
- `"error"` 或 `2` - 开启规则，使用错误级别的错误：`error` (当被触发的时候，程序会退出)

```js
rules: {
  semi: "error", // 禁止使用分号
  'array-callback-return': 'warn', // 强制数组方法的回调函数中有 return 语句，否则警告
  'default-case': [
    'warn', // 要求 switch 语句中有 default 分支，否则警告
    { commentPattern: '^no default$' } // 允许在最后注释 no default, 就不会有警告了
  ],
  eqeqeq: [
    'warn', // 强制使用 === 和 !==，否则警告
    'smart' // https://eslint.bootcss.com/docs/rules/eqeqeq#smart 除了少数情况下不会有警告
  ],
}
```

更多规则详见：[规则文档](https://eslint.bootcss.com/docs/rules/) :smile:

3 extends 继承

开发中一点点写 rules 规则太费劲了，所以有更好的办法，继承现有的规则。

现有以下较为有名的规则：

- [Eslint 官方的规则](https://eslint.bootcss.com/docs/rules/)：`eslint:recommended`
- [Vue Cli 官方的规则](https://github.com/vuejs/vue-cli/tree/dev/packages/@vue/cli-plugin-eslint)：`plugin:vue/essential`
- [React Cli 官方的规则](https://github.com/facebook/create-react-app/tree/main/packages/eslint-config-react-app)：`react-app`

```js
// 例如在React项目中，我们可以这样写配置
module.exports = {
  extends: ["react-app"],
  rules: {
    // 我们的规则会覆盖掉react-app的规则
    // 所以想要修改规则直接改就是了
    eqeqeq: ["warn", "smart"],
  },
};
```

4 VSCode Eslint 插件

打开 VSCode，下载 Eslint 插件，即可不用编译就能看到错误，可以提前解决

但是此时就会对项目所有文件默认进行 Eslint 检查了，我们 dist 目录下的打包后文件就会报错。但是我们只需要检查 src 下面的文件，不需要检查 dist 下面的文件。

所以可以使用 Eslint 忽略文件解决。在项目根目录新建下面文件:

- `.eslintignore`

```eslintignore
# 忽略dist目录下所有文件
dist
```

## Babel

JavaScript 编译器。

主要用于将 ES6 语法编写的代码转换为向后兼容的 JavaScript 语法，以便能够运行在当前和旧版本的浏览器或其他环境中

### 配置文件(Babel)

配置文件由很多种写法：

- `babel.config.*`：新建文件，位于项目根目录
  - `babel.config.js`
  - `babel.config.json`
- `.babelrc.*`：新建文件，位于项目根目录
  - `.babelrc`
  - `.babelrc.js`
  - `.babelrc.json`
- `package.json` 中 babel：不需要创建文件，在原有文件基础上写
Babel 会查找和自动读取它们，所以以上配置文件只需要存在一个即可

### 具体配置(Babel)

我们以 `babel.config.js` 配置文件为例：

```js
module.exports = {
  // 预设
  presets: [],
};
```

1 presets 预设

简单理解：就是一组 Babel 插件, 扩展 Babel 功能

- `@babel/preset-env`: 一个智能预设，允许您使用最新的 JavaScript。
- `@babel/preset-react`：一个用来编译 React jsx 语法的预设
- `@babel/preset-typescript`：一个用来编译 `TypeScript` 语法的预设

2 babel配置例子

需要安装babel相关插件

```npm
npm install @babel/core @babel/preset-env @babel/plugin-transform-runtime babel-loader @babel/runtime or @babel/runtime-corejs3 -D
```

```js
{
  // babel.config.js
  module.exports = {
    presets: [
        [
            '@babel/preset-env',{
                useBuiltIns: "usage",
                corejs: 3
            }
        ]
    ],
    plugins: ['@babel/plugin-transform-runtime']
}
}
```

3 搭配browserslistrc

创建文件`.browserslistrc`

```browserslistrc
> 0.5%
last 2 version
not dead
```
