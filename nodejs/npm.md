# NPM

## 语义化版本(Semver)

语义化版本管理是包管理的一个重要约定和基础

**版本格式**

* 正式发布(`release`)的包版本：总共包含三个数字`X.Y.Z`(`major.minor.patch`)
* 预发布版(`pre-release`)的包版本：`X.Y.Z-[a-zA-Z0-9.]`，用于支持包的不同[生命周期](https://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E9%80%B1%E6%9C%9F)
  * `pre-aplha`：功能不完整的版本
  * `alpha`：功能还未完善，还需要测试
  * `beta`：功能完善，对外公开的测试版本，由第三方参与测试
  * `Release Candidate(RC)`：功能完善，测试通过。`作为发布的候选版本，如没有问题可发布为正式版本

**版本规范**

* 版本号必须是不能以0开头非负整数。如`1.01.1`、`1.a.1`这些都是不合法的
* 任何修改都必须作为新版本发布，而不能改在已发布的版本里。升级这些数字(版本号)时，需要遵循以下的约定
  * `major`(主版本)：发生了不兼容的变更，升级后minor和patch重置为0
  * `minor`(次版本)：新增了向下兼容的功能，升级后patch重置为0
  * `patch`(修订版本)：进行了向下兼容的bug修复
* `major`为`0`时，表示初始开发版本，不是稳定的版本。在这个`major`为`0`的版本内，改动有可能是不向下兼容的

**版本范围**

我们在package.json中会声明对包的版本依赖，它可以是一个特定版本，也可以是一个范围。同时在进行包更新(`npm update`)时，根据这些版本规则来判断包可以更新到哪个版本

| 符号           | 说明                                                                                               |
| -------------- | -------------------------------------------------------------------------------------------------- |
| `^`            | 它只会进行不改变最左边非零数的更新，例如`^0.13.0`会更新到`0.13.2`,但是不会更新到`0.14.0`或以上版本 |
| `~`            | 更新patch                                                                                          |
| `-`            | 一个版本范围，如`1.1.1-1.3.1 `                                                                     |
| `>、>=、<=、<` | 大于、大于等于、小于等于、小于指定的版本                                                           |
| `=`            | 指定一个特定版本，`=0.13.0`等效于`0.13.0`                                                          |
| `\|\|`         | 多个版本集合，如`< 2.1 || > 2.6`                                                                   |

除了以上还有几个特殊规则
* `latest`：最后一个可用版本
* `没有指定任何符号`：接收一个特定的版本，如`0.13.0`

## package.json文件 
package.json里面包含了项目相关配置信息，这些配置信息可用于不同使用场景。例如存储了依赖的包和版本、程序入口等

先看一个例子：

```json
{
  "name": "test-project",
  "version": "1.0.0",
  "description": "A test project",
  "main": "src/main.js",
  "private": true,
  "scripts": {
    "start": "npm run dev",
  },
  "keywords": [
    "components"
  ],
  "homepage":"https://github.com/xxxx.index",
  "dependencies": {
    "vue": "^2.5.2"
  },
  "files": [
    "lib",
    "dist"
  ],
  "devDependencies": {
    "autoprefixer": "^7.1.2"
  },
  "engines": {
    "node": ">= 6.0.0",
    "npm": ">= 3.0.0"
  },
  "browserslist": ["> 1%", "last 2 versions", "not ie <= 8"]
}
```
#### 属性说明

* `name`：包名，npmjs上查看到的名称
* `version`：版本号
* `description`：包描述信息
* `script`：一系列可通过`node run`或者`node`来运行的脚步
* `private:true`：防止被发布到npm
* `main`：包文件入口，第三方import时，默认就是指向这个文件
* `files`：需要发布到npmjs上的文件
* `peerDependencies`：用户手动安装依赖，不依赖在自己包内。
* `dependencies`：release时需要打包进代码的依赖
* `devdependencies`：开发时用到的包，在release中不需要用到，比如webpack、babel、单元测试、项目构建的依赖包
* `engines`：当前包运行的Node.js版本范围
* `broswerslist`：当前包支持的浏览器范围，数据来源caniuse
* `module`://TODO

npmjs和这些属性的对应关系，以React为例子
//TODO

#### node script 说明


## package_lock.json

## npm包管理



## 参考资料

* [semver](https://semver.org/)
* [软件生命周期](https://zh.wikipedia.org/wiki/%E8%BB%9F%E4%BB%B6%E7%89%88%E6%9C%AC%E9%80%B1%E6%9C%9F)
