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

- Build dist `npm run build:examples` in `./w3modal`
- Copy `.env.example` and rename to `.env`,  get project id from [walletconnect clound](https://cloud.walletconnect.com/)
- Run vue-html-ethers5 `cd examples/vue-html-ethers5 && npm run dev:example` 

### Remote Deployment

- Run on server with vscode remotessh

### Todo List

- [ ] This is a todo item.
- [x] This is done work item.


### License