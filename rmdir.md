# Linux rmdir 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux rmdir 命令删除空的目录。

### 语法

```
rmdir [-p] dirName
```

**参数**：

- -p 是当子目录被删除后使它也成为空目录的话，则顺便一并删除。
- 

### 实例

- 将工作目录下，名为 a 的子目录删除 :

 ```
  rmdir a # 相当于 rm -r a
 ```

- 在当前目录下的 a/b/c 目录中，删除名为 c 的子目录。若 c 删除后，b 目录成为空目录，则 b 亦予删除。a同理

 ```
  mkdir -p a/b/c
  rmdir -p a/b/c
 ```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)