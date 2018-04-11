1. 只宣告A=10跟B=3變數，讓他們交換
方法一：XOR運算(又是他)：
```php
<?php
    $a=10;
    $b=3;
    echo $a."|".$b.PHP_EOL;
    $a ^= $b;
    $b ^= $a;
    $a ^= $b;
    echo $a."|".$b.PHP_EOL;
?>
```
解說一下

10的二進位是1010        
3的二進位是0011

XOR的規則是只有一個位元為1的時候才會為1     
其他情況都是0

    $a ^= $b;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1010      
xor &nbsp;&nbsp;&nbsp;0011        
<p>------------------</p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A=1001

    $b ^= $a;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0011      
xor &nbsp;&nbsp;&nbsp;1001        
<p>------------------</p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;B=1010        

    $a ^= $b;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1001      
xor &nbsp;&nbsp;&nbsp;1010        
<p>------------------</p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A=0011

他們的二進位就被交換了！！神奇

接著轉回十進位      
A(0011)=0+0+ 1 * (2 * 1) + 1 * (2*0)=3      
B(1010)=1 * ( 2 * 2 * 2 ) + 1 * ( 2 * 1 )=10

方法二 ：

```php
<?php
    $a=10;
    $b=3;
    echo $a."|".$b.PHP_EOL;
    
    list($a, $b) = array($b, $a);
    
    echo $a."|".$b.PHP_EOL;
?>
```

方法三 ：減法（也是我現場用的方法QQ）

```php

<?php

    $a=10;
    $b=3;
    
    $a+=$b;
    $b=$a-$b;
    $a-=$b;
    echo $a.PHP_EOL.$b;
?>
```
2. 說出知道的nosql，請說明應用環境

MongoDB，由於nosql資料表欄位相當彈性應用環境，一般來說應該是用在資料巨量，然後不複雜的地方
比如IOT，不過nosql我相當缺少經驗，所以這題講不出甚麼所以然......

3. 請說明session跟cookie分別用處跟特性

cookie主要是作用在客戶端，這個部份我常常使用GitHub時可能開new issue，打到一半不小心按到上一頁，或是沒開分頁跑去逛別的庫，不管怎麼樣那打到一半的issue都不會消失XD
通常也蠻常拿來紀錄帳號密碼的吧，只是我都不會去使用這類功能，一方面覺得不安全，一方面也是因為這樣久了自己都把帳號密碼忘記了，然後可能換個瀏覽器或是電腦都忘光光

session的部份我以前主要是拿來驗證使用者身份，網頁可以透過驗證session來確認這個使用者是不是用戶，是的話就取出對應用戶的資料。 

我這兩邊經驗好少......

4. 請寫出1* 2+2*3+3....+n       
遞迴版
```php
<?php

function rsum($n){
    if($n>=2){
        return rsum($n-1)+$n*($n-1);
    }
    else{
        return 0;
    }
}
echo rsum(10);

?>
```
非遞迴

```php
<?php

function rsum($n){
    $sum=0;
    
    for($i=1;$i<$n;$i++){
        
        $sum+=($i+1)*$i;
        
    }
    return $sum;
}
echo rsum(10);
?>
```
非常有趣的一題XD我現場根本亂寫R        
5. 有沒有用過linux？有的話請寫出使用經驗

平常都有用Ubuntu，使用經驗的話是文書操作、休閒娛樂、寫程式都在Ubuntu，除非碰到一定要在windown上使用的事情，不過幾乎沒有，因為ubuntu也幾乎能做到，但有些東西在linux上的解決方案都特別搞剛就是了......就看願不願意花時間

6. 請寫出Left Join的語法，自由發揮
```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;
```


7. 說明建構子跟解構子，及運用方式       

進入一個class如果有function __construct()就先執行，沒有東西跑之後就執行__destruct()
寫原生PHP蠻常見的使用方式是拿來寫連線sql