# Hixtrip FE Online

## 准备

- fork 此仓库
- 根据如下要求实现相关代码
- 完成要求
  - 提交`pull request`
  - 提供页面截图

## 需求

1. 目前已经有`src/api/user.ts` 以及 `src/api/org.ts` 两个 API
2. 需要实现如下效果界面：

![](./docs/preview.jpg)

> 功能要求：
- 不限 ```React``` 或者 ```Vue```
- 需要拆分 `OrgTree` 以及 `UserTable` 两个组件
  - 两个组件自己维护相关的数据。
  - 体现两个组件的互相通信。
- 组织架构根据点上级节点进行查询子级节点实现异步加载。
- 用户 ```Table ``` 数据跟据点击 ```组织架构树形节点``` 以及 ```输入搜索关键字``` 查询。
  - 需要考虑防抖节流等功能点
- 风格不限
  - 示例图仅仅是效果展示，不需要完全符合。
  - 可以使用 ```UI Framework```, 如 ```ant-design```, ```element-ui```等
  - 如果不用```UI Framework```, 可以直接用原生的```<ul> <li>```, ```<table>``` 实现，不用实现相关的CSS样式, 可以加分。

## 其他简答题

### 如何将如下的`JSON`正确解析成 `Object`
```json
{
  "userId": 111323290434354540545
}
```
回答：
```
const jsonString = '{"userId": 111323290434354540545}';
const jsonObject = JSON.parse(jsonString);
console.log(jsonObject.userId); // 输出：111323290434354540545
```
### 前端需要*稳定*每隔`1s`向服务端请求`API`, 请问如何实现？
回答：
```
// 定义一个函数用于向服务端请求API
function fetchDataFromServer() {
    // 向服务端请求API的代码，可以使用 fetch 或者 XMLHttpRequest
    // 这里假设使用 fetch，你需要根据实际情况修改
    fetch('your_api_url')
        .then(response => response.json())
        .then(data => {
            // 在这里处理从服务端获取到的数据
            console.log(data);
        })
        .catch(error => {
            // 在这里处理请求失败的情况
            console.error('Error fetching data:', error);
        });
}

// 每隔1秒执行一次 fetchDataFromServer 函数
setInterval(fetchDataFromServer, 1000);
```

### 什么情况下，你会为你的项目引入状态管理库，比如`Redux`, `Pinia`, 可以简述一下起到了什么作用么？
回答：一般用来管理复杂的应用状态、大型应用、跨组件通信、时间旅行调试以及异步数据管理等情况。这些库提供了统一的状态管理机制，帮助提高代码的可维护性、可扩展性和开发效率。

### 为什么`ESM`与`CJS`不能兼容？
回答：
ESM（ECMAScript Modules）和CJS（CommonJS）是两种不同的模块系统，它们有不同的语法和加载机制，因此不能直接兼容。

1. **语法不同**：ESM 使用 `import` 和 `export` 关键字来定义模块，而CJS 使用 `require()` 和 `module.exports` 或 `exports` 来定义模块，这两种语法不兼容。

2. **加载机制不同**：ESM 是静态导入，模块在编译时确定，而CJS 是动态加载，模块在运行时加载，这两种加载机制也不兼容。

由于这些差异，ESM 和 CJS 不能直接在同一个代码文件中混合使用，需要通过转换工具（如Babel）或者运行时环境（如Node.js的`--experimental-modules`标志）来实现互相之间的兼容性。
