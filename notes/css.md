#### 单行超出省略

```
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
```

#### 双行超出省略

```
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
  // autoprefixer: on
  -webkit-line-clamp: 2;
```

#### 三角形

```
  width: 0;
  height: 0;
  border-width: 0 40px 40px;
  // border-width: 0 40px 40px 0;
  // 设置左边border宽度为0，则为直角三角形
  border-style: solid;
  border-color: transparent transparent red;
```