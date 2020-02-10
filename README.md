### Nodejs单元测试小结

- 对Node.js单元测试的学习
- 也可用作Node项目工程模版
- 原文参考自[Nodejs单元测试小结](https://segmentfault.com/a/1190000002921481)

### 运行环境

- node >= 0.12.2
- mongodb >= 3.0.3

### 技术体系

- express
- mongodb

### quick start

```
$ git clone https://github.com/shiyunlai/node-test-demo.git
$ npm i
$ mongod --dbpath /usr/local/Cellar/mongodb/3.6.3/data/db/   # 启动mongodb
$ node app.js
```

### 执行单元测试

```
$ npm i mocha -g
```

执行mocha测试(注意：不要同时启动app.js)

```
$ mocha
```
或者
```
$ npm run test
```

输出

```
Mac:node-test-demo megapro$ mocha


(node:17374) DeprecationWarning: `open()` is deprecated in mongoose >= 4.11.0, use `openUri()` instead, or set the `useMongoClient` option if using `connect()` or `createConnection()`. See http://mongoosejs.com/docs/4.x/docs/connections.html#use-mongo-client
listening on port  3000
(node:17374) DeprecationWarning: Mongoose: mpromise (mongoose's default promise library) is deprecated, plug in your own promise library instead: http://mongoosejs.com/docs/promises.html
  site/test.js
    sign up
      ✓ should not sign up an user when loginname is empty (96ms)
      ✓ should not sign up an user when password is empty
      ✓ should sign up an user
      ✓ should not sign up an user when it is exist
    sign in
      ✓ should not sign in successful when loginname is empty
      ✓ should not sign in successful when loginname is not exist
      ✓ should not sign in successful when password is wrong
      ✓ should sign in successful

  site/test.js
    topic create
      ✓ should not create topic when title is empty
      ✓ should create a topic successful

  10 passing (190ms)
```


### 测试覆盖率

```
$ npm i istanbul -g 
```
然后执行
```
$ npm run cover
```

输出
```

  10 passing (84ms)

=============================================================================
Writing coverage object [/Users/megapro/Develop/nodejs/node-test-demo/coverage/coverage.json]
Writing coverage reports at [/Users/megapro/Develop/nodejs/node-test-demo/coverage]
=============================================================================

=============================== Coverage summary ===============================
Statements   : 96.97% ( 128/132 )
Branches     : 83.33% ( 20/24 )
Functions    : 100% ( 19/19 )
Lines        : 96.9% ( 125/129 )
================================================================================
```

## 工程目录介绍
```
.
├── controllers                    // 控制层
|   ├── site.js                    // 注册登录控制
|   └── topic.js                   // 话题控制
├── models                         // 数据模型
|   ├── index.js                   // 出口文件
|   ├── topic.js                   // 话题模型
|   └── user.js                    // 用户模型
├── proxy                          // 数据控制层
|   ├── topic.js                   // 话题数据控制
|   └── user.js                    // 用户数据控制
├── tests                          // 单元测试
|   ├── support/support.js         // 模拟数据
|   ├── user.test.js               // 注册登录控制测试
|   └── topic.test.js              // 话题控制测试
├── app.js                         // 项目主文件
├── consig.js                      // 项目配置文件
├── package.json                   // 包文件
└── router.js                      // 路由配置
```


### 如何开发单元测试

- 安装mocha, npm i mocha
- 在工程目录下新建test目录, mkdir test/
- 新建单元测试文件, touch xxx.test.js, 必须 test.js 结尾
- 
