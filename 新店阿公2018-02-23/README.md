工作內容是維護、開發兩套系統，分別是Java網頁跟C#(webform)網頁，未來三到五年要全面改成 ASP . NET MVC
***
### 印象中的題目
1. 寫出1~10總和程式

```c
#include<stdio.h>

int main(){
    int i=0;
    int sum=0;

    for(i;i<=10;i++){
        sum+=i;
    }
    printf("總和:%d\n",sum);
}
```

2. 承上題，改成遞迴

```c
#include<stdio.h>

int sum(int n){
    if(n<1){
        return 0;
    }
    else{
        return n + sum(n - 1);
    }
}

int main(){

    printf("總和:%d\n",sum(10));
}

```

3. get跟post有甚麼不一樣
```text
傳送私密資料時使用post較合適，get會直接把資料顯示在網址上
```


4. 下列同名函式如何判斷會執行哪個？
```java
    public static String someMethod(int i,string name,int sum) 
    { 
        return 1;
    }
 
    public static String someMethod(Integer integer)
    {
        return 2;
    }
```
```text
看傳遞的參數哪個符合就執行哪個
```

5. 甚麼是MVC
```text
M:用來設定對應資料表欄位，讓資料表欄位可以像物件一樣被使用
V:前端畫面顯示
C:看網址來決定使用哪個控制器執行當中的行為
```
說來汗顏，當初實習用Laravel的時候所有程式幾乎都塞在控制層，後來用ASP . NET MVC的時候有比較良好的規劃了，除了MVC三層以外還另外切出幾層來處理邏輯


6. 下列兩個表格如何取出每個公司業務總金額        

*company*
<table>
    <tr>
    <td>公司</td>
    <td>業務編號</td>
    </tr>
    <tr>
        <td>台北</td>
        <td>A</td>
    </tr>
    <tr>
        <td>台中</td>
        <td>B</td>
    </tr>
    <tr>
        <td>高雄</td>
        <td>C</td>
    </tr>
 </table>       

*business*
 <table>
    <tr>
    <td>業務</td>
    <td>金額</td>
    </tr>
    <tr>
        <td>A</td>
        <td>100</td>
    </tr>
    <tr>
        <td>B</td>
        <td>2000</td>
    </tr>
    <tr>
        <td>B</td>
        <td>900</td>
    </tr>
    <tr>
        <td>C</td>
        <td>100</td>
    </tr>
    <tr>
        <td>C</td>
        <td>1000</td>
    </tr>
    <tr>
        <td>A</td>
        <td>800</td>
    </tr>
 </table>

```sql
SELECT company.公司, SUM(business.金額)  
FROM company, business
WHERE company.業務 = business.業務
GROUP BY company.公司
```

<table>
    <tr>
    <td>公司</td>
    <td>金額</td>
    </tr>
    <tr>
        <td>台中</td>
        <td>2900</td>
    </tr>
    <tr>
        <td>台北</td>
        <td>900</td>
    </tr>
    <tr>
        <td>高雄</td>
        <td>1100</td>
    </tr>
 </table>

7. CRUD

* 找出Xindian表的企劃部在1914年購買了甚麼器材

```sql
SELECT * FROM Xindian WHERE 單位='企劃';
```         
* 請在Linkou表新增資訊部在1999-02-24購買價值3000的路由

```sql
INSERT INTO Linkou(單位, 價格, 器材, 購入日期) VALUES ('資訊部',3000,'路由','1999-02-24');
```

* 把Xindian表的業務部ipad器材價格更改成38000

```sql
UPDATE Xindian SET 價格=38000 WHERE 單位='業務';
```

* 把Linkou表1999-02-24資訊部那一列刪除

```sql
DELETE FROM Linkou WHERE `日期`='1999-02-24';
```

*Xindian*
<table>
    <tr>
    <td>xid</td>
    <td>單位</td>
    <td>器材</td>
    <td>價格</td>
    <td>日期</td>    
    </tr>
    <tr>
        <td>1</td>
        <td>企劃</td>
        <td>麥克筆</td>
        <td>50</td>
        <td>1914-11-10</td>
    </tr>
    <tr>
        <td>2</td>
        <td>業務</td>
        <td>ipad</td>
        <td>42000</td>
        <td>1938-04-23</td>
    </tr>
    <tr>
        <td>3</td> 
        <td>行政</td>
        <td>A4夾</td>
        <td>10</td>
        <td>2017-6-10</td>
    </tr>
 </table>

*Linkou*

<table>
    <tr>
    <td>lid</td>
    <td>單位</td>
    <td>器材</td>
    <td>價格</td>
    <td>日期</td>    
    </tr>
    <tr>
        <td>1</td>
        <td>人事部</td>
        <td>螢幕</td>
        <td>30000</td>
        <td>1999-01-10</td>
    </tr>
    <tr>
        <td>2</td>
        <td>研發部</td>
        <td>達靈頓電晶體</td>
        <td>400</td>
        <td>1978-03-23</td>
    </tr>

 </table>

這題我看了頗多次，有兩個表格，可是沒考連結，不太懂用兩個表格的用意是甚麼，應該就是簡單的CRUD吧......

***

無聲卡QQ
