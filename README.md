# C語言-程式筆記 (KeRong)  

![](https://i.imgur.com/Sas5LcP.gif)
<!--![](https://i.imgur.com/sKtp2HB.jpg)-->

<!--![](https://i.imgur.com/kApUvvh.gif)-->
## 概述  
**C語言**具有高效、靈活、功能豐富、表達力強和較高的[可移植性](https://zh.wikipedia.org/wiki/%E7%A7%BB%E6%A4%8D_(%E8%BB%9F%E9%AB%94) "移植 (軟體)")等特點，在[程式設計](https://zh.wikipedia.org/wiki/%E7%A8%8B%E5%BA%8F%E8%AE%BE%E8%AE%A1 "程式設計")中備受青睞，成為最近25年使用最為廣的程式語言[TIOBE Programming Community Index](https://www.tiobe.com/tiobe-index/)
，並且廣泛用於[系統軟體](https://zh.wikipedia.org/wiki/%E7%B3%BB%E7%BB%9F%E8%BD%AF%E4%BB%B6 "系統軟體")與[應用軟體](https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E8%BD%AF%E4%BB%B6 "應用軟體")的開發。
##### 推薦的編輯器：[Code::Blocks](https://www.codeblocks.org/)、[Visual Studio](https://visualstudio.microsoft.com/zh-hant/downloads/)、[Eclipse](https://www.eclipse.org/downloads/)  

## 資料型態  

|關鍵字 |型態 |位元組|   範圍  |格式化字串|
|:----:|:--:|:---:|:------:|:------:|
|bool  |布林 |  1  |<font color=Red>false</font> or <font color=Green>true</font>|%d|
|char  |字元 |  1  |-128 ~ 127|%c|
|short |短整數|  2 |-2^15^ ~ 2^15^-1|%hd|
|int   |整數 |  4  |-2^31^ ~ 2^31^-1|%d|
|long long|長整數|  8 |-2^63^ ~ 2^63^-1|%lld|
|float |單精度浮點|  4  |2.939x10^−38^ ~ 3.403x10^38^|%f|
|double|雙精度浮點|8|5.563x10^309^ ~ 1.798x10^308^|%lf|

## 運算子  

### 算術運算子  
| 運算子名稱 | 語法 | 運算子名稱 | 語法  |
|:-:|:-:|:-:|:-:|
| 一元正號 | +a | 一元負號 | -a  |
| 加法 | a + b | 減法 | a - b  |
| 乘法 | a * b | 除法 | a / b  |
| 前置遞增 | ++a | 後置遞增 | a++  |
| 前置遞減 | - - a | 後置遞減 | a - -  |
| 以( )賦值 | a(運算)= b | 取餘 | a % b  |

**預防除零** n=123/float(a) -> a如果是0  (非法的運算)  
n所定義的資料型態為int，會是INT_MIN  
n所定義的資料型態為浮點數↓  
&nbsp;**1.#INF00**表示**無窮大的正數**(float)  
**-1.INF00**表示**無窮大的負數**(float)  
### 比較運算子  
| 運算子名稱 | 語法 | 運算子名稱 | 語法  |
|:-:|:-:|:-:|:-:|
| 小於 | a < b | 小於或等於 | a <= b  |
| 大於 | a > b | 大於或等於 | a >= b  |
| 不等於 | a != b | 等於 | a == b  |
| 邏輯取反 | !a | 邏輯 AND | a && b  |
| 邏輯 OR | a \|\| b | 　 | 　  |

### 位元運算子  
| 運算子名稱 | 語法 | 運算子名稱 | 語法  |
|:-:|:-:|:-:|:-:|
| 位元左移 | a << b | 位元右移 | a >> b  |
| 位元 OR | a \| b | 位元 AND | a & b  |
| 位元一的補碼 | ~a | 位元 XOR | a ^ b  |

透過**位元運算子**取代**算術運算子**
- a % 2^n^ = a & (n-1)
- a + b = a^b + (a & b) << 1
- a / 2^n^ = a >> n
- A * 2^n^ = A << n
### 其他運算子  
| 運算子名稱 | 語法 | 運算子名稱 | 語法  |
|:-:|:-:|:-:|:-:|
| 陣列下標 | a\[b\] | 函數呼叫 | a()  |
| 取址 | &a | 取值 | *a  |
| 成員 | a.b | 成員指標 | a->b  |
| 逗號 | a , b | 三元條件 | a ? b : c  |


## 註解 (用來說明程式的含意)  
- <font color=Red>/* </font> something <font color=Red>*/</font>   圍繞的文字會被電腦略過，跨行註解
- <font color=Red>//</font>             兩個正斜線的單行註解
## 簡單的範例程式碼  

```c
#include<stdio.h>   //輸入輸出函式庫
int main(){         //程式執行完回傳一個整數值
    int n;          //整數型態n
    scanf("%d",&n); //將鍵盤輸入至stdin的資料，依整數型態存入n
    printf("%d",n); //依整數型態，印出n
    return 0;       //程式完成回傳0，通常0表示程式未發生錯誤
}
```

## 基本結構  

### 選擇結構  
```c
if(條件){        //優先判斷
    actions;
}
else if(條件){   //次依判斷
    actions;
}
else{           //其餘條件
    actions;
}
```
### 重複結構  
```c
/*=======<for>===========*/
for(int x=0;x<10;x++){
    actions;
    if(x==5){
        continue;        //條件成立，單純跳脫x==5的迴圈
    }
}
/*=======<while>===========*/
int n=0;
while(n<10){
    actions;
    if(n==5){
        break;          //條件成立，當x==5直接停止迴圈
    }
    n+=1;
}
/*=======<do while>===========*/
do {                    //先做再判定條件
  statement;
} while (condition);
```
### 多重選擇結構  
```c
switch (value){
    case 1:            //當value==1做
        actions
        break;
    case 2:            //當value==2做
        actions
        break;
    default:           //其餘狀況
        actions
        break;
}
```
## GCC(GNU Compiler Collection)
- gcc -o test.exe test.c//產生executable file
- gcc test.exe <input.txt> out.txt//輸出結果到out.txt
- gcc -E test.c //查看預處理結果
## 常見標頭檔 [C standard library](https://cplusplus.com/reference/clibrary/)  
```c
#include<stdio.h>　　　　 //定義輸入、輸出函式
#include<stdlib.h>　　　　//定義雜項函式及記憶體分配函式
#include<string.h>　　　　//字串處理
#include<ctype>          //定義字元分類函式
#include<limits.h>　　　　//定義各種資料型別最值的常量
#include<math.h>　　　　　//定義數學函式
#include<stdbool.h>      //定義bool類型資料(C99)
#include<iso646.h>       //定義位元和邏輯運算子巨集
```
#### #include <filename.h>和#include "filename.h"區別  
#### <filename.h> 編譯器先從標準庫路徑開始搜索文件名.h，使得系統文件調用較快  
####  "filename.h" 先從用戶的路徑開始尋找文件名，然後去尋找系統路徑，使得尋找自定義文件較快  

## <stdio.h> (定義輸入、輸出函式)  
|標識符 |說明|
|:----:|:------:|
|stderr|標準錯誤流|
|stdin |標準輸入流|
|stdout|標準輸出流|
### Marcos 巨集  
```c
#define true 1                         //定義true=1
#define max(a,b) ((a>=b)?a:b)          //三元運算取最大值
/*====<可以透過'\'來分段編寫macro>===*/
#define swap(a,b){\
    int temp=a;\
    a=b;\
    b=temp;\
}
#define STR(s) #x                      //將STR(x)內轉形成字串
#define COMBINESTR(x,y) x##y           //串接xy(數字)
#define makechar(x) #@x                //轉成字元
#define max(a, b)     \                //取最大值(根據資料型態決定)
{(typeof(a) _a = a;   \
  typeof(b) _b = b;   \
  _a > _b ? _a : _b;) \
}
#define swap(a,b){\                     //兩數交換(快速且不會overflow)
    a=a^b;\
    b=a^b;\
    a=a^b;\
}
/*======<格式化輸出>=======*/
void is_int(int x) { printf("%d\n", x); }
void is_char(char x) { printf("%c\n", x); }
void is_string(char *x) { printf("%s\n", x); }
void is_double(double x) { printf("%f",x);}
void is_float(float x) {printf("%f\n",x);}
#define print(X)\
    _Generic((X),\                //_Generic選擇
    int:is_int,\
    char:is_char,\
    char *:is_string,\
    double:is_double,\
    default:is_float\
    )(X)
```
### EOF (通常為-1)  
- End-of-File 以指示已到達文件結尾或指示其他一些失敗條件  
### NULL (通常為0)  
- 空指針常量  
### BUFSIZ (設置流緩衝區)  
```c
void setbuf ( FILE * stream, char * buffer );
int setvbuf(FILE * stream,   char   * buf,   int type,   unsigned size);
```
- _IOFBF (滿緩衝)：當緩衝區為空時，從流讀入資料。或當緩衝區滿時，向流寫入資料。  
- _IOLBF (行緩衝)：每次從流中讀入一行資料或向流中寫入—行資料。  
- _IONBF(無緩衝)：直接從流中讀入資料或直接向流中寫入資料，而沒有緩衝區。  
### Formatted input/output:  
#### printf (用於將格式化後的資料輸出到標準輸出)  
```c
int printf(const char * restrict format, ...)//正確返回輸出的字元總數，錯誤返回負值
printf("%[格式][最小寬度][.精度][類型長度]");
setbuf(stdout,NULL);          //清空緩衝區
setvbuf(stdout,NULL,_IOFBF,0);//清空緩衝區
```
- %c：以字元方式輸出
- %s：字串輸出
- %d：以10進位整數輸出
- %f：浮點數輸出
- %o：以8進位整數方式輸出
- %u：無號整數輸出
- %x：將整數以 16 進位方式輸出
- %e：使用科學記號顯示浮點數
- %g：浮點數輸出，不輸出無意義的0
- %lu：long unsigned 型態的整數
- %p：指標型態
- %%：輸出%
- \n：換行。將游標移到下一行起始點
- \t：將游標移到下一個tab定位點
- \a：警告。讓系統發出警告聲
- \\"：輸出"
- \\\：輸出\
- %5d：默認向右對齊,左邊補空格
- %-5d：向左對齊,右邊補空格
- %+d：輸出正負號
- % d：正號用空格替代，負號輸出-
- %06d：左邊不足以0替代
- %0*d,6：(延伸上面)左邊不足以0替代
- %.8f：超過精度，截斷
- %.8f：不足精度，補後置0
```c
/*==========<三元運算子>=========*/
printf("%d", 1 > 0 ? 1 : 0);    
printf(1 < 0 ? "%d" : "%c", 65);
/*=========<輸出由右至左推>======*/
int a=1; 
printf("%d %d %d %d %d %d\n",a++, ++a, a++, ++a, a++, ++a );//6 7 4 7 2 7
```
#### sprintf (發送str指向一個字串的格式化輸出)  
```c
int sprintf ( char * str, const char * format, ... );
example:
char s[99]={'\0'};                //存放位置
sprintf(s,"%d",123);              //存放123至陣列s
sprintf(s, "%.2f", (double)100);  //100強制轉型double並存放至陣列s
```
#### snprintf (比sprintf多了一個參數，能控制要寫入的長度，更加安全)  
```c
int snprintf ( char * str, size_t size, const char * format, ... );
example:
char s[99]={'\0'};            //存放位置
snprintf(s,2,"%d",123);       //存放12至陣列s
```

#### scanf (格式化的輸入)  

```c
int scanf ( const char * format, ... );//不安全函數，會有overflow狀況
1.成功讀入(回傳1)
2.非指定格式讀入(回傳0)
3.讀入EOF(回傳-1)
scanf("%[*][輸入數據寬度][類型]");
1.遇空格、換行、跳格鍵(停止)
2.遇寬度結束(停止)
3.遇不正常輸入(停止)
```
- %c：讀入1個字元
- %(數量)c：讀入(數量)個字元
- %s：讀入字串(空白、換行中斷)
- %d：讀入10進位整數
- %i：讀入10進位，8進位，16進位整數 
- %o：讀入8進位整數
- %x：讀入16進位整數
- %f：讀入浮點數
- %lf：讀入雙精確(double)浮點數
- %%：讀入%
- %p：讀入一個指標
- %u：讀入無符號10進位整數
- %n：至此已讀入的字元數
- %*(數量)(類型)：讀取(數量)(類型)，直接忽略，不存
- %[]：掃描字符集合(a-z,A-z,0-9,'\n')
- %(數量)[]：掃描(數量限制)字符集合
- %[^]：掃描非字符集合
- %*[^=]：掃描非字符集合，並且不保存，而這時會存下'='
- %*[^=]=%s：掃描非字符集合，並且不保存，而這時會存下'='後面的字串
- %[^\n]%*c：整行讀入
```c
假設測資是a=3,b=2,c=3
scanf("a=%d,b=%d,c=%d",&a,&b,&c);           //非格式化存入資料
scanf("%80[a-z | A-Z | 0-9|,.-]", address); //80個指定字元讀入
```
#### sscanf (從s讀取數據並依格式將它們存儲到位置)  
```c
int sscanf ( const char * s, const char * format, ...);
example:
char sentence []="KeRong is 18 years old";
char str [20];
int i;
sscanf (sentence,"%s %*s %d",str,&i);
printf ("%s -> %d\n",str,i);//KeRong -> 12 
```
### Character input/output:  
#### getchar (從標準輸入獲取字元)  
```c
int getchar ( void );//返回的是獲取ascii值，錯誤回傳-1
example:
do{
    c=getchar();
    putchar(c);
}while (c != '\n');
```
#### gets (從標準輸入讀取字串並將它們儲到 str 中，直到到達換行符或文件結尾)  
```c
char * gets ( char * str );//成功返回該字串，不成功返回(null)
example:
char string [256];
gets(string);        //123abc
printf("%s",string); //out:123abc
```
#### putchar (將一個字元寫入標準輸出)  
```c
int putchar ( int character );//回傳ascii值，錯誤則回傳EOF(-1)
example:
char c;
for (c = 'A' ; c <= 'Z' ; c++){
    putchar(c);        //印書A~Z
}
```
#### puts (將str字串寫入標準輸出，並附加一個換行符'\n')  
```c
int puts ( const char * str );//成功回傳一個非負整數，錯誤回傳EOF(-1)
example:
char string [] = "Hello world!";
puts(string);
```
## <stdlib.h> (定義雜項函式及記憶體分配函式)  
### 數據類型  
| 名字 | 描述 |
| --- | --- |
| size_t | 算子sizeof返回結果的數據類型，實際上是無符號整數|
| div_t、ldiv_t、lldiv_t| 函數div、ldiv、lldiv的返回結果的數據類型，包含兩個整數的結構類型 |


### String conversion   
| 名字 | 描述 |
| :-: | --- |
| atof | 把字串轉換為雙精度浮點數|
| atoi | 把字串轉換為整數|
| atol | 把字串轉換為長整數|
| atoll | 把字串轉換為長長整數|
| strtod | 把字串轉換為雙精度浮點數，檢查結果是否溢出，並返回字串不能轉換部分的地址 |
| strtof | 把字串轉換為單精度浮點數，檢查結果是否溢出，並返回字串不能轉換部分的地址 |
| strtold | 把字串轉換為長雙精度浮點數，檢查結果是否溢出，並返回字串不能轉換部分的地址 |
| strtol | 把字串轉換為長整數，檢查結果是否溢出，並返回字串不能轉換部分的地址. |
| strtoll | 把字串轉換為長長整數，檢查結果是否溢出，並返回字串不能轉換部分的地址. |
| strtoul | 把字串轉換為無符號長整數，檢查結果是否溢出，並返回字串不能轉換部分的地址. |
| strtoull | 把字串轉換為無符號長長整數，檢查結果是否溢出，並返回字串不能轉換部分的地址|

### Dynamic memory management  
#### malloc (動態內存分配，其內容不初始化)  

```c
void* malloc (size_t size);
example:
/*=======<一維>========*/
int *array=(int *)malloc(n*sizeof(int));//等同int array[n];
/*=======<二維>========*/
char **sentence=(char **)malloc(row*sizeof(char *));
for(int y=0;y<row;y++){
    sentence[y]=(char *)malloc((column+1)*sizeof(char));//字串結尾'\0'
}
```

#### calloc (數組的動態內存分配，且初始化為全零)  

```c
void* calloc (size_t num, size_t size);
example:
/*=======<一維>========*/
int *array=(int *)calloc(n,sizeof(int));//等同int array[n]={0};
/*=======<二維>========*/
char **sentence=(char **)calloc(row,sizeof(char *));
for(int y=0;y<row;y++){
    sentence[y]=(char *)calloc((column+1),sizeof(char));//字串結尾'\0'
}
```
#### realloc (釋放舊動態內存，按照給的尺寸分配新的動態內存，舊的內存塊的內容儘量複製到新的內存)  
```c
void* realloc (void* ptr, size_t size);//新位址與舊位置並不保證相同
example:
int input;
int count = 0;
int* numbers = NULL;
int* more_numbers = NULL;
while(scanf("%d",&input)!=EOF && input){//輸入0停止
    count+=1;
    more_numbers=(int *)realloc(numbers,count*sizeof(int));
    numbers=more_numbers;
    numbers[count-1]=input;
}
for (int x=0;x<count;x++){
    printf ("%d ",numbers[x]);    //印出資料
}
free (numbers);
/*========<字串>=====*/
char *str=(char *)malloc(15*sizeof(char));
strcpy(str,"Hello ");
char *new_str=(char *)realloc(str,25*sizeof(char));
str=new_str;
strcat(str,"world");
printf("%s",str);//Hello world
free(str);
```
#### free (系統釋放動態分配的內存，如果是空指針，則無動作發生)  

```c 
void free (void* ptr);
example:
int *array=(int *)malloc(99*sizeof(int));
free(array);
```
### Searching and sorting  

#### bsearch (二元搜索)  

```c
void* bsearch (const void* key, const void* base,
               size_t num, size_t size,
               int (*compar)(const void*,const void*));
example:
int cmp(const void *a,const void *b)
{
  return (*(int*)a - *(int*)b);
}
int list[6]={50,20,60,40,10,30};
int main(){
    int key=40;
    qsort(list,6,sizeof(int),cmp);
    int *search=(int*)bsearch(&key,list,6,sizeof(int),cmp);
    if(search!=NULL){
        printf("%d is in the array.\n",*search);
    }
    else{
        printf("%d is not in the array.\n",key);
    }
    return 0;
}
```

#### qsort(快速排序)  

```c
void qsort (void* base, size_t num, size_t size,
            int (*compar)(const void*,const void*));
example:
int cmp(const void *a,const void *b)
{
  return (*(int*)a - *(int*)b);
}
int main(){
    int list[6] = { 50, 20, 60, 40, 10, 30};
    qsort(list,6,sizeof(int),cmp);
    for(int x=0;x<6;x++){
        printf("%d ",list[x]);
    }
    return 0;
}
```

### Integer arithmetics  

|名字|描述|
|:-:|:-:|
| abs、labs、llabs| 計算整數的絕對值|
| div、ldiv、lldiv | 計算整數除法的商與餘數 |
- int quot; // quotient(商數)
- int rem; &nbsp;// remainder(餘數)
- div_t (int Numerator, int Denominator);

```c
div_t divresult;
divresult = div (38,5);
printf ("quot = %d,rem = %d\n", divresult.quot, divresult.rem);//quot = 7,rem = 3
```

## <string.h> (字串處理)  
### Copying  
#### memcpy (str2複製n個字元到儲存到str1，記憶體區域不能重疊)  
```c
void *memcpy(void *str1, const void *str2, size_t n);
example:
struct {
    char name[40];
    int age;
} person, person_copy;
int main (){
    char myname[] = "KeRong";
    memcpy(person.name,myname,strlen(myname)+1);
    person.age=18;
    memcpy(&person_copy,&person,sizeof(person));
    printf("person_copy: %s, %d \n",person_copy.name,person_copy.age);
    return 0;
}
/*=======<從第幾個字元複製>========*/
char s[]={"kerong krameri120 hello"};
char d[20];
memcpy(d, s+7,10);
//memcpy(d,s+7*sizeof(char),10*sizeof(char));
d[10]='\0';
printf("%s", d);//krameri120
```
#### memmove (str2複製n個字元到儲存到str1，記憶體區域能重疊，比memcpy安全)  
```c
void * memmove ( void * destination, const void * source, size_t num );
example:
char str[]="memmove can be very useful......";
memmove(str+20,str+15,11);
puts(str);//memmove can be very very useful.
```
#### strcpy (把src所指向的字串複製到dest，dest不夠大會有溢出狀況)  
```c
char * strcpy ( char * destination, const char * source );
example:
char str[40];
char str1[]="Sample string";
strcpy (str,str1);
puts(str);//Sample string
```
#### strncpy (把src所指向的字串複製到dest，最多複制n個字元)
```c 
char * strncpy ( char * destination, const char * source, size_t num );
example:
char str1[]= "To be or not to be";
char str2[40];
char str3[40];
strncpy(str2,str1,sizeof(str2));
strncpy(str3,str2,5);
str3[5] = '\0';
puts(str1);//To be or not to be
puts(str2);//To be or not to be
puts(str3);//To be
```

### Concatenation  
#### strcat (src指向結尾的字串的字串附加到指向dest)  
```c
char * strcat ( char * destination, const char * source );
example:
char str[80]={"String are "};
strcat(str,"concatenated.");
puts(str);//String are concatenated.
```
#### strncat (追加src指向字串結尾的字串到dest指向最多n個字元長)  
```c
char * strncat ( char * destination, const char * source, size_t num );
example:
char str1[20]={"To be "};
char str2[20]={"or not to be"};
strncat(str1, str2, 6);
puts(str1);//To be or not to be
```

### Comparison  

|返回值|表示|
|:-:|:-:|
|<0|str1<str2|
|=0|str1=str2|
|>0|str1>str2|

- 根據ascii比較字元大小  

#### memcmp (把ptr1和ptr2的前n個字元進行比較)  
```c
int memcmp ( const void * ptr1, const void * ptr2, size_t num );
example:
int n=memcmp(str1, str2, 5);
```
#### strcmp (把str1和str2進行比較)  
```c
int strcmp ( const char * str1, const char * str2 );
example:
int n=memcmp(str1,str2);
```
#### strncmp (把str1和str2的前n個字元進行比較)  
```c
int strncmp ( const char * str1, const char * str2, size_t num );
example:
int n=memcmp(str1,str2,5);
```

### Searching  
#### memchr (搜索str指向字串的前n個字元中第一次出現的字元c)  
```c
const void * memchr ( const void * ptr, int value, size_t num );
example:
char str[] = "Example string";
char *search=(char*)memchr(str,'p',strlen(str));
printf("%d",search-str);//4
```
#### strchr (搜索str指向字串第一次出現的字元c) 
```c
const char * strchr ( const char * str, int character );
example:
char str[] = "Example string";
char *search=strchr(str,'s');;
printf("%d",search-str);//8
```
#### strrchr (搜索str指向字串最後一次出現的字元c)
```c
const char * strrchr ( const char * str, int character );
example:
char str[] = "kerong krameri120";
char *search=strrchr(str,'r');;
printf("%d",search-str);//12
```
#### strpbrk (str1中找出最先含有str2中任一字元的位置) 
```c
strpbrk -> string pointer break
const char * strpbrk ( const char * str1, const char * str2 );
example:
char str[] = "This is a sample string";
char key[] = "aeiou";
char *search=strpbrk(str,key);
printf("%d",search-str);//2(i)
```
#### strspn (str1連續有幾個字元都含字串str2中的字元)  
```c
size_t strspn ( const char * str1, const char * str2 );
example:
char strtext[] = "12s9th";
char cset[] = "1234567890";
int i=strspn(strtext,cset);
printf("%d\n",i);//2
```
#### strcspn (str1連續有幾個字元都不含字串str2中的字元)  
```c
strcspn -> complementary span
size_t strcspn ( const char * str1, const char * str2 );
example:
char str[] = "fcb7a3";
char keys[] = "1234567890";
int i=strcspn(str,keys);
printf("%d\n",i);//3
```
#### strstr (找到第一次出現在str1字串中的str2字串)  
```c
const char * strstr ( const char * str1, const char * str2 );
example:
char str[] ="a simple b simple";
char *search=strstr(str,"simple");
printf("%d",search-str);//2
strncpy(search,"sample",6);
search=strstr(str,"simple");//again
printf("%d",search-str);//11
```
#### strtok (分解字串str為一組字串，delim為分隔符)
```c
char * strtok ( char * str, const char * delimiters );
example:
char str[] ="- This, a sample string.";
char *pick;
pick=strtok(str," ,.-");
while(pick!= NULL)
{
    printf("%s\n",pick);
    pick=strtok(NULL, " ,.-");
}
/*
out:
This
a
sample
string
*/
```
### Other  
#### strlen (計算給定字串的長度)
```c
size_t strlen ( const char * str );
example:
char str[]= "kerong"; 
printf("Length:%d", strlen(str));//Length:6
```
#### memset (複製字元value到ptr指定字串num個字元)
```c
void * memset ( void * ptr, int value, size_t num );
example:
char str[] = "kerong krameri120";
memset(str,'-',6);
puts(str);//------ krameri120
```
## <ctype.h> (測試字元是否屬於特定的字元類別)  
|名字|描述|
|:-:|-|
| isalnum | 是否為字母數字  |
| isalpha | 是否為字母  |
| islower | 是否為小寫字母  |
| isupper | 是否為大寫字母  |
| isdigit | 是否為數字  |
| isxdigit| 是否為16進位數字|
| iscntrl | 是否為控制字元  |
| isgraph | 是否為圖形字元 |
| isspace | 是否為空格字元(包括制表符、回車、換行)等 |
| isblank | 是否為空白字元（包括水平制表符）|
| isprint | 是否為可列印字元|
| ispunct | 是否為標點  |
| tolower | 轉換為小寫  |
| toupper | 轉換為大寫  |


## <limits.h> (定義了整數類型的一些極限值)  

|name|value|name|value|name|value|
|:-:|:-:|:-:|:-:|:-:|:-:|
| CHAR_BIT | 8 |SCHAR_MIN|-128| SCHAR_MAX|127|
| CHAR_MIN | -128 | CHAR_MAX | 127 | UCHAR_MAX | 255 |
| SHRT_MIN | -32768 | SHRT_MAX | 32767 |USHRT_MAX | 65535 |
| INT_MIN | -2^31^ |INT_MAX | 2^31^ -1 | UINT_MAX | 2^32^ -1|
| LONG_MIN | -2^31^ |LONG_MAX | 2^31^ -1 | ULONG_MAX | 2^32^ -1|
| LLONG_MIN | -2^63^ | LLONG_MAX | 2^63^ -1 |ULLONG_MAX |2^64^ -1|
## <math.h> (定義數學函式)   
### Trigonometric functions
- #define PI acos(-1)  
- radian=degrees*PI/180.0  
- degrees=radian*180/PI  

| 函數原型 | 描述  |
|-|:-:|
| double sin(x)  | 正弦  |
| double cos(x)  | 餘弦  |
| double tan(x)  | 正切  |
| double asin(x) | 反正弦   |
| double acos(x) | 反餘弦   |
| double atan(x) | 反正切  |
| double atan2(y,x)|  反正切    |
| double sinh(x) | 雙曲正弦  |
| double cosh(x) | 雙曲餘弦  |
| double tanh(x) | 雙曲正切  |

### Exponential、Logarithmic、Power functions
| 函數原型 | 描述  |
|:-|-|
| double exp(x)  | 指數函數  |
| double sqrt(x) | 開平方根  |
| double cbrt(x) | 開立方根  |
| double log(x)  | 自然對數  |
| double log10(x)| 常用對數  |
| double pow(x,y)| 計算x^y^   |
| double hypot(a,b)|計算直角三角形斜邊長度|

### Rounding and remainder functions
| 函數原型 | 描述  |
|:-|-|
|double ceil(x)|上取整|
|double floor(x)|下取整|
|double round(x)|四捨五入|
|double trunc(x)|小數直接捨去|
|double fmod(x,y)|返回除以x/y的剩餘值|


### Other functions
| 函數原型 | 描述  |
|-|-|
|double fabs(x)|求浮點數的絕對值|
|double abs(x)|求整數的絕對值|
|double fma(x,y,z)|x * y + z (皆為double)|
## <stdbool.h> (包含四個用於布林型的預定義巨集)  

|name|value|
|:-:|:-:|
|bool|_Bool|
|true|1|
|false|0|
|__bool_true_false_are_defined|1|

## <iso646.h> (位元和邏輯運算子的巨集)  

|巨集|定義為|巨集|定義為|
|:-:|:-:|:-:|:-:|
|not|!|not_eq|!=|
|and|&&|or|\|\||
|and_eq|&=|or_eq|\|=|
|xor|^|xor_eq|^=|
|bitand|&|bitor|\||
|compl|~| | |

## Struct(結構)
```c
struct <結構型態名稱>{  
    <資料型態1> <欄位名稱1>；
    <資料型態2> <欄位名稱2>；
}；
example:
struct student{       //此結構為struct student
     int studenID;    //學號
     char name[20];   //姓名
};
```
- 使用結構變數和點號運算子 (.)
```c
struct student myclass;                       //定義myclass類別為struct student
scanf("%d%s",&myclass.studenID,myclass.name); //輸入學號和姓名到myclass
printf("%d %s",myclass.studenID,myclass.name);//輸出學號和姓名
```
- 使用指向結構變數的指標和箭號運算子(->)
```c
struct student *ptr=&myclass;                  //承接上面程式碼
printf("%d %s\n", ptr->studenID,ptr->name);    //輸出學號和姓名
//ptr->studenID 等於 (*ptr).studenID
```
## Typedef(自定義類型)
```c
typedef struct{  
    <資料型態1> <欄位名稱1>；
    <資料型態2> <欄位名稱2>；
}<結構型態名稱>；
example:
typedef sturct {
    char name[20];    //姓名
    int id;           //學號
    double score;     //成績
}studtype;            //studtype是結構型態的名稱
```
- 結構型態之變項宣稱與初值設定
```c
studtype stu1= {"kerong",38,80};
//利用自訂結構型態studtype宣稱結構變項stu1
//並設定結構變項stu1各欄位之初值
```
- 利用指定敘述以操作結構變項之內容
```c
stu1.name[] ="krameri120";
stu1.id = 30;
stu1.score = 85;
```
- 透過Dynamic Memory建立學生資料表
```c
typedef struct{
     int studenID;    //學號
     char name[20];   //姓名
}student;
int main(){
    student *data_sheet=(student *)malloc(10*sizeof(student));     //定義最大10名學生資料表
    for(int x=0;x<10;x++){
        scanf("%d%s",&data_sheet[x].studenID,data_sheet[x].name);   //輸入10名學生資料
    }
    for(int x=0;x<10;x++){
        printf("%d %s\n",data_sheet[x].studenID,data_sheet[x].name);//輸出10名學生資料
    }
    return 0;
}
```
## Union (聯合)
- union中可以定義多個成員，union的大小由最大的成員的大小決定。   
- union成員共享同一塊大小的內存，一次只能使用其中的一個成員。   
- 對某一個成員賦值，會覆蓋其他成員的值
```c
typedef union{
    <資料型態1> <欄位名稱1>；
    <資料型態2> <欄位名稱2>；
}<聯合型態名稱>；
/*
目的:
1.解決相同信息的困擾，避免重複代碼，提高程式碼的簡潔性
2.節省內存
*/
```
## Enum(列舉)
```c
typedef enum{ 
   <列舉值1>, 
   <列舉值2>,
}<列舉資料型態名稱>；
example:
typedef enum {//定義禮拜一到禮拜日所代表的值1~7
   Monday=1,Tuesday,Wedsday,Thursday,Friday,Saturday,Sunday
}day;         //結構名稱定義為day
int main(){
    day today;
    char str_day[][10]={" ","Monday","Tuesday","Wedsday",
                 "Thursday","Friday","Saturday","Sunday"};
    for(today=Monday;today<=Sunday;today++){
        printf("%d %s\n",today,str_day[today]);//依序輸出大小和星期
    }
    return 0;
}
```

