# lerna-test


#### blog
lerna的简单尝试

1. 用途
    * 针对那些托管在npm上比较大的包进行管理、发布
    * 一般这些包，有许多模块，每个模块之间有依赖关系，每次发布都可能存在需要更新`package.json`中`version`字段的情况
2. 简单案例
    1. 创建空目录并进入，如`mkdir lerna-test && cd lerna-test`
    2. 托管到github上，`git init`等一系列，略
    3. 初始化`lerna init`，此时目录结构（主要部分）如下
        ```
        ├── lerna.json
        ├── package.json
        └── /packages
        ```
    4. 进入packages目录，创建新的空目录`module-1`并进入
    5. 初始化package`npm init -y`，此时目录结构（主要部分）如下
        ```
        ├── lerna.json
        ├── package.json
        └── /packages
        └── /module-1
            └── package.json
        ```
    6. 手动在`/module-1/package.json`依赖，比如lodash
        ```
        "devDependencies": {
            "lodash": "^4.17.10"
        }
        ```
    7. 回到根目录`lerna-test`下，运行`lerna bootstrap`，发现已经安装上了lodash依赖。
    8. 此时将项目跟新到github上
    9. 发布npm包 `lerna publish`，按照提示配置，进行发布。
3. lerna模式
    1. fixed模式
    2. independent模式