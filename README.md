# odoo-develop
基于vscode.devcontainers的odoo开发环境

# 说明
* 目前仅支持Odoo 16.0
* 基础环境：
    * docker
    * vscode:
        * devcontainers 扩展

# 用法
* 克隆本项目
    ```
    // in shell
    git clone https://github.com/indiefun/odoo-develop.git
    ```
* 使用vscode打开本工程
    ```
    // in shell
    code odoo-develop
    ```
* 使用devcontainer重新打开
    ```
    // ctrl+shift+p ->
    Dev Containers: Reopen in Container
    ```
* 运行调试
    ```
    // ctrl+shift+p ->
    Debug: Start Debugging
    ```

# 问题
* 启动参数在.vscode/launch.json里面配置