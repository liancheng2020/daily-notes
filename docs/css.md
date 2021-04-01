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

### 滤镜

```
  filter: blur(10px);
```

### flex布局

#### 水平垂直居中

```
  display: flex;
  justify-content: center;
  align-items: center;
```

##### 左右布局

```
  display: flex;
  justify-content: space-between;
  align-items: center;
```
##### 纵向布局

```
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
```