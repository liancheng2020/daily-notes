#### base64上传图片

```
  doUpload(file: { raw: Blob }) {
    let reader = new FileReader()
    reader.readAsDataURL(file.raw)
    reader.onload = (event: any) => {
      console.log(event.srcElement.result)
    }
  }
```

#### formData上传图片

```
  doUpload(params: any) {
    if (params.size > 1024 * 1024 * 5) {
      return this.$message.warning('导入文件过大，请导入5MB以内的文件')
    }
    const loading = this.$loading(ConstantMgr.loadingOption)
    let formData = new FormData()
    formData.append('name', params.file.name)
    formData.append('file', params.file)
    FileUploadApi.upload(formData)
      .then((resp) => {
        loading.close()
        this.$emit('success', resp.data)
      })
      .catch((e) => {
        loading.close()
        this.$message.error(e.message)
      })
  }
```
