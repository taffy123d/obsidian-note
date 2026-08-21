
# grep 命令用法大全

grep 是 Linux 中最强大的文本搜索工具之一，其名称来源于 **Global Regular Expression Print**（全局正则表达式打印）。它可以在文件或标准输入中搜索匹配指定模式的行，并打印出来。grep 家族包含三个命令：

| 命令 | 说明 |
|------|------|
| `grep` | 标准 grep，支持基本正则表达式 |
| `egrep` | 扩展 grep（等同于 `grep -E`），支持扩展正则表达式 |
| `fgrep` | 固定 grep（等同于 `grep -F`），按字面意思解释所有字符，元字符不作为特殊字符处理 |


## 一、命令格式

```bash
grep [选项] PATTERN [文件...]
```

其中 PATTERN 可以是普通字符串或正则表达式，文件可以是一个或多个，如果不指定文件则从标准输入读取。


## 二、常用选项大全

### 2.1 基础选项

| 选项 | 说明 | 示例 |
|------|------|------|
| `-i` | 忽略大小写 | `grep -i "error" logfile` |
| `-v` | 反向匹配，显示不包含模式的行 | `grep -v "debug" logfile` |
| `-n` | 显示匹配行的行号 | `grep -n "error" logfile` |
| `-c` | 只输出匹配的行数 | `grep -c "error" logfile` |
| `-l` | 只显示包含匹配模式的文件名 | `grep -l "pattern" *.txt` |
| `-h` | 查询多个文件时不显示文件名 | `grep -h "pattern" *.log` |
| `-w` | 全词匹配 | `grep -w "main" *.c` |
| `-o` | 只输出匹配的部分，而非整行 | `grep -o "[0-9]\+" file` |
| `-s` | 不显示错误信息 | `grep -s "pattern" file` |

### 2.2 上下文控制选项

| 选项 | 说明 | 示例 |
|------|------|------|
| `-A N` | 显示匹配行及其后 N 行（After） | `grep -A 5 "error" log` |
| `-B N` | 显示匹配行及其前 N 行（Before） | `grep -B 5 "error" log` |
| `-C N` | 显示匹配行及其前后各 N 行（Context） | `grep -C 5 "error" log` |

### 2.3 递归与目录选项

| 选项 | 说明 | 示例 |
|------|------|------|
| `-r` 或 `-R` | 递归搜索目录下的所有文件 | `grep -r "pattern" /var/log` |
| `--include=模式` | 只搜索匹配指定模式的文件 | `grep -r --include="*.log" "error" /var/log` |
| `--exclude=模式` | 排除匹配指定模式的文件 | `grep -r --exclude="*.log" "error" /var/log` |
| `--exclude-dir=目录` | 排除指定目录 | `grep -r --exclude-dir="backup" "error" /var/log` |
| `-d ACTION` | 指定处理目录的方式（read/skip/recurse） | `grep -d skip "pattern" dir/` |

### 2.4 正则表达式选项

| 选项 | 说明 | 示例 |
|------|------|------|
| `-E` | 使用扩展正则表达式（等同于 egrep） | `grep -E "error|warning" log` |
| `-F` | 将模式视为固定字符串（等同于 fgrep） | `grep -F "*.txt" file` |
| `-P` | 使用 Perl 兼容的正则表达式 | `grep -P "\d{3}" file` |
| `-f 文件` | 从文件中读取多个模式 | `grep -f patternfile file` |

### 2.5 输出控制选项

| 选项 | 说明 | 示例 |
|------|------|------|
| `--color=auto` | 高亮显示匹配的文本 | `grep --color=auto "pattern" file` |
| `-m N` | 只输出前 N 个匹配行 | `grep -m 5 "error" logfile` |
| `-q` | 静默模式，不输出任何内容（只用于获取退出状态） | `grep -q "pattern" file` |
| `-a` | 将二进制文件当作文本文件处理 | `grep -a "pattern" binaryfile` |
| `--binary-files=without-match` | 忽略二进制文件 | `grep --binary-files=without-match "pattern" dir/` |


## 三、正则表达式

grep 的核心在于正则表达式。默认使用**基本正则表达式（BRE）**，使用 `-E` 启用**扩展正则表达式（ERE）**。

### 3.1 基本正则表达式元字符

| 元字符 | 说明 | 示例 |
|--------|------|------|
| `^` | 匹配行首 | `grep '^root' /etc/passwd` |
| `$` | 匹配行尾 | `grep 'bash$' /etc/passwd` |
| `.` | 匹配任意单个字符（除换行符） | `grep 'r..t' /etc/passwd` |
| `*` | 匹配前一个字符 0 次或多次 | `grep 'ab*c' file` |
| `[]` | 匹配括号内的任意一个字符 | `grep '[aeiou]' file` |
| `[^]` | 匹配不在括号内的任意一个字符 | `grep '[^0-9]' file` |
| `\<` | 匹配单词开头 | `grep '\<north' file` |
| `\>` | 匹配单词结尾 | `grep 'west\>' file` |
| `\{n\}` | 精确匹配 n 次 | `grep 'o\{2\}' file` |
| `\{n,m\}` | 匹配 n 到 m 次 | `grep 'o\{2,4\}' file` |
| `\(\)` | 分组 | `grep '\(ab\)*' file` |

### 3.2 扩展正则表达式（`-E`）额外元字符

| 元字符 | 说明 | 示例 |
|--------|------|------|
| `+` | 匹配前一个字符 1 次或多次 | `grep -E '3+' file` |
| `?` | 匹配前一个字符 0 次或 1 次 | `grep -E '2?[0-9]' file` |
| `\|` | 或（匹配多个模式之一） | `grep -E 'error\|warning' log` |
| `()` | 分组 | `grep -E '(error|warning)' log` |
| `{}` | 次数匹配（无需转义） | `grep -E '[0-9]{3}' file` |

### 3.3 常用正则表达式示例

```bash
# 匹配 IP 地址
grep -E "([0-9]{1,3}\.){3}[0-9]{1,3}" access.log

# 匹配邮箱地址
grep -E "[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}" user.log

# 匹配以数字开头的行
grep -E "^[0-9]+" file.txt

# 匹配以大写字母开头的单词
grep -E "\b[A-Z][a-z]+\b" file.txt

# 匹配日期格式 YYYY-MM-DD
grep -E "^[0-9]{4}-[0-9]{2}-[0-9]{2}" logfile
```


## 四、管道配合用法

grep 的输入可以来自标准输入或管道，而不仅仅是文件。管道 `|` 将一个命令的输出作为 grep 的输入。

### 4.1 进程过滤

```bash
# 查找 nginx 进程
ps -ef | grep nginx

# 查找 sshd 进程，并排除 grep 自身
ps aux | grep sshd | grep -v grep

# 查找 Java 进程
ps -ef | grep java
```

### 4.2 日志实时监控

```bash
# 实时监控日志，过滤包含 ERROR 的行
tail -f app.log | grep "ERROR"

# 实时监控并显示完整的异常堆栈（匹配行后 30 行）
tail -f error.log | grep -A 30 "NullPointerException\|TimeoutException"

# 实时监控，忽略大小写，匹配多个异常类型
tail -f application.log | grep -Ai30 "ERROR\|Exception"
```

### 4.3 命令输出过滤

```bash
# 只显示目录（以 d 开头的行）
ls -l | grep '^d'

# 查看网络连接，过滤出 ESTABLISHED 状态
netstat -an | grep ESTABLISHED

# 查看内存信息，过滤出 Mem 行
free -h | grep Mem

# 查看 CPU 信息，过滤出型号
cat /proc/cpuinfo | grep "model name"
```

### 4.4 多级管道（多个 grep 串联）

```bash
# 在日志中查找 ERROR，然后从中过滤掉 "ignored"
grep "ERROR" app.log | grep -v "ignored"

# 查找包含 "timeout" 的行，再取前后 10 行上下文
grep "timeout" app.log | grep -B10 -A10 "ERROR"

# 查找特定时间段的日志
grep "2023-11-15 14:" app.log | grep -A20 "事务回滚"
```

### 4.5 与统计命令组合

```bash
# 统计包含 "ERROR" 的行数
grep "ERROR" app.log | wc -l

# 统计当前目录下所有 .log 文件中 ERROR 出现的总次数
grep -c "ERROR" *.log | sort -nr -t: -k2

# 统计各 IP 的访问次数（配合 awk 和 sort）
grep "GET" access.log | awk '{print $1}' | sort | uniq -c | sort -nr
```

### 4.6 与 xargs 组合

当 grep 的输出（如文件名列表）需要作为另一个命令的参数时，使用 `xargs`：

```bash
# 找出包含 "pattern" 的文件并删除
grep -l "pattern" * | xargs rm

# 查找所有 .txt 文件，搜索其中的 "example"
find . -type f -name "*.txt" | xargs grep "example"

# 查找包含特定内容的文件并显示文件名
find . -name "*.py" | xargs grep "test"
```

### 4.7 与分页器组合

```bash
# 搜索结果过多时，用 less 分页查看
grep -r "keyword" /path | less

# 查看带上下文的匹配结果
grep -A50 "NullPointerException" application.log | less
```

### 4.8 高级管道技巧

```bash
# 将输出按模式拆分到不同文件
command | tee >(grep 'pattern1' > file1.txt) >(grep 'pattern2' > file2.txt) > /dev/null

# 错误输出也重定向到 grep（2>&1）
command 2>&1 | grep "error"

# 排除健康检查等干扰信息
grep -v "健康检查\|心跳" app.log | grep -A30 "异常"
```


## 五、实战场景

### 5.1 日志分析

```bash
# 查找 HTTP 500 错误及其上下文（前后各 5 行）
grep -C 5 "HTTP/1.1\" 500" /var/log/nginx/access.log

# 查找登录失败记录及其前后各 5 行
grep -B 5 -A 5 'failed login' /var/log/auth.log

# 多文件异常频率分析
grep -c "ConnectionTimeout" *.log | sort -nr -t: -k2
```

### 5.2 配置文件检查

```bash
# 查看非注释行（排除以 # 开头的行）
grep -v '^#' /etc/ssh/sshd_config

# 查找配置文件中所有监听端口
grep '^Listen' /etc/apache2/ports.conf

# 查找配置项，忽略空行和注释
grep -v '^#' nginx.conf | grep -v '^$'
```

### 5.3 压缩文件搜索

```bash
# 直接在 .gz 压缩文件中搜索（无需解压）
zgrep -A 30 -H "OutOfMemoryError" *.gz

# 结合 zcat 处理特殊压缩格式
zcat app.log.gz | grep "ERROR"
```

### 5.4 代码搜索

```bash
# 在项目中递归搜索函数定义
grep -r "function" /home/user/code

# 只搜索特定扩展名的文件
grep -r --include="*.c" "main" /project/src

# 全词匹配，避免匹配到子字符串
grep -w '\<main\>' *.c
```


## 六、退出状态（Exit Status）

grep 的退出状态可以在 Shell 脚本中用于条件判断：

| 退出状态 | 含义 |
|----------|------|
| `0` | 找到了匹配的行 |
| `1` | 没有找到匹配的行 |
| `2` | 发生错误（如文件不存在） |

```bash
# 在脚本中使用
if grep -q "pattern" file; then
    echo "找到匹配"
else
    echo "未找到匹配"
fi

# 检查上一个命令的返回值
grep "root" /etc/passwd
echo $?  # 0 表示找到，1 表示未找到
```


## 七、性能优化建议

| 优化方式 | 说明 |
|----------|------|
| 使用 `-F` | 固定字符串搜索比正则表达式快很多，可节省约 80% 内存 |
| 使用 `--include` | 限定搜索的文件类型，减少扫描范围 |
| 使用 `-m N` | 限制匹配数量，找到 N 个后即停止 |
| 使用 `-I` | 忽略二进制文件 |
| 使用 `--exclude` | 排除不需要搜索的文件或目录 |
| 配合 `less` | 大数据集使用分页查看，避免终端卡顿 |

```bash
# 性能优化示例
grep -F "exact_string" large_file.txt          # 固定字符串搜索
grep -r --include="*.log" "ERROR" /var/log/    # 只搜索 .log 文件
grep -m 10 "ERROR" huge.log                    # 只找前 10 个
```


## 八、快速参考卡片

```bash
# 基础搜索
grep "pattern" file
grep -i "pattern" file        # 忽略大小写
grep -v "pattern" file        # 反向匹配
grep -n "pattern" file        # 显示行号
grep -c "pattern" file        # 统计行数

# 正则搜索
grep -E "pattern1|pattern2" file
grep "^start" file            # 行首匹配
grep "end$" file              # 行尾匹配
grep -w "word" file           # 全词匹配

# 上下文
grep -A 5 "pattern" file      # 后5行
grep -B 5 "pattern" file      # 前5行
grep -C 5 "pattern" file      # 前后各5行

# 递归搜索
grep -r "pattern" /path/
grep -r --include="*.log" "pattern" /path/

# 管道组合
ps -ef | grep "process"
tail -f log | grep "ERROR"
grep -l "pattern" * | xargs rm

# 压缩文件
zgrep "pattern" file.gz
```