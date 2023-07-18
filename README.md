# C-p49-2-
C语言学习笔记 p49 字符串函数的使用和剖析(2)
#include<stdio.h>
#include<string.h>
//strcmp库函数函数模版:int strcmp(const char* str1, const char* str2)
int main()
{
    char* p1="abcdef";
    char* p2="sqwer";
    int ret=strcmp(p1,p2);
    printf("%d\n",ret);
    return 0;
}//p1>p2返回>0的数，p1=p2返回0，p1<p2返回<0的数(这是gcc编译器)


//实现my_strcmp
int my_strcmp(const char* str1,const char* str2)
{
    assert(str1 && str2);
    //比较过程
    while(*str1==*str2)
    {
        if(*str1=='\0')
        {
            return 0;//相等
        }
        str1++;
        str2++;
    }
    if(*str1>*str2)
        return 1;//大于
    else(*str1<str2)
        return -1;//小于
}
int main()
{
    char* p1="abcdef";
    char* p2="abqwe";
    int ret=my_strcmp(p1,p2);
    printf("ret=%d\n",ret);
    return 0;
}


int main()
{
    char arr1[5]="abc";
    char arr2[]-"hello bit";
    strcpy(arr1,arr2);
    printf("%s\n",arr1);
    return 0;
}//这样就会挂，因为这种不带n的字符串库函数是不受\0限制的
//长度受限制的字符串库函数:1.strncpy  2.strncat  3.strncmp

int mian()
{
    char arr1[5]="abc";
    char arr2[]="hello bit";
    //strncpy库函数原型:char* strncpy(char* strDest,const char* strSource,size_t count); count单位是字节
    strncpy(arr1,arr2,4);
    return 0;
}



int main()
{
    //strnccat原型和strncpy原型如出一辙
    char arr1[30]="hello";
    char arr2[]="world";
    strncat(arr1,arr2,3);
    printf("%s\n",arr1);
    return 0;
}//不管追加几个后面都补了一个\0
