    onSubmit(evt) {
      evt.preventDefault();
      const formdata = {
        method: "post",
        headers: { "content-type": "application/x-www-form-urlencoded" },
        data: qs.stringify(this.form),
        url: "api接口链接"
      };
      axios(formdata)
        .then(response => {
          alert("感谢您的提交，稍后将安排专人与您联系。");
          window.location.reload();
        })
        .catch(error => {
          alert("提交失败，请重试！");
          window.location.reload();
        });
    }
