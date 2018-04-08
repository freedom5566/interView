1. 試著使用class繼承另外一個class 

```php
<?php

class foo
{
    protected static $str="OOP";
}

class bar extends foo
{
    public function printItem()
    {
        echo 'Bar: ' . parent::$str . PHP_EOL;
    }
}


$bar = new bar();

echo $bar->printItem(); 

```

2. 用php印出九宮格

```php
<?php

echo "<table>";
    for($i=1;$i<=9;$i++){
        if($i==1){
            echo "<tr>";
        }
        
        echo "<td>".$i."</td>";
        if($i==3){
            echo "</tr>";
            echo "<tr>";
            
        }
        if($i==6){
            echo "</tr>";
            echo "<tr>";
        }
        if($i==9){
            echo "</tr>";
        }
    }
echo "</table>";
?>
```

3. get跟post的差別

有時候阿，我真的不知道出這種題目的人是想要甚麼答案，不如出個情境題，來問面試者該情況需要使用哪個