# interView
:laughing: 紀錄一些面試碰到的問題

*主要是訂正問題和自我檢視*



***
* git指令介面無法顯示中文問題
```sh
vim .git/config
[core]下增加quotepath=false
```

* 縮排總是亂跳的問題        
這個選項是根據你打開的文件來猜測你的縮排是幾個空白，設成false
`"editor.detectIndentation":false`
        
*如果只有一個commit怎麼退回？*    
[stack](https://stackoverflow.com/questions/10911317/how-to-remove-the-first-commit-in-git/32765827#32765827 "stack")
