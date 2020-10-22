#### 单行超出省略

```git
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
```

#### 双行超出省略

```git
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  /* autoprefixer: off */
  -webkit-box-orient: vertical;
  // autoprefixer: on
  -webkit-line-clamp: 2;
```