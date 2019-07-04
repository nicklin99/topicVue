
### 兼容ie9

vue-cli2,打开 build/webpack.base.conf.js,

将`entry: {
    app: './src/main.js'
  }`

修改为 `entry: {  app: ["babel-polyfill","./src/main"]}`

如果有引用iview

```js

{
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), resolve('node_modules/webpack-dev-server/client')]
      },
```

修改为

```js

{
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('node_modules/iview'), resolve('test'), resolve('node_modules/webpack-dev-server/client')]
      },
```