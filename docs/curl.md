#### GET请求
 
```
  curl https://daojia-test.hd123.com:9999/abouts
```

#### POST请求

```
  curl -d "gpas=1.2.0&sas=1.4.0" https://daojia-test.hd123.com:9999/abouts
```
```
  curl -X POST "https://ays-test.hd123.com/MAS-OPENAPI-SERVICE/v2/-/service/permission/register" -H "accept: application/json;charset=utf-8" -H "Content-Type: application/json" -d "{ \"applicationId\": \"qtyCenter\", \"group\": { \"id\": \"init/initTask\", \"name\": \"初始化/初始化任务\" }, \"items\": [ { \"id\": \"ias.task.view\", \"name\": \"任务查看\" },{ \"id\": \"ias.task.edit\", \"name\": \"任务编辑\" } ], \"orgId\": \"-\", \"orgType\": \"-\"}"
```