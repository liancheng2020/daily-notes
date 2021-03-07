

```
  /**
   * 操作权限
   * 使用示例：v-if="hasPermission('optTodo.edit')"
   */
  static hasPermission(permission: string) {
    const storePermissionList = store.state.permission
    if (!storePermissionList || storePermissionList.length === 0) {
      return false
    }
    const storePermission = storePermissionList.find((item: string) => {
      return item === permission
    })
    return !!storePermission
  }
```