# find and do other
find -name '*.md'  | while read file_name; do iconv -f GBK -t UTF-8 $file_name -o $file_name ; done
