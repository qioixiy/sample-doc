# bash template
```
#!/usr/bin/env bash

set -o errexit
set -o nounset
set -o pipefail
readonly SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

main() {
    # your code goes here...
}

main "${@}"
```

# shell string op
## ${var##*/}, 从左开始最大化匹配到字符"/"，然后截掉左边内容（包括字符"/"）,返回余下右侧部分
```
# 提取到文件名
$ var=/dir1/dir2/file.txt
$ echo ${var##*/}
file.txt
# 提取到文件后缀
$ echo ${var##*.}
txt
```
## ${var#*.}, 从左开始第一次匹配到字符"."，然后截掉左边内容（包括字符"."）,返回余下右侧部分
```
# 提取后缀
$ var=/dir1/dir2/file.tar.gz
$ echo ${var#*.}
tar.gz
```
## ${var%/*}，从右开始第一次匹配到字符"/"，然后截掉右边内容（包括字符"/"）,返回余下左侧部分
```
$ var=/dir1/dir2/file.txt
$ echo ${var%/*}
/dir1/dir2
```
## ${var%%.*}, 从右开始最大化匹配到字符"."，然后截掉右边内容（包括字符"."）,返回余下左侧部分
```
$ var=/dir1/dir2/file.txt
$ echo ${var%%.*}
/dir1/dir2/file
```
