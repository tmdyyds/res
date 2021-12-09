#### 如何判断闰年

>能被4整除的大多是闰年；能被100整除而不能被400整除的年份不是闰年
>
>```
>if( (year%400==0 || year%100!=0) &&(year%4==0))
>    cout<<"It is a leap year";
>else
>    cout<<"It is not a leap year";
>```
>
>

​	

