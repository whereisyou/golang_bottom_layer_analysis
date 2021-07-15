`break`出`for/switch 或 for/select`的一种解决方案是**使用带标签的 break**，如下所示：

```
COPYloop:
  for {
    select {
    case <-ch:
    // Do something
    case <-ctx.Done():
      break loop
    }
  }
```

