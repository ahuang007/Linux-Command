# Linux fold 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux fold 命令用于限制文件列宽。

fold 指令会从指定的文件里读取内容，将超过限定列宽的列加入增列字符后，输出到标准输出设备。若不指定任何文件名称，或是所给予的文件名为"-"，则fold指令会从标准输入设备读取数据。

### 语法

```
fold [-bs][-w<每列行数>][--help][--version][文件...]
```

**参数**：

- -b或--bytes 以Byte为单位计算列宽，而非采用行数编号为单位。
- -s或--spaces 以空格字符作为换列点。
- -w<每列行数>或--width<每列行数> 设置每列的最大行数。
- --help 在线帮助。
- --version 显示版本信息。

### 实例

将一个名为testfile 的文件的行折叠成宽度为30，可使用如下命令：

```
[root@localhost root ]$ fold -w 30 test.lua 
```

为了对比，先将 test.lua 文件输出如下：

```
[root@localhost root ]$ cat test.lua 
local utils = {}
function utils.var_dump(data, max_level, prefix)
    if type(prefix) ~= "string" then
        prefix = ""
    end
    if type(data) ~= "table" then
        print(prefix .. tostring(data))
    else
        print(data)
        if max_level ~= 0 then
            local prefix_next = prefix .. "    "
            print(prefix .. "{")
            for k, v in pairs(data) do
                io.stdout:write(prefix_next .. k .. " = ")
                if type(v) ~= "table" or (type(max_level) == "number" and max_level <= 1) then
                    print(v, ",")
                else
                    if max_level == nil then
                        utils.var_dump(v, nil, prefix_next)
                    else
                        utils.var_dump(v, max_level - 1, prefix_next)
                    end
                end
            end
            print(prefix .. "}")
        end
    end
end

local stage = {}
stage.items = {}
table.insert(stage.items, {type = 'IT_GOLD', value = 9})

for _, v in ipairs(stage.items) do 
	if v.type == 'IT_GOLD' then 
		v.value = v.value + math.floor(v.value*25/100)
	end
end 

utils.var_dump(stage.items)

```

然后使用fold命令折叠显示：

```
[root@localhost root ]$ fold -w 30 test.lua 
local utils = {}
function utils.var_dump(data, 
max_level, prefix)
    if type(prefix) ~= "string
" then
        prefix = ""
    end
    if type(data) ~= "table" t
hen
        print(prefix .. tostri
ng(data))
    else
        print(data)
        if max_level ~= 0 then
            local prefix_next 
= prefix .. "    "
            print(prefix .. "{
")
            for k, v in pairs(
data) do
                io.stdout:writ
e(prefix_next .. k .. " = ")
                if type(v) ~= 
"table" or (type(max_level) ==
 "number" and max_level <= 1) 
then
                    print(v, "
,")
                else
                    if max_lev
el == nil then
                        utils.
var_dump(v, nil, prefix_next)
                    else
                        utils.
var_dump(v, max_level - 1, pre
fix_next)
                    end
                end
            end
            print(prefix .. "}
")
        end
    end
end

local stage = {}
stage.items = {}
table.insert(stage.items, {typ
e = 'IT_GOLD', value = 9})

for _, v in ipairs(stage.items
) do 
	if v.type == 'IT_GOLD'
 then 
		v.value = v.va
lue + math.floor(v.value*25/10
0)
	end
end 

utils.var_dump(stage.items)

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)