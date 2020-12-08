# 公司移动端项目打包自动去除 vconsole 代码

## Usage

```npm
npm i @babel/plugin-remove-vconsole --save-dev (or yarn)
```

* in babel config file (eg .babelrc)

```js
{
  plugins: ['remove-vconsole']
}
```

* webpack production config file

```js

{
  test: /\.(js|jsx|mjs)$/,
  include: paths.appSrc,
  loader: require.resolve('babel-loader'),
  options: {
    customize: require.resolve(
      'babel-preset-react-app/webpack-overrides'
    ),

    plugins: ['remove-vconsole', ...],

    // This is a feature of `babel-loader` for webpack (not Babel itself).
    // It enables caching results in ./node_modules/.cache/babel-loader/
    // directory for faster rebuilds.
    cacheDirectory: true,
    cacheCompression: true,
    compact: true
  }
}
```

打包之后，自动去除 Vconsole 的 引入

```js
import VConsole from 'vconsole';
new VConsole();
```
