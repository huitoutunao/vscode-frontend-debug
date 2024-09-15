# vue2 调试模式

vue.config.js 配置 source-map
```js
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  configureWebpack(config) {
    config.devtool = 'source-map'
  },
})
```

launch.json 配置 sourceMapPathOverrides
```json
{
    // 使用 IntelliSense 了解相关属性。
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Vue2 Chrome 调试模式",
            "port": 9222,
            "request": "attach",
            "type": "chrome",
            "webRoot": "${workspaceFolder}",
            "sourceMapPathOverrides": {
                "webpack://test-vue2-debug/src/*": "${workspaceFolder}/src/*"
            }
        }
    ]
}
```