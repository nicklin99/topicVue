
# vue cli3

## 环境变量

> 引用文档

    .env                # 在所有的环境中被载入
    .env.local          # 在所有的环境中被载入，但会被 git 忽略
    .env.[mode]         # 只在指定的模式中被载入
    .env.[mode].local   # 只在指定的模式中被载入，但会被 git 忽略

### 示范

.env

```
VUE_APP_APPID=appid0
```

.env.test

测试环境appid

```
NODE_ENV=production
VUE_APP_APPID=appid1
```

.env.production

生产环境appid

```
VUE_APP_APPID=appid1
```

package.json script 字段增加`"build:test": "vue-cli-service build --mode test",`,执行`npm run build:test`,生产`npm run build`

```

  "scripts": {
    "build": "vue-cli-service build",
    "build:test": "vue-cli-service build --mode test",
    "lint": "vue-cli-service lint",
    "start": "vue-cli-service serve"
  },
```

读取配置变量,代码里写`process.env.VUE_APP_APPID`不同的环境包，打包时候代码里的 process.env.VUE_APP_APPID 会被配置的值所取代

### 注意

1. 只有以 VUE_APP_ 开头的变量会被 webpack.DefinePlugin 静态嵌入到客户端侧的包中