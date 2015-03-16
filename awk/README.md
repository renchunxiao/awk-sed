1. 显示所有电话号码
2. 显示Dan的电话号码
3. 显示Susan的名字和电话号码
4. 显示所有以D开头的姓
5. 显示所有以一个C或E开头的名
6. 显示所有只有四个字符的名
7. 显示所有区号为916的人名
8. 显示Mike的捐款.显示每个值时都有以$开头.如$250$100$175
9. 显示姓,其后跟一个逗号和名,如Jody,Savage
10. 写一个awk的脚本,它的作用:
	 - 显示Savage的全名和电话号码
	 - 显示Chet的捐款
	 - 显示所有头一个月捐款$250的人名.
注:区号本来是圆括号表示的.

答案

1. awk -F ':' '{print $2}' 1.txt 
2. awk -F ':' '/Dan/ {print $2}' 1.txt
3. awk -F ':' '/Susan/ {print $1, $2}' 1.txt
4. awk -F '[:| ]' '$2 ~ /^D/ {print $2}' 1.txt
5. awk -F '[:| ]' '$1 ~ /^[C|E]/ {print $1}' 1.txt
6. awk 'length($1) == 4 {print $1}' 1.txt
7. awk -F '[:| ]' '$3 ~ /\[916\]/ {print $1,$2}' 1.txt
8. awk -F ':' '/Mike/ {print "$" $3 "$" $4 "$" $5}' 1.txt
9. awk -F '[:| ]' 'BEGIN { OFS=","}{print $1,$2}' 1.txt
10. awk -F '[:| ]' '{if($2=="Savage") {print $1,$2,$3,$4} else if ($1=="Chet") {print $5,$6,$7} else if ($5=="250") {print $1,$2}}' 1.txt

