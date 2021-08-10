- 引入sortable.js的包
```
  npm install sortable.js --save
```
- 或者安装vuedraggable
```
  npm i -S vuedraggable
```

- vuedraggable依赖Sortable.js，所以下载了vuedraggable，我们便可以直接引入Sortable使用Sortable的特性；
- vuedraggable是Sortable一种加强，实现组件化的思想，可以结合Vue，使用起来更方便；
- 使用Sortable时，还需构建一下，
```
  import Sortable from 'sortablejs'
```

#### 行拖拽事件

```
  rowDrop() {
    const tbody = document.querySelector('.el-table__body-wrapper tbody')
    const self = this
    self.sortTable = Sortable.create(tbody, {
      disabled: false,
      animation: 150, // 拖拽延时
      onEnd(newVal: any, oldVal: any) {
        const currRow = self.sortList.splice(oldVal, 1)[0]
        self.sortList.splice(newVal, 0, currRow)
      }
    }) // 创建排序table
  }
```

#### 列拖拽事件

```
  columnDrop() {
    const wrapperTr = document.querySelector('.el-table__header-wrapper tr')
    this.sortable = Sortable.create(wrapperTr, {
      animation: 180,
      delay: 0,
      onEnd(evt: any) {
        const oldItem = this.dropCol[evt.oldIndex]
        this.dropCol.splice(evt.oldIndex, 1)
        this.dropCol.splice(evt.newIndex, 0, oldItem)
      }
    })
  }
```