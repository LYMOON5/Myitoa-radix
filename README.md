#include<stdio.h>

void Reverse(char *str)//字符串逆置 
{
	char *p = str;
	while(*p != '\0')
	{
		p++;
	}

	char tmp;
	for(p--;str < p;str++,p--)
	{
		tmp = *p;
		*p = *str;
		*str = tmp;
	}
}

//考虑到进制的itoa
void Myitoa(int num,char *str,int radix)
{
	char chars[] = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";//每个都映射到下标 
	int i = 0;
	do
	{
		str[i++] = chars[num % radix];
		num /= radix;
	}while(num != 0);
	str[i] = '\0';

	Reverse(str);//调用逆置函数完成整型转换成字符串 
}

int main()
{
	char str[100];
	Myitoa(1234567,str,16);
	printf("str=%s\n",str);
	
	return 0;
}

