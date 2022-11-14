# Linux_learn_find
find 用法

# find 用法

find 目錄 參數 條件

參考 : 

[https://blog.gtwang.org/linux/unix-linux-find-command-examples/](https://blog.gtwang.org/linux/unix-linux-find-command-examples/)

[https://stackoverflow.com/questions/4210042/how-do-i-exclude-a-directory-when-using-find](https://stackoverflow.com/questions/4210042/how-do-i-exclude-a-directory-when-using-find)

`find . -type d 'xxx*'`

參數

- 目錄搜尋層數
- maxdepth 第幾層
- find . -maxdepth 1
- 忽略特定目錄
- -not -path 目錄
- `find . -name '123' -not -path './usr/*'`
- path 目錄 -prune -o
- `find . -path ./usr -prune -o -name '123'`
- -user 使用者
- `find . -user topstd -name '*' -exec ls -l {} \;`
- 排除 使用者
- `find . ! -user topstd -name '*' -exec ls -l {} \;`
- -szie 大小
- `find . -size +10k`
- 小於 10 k
- `find . -size -10k`

[https://stackoverflow.com/questions/38843212/how-to-use-echo-with-find-in-bash](https://stackoverflow.com/questions/38843212/how-to-use-echo-with-find-in-bash)

The shell redirection, `>>` is being done at first, a file named `{}` is being created before even the `find` starts and the strings (the number of files are in there) are being written to the file `{}`.

You need:

```
find . -type f -exec bash -c 'echo "This file found" >>"$1"' _ {} \;
```
