# reference

- https://www.cnblogs.com/xueda120/p/3575054.html
- https://blog.csdn.net/uytguytgf/article/details/125537357
- https://www.cnblogs.com/limojin/p/8331162.html

# 起头模板

- https://blog.csdn.net/idiot5lie/article/details/118650688

cin/cout要比scanf/printf慢一些（因为cin和cout是处理缓冲区的数据），尽可能使用scanf/printf以避免测试大量数据时因为输入输出慢而导致TLE。 putchar/getchar要比scanf/printf更快。

在调用 `ios::sync_with_stdio(false) `后，cout 与 stdout 不再共享同一块缓冲区，它们分别管理自己的缓冲区。简述，`ios::sync_with_stdio`函数作用为设置标准 C++ 流是否与标准 C 流在每次输入/输出操作后同步。正是因为这种同步，所以 cin、cout 比 scanf、printf 速度要慢，如果我们在使用 cin、cout 输入输出前加一句 `ios::sync_with_stdio(false)`，即取消缓冲区同步，可节省时间，效率与 scanf、printf 相差无几。

`std::cin::tie`是将两个stream绑定的函数，空参数的话返回当前的输出流指针。
std :: cin默认是与std :: cout绑定的，所以每次操作的时候都要调用fflush，这样增加了IO的负担，通过tie(nullptr)来解除std :: cin和std :: cout之间的绑定，进一步加快执行效率。

起头模板：

```cpp
# include<bits/stdC++.h>
using namespace std;
int main(void) {
	ios::sync_with_stdio(False);
	cin::tie(nullptr);
	...
	return 0;
}
```

# 数字输入输出cin/cout

# 字符串输入输出

# 数字输入输出scanf/printf

在线判决系统是机器判题系统，也就是俗称的OJ（Online Judge），机器判决的一个特点就是必须100%的吻合才能判为正确，否则要么WA,PE。同时对于提交的程序还有一定的时间限制，如果超过时间则会判超时。OJ一般采用的是标准输入输出，所以提交的时候我们不必要使用文件读入输出（这与高中的信息学是不同的），机器判决只针对程序结果，不针对程序，所以很多时候直接提交数据也是可以的，俗称打表。

1. 第一种（EOF判断停止）

   Input

   The input will consist of a series of pairs of integers a and b, separated by a space, one pair of integers per line.
   Output

   For each pair of input integers a and b you should output the sum of a and b in one line, and with one line of output for each line in input.
   Sample Input

   ```
   1 5
   10 20
   ```

   Sample Output

   ```
   6
   30
   ```

   ```cpp
   int main(void){
       int a=0;int b=0;
       while(~scanf("%d %d",&a,&b)){
           printf("%d\n",a+b);
       }

       return 0;

   }
   ```
2. 给定测试组数

```cpp
int main(void){
	int n = 0;
	scanf("%d",&n); 
	whlie(n--){ 
      		这里处理每一组输入.然后直接按格式输出,没必要开数组存储答案. 
  	} 
	return 0;

}  

```

3.以0或-1结束的输入.

```cpp
while(scanf("%d",&n),n!=0) {  
	处理每一组数据,并输出.
}
```

# 函数知识

## 1 scanf()/printf()函数

### 1.1 scanf()

- 原型：int scanf(const char *restrict format, ......);
- 入口参数：第一个参数是格式字符串，它指定了输入的格式，......格式化后的字符串存取地址。
- 返回值：函数返回值为int类型，如果读取到了“文件结束”则返回EOF，EOF为Ctrl+z或者Ctrl+d。其他情况则返回int型数字，例如：int res = scanf("%d %d",&a,&b); 如果a,b都读取成功，则返回2；如果a,b只读取成功了一个，则返回1；如果a,b都没有读取成功，则返回0。
- 说明：scanf()函数是C语言库中的函数，但由于C++ 的向下兼容性，所以在C++中也可以使用此函数。此函数是从标准输入流stdio（一般是键盘输入）中读取数据，并将其按照指定格式输入到指定地址。
- 头文件：#include <stdio.h>

  ```cpp
  #include <stdio.h>
  #include <iostream>
  using namespace std;

  int main()
  {
      int a,b;
      scanf("%d %d",&a,&b); //注意此处输入的格式，两个输入数字之间要以空格分隔开来。
      printf("%d %d",a,b);
      /*
      输入：
      1 2回车键
      输出：
      1 2
      */
  }
  ```

  ```
  \n 换行
  \t 制表符

  %d 表示整数  
  %f 表示浮点数（小数）  
  %lf 表示双精度浮点数  
  %c 表示一个字符  
  %s 表示一个字符串  

  %03d 表示用3位输出一个整数，不够三位用0补齐  
  //eg：使用%03d 输出3时，printf（“a：%03d \n”，a）；显示结果为003  
  %.2f 表示小数点后取两位，用于四舍五入  
  %1.3f 表示小数点前保留1位，小数点后保留3位
  ```

这里强调一下：网上很多文章都说 `%f` 和 `%lf`是一样的，即不管单精度，双精度浮点数，都可以用 `%f`, 但我在POJ上做过测试，输出Double时用 `%f`确实也可以 ，但读入时，用 `%f`就报WA，所以大家如果对Double进行读写的话，都用 `%lf`吧。说到Double，再啰嗦一句，建议大家要用到浮点数时都用Double，不要用float，因为在很多情况下，float精度不够会导致WA。
