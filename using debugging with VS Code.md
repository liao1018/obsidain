#node 

---

### different error types
1.  syntax error
    -   read your file.
2.  runtime error
    -   look into error messages
3.  logic error

### debugging logic errors
-   run→start debugging
-   會有一個控制欄
-   設置停下點(break point)
-   之後就可以去觀察該時候的個變數
-   可以點擊下一步去看下一步各個變數的狀態

> 記得要在你開啟你要執行的檔案去run debugging.

> debug console 裡面也可以run code，不會影響到上面runtime code.

> 旁邊的variables 可以double click 去更改，會影響到runtime code.

### 其他設定：自動restart debugging
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-node",
            "request": "launch",
            "name": "Launch Program",
            "skipFiles": [
                "<node_internals>/**"
            ],
            "program": "${workspaceFolder}/modules/4./45./app.js",
            "restart": true,
            "runtimeExecutable": "nodemon",
            "console": "integratedTerminal"
        }
    ]
}
```
- program 代表 run debugging 的時候要run 的program.