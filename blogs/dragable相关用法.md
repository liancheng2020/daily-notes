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
- 行拖拽--数据来源于以每一行数据组成的数组；
- 列拖拽--数据来源于以每一列数据组成的数组。

#### 行拖拽事件

```
  rowList: any[] = []  // 原数组
  sortList: any[] = [] // 排序数组
  sortTable: any  // 排序table

  rowDrop() {
    const tbody = document.querySelector('.el-table__body-wrapper tbody')
    const self = this
    self.sortTable = Sortable.create(tbody, {
      disabled: false,
      animation: 150, // 拖拽延时
      onEnd(newVal: any, oldVal: any) {
        const currRow = self.rowList.splice(oldVal, 1)[0]
        self.rowList.splice(newVal, 0, currRow)   // 界面拖拽处理
        const temp: any = sortList.splice(newVal.oldIndex, 1)[0]
        self.sortList.splice(newVal.newIndex, 0, temp) // 排序数组实际处理
      }
    }) // 创建排序table
  }

  this.sortTable.destroy()  // 销毁排序table
```

#### 列拖拽事件

```
  columnList: any[] = []  // 原数组
  sortList: any[] = [] // 排序数组
  sortTable: any  // 排序table

  columnDrop() {
    const tbody = document.getElementById('sort')
    const self = this
    self.sortTable = Sortable.create(tbody, {
      animation: 150, // 拖拽延时
      onEnd(val: any) {
        const curColumn = self.sortList.splice(val.oldIndex, 1)[0]
        self.sortList.splice(val.newIndex, 0, curColumn)
      }
    }) // 创建排序table
  }

  this.sortTable.destroy()  // 销毁排序table
```