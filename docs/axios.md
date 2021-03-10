#### 单一获取api数据

```
axios({
        method: "post",
        url: "api"
    })
    .then(response => {
        this.data = response.data.result;
    })
    .catch(error => {
        console.log("error!");
    });
```

#### 根据请求参数(body)获取api数据

```
axios
    .post("api", {
        userid: "",
        orderid: ""
    })
    .then(res => {
        this.data = res.data.result;
    })
    .catch(error => {
        console.log("error!");
    });
```

#### 向api提交表单数据

```
const formdata = {
    method: "post",
    headers: {
        "content-type": "application/x-www-form-urlencoded"
    },
    data: qs.stringify({
        phone: this.phone,
        code: this.code,
        pwd: this.pwd
    }),
    url: "api"
};
axios(formdata)
    .then(response => {
        this.data = response.data.result;
    })
    .catch(error => {
        console.log("error!");
    });
```
