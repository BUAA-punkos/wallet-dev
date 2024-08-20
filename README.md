# wallet-dev
An dev resolution for wc based punkos wallet

> 修改子模块代码后先提交子仓库代码，再提交总仓库代码

### Architecture

```mermaid
graph LR
    [UserClient] --> {ConnectionRelay} --> {DAppEndpoint}
```

### Dependencies

#### 1. Bsic dependcies

| Name |Version | describtion | 
|----| ------- |  ----------- |
| Node  |  18.20 | | javascript env|
| Npm |1.22.22 | package manager |
| Vscode | latest | base ide |
 
#### 1. Wallet client

| Name |Version | describtion | 
|----| ------- |  ----------- |
| Android studio | latest| build apk package|
| Xcode | latest| build ios package|
| Capacitor | 6.0| Web to App framework |
| React | 17.0 | web ui framework |
| NextUI | 1.0.8 | web ui framework |
| Wallet sdks | -- | supported multi wallet |
 
 #### 2. Connection relay

| Name |Version | describtion | 
|----| ------- |  ----------- |
| Redis | 6.0 |  cache service|
| WC Core | 2.0| base suppport by walletconnect |

 #### 3.  DApp enpoint modal

| Name |Version | describtion | 
|----| ------- |  ----------- |
| Vite | 5.0 |  web build tool |
| Vue | 3.2.4|  ui framework |
| Electron | 26.0.4|  desktop framework |

> If needed, integrate walletconnect core here.

### Local Development
#### 1. Install dependcies
```shell
cd client && npm install 
cd relay && npm install 
cd w3modal && npm install 
```
#### 2. Run relay server

- Install redis service in local or use remote redis service `redis://redis.buaadcl.tech:3010/1` (the last number must greater than 0, because 0 is using for production relay).
- Copy `.env.example` and rename to `.env.local`,  get relay url from above.
- Run server by cmd `npm run start` in `./relay`, and log like this:
![relay-log](./relay/docs/image.png)

### 3. Run client web

- Copy `.env.example` and rename to `.env.local`,  get project id from [walletconnect clound](https://cloud.walletconnect.com/), other id etc.
- excute cmd `npm run dev` in `./client` . 
- open `http://localhost:3002`

### 4. Run Dapp web3modal

- Build local module dist `npm rurn build` in  `./w3modal`
- Build example dist `npm run build:examples` in `./w3modal` 
- Copy `.env.example` and rename to `.env`,  get project id from [walletconnect clound](https://cloud.walletconnect.com/)
- Run vue-html-ethers5 `cd examples/vue-html-ethers5 && npm run dev:example` 

### Remote Deployment

- Run on server with vscode remotessh

### Todo List

- [ ] This is a todo item.
- [x] This is done work item.
- [ ] kadena私钥真实生成
- [ ] btc签名调试
- [ ] 私钥导入支持
- [ ] 自选链地址生成
- [ ] ui显示优化，设置界面优化


### License


### 关于git多模块仓库

在GitHub中，如果你想在一个仓库中通过文件夹链接到其他多个仓库，可以使用Git的子模块（submodules）。这允许你将一个Git仓库作为另一个Git仓库的子目录。

这里是如何设置和使用Git子模块的步骤：

### 1. 添加子模块
在你的主仓库中，可以通过以下命令添加子模块：
```bash
git submodule add <仓库URL> <路径/文件夹名>
```
例如，如果你想将一个名为 `Library` 的仓库添加为子模块，存放在 `external/Lib` 文件夹中，你可以这样做：
```bash
git submodule add https://github.com/exampleuser/Library.git external/Lib
```

### 2. 初始化子模块
添加子模块后，你需要初始化并更新子模块：
```bash
git submodule init
git submodule update
```

### 3. 克隆带有子模块的仓库
如果你克隆了一个包含子模块的仓库，你需要在克隆后拉取子模块内容：
```bash
git clone <仓库URL>
cd <仓库名称>
git submodule update --init --recursive
```

### 4. 更新子模块
如果子模块的源仓库有更新，你需要在主仓库中更新子模块：
```bash
git submodule update --remote
```

### 5. 提交和推送更改
当你对子模块或主仓库进行更改后，需要先在子模块中提交和推送更改，然后再在主仓库中提交和推送：
```bash
# 在子模块中
cd external/Lib
git add .
git commit -m "Update submodule"
git push

# 回到主仓库
cd ../..
git add external/Lib
git commit -m "Update submodule reference"
git push
```

这样，你就可以在GitHub仓库中通过文件夹的形式链接到其他多个仓库，每个链接都指向各自独立的Git仓库。这种方法非常适合管理依赖库或组织大型项目中的各个组件。