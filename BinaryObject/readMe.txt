 位运算：
   2&3   3|4
   2<<2

   
   1byte=8bit
  1
  
  0 0 0 0 0 0 0 1   2进制的1的原码 反码 补码
  0 0 0 0 0 0 0 0   2进制的0的原码 反码 补码
   
  -1
  1 0 0 0 0 0 0 1
   
   
   
   计算机中真正参与运算的是  补码！
  
  在java中所有的数字都是有符号的！  符号就是  正 0   负 1
   最高位（最左边的）的 0和1 就是 符号位
 
 
 什么是最高位？ 就是最左边的数字！
  java中最小的单位是 byte（字节）
 
  生活中我们买了一个50G的内存条！ 插入到我们的电脑中 有50G吗？？
  没有！ 因为所有的厂商都是以  1G=1000MB 来计算的！
 但是我们的电脑 是以  1G=1024MB 来计算的！所以 不足50G！
 
 
  
01. 原码

02. 反码

03. 补码



68

6*10的1次方+8*10的0次方

1byte = 8 bit


1   10进制

0 0 0 0 0 0 0 1   二进制

1*2的0次方  

1+2

	0 0 0 0 0 0 0 1
+	0 0 0 0 0 0 1 0
--------------------
    0 0 0 0 0 0 1 1 ==》  1*2的0次方+1*2的1次方 ===》3


符号位 就是 最高位（最左边的）
 0  正数
 1  负数


-1

 1 0 0 0 0 0 0 1

-2
 1 0 0 0 0 0 1 0   


 1 - 2

     01.找到-2的原码
 
  1 0 0 0 0 0 1 0      02.需要把原码转换成反码
  1 1 1 1 1 1 0 1      03.反码需要转换成补码
  1 1 1 1 1 1 1 0      04.得到-2 运算的 补码
+ 0 0 0 0 0 0 0 1
---------------------------     
  1 1 1 1 1 1 1 1      得到的是结果的补码   需要转换成反码 再转换成原码
  1 1 1 1 1 1 1 0      得到了结果的反码
  1 0 0 0 0 0 0 1      得到了结果的源码   -1


4  - 3

 1 0 0 0 0 0 1 1      01.找到-3的原码  把原码转换成反码
 1 1 1 1 1 1 0 0      02.反码需要转换成补码
 1 1 1 1 1 1 0 1      03.得到补码 可以运算
+0 0 0 0 0 1 0 0      
---------------------------------------------
 0 0 0 0 0 0 0 1      结果是正数  1


注意点

01. 计算机中运算的都是补码
02. 正数和0的反码补码原码都是一致的
03. 在java中所有的数字都是有符号
04. 负数的反码=符号位不变+其他位取反（0=1  1=0）
05. 负数的补码=反码+1



算术右移    ：  符号位不变，低位溢出删除！ 高位补零！

int newCapacity = oldCapacity + (oldCapacity >> 1);

int newCapacity=10+(10 >> 1);


10 >> 1

10: 指的是需要位移的数字
>>：位移方向
1 ：位移的位数

 01.首先找到10的2进制

 0 0 0 0 1 0 1 0
   0 0 0 0 1 0 1 0       02.右移一位
-------------------------
 0 0 0 0 0 1 0 1        1*2的0次方+1*2的2次方=5



算术左移  ：   符号位不变，高位溢出删除！ 低位补零！


   10  <<  1

    01.首先找到10的2进制

     0 0 0 0 1 0 1 0
   0 0 0 0 1 0 1 0       02.左移一位
------------------------------------
     0 0 0 1 0 1 0 0     1*2的2次方+1*2的4次方=20


 逻辑右移：  不管符号位！ 低位溢出删除！ 高位补零！    没有逻辑左移！！！
           

 10 >>> 2

 0 0 0 0 1 0 1 0
     0 0 0 0 1 0 1 0
---------------------------
 0 0 0 0 0 0 1 0     1*2的1次方=2




 -1
  1 0 0 0 0 0 0 1    01.原码
  1 1 1 1 1 1 1 0    02.反码
  1 1 1 1 1 1 1 1    03.补码
    1 1 1 1 1 1 1 1  04.右移一位  高位补零  
-----------------------------------
  0 1 1 1 1 1 1 1 

===》  结果2147483647



位运算：

01.按位与 &  ：  两位都为1，结果为1

 3 & 4

   0 0 0 0 0 0 1 1 
&  0 0 0 0 0 1 0 0
-------------------------
   0 0 0 0 0 0 0 0


2 & 3
   0 0 0 0 0 0 1 1 
&  0 0 0 0 0 0 1 0 
---------------------
   0 0 0 0 0 0 1 0 



02.按位与 |：两位有一个为1，结果为1


 3 | 4

   0 0 0 0 0 0 1 1 
|  0 0 0 0 0 1 0 0
-------------------------
   0 0 0 0 0 1 1 1


2 | 3
   0 0 0 0 0 0 1 1 
|  0 0 0 0 0 0 1 0 
---------------------
   0 0 0 0 0 0 1 1 


03.按位异或 ^  ：两位必须是一个为0 一个为1的时候，结果才是1！

 3 ^ 4

   0 0 0 0 0 0 1 1 
^  0 0 0 0 0 1 0 0
-------------------------
   0 0 0 0 0 1 1 1


2 ^ 3
   0 0 0 0 0 0 1 1 
^  0 0 0 0 0 0 1 0 
---------------------
   0 0 0 0 0 0 0 1 



04.按位取反  ~ : 仅限于一个表达式运算

 ~ 3

~  0 0 0 0 0 0 1 1 
---------------------
   1 1 1 1 1 1 0 0    原码
   1 0 0 0 0 0 1 1    反码
   1 0 0 0 0 1 0 0    补码
-----------------------      -4



















