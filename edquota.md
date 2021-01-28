# Linux edquota命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux edquota 命令用于编辑用户或群组的磁盘配额。

edquota预设会使用vi来编辑使用者或群组的磁盘配额设置。

### 语法

```
edquota [-p <源用户名称>][-ug][用户或群组名称...]
```

或

```
edquota [-ug] -t
```

**参数**：

- -u 设置用户的磁盘配额，这是预设的参数。
- -g 设置群组的磁盘配额。
- -p<源用户名称> 将源用户的磁盘配额设置套用至其他用户或群组。
- -t 设置宽限期限。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)