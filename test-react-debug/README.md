# vscode 调试

**先启动项目服务，再启动 Chrome 调试模式。**

win10 命令启动调试模式 Chrome，`--remote-debugging-port=9222` 设置应用程序端口号，`--user-data-dir` 用户记录数据目录，可以在 D 盘新建目录 chrome-debug。
```shell
start "" "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222 --user-data-dir="D:\chrome-debug"
```

launch.json 配置文件如下：
```json
{
    "configurations": [
        {
            "name": "React Chrome 调试模式",
            "port": 9222,
            "request": "attach",
            "type": "chrome",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```