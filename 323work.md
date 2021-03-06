# 数字系统
## 练习题
1.  a.(01101)=1+4+8=13
    c.(011110.01)=2+4+8+16+0.25=30.25
2.  a.(AB2)=2+16+11+256*10=2738
    c.(ABB)=11+11*16+10*256=2747
3.  a.(237)=7+3*8+2*64=159
    c.(617.7)=7+1*8+6*64=7*0.125=399.875

4.  a. 1234 =（100 1101 0010）2

    c. 124.02 
    124.02=124+0.02
    124=64+32+16+8+4
    0.02*2=0.04 *2=0.08 *2=0.16 *2=0.32 *2=0.64= 1111100.00000）2

5. 转化为8进制：
    a. 1156/8=144······4
    144/8=18······0
    18/8=2······2
    2/8=0······2
    1156=（2204）8

    c. 11.4=11+0.4
    11/8=1······3
    1/8=0······1
    0.4 *8=3.2
    0.2 *8=1.6 
    0.6 *8=4.8
    0.8 *8=6.4 
    0.4 *8=3.2
    11.4=（13.31463）8


6. 转化为16进制
    a. 567/16=35······7
    35/16=2······3
    2/16=0······2
    结果为：（237）16

    c. 12.13=12+0.13
    12/16=0······12
    0.13 *16=2.08
    0.08 *16=1.28
    0.28 *16=4.48
    0.48 *16=7.68
    0.68 *16=10.88
    结果为：（C.2147A）16

7. 8进制转化为16进制
    a. (514)8 = (101 001 100)2 = (1 0100 1100)2 = (14C)16

    c. (13.7)8 =(1 011.111)2= (1011.1110)2= (B.E)16


8. 16进制转化为8进制
     a. (51A)16=(0101 0001 1010)2=(010 100 011 010)2= (2432)8

     c. (BB.C)16=(1011 1011.1100)2=(010 111 011.110)2= (273.6)8

9. 2进制转化为8进制
     a. (01101)2=(001 101)2= (15)8

     c. (011110.01)2= (011 110.010)2= (36.2)8

10. 2进制转化为16进制
    a. (01101)2=(0000 1101)2=(0D)16

    c. (011110.01)2=(0001 1110.0100)2=(1E.4)16

14. 不进行转换，找出下面各个情况中在目标系统中所需的最少数码数量:
a.5个十进制数码转换为二进制
x>=k*(logb1/logb2),其中k=5,b1=10,b2=2 ； x最少为17

b.4个十进制数码转换为八进制
x>=k*(logb1/logb2),其中k=4,b1=10,b2=8 ；x最少为5

c.7个十进制数码转换为十六进制
x>=k*(logb1/logb2),其中k=7,b1=10,b2=16 ；x最少为6

15. 不进行转换，找出下面各个情况中在目标系统中所需的最少数码数量:

a.5位二进制数码转换为十进制
x>=k*(logb1/logb2),其中k=5,b1=2,b2=10 ；x最少为2

b.3个八进制数码转换为十进制
x>=k*(logb1/logb2),其中k=3,b1=8,b2=10 ；x最少为3

c.3个十六进制数码转换为十进制
x>=k*(logb1/logb2),其中k=3,b1=16,b2=10 ；x最少为4

19. 找出用于存储下列整数所需的最小位数 :
a. 小于1000
10
b. 小于100000
17

c. 小于64
6

d. 小于256
8



# 数据存储
## 练习题
1. 我们可以有多少不同的5位模式?
答： 2的5次方=32

2. —些国家的车牌有两个十进制数码(0〜9),我们可以有多少种不同的车牌?如果不允许使用数码0,又会有多少种不同的车牌?
答：10的平方=100种
9的平方=81种

3. 用2个数码跟3个大写字母(A〜Z)的车牌来重做上题。
答： 10的平方26的三次方等于1757600
9的平方26的三次方等于1423656

4. —个公司决定给每个员工分配唯一的位模式。如果该公司有900名雇员，构建该表示法的系统最少需要多少位?可分配多少位模式?如果再雇佣另外300名员工，系统需要增加位数吗?说明答案。
答： 2的n次方等于900，则n约等于10 最少需要10位
2的10次方=1024 可分配1024位模式
900+300=1200>=1024 所以需要增加1位为11位

5. 将下列十进制数转换成16位二进制补码表示法
a.102 b.-179 c.534 d.62 056
答： a: 102=(0000 0000 0110 0110)2
b: +179=(0000 0000 1011 0011)2
反码：(1111 1111 0100 1100)2
补码：(1111 1111 0100 1101)2

c. 534=(0000 0010 0001 0110)2
d. 62056不在（-32768，32767）之间

6. 下面是一些二进制补码表示的二进制数。请问如何改变它们的正负。
a.01110111 b.11111100 c.O111O111 d.11001110
答：a:1000 1001
b:0000 0100
c:1000 1001
d:0011 0010
（补码减1取反码）

16. 如果在一个数上应用二进制补码表示法转换两次，将会得到原数。在下面的数上试试看。
a.01110111 b.11111100 c.O1110100 d.11001110
答：a: 0111 0111----1000 1001----0111 0111
b: 1111 1100----0000 0100----1111 1100
c: 0111 0100----1000 1100----0111 0100
d: 1100 1110----0011 0010----1100 1110

24. 将下列8位二进制反码表示的数转换成十进制数
a.01110111 b.11111100 c.01110100 d.11001110
答：a: 0111 0111是正数，所以十进制数为64+32+16+4+2+1=119
b: 1111 1100 补码为1111 1101 为负数。原码为：0000 0011 正数，所以十进制数为：-3
c: 0111 0100 补码为0111 0101为正数。所以十进制为64+32+16+4=116
d: 1100 1110 补码为1100 1111 为负数。原码为0011 0001.所以十进制数为：-（32+16+1）=-49

25. 另一种求二进制补码的方法是首先转换成二进制反码表示法，然后把结果加1(二进制加法在第4章讲解)。试用两种方法转换下面的数，分析比较结果。
a.01110111 b.11111100 c.01110100 d.1100
答： a：0111 0111----1000 1001
0111 0111----1000 1000----1000 1001

b：1111 1100----0000 0100
1111 1100----0000 0011----0000 0100

c：0111 0100----1000 1100
0111 0100----1000 1011----1000 1100

d：1100----0100
1100----0011----0100



