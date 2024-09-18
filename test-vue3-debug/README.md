# vue3 调试模式

launch.json
```json
{
    // 使用 IntelliSense 了解相关属性。
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Vue3 Chrome 调试模式",
            "port": 9222,
            "request": "attach",
            "type": "chrome",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

## 调试源码

在 vue3 源码目录运行 `pnpm run build -s` 命令可以打包出带 map 的文件。

rollup.config.js 配置如下：
```js
output.sourcemapPathTransform = (relativeSourcePath, sourcemapPath) => {
    const newSourcemapPath = path.join(path.dirname(sourcemapPath), relativeSourcePath)
    return newSourcemapPath
}
```

把打包出来的 `runtime-core/dist` 文件放到 `node_modules/@vue/runtime-core` 目录下，然后配置下 `vite.config.js` 的 optimizeDeps，接着删除 `.vite` 缓存文件，重新编译。
```js
export default defineConfig({
  // ...省略代码
  optimizeDeps: {
    exclude: ['vue']
  },
})
```

**在当前项目运行断点调试。**