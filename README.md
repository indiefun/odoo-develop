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
    git clone https://github.com/indiefun/odoo-develop.git
    ```
* 克隆Odoo项目
    ```
    git clone -b 16.0 --single-branch --depth=1 https://github.com/odoo/odoo.git
    ```
* 使用vscode打开本工程
    ```
    code odoo-develop
    ```
* 打开devcontainers环境
* 直接运行launch启动odoo

# 问题
* 启动参数在.vscode/launch.json里面配置