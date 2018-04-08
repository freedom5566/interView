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
xor &nbsp;&nbsp;0011        
<p>------------------</p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A=1001

    $b ^= $a;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0011      
xor &nbsp;&nbsp;1001        
<p>------------------</p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;B=1010        

    $a ^= $b;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1001      
xor &nbsp;&nbsp;1010        
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

3. 請說明session跟cookie分別用處跟特性
4. 請寫出1* 2+2*3+3....+n
5. 有沒有用過linux？有的話請寫出使用經驗
6. 請寫出Left Jion的語法，自由發揮
7. 說明建構子跟解構子，及運用方式
