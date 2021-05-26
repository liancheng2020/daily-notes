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