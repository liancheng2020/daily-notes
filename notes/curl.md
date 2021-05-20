
#### curl 相关命令


```
  以网址 127.0.0.1:8080 为例
```
- get 请求如下：

```
  curl https://127.0.0.1:8080
```

- post 请求如下：

```
  curl -X POST "https://127.0.0.1:8080" -H "accept: application/json;charset=utf-8" -H "Content-Type: application/json" -d "body请求体"
```