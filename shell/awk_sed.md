# awk 与 sed使用记录

## awk

 输出单双引号

	双引号：
	awk '{print "\""}'        #放大：awk '{print "  \"  "}'
	使用“”双引号把一个双引号括起来，然后用转义字符\对双引号进行转义，输出双引号。
```
单引号：
awk '{print "'\''"}'       # 放大: awk '{print  "  '  \  '  '   " }'
```



合并行数

```awk
awk '{if(NR%5!=0)ORS=" ";else ORS="\n "}1'     
5是行数，根据情况修改
```



awk 使用变量例子

```awk
awk 'BEGIN { i=0; } {i+=1; if(i%2==0) print $0; else {gsub(/0e/, "1e"); print}}' file
awk 'BEGIN { i=j=0;} {if($2!=0.0){i+=$2*$2; j+=1; printf "%e\t%d\n", i , j}}' file
awk 'BEGIN { i=0;} {while(i<320) {printf "%.10e\n", $1; i =i+1}}' file
awk '{if($2!=0) print $0 "\t" ($2-$3) "\t" ($2-$3)/$2; else print $0 "\t" ($2-$3) "\t" 0}' file
```



awk 使用分隔符

```awk
awk 'BEGIN {FS=":";} {print $1;}' file
```



## sed

To remove duplicated line, 3 ways availabe as below

```sed
sort -k2n file | sed '$!N; /^\(.*\)\n\1$/!P; D'
sort -k2n file | awk '{if ($0!=line) print;line=$0}'
sort -k2n file | uniq > a.out
```

替换

```sed
sed 's/"//g' file
去掉文件里所有的双引号
```

​	

