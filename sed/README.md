1. 把Jon的名字改成Jonathan.
2. 删除头三行
3. 显示5-10行
4. 删除包含Lane的行.
5. 显示所有生日在November-December之间的行
6. 把三个星号(***)添加到也Fred开头的行
7. 用JOSE HAS RETIRED取代包含Jose的行
8. 把Popeye的生日改成11/14/46
9. 删除所有空白行
10. 写一个脚本,将:
       - 在第一行之前插入标题PERSONNEL FILE.
       - 删除以500结尾的工资
       - 显示文件内容,把姓和名颠倒
       - 在文件末尾添加THE END

答案

1. sed "s/Jon/Jonathan/" 1.txt
2. sed "1,3d" 1.txt
3. sed "5,10! d" 1.txt
4. sed "/Lane/ d" 1.txt
5.
6. sed "/^Fred/ s/^/***/" 1.tx
7. sed "/Jose/ s/^.*$/JOSE HAS RETIRED/" 1.txt
8. sed "s/[0-9]*\/[0-9]*\/[0-9]*/11\/14\/46/" 1.txt
9. sed "/^$/ d" 1.txt
10. `sed -e "1 i PERSONNEL FILE" -e "$ a THE END" -e "/500$/d" -e "s/\([^\-]*\) \([^\-]*\):\(.*\)/\2 \1:\3/" 1.txt`

