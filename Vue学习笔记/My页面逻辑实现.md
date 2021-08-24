# My页面逻辑分析

## 配置页面路由

> 项目经理完成

## 页面布局   未登录  or  登录

> 处理页面登录状态,是否有token

## 页面样式调整



## 封装获取用户信息请求

> 封装获取用户信息

## 填充数据到页面中



## 退出登录,设置vuex中的user 的token为null



## 设置退出登录提示按钮Dialog



## axios统一添加请求头

```js
axios({
  method: "",
  url: "",
  headers: {
    Authorization: "Bearer token"
  }
})
```

## 请求拦截器

```js
// 请求拦截器
// Add a request interceptor
request.interceptors.request.use(function (config) {
  // Do something before request is sent
  const { user } = store.state

  // 如果用户已登录，统一给接口设置 token 信息
  if (user) {
    config.headers.Authorization = `Bearer ${user.token}`
  }

  // 处理完之后一定要把 config 返回，否则请求就会停在这里
  return config
}, function (error) {
  // Do something with request error
  return Promise.reject(error)
})
```





## 问题

直接获取vuex中的数据和放到data中再存取有什么区别

> 一个是响应式跟新到页面,一个没有响应式