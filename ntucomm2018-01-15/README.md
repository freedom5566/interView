一半行政一半資訊(?)，到場面試的時候還有考行政庶務相關......

# Linux(指令題)

* 如何察看檔案權限看擁有者
```sh
$ls -al
```
* 請簡述如何更改資料夾底下所有檔案的權限和所屬群組
```sh
$sudo chgrp -R 你要更改的群組 目標資料夾
$sudo chomd -R 你要更改的權限 目標資料夾
```
# Apache
* 情境題        
    1. 今天有一個網站的根目錄是/testcomm，裏面的所有資料夾都開放外界瀏覽。若我們想要拒絕外界對於其底下X目錄的訪問，但開放X目錄底下的子目錄Y，也就是只有當我們使用網址`https://comm.ntu.edu.tw/X.Y`時可以瀏覽Y目錄的內容，但是`https://comm.ntu.edu.tw/X`會被禁止訪問，請問該怎麼設定
    ```
     <Directory "/testcomm/x">
        AllowOverride None
        Require all denied
    </Directory>

    <Directory "/testcomm/x/y">
        AllowOverride None
        Require all granted
    </Directory>
    ```
    抱歉那個X.Y那個我真的看不太懂......     

    2. 承上題，若我們想要限制IP 140.112.41以下往段才可以存取Y目錄，請問該怎麼設定
    ```
    <Directory "/testcomm/x/y">
        AllowOverride None
        Require all denied
        Require ip 140.112.41
    </Directory>
    ```

# PHP

* 請問sites-available和sites-enabled兩個資料夾扮演的角色有甚麼不同？

    sites-enabled就是指向sites-avaiable的連結，通常設置virtualHost會編輯sites-avaiable資料夾裡的文件。 


* 請簡述VirtualHost的概念及應用     

    可以把多個網域放在一個主機上，方便管理

上面兩題算PHP？？？？？？

* 情境題

    1. 若server裏有名為"comm"的session，我們想要印出comm裏面的內容，包含key跟value，請問程式碼該如何設計？
    ```php
    <?php
        var_dump($_SESSION["comm"]);
    ?>
    ```
    2. 如果我們想在一個表單欄位`<input>`裏面放置一個ssion變數的內容，但若該session內容是空值或NULL，則欄位內容預設為"No session"，在使用者隨時可以修改input的內容前提下，請問該欄位程式碼可以如何設計？ 

    ```html
    <input type="text"  value="<?php $_SESSION['comm']??"No Session"; ?>" />
    ```

    3. 今有三種材料A、B、C，金額分別是aa,bb,cc，只有經費K元的情況下，如何購買可以使材料的總個數最多？三種材料至少各一個，購買個數分別是a,b,c，若有多種解答請依規定找出最佳解：選a最大的;若a相同，選b最大的;若b相同，則選c最大的。 
    請寫一個函式，回傳一個陣列，此陣列放置a,b,c
    i.e.,function BestAssign(aa,bb,cc,K);
    ```php
    <?php
    //金額
    $a=rand(1,100);
    $b=rand(1,100);
    $c=rand(1,100);
    $k=rand(1,100);

    function BestAssign($aa, $bb, $cc, $K){
        //計算次數
        $asum=0;
        $bsum=0;
        $csum=0;

        //找出最便宜的東西
        $max=$aa;
        $min=$aa;
        if($max<$bb) $max=$bb;
        else if ($min>$bb)$min=$bb;
        if($max<$cc) $max=$cc;
        else if ($min>$cc)$min=$cc;

        if($K>($aa+$bb+$cc)){
            //三樣東西至少一次
            $K-=$aa;$asum++;
            $K-=$bb;$bsum++;
            $K-=$cc;$csum++;
            while($K>$min){
                if($min==$aa){
                    $K-=$aa;
                    $asum++;
                }
                elseif($min==$bb){
                    $K-=$bb;
                    $bsum++;
                }
                else{
                    $K-=$cc;
                    $csum++;
                }
            }
            $array=["a"=>$asum,"b"=>$bsum,"c"=>$csum];
            return $array;
        }
        else {
            return "你的錢不夠各買一個！";
        }
    }
        var_dump(BestAssign($a,$b,$c,$k));
    ?>

    ```

# SQL

* 情境題        
    1. 一個資料表(table)裏面有name,nickname兩個字串欄位，我們想要把所有內容包含"comm"的欄位一次抓出來，請問SQL部份該如何實作？ 
    e.g.,"hellocommhihihi"
    ```SQL
    SELECT * FROM table WHERE name LIKE "%comm%" OR nickname LIKE "%comm%";
    ```
    2. 若在php裏面執行mysql_query()卻回傳false，請問如何找出query執行問題的錯誤點？ 
    ```php
    echo mysql_errno().":".mysql_error();
    ```
    我的天阿=_=2018年PHP還有人用mysql擴充連資料庫

    3. (結合PHP)今有一會員系統使用一個資料表，該表總共有兩個欄位name,email，分別儲存名字和信箱，每個會員以信箱做區別。我們只提供一個php頁面給使用者註冊或者更改資料，在不保證會重複註冊的情況下，程式碼該怎麼設計才能使資料表裡面的會員都不會重複？

    一開始創資料表的時候設定email不能有重複值，PHP這邊取出資料後在對比一次有無重複值，沒有才能註冊

