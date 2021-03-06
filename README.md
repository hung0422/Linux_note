# Linux

## 基礎指令
* 印出目前是哪個帳號
```
whoami
```
* 印出當前所在目錄
```
pwd
```
* 顯示當月月曆
```
cal
```
* Linux內建的操作手冊
```
man “指令名”
```
* 顯示指令說明
```
info “指令名”
```
* 簡潔說明
```
whatis “指令名”
```
* 指令自帶的help選項
```
“指令名” --help
```
* 操作手冊
```
man “指令名稱”
```

## 切換所在目錄 (cd)
* cd [目錄名稱]

| 範例     | 說明                 |
| ------------ | -------------------- |
| cd /         | 切換至根目錄         |
| cd /usr/lib/ | 切換至/usr/lib目錄   | 
| cd ~ 或 cd   | 切換至帳號的家目錄   |
| cd ..        | 切換至上層目錄       |
| cd ../../    | 切換至上上層目錄     |
| cd -         | 切換至上次所在的路徑 |
## 檢視目錄或檔案資訊 (ls)
* ls [目錄或檔案]

| 範例 | 說明                     |
| -------- | ------------------------ |
| ls -l    | 以詳細資訊方式顯示       |
| ls -d    | 顯示目錄本身             | 
| ls -a    | 顯示隱藏檔               |
| ls -h    | 以易懂的方式顯示檔案大小 |
| ls -r    | 反向排序顯示             |
| ls -S    | 依檔案大小排序顯示       |
| ls -t    | 依修改時間排序顯示       |
## 清除螢幕畫面 (clear、reset)
* 清除螢幕畫面(可以往上捲動)
```
clear
```
* 清除螢幕畫面(無法往上捲動)
```
reset
```

## 查詢指令操作歷史紀錄 (history)
* history [N]

| 範例     | 說明                             |
| ------------ | -------------------------------- |
| history      | 列出所有指令操作紀錄             |
| history 5    | 列出最近5筆指令操作紀錄          | 
| history -c   | 刪除全部紀錄                     |
| history -d 2 | 刪除編號2號的指令紀錄            |
| !!           | 執行上一個指令                   |
| !wh          | 執行上一個名稱為wh開頭的歷史指令 |
| !5           | 執行編號第5個指令紀錄            |
| -6           | 執行倒數第6個指令紀錄            |
## Shell萬用字元 (wildcard)
| 字元  | 功能                           | 範例 |
|:-----:| -------------------------------| --|
| *     | 比對0個以上任意字元            | c*　表示以c開頭的所有檔案/目錄  |
| ?     | 比對恰有一個任意字元         　| c??　表示以c開頭，且名稱長度為3個字元  |
| [ ]   | 比對一個括號內指定的字元       | file[159]　表示file1或file5或file9 |
| [ - ] | 比對在編碼順序範圍內的一個字元 | [0-9]　表示0至9之間任一個字元<br> [b-d]*　表示開頭為b或c或d的所有檔案/目錄 |
| [ ^ ] | 反向選擇 (黑名單)              | [^abc]　代表非a，b，c的其他任一個字元 |
| { , } | 以逗號為間隔進行列舉    | cp {*.txt,*.pdf} /tmp　表示將pdf及txt複製到/tmp |
## 新增目錄(mkdir)
* mkdir 目錄名稱
* 自動產生路徑串中尚未存在的目錄
```
mkdir -p
```

| 範例               | 說明                                |
| ---------------------- | ----------------------------------- |
| mkdir dir1             | 於當前目錄內建立dir1                |
| mkdir dir2 dir3        | 於當前目錄內同時建立2個目錄         | 
| mkdir /home/user1/dir4 | 使用絕對路徑建立目錄                |
| mkdir -p a/b/c/        | 若a及b及c原本都不存在，就必須使用-p |
## 刪除空目錄(rmdir)
* rmdir 目錄名稱
* 刪除指定目錄後，若它的上一層目錄也變成空目錄時，就會被刪除
```
rmdir -p
```

| 範例               | 說明                            |
| ---------------------- | ------------------------------- |
| rmdir dir1             | 使用相對路徑刪除空目錄dir1      |
| rmdir /home/user1/dir2 | 使用絕對路徑刪除空目錄dir2      | 
| rmdir dir3 dir4        | 同時刪除空目錄dir3與dir4        |
| rmdir -p a/b/c         | 一次刪除階層式空目錄(a , b , c) |
| rmdir d1/d2/d3         | 只會刪掉空目錄d3                |
| rmdir *                | 刪除當前目錄下的所有空目錄      |
## 新增檔案(touch) / 修改時間戳記
* touch 檔案名稱

| 範例                     | 說明                  |
| ---------------------------- | --------------------- |
| touch file1                  | 新增file1             |
| touch file2 file3 /tmp/file4 | 同時新增多個檔案      | 
| touch {1..3}.txt             | 新增1.txt 2.txt 3.txt |
* 更改檔案(目錄)被存取或修改的時戳

| 範例                    | 說明                             |
| --------------------------- | -------------------------------- |
| touch -t 201401020304 file1 | 將檔案時戳修改成 2014/01/02 3:04 |
| touch file1                 | 將檔案時戳改成當前時間           | 
| touch dir1                  | 將目錄時戳改成當前時間           |
## 刪除檔案或目錄(rm)
* rm 檔案(目錄)名稱
* 互動模式(interactive)，在刪除前會向使用者確認
```
rm -i
```
* rm 遞迴刪除
```
rm -r
```

| 範例   | 說明                                |
| ---------- | ----------------------------------- |
| rm file1   | 將file1刪除                         |
| rm -r dir1 | 將dir1目錄完整刪除                  | 
| rm *.txt   | 將當前目錄內附檔名為txt的檔案都刪除 |
## 複製檔案或目錄(cp)
* cp 來源… 目標

| 參數  | 說明                                                       |
| ------| ---------------------------------------------------------- |
| cp -r | 遞迴複製，用於目錄的複製                                   |
| cp -p | 連同檔案的屬性一起複製過去                                 | 
| cp -d | 若來源檔為連結檔的屬性(link)，則複製連結檔屬性而非檔案本身 |
| cp -i | 若目標檔已經存在時，複製前會向使用者確認                   |
| cp -u | 更新，若目標時間比較舊或不存在時，才會進行複製             | 
| cp -a | 相當於 -p -d -r 一起併用                                   |

| 範例             | 說明                                         |
| -------------------- | -------------------------------------------- |
| cp file1 file2       | 將file1複製成file2                           |
| cp -r dir1 dir2      | 若目錄dir2不存在，就將dir1複製為dir2<br> 若目錄dir2已存在，就把dir1複製到dir2內                  | 
| cp file1 /tmp/file2  | 複製file1到/tmp/ 內，並命名為file2           |
| cp -a dir1/ /tmp/    | 把dir1複製到/tmp/ 內，並保留屬性             |
| cp file1 file2 /tmp/ | 把file1及file2複製到/tmp/ 內                 | 
| cp -u file1 file3    | 當file3不存在或是比file1舊的時後才會進行複製 |
## 移動檔案或目錄(mv)
* mv 來源 目標

| 參數  | 說明                                     |
| ------| ---------------------------------------- |
| mv -i | 若目標檔已經存在時，移動前會向使用者確認 |
| mv -f | 強制直接覆寫                             | 
| mv -u | 更新，若目標時間比較舊才會覆寫           |
| mv -n | 不會覆寫已存在的檔案                     |
## 顯示檔案內容(cat)
* cat 檔案

| 範例     | 說明                                 |
| ------------ | ------------------------------------ |
| cat file1    | 顯示file1內容                        |
| cat -b file1 | 會顯示行號，僅針對非空白行做行號顯示 | 
| cat -n file1 | 會顯示行號，連同空白行也會有行號     |
## 顯示檔案頭尾內容(head / tail)
| 範例          | 說明                       |
| ----------------- | -------------------------- |
| head file1        | 預設會顯示前10行           |
| head -n 20 file1  | 顯示前20行                 | 
| head -n -40 file1 | 顯示除了最後40行外的所有行 |
| tail file1        | 預設顯示末10行             |
| tail -n 20 file1  | 顯示末20行                 | 
| tail -n +50 file1 | 顯示除開頭50行外的所有行數 |
## 分頁顯示檔案內容 (more / less)
| 按鍵     | 說明                 |
| ---------| -------------------- |
| Enter    | 向下翻一行           |
| 空白鍵   | 向下翻一頁           | 
| b        | 往回翻一頁           |
| :f       | 顯示出檔名及目前行數 |
| q        | 立刻結束             | 
| PageUp   | 向上(下)翻一頁       |
| PageDown | 向下翻一頁           |
| / 字串   | 往後搜尋字串         |
| ? 字串   | 往前搜尋字串         | 
| n        | 重複前一個搜尋       |
## 磁碟的用量(du)
* 以易懂的方式顯示大小
```
du -h [檔案/目錄]
```
* 總結顯示總用量
```
du -sh [檔案/目錄]
```
* 顯示每個項目的用量
```
du -ah [檔案/目錄]
```

## 檔案系統的用量(df)
* 顯示所有檔案系統的資訊
```
df
```
* 以易懂的方式顯示大小
```
df -h
```

## 計算字數(wc)
* wc [檔案]
* 計算行數
```
wc -l
```
* 計算字數
```
wc -w
```
* 計算byte數
```
wc -c
```

## 印出字串(echo)
* 印出test
```
echo test
```
* 印出test後不換行
```
echo -n test2 
```
* 印出環境變數PATH的值
```
echo $PATH
```

## 指令別名 (alias / unalias)
* 可用來用方便記憶的字串取代長指令
* 設定cl等同clear
```
alias cl=“clear” 
```
* 刪除cl的別名
```
unalias cl
```
* 查看目前所有的別名
```
alias 
```
## 搜尋檔案或目錄位置(locate)
* locate “檔名關鍵字”
* 尋找速度比翻硬碟快，但若未更新索引表，搜尋結果可能失真
  * 更新索引表 -> 以root身分執行 updatedb

| 範例         | 說明                                |
| ---------------- | ----------------------------------- |
| locate user1     | 在絕對路徑中出現user1字串的都會列出 |
| locate -b user1  | 基本檔名有出現user1字串的才會列出   | 
| locate -c user1  | 只顯示找到的數量                    |
| locate “*.img”   | 找副檔名為img的檔案                 |
## 尋找檔案位置(find)
* find [搜尋路徑]… [選項]… 字串

| 根據     | 用法                           | 說明 |
| -------- | -------------------------------| --|
| 名稱     | -name 檔名            | 檔名若是使用萬用字元則須使用引號  |
| 使用者   | -user 帳號<br> -group 群組 | 也可以用 -uid<br> 也可以用 -gid |
| 檔案類型 | -type f<br> -type d       | f表示為檔案<br> d表示為目錄 |
| 時間     | -mtime 4<br> -mtime +4 <br> -mtime -4<br> -newer file1 | 4天前當天被更動過<br> 4天前(不含第4天)內被更動過<br> 4天內被更動過<br> 比 file1 還要新的 |
| 檔案大小 | -size [+-]SIZE<br> -empty  | c代表byte，k代表KB，M代表MB，G代表GB<br> 空的檔案或目錄 |
| 搜尋深度 | -maxdepth N  | 進入指定目錄下層目錄時，最深不超過N層 |

| 範例                            | 說明                                 |
| ----------------------------------- | ------------------------------------ |
| find /lib/ -name “java”             | 找出/lib/目錄(及子目錄)內的java      |
| find /lib/ -maxdepth 1 -name “java” | 搜尋/lib/目錄(不含子目錄)內的java    | 
| find /bin/ -size +500k              | 列出/bin/內大於500KB的檔案或目錄     |
| find . -empty -type f               | 列出當前目錄下的空檔案               |
| find /boot/ -type d                 | 列出/boot/內所有目錄                 |
| find /bin/ -name “??”               | 列出/bin/內名稱為2個字元的檔案或目錄 |
## exec
* 利用find找出大量目標後，想要直接套用某個指令
* 找出所有大於500MB的檔案並刪除
```
find / -size +500M -exec rm {} \;
```
* 將 /tmp(及子目錄)內找到的*.txt複製到家目錄內
```
find /tmp/ -type f -name “*.txt” -exec cp {} ~ \;
```

## 輸出資料流
| 符號 | 說明                                       |
|:----:| ------------------------------------------ |
| >    | 重導stdout，覆蓋掉原始檔案內容             |
| >>   | 重導stdout，附加在原始檔案內容後端         | 
| 2>   | 重導stderr，覆蓋掉原始檔案內容             |
| 2>>  | 重導stderr，附加在原始檔案內容後端         |
| &>   | 重導stderr與stdout，並覆蓋掉原始檔案內容   |
| &>>  | 重導stderr與stdout，附加在原始檔案內容之後 |

| 範例                          | 說明                            |
| ----------------------------- | ------------------------------- |
| history > a.txt               | 將歷史紀錄寫入a.txt             |
| echo “Mary” >> login.txt      | login.txt檔案最後一行新增“Mary  | 
| 指令 2> /dev/null             | 錯誤訊息導向至/dev/null         |
| 指令 &>> log.txt              | 正確及錯誤結果都會附加至log.txt |
| 指令 >correct.log 2>error.log | 兩種結果分開儲存                |
## 管線(pipe)
* 把前一個指令的stdout拿來當做後一個指令的stdin
* 把history的結果進行分頁顯示
```
history | less
```
* 計算前10行的行數/字數
```
head /etc/passwd | wc
```

## 產生序列數字
* seq 起始值 [累加值] 結束值
* 產生1,2,3…,10
```
seq 1 10
```
* 產生01,03,05,07,09,11
```
seq -w 1 2 11
```

## 排序(sort)
| 參數             | 說明                           |
| ---------------- | ------------------------------ |
| sort -r          | 反向(由大到小)排序             |
| sort -n          | 以數值由小到大排序             | 
| sort -M          | 以月份排序                     |
| sort -f          | 忽略大小寫的差異               |
| sort -u          | 排序並過濾重複的資料           | 
| sort -t 分隔字元 | 指定排序時所用的欄位元分隔字元 |
| sort -k 數字     | 以第幾個欄位來排序             |

| 範例               | 說明                       |
| ------------------ | -------------------------- |
| sort file1         | 字典順序，100 會排在94前面 |
| sort -n file1      | 數值順序，94 會排在100前面 | 
| sort -n -k 2 file1 | 以第2筆欄位數值排序        |
## 檔案分割(split) 與合併(cat)
* 先產生範例檔案
```
seq 1 99 > demo.txt
```
* 對檔案分割
```
 split -l 30 demo.txt
```
* 檔案內容上下合併
```
cat xaa xab > demo2.txt
```

## 檔案內容左右合併 (paste / join)
* a.txt

| Tom  | 100 |
| ---- | --- |
| Mary | 89  |
| Jojo | 60  | 
* b.txt

| Tom  | A |
| ---- | - |
| Mary | B |
| Jojo | D |
| Jan  | F |

* ```pasta a.txt b.txt```

| Tom  | 100 | Tom  | A |
| ---- | --- | ---- | - |
| Mary | 89  | Mary | B |
| Jojo | 60  | Jojo | D |
|      |     | Jan  | F |

* ```join a.txt b.txt```

| Tom  | 100 | A |
| ---- | --- | - |
| Mary | 89  | B |
| Jojo | 60  | D |
## 剪切訊息的內容(cut)
| 參數            | 說明                                                             |
| --------------- | ---------------------------------------------------------------- |
| cut -c 字元     | 依字元抓取                                                       |
| cut -f 數字N    | 取出第N筆欄位，左起由1起算                                       | 
| cut -d 分隔符號 | 預設是TAB符號，但若分隔符號為空白時，則可用單引號包起來，例如 -d |

| 範例                         | 說明                  |
| ---------------------------- | --------------------- |
| ls -l | cut -c 1-10          | 抓取第1至第10個字元   |
| ls -l | cut -d „空白鍵‟ -f 3 | 以空白分隔，抓取第3欄 | 
| echo $PATH ｜ cut -d : -f 2  | 以:為分隔，抓取第2欄  |
| cut -d : -f 2-4 /etc/passwd  | 抓取檔案第2,3,4欄     |
## 取代文字 (tr)
* 刪除訊息當中的SET1這個字串
```
tr -d
```
* 取代重複的字元
```
tr -s
```
* 將所有的小寫變成大寫
```
cat /etc/passwd | tr ‟[a-z]‟ ‟[A-Z]‟
```
* 將冒號 (:) 刪除
```
cat /etc/passwd | tr -d “:”
```

## awk文字處理工具
* awk „條件類型1{動作1} ...‟ 檔案路徑

## sed文字處理工具

| 範例                             | 說明                            |
| -------------------------------- | ------------------------------- |
| sed „s/root/ROOT/g‟ /etc/passwd  | 將root改成ROOT                  |
| sed „s/root//g‟ /etc/passwd      | 將root字串刪除                  | 
| sed -n „5,7p‟ /etc/passwd        | 顯示第5,6,7行                   |
| sed „2,5d‟ /etc/passwd           | 將第2行~第5行刪除               |
| sed „2a hello‟ /etc/passwd       | 第2行下面附加一行字串”hello”    |
| sed „2,5c hello‟ /etc/passwd     | 第2行至5行被替換成一行字串hello |
## 在檔案內搜尋字串(grep)
* grep [選項] 比對字串 [檔案]

| 參數             | 說明                                   |
| ---------------- | -------------------------------------- |
| grep -o          | 只印出相符的字串                       |
| grep -n          |印出字串所在的那一行編號                | 
| grep -H          | 印出字串所在檔名                       |
| grep -r          | 也搜尋子目錄                           |
| grep -v          | 反向選擇                               | 
| grep -i          | 不區分大小寫                           |
| grep -l          | 列出檔案內容符合指定的樣式的檔案名稱   |
| grep -L          | 列出檔案內容不符合指定的樣式的檔案名稱 | 
| grep -w          | 須全字相符                             |
| grep -c          | 印出具相符結果的總行數                 |
| grep -s          | 不要顯示錯誤資訊                       | 
| grep -m N        | 只列出前N個                            |
| grep -A 顯示行數 | 找到字串的後(after)幾行也會顯示出來    |
| grep -B 顯示行數 | 找到字串的前(before)幾行也會顯示出來   |

| 範例                          | 說明                                    |
| ----------------------------- | --------------------------------------- |
| grep -n -w “home” /etc/passwd | 顯示/etc/passwd檔案內出現home的地方     |
| grep -o “home” /etc/passwd    | 只印出”home”，不會印出其他字元          | 
| grep -c “home” /etc/passwd    | 顯示/etc/passwd檔案內含有home字串的行數 |
| grep -H “home” /etc/*         | 找出/etc/目錄下含有home字串的所有檔案   |
| history | grep “is”           | 列出指令記錄內出現is字串記錄            |
| grep -Hn “is”                 | 從標準輸入搜尋is字串                    |
## vi
* 開啟(或自動新增)test.txt
```
vi test.txt
```

* 指令模式(:)

| 指令        | 說明                |
| ----------- | ------------------- |
| h           | help                |
| w           | 存檔                | 
| w 檔名      | 另存新檔            |
| wq 或 zz    | 存檔並離開vi        |
| q!          | 強制離開v           | 
| 5,9 w 檔名  | 不將第5~9行存到檔案 |
| :set number | 顯示行號            |

* 一般模式(ESC)

| 指令  | 說明                                     |
| ----- | ---------------------------------------- |
| 0     | 移動到此行的開頭                         |
| $     | 移動到此行的結尾                         | 
| 5G    | 移動到檔案的第5行                        |
| 1G    | 移動到檔案的第一行                       |
| G     | 移動到檔案的最後一行                     | 
| dd    | 刪除游標所在的一整行                     |
| 5dd   | 刪除游標開始的5行                        |
| 6,9d  | 刪除6-9行                                |
| yy    | 複製游標所在的一整行                     |
| yw    | 複製目前單字                             | 
| p     | 將複製(或刪除)的內容插入到游標位置的後面 |
| P     | 將複製(或刪除)的內容插入到游標位置的前面 |
| /字串 | 搜尋字串，按n找下一筆，N找上一筆         |

## Shell變數命名規則
* 檢視所有環境變數值
```
export
```
* 印出單一變數值
```
echo $變數名稱
#or
echo ${變數名稱}
```
* 設定變數值
  * 變數預設視為字串形式
  * 等號兩邊不能接空白字元
  ```
  name=apple
  ```
  * 變數值內若需要空白字元，可使用單引號或雙引號
  ```
  name="CoCo Lee"
  ```
  * 使用單引號會印出原始字串而非變數值
  ```
  輸入:echo $HISTSIZE
  輸出:1000
  輸入:echo ${HISTSIZE}
  輸出:1000
  輸入:"$HISTSIZE"
  輸出:1000
  輸入:echo '$HISTSIZE'
  輸出:$HISTSIZE
  ```
  * 使用雙引號才能保留原始空白
  ```
  輸入:name="Coco     Lee"
  輸入:echo $name
  輸出:Coco Lee
  輸入:echo "$name"
  輸出:Coco     Lee
  ```
  * 跳脫字元
   * \‟表示無特殊意義的單引號
   * \”表示無特殊意義的雙引號
   * \\ 表示無特殊意義的右斜線
* 移除變數
```
unset name
```
* 讀取來自鍵盤輸入的變數值
 * -p : 向使用者印出提示字串
```
read 變數名稱
```
```
  輸入:read -p "input your name:" name
  (鍵盤輸入jojo)
  輸出:input your name:jojo
  輸入:echo "$name"
  輸出:jojo
```

## Shell Script
* ```#!/bin/bash```放置於Script的第一行，宣告將用/bin/bash程式來解譯這個指令稿
  * 範例
  ```
  #!/bin/bash
  echo “Input your name:”
  read username #輸入資料會儲存至變數username
  echo $username #印出變數值
  ```
* 其他以 # 開頭的行則表示為註解
* 指令稿的執行方式
  * 在Shell裡設定的變數不會影響原系統
   * ```bash test.sh```or```./test.sh```
  * 在Shell裡設定的變數會影響原系統
   * ```source test.sh```or```. test.sh```
* 用於指令稿中的特殊變數

| 變數       | 意義                          |
| ---------- | ----------------------------- |
| $#         | 參數的個數                    |
| $0         | 當前的腳本名稱 (或指令的名稱) | 
| $1,$2,…,$9 | 分別代表傳進來的第幾個參數    |
* 指令結束狀態
  * 執行指令後，系統會回傳一個「執行結果狀態碼」
    * 若指令正常結束，狀態碼為「0」
    * 若指令錯誤或異常結束，狀態碼為「大於0的整數值」
  * 以 $? 查出狀態碼
    * 此特殊變數可以列出「上一個指令」執行結果的狀態碼
* 條件判斷式
  * 簡單條件判斷式
  ```
  if [ 條件判斷式 ]; then
  　當條件判斷式成立時，進行的工作內容；
  fi
  ```
  * 多重條件判斷式
  ```
  if [ 條件判斷式 ]; then
  　當條件判斷式一成立時，進行的工作內容；
  elif [ 條件判斷式二 ]; then
  　當條件判斷式二成立時，進行的工作內容；
  else
  　當一與二都不成立時，進行的工作內容；
  fi
  ```
* 檔案類型及權限的判斷
 * 可利用test測試(用echo $?取出結果)
 ```
 test -f /home/user1/file1
 echo $?
 ```
 
| 符號 | 說明                       |
| --   | -------------------------- |
| -f   | 檢查檔案是否存在           |
| -d   | 檢查目錄是否存在           | 
| -e   | 檢查檔案或目錄是否存在     |
| -r   | 檢查該檔案、目錄是否可讀   |
| -w   | 檢查該檔案、目錄是否可寫   | 
| -x   | 檢查該檔案、目錄是否可執行 |
| -L   | 檢查連結檔是否存在         |
## 宣告變數的類型(declare)
* 變數預設為字串型態
* 使用declare可宣告變數類型
  * -i ：變數為整數(integer)(沒有小數點)
    * 整數變數可以進行數值運算或比較數值大小
  ```
  輸入:sum=10+20+30
  輸入:echo $sum
  輸出:10+20+30
  ```
  ```
  輸入:declare -i sum2
  輸入:sum2=10+20+30
  輸入:echo $sum2
  輸出:60
  ```
  * -a：變數為陣列(array)
    * 陣列的設定方式為```var[index]=content```
  ```
  輸入:declare -a car
  輸入:car[1]=“ford”
  輸入:car[2]=“benz”
  輸入:car[3]=“bmw”
  輸入:echo ${car[2]}
  輸出:benz
  ```
  * -x：將變數設定為環境變數
  * -r ：將變數設定成為唯讀，不可再被更改內容，也不能unset
* 命令執行的判斷依據 (; 及 && 及 ||)
  * 指令1 ; 指令2
    * 分號用來區隔前後兩個指令，依序執行
    * 不論指令1是否執行成功，都會繼續執行指令2
    ```
    cd /tmp ; rm *.txt
    ```
  * 指令1 && 指令2(表示and)
    * 若指令1正確執行(回傳值為0)，才會執行指令2
    * 若指令1執行錯誤(回傳錯誤代碼)就終止
  * 指令1 || 指令2(表示or)
    * 若指令1正確執行(回傳值為0)，則指令2不執行
    * 若指令1執行錯誤 (回傳錯誤代碼)，則執行指令2
    
## 迴圈
* for...do...done
  * for迴圈通常用於循序處理資料，讓包在段落內的指令可以重複執行
  * 範例:依序印出Tom、Mary、John
```
for var in Tom Mary John
do
　echo $var
done
```
* while…do…done
  * 當判斷式成立時進行迴圈，直到條件不成立才停止
    * 語法
  ```
  while [ 判斷式 ]
  do
  　程式段落
  done
  ```
    * 範例:印出 0 ~ 9
  ```
  i=0 
  while [ $i != 10 ]
  do
  　echo $i　#印出i的值
  　i=$(($i+1))　#讓 i 每次都增加 1
  done
  ```
* while…do…done
  * 範例:讀檔
```
while read input #將讀取的資料存到input變數
do
　echo $input 
done < /etc/passwd #這裡使用了資料流導入符號
```
* until…do…done
  * 判斷式條件成立時就終止迴圈， 否則持續進行迴圈
    * 語法
  ```
  until [ 判斷式 ]
  do
  　程式段落
  done
  ```
    * 範例:印出 0 ~ 9
  ```
  i=0
  until [ $i -ge 10 ]
  do
  　echo $i #印出i的值
  　i=$(($i+1)) #讓 i 每次都增加 1 
  done
  ```
  
## 工作排程
* 一次性的工作排程(at)
  * 下達工作指令 ```at [-m] TIME```
    * -m：將工作的輸出結果mail 給下達指令的帳號
    * TIME指定執行時間
    
    | TIME格式         | 範例              | 說明           |
    | ---------------- | ----------------- | -------------- |
    | HH:MM            | 11:00             | 今天11點       |
    | HH:MM YYYY-MM-DD | 04:00 2002-05-30  | 2002/5/30 4:00 |
  * 查看目前的工作排程 ```atq```
  * 刪除排程 ```atrm [工作編號]```
  * 範例
  ```
  at -m 3pm
  at> echo hello
  ```
* 循環性的工作排程(crontab)
  * crontab可讓系統於指定時間(或週期)自動執行某些任務
  ```
  分 時 日 月 星期 指令(或Script)
  ```
  
| 欄位 | 分   | 時   | 日   | 月   | 星期 |
| --   | ---- | ---- | ---- | ---- | ---- |
| 範圍 | 0-59 | 0-23 | 1-31 | 1-12 | 0-7  |

| 特殊字符 | 說明                         |
|:--------:| ---------------------------- |
| *        | 代表任何時刻                 |
| ,        | 列舉時段，以逗號做分隔       | 
| -        | 代表一段時間範圍內           |
| /數字    | 亦即是『每隔單位間隔』的意思 |
| @yearly  | 等同 0 0 1 1 *               | 
| @daily   | 等同 0 0 * * *               |
| @hourly  | 等同 0 * * * *               |
| @reboot  | 系統啟動時執行               |

| crontrb範例               | 說明                             |
| ------------------------- | -------------------------------- |
| 0 22 * * 5 指令或腳本     | 每週五22點執行                   |
| 0 9,11 * * * 指令或腳本   | 於每日09:00及11:00 執行          | 
| */5 * * * * 指令或腳本    | 每5分鐘執行                      |
| * * * * * 指令或腳本      | 每分鐘都執行                     |
| 0 9-18 * * 1-5 指令或腳本 | 於每週一到週五的09:00至18:00執行 | 
| @yearly 指令或腳本        | 於每年元旦執行該腳本             |
| @reboot 指令或腳本        | 開機後執行該腳本                 |

## 透過 systemctl 管理系統服務運行

* ```systemctl [動作] [服務名稱]``` (需root權限)

| 範例                       | 說明                           |
| -------------------------- | ------------------------------ |
| systemctl stop 服務名稱    | 停止該系統服務                 |
| syetemctl start 服務名稱   | 啟動該系統服務                 | 
| syetemctl restart 服務名稱 | 重啟該系統服務                 |
| syetemctl reload 服務名稱  | 重新載入設定檔案，不需停止服務 |
| syetemctl enable 服務名稱  | 於下次開機時啟動服務           | 
| syetemctl disable 服務名稱 | 於下次開機時停止服務           |
| systemctl status 服務名稱  | 檢視服務運行狀態               |

## 壓縮與備份
* 壓縮與解壓縮
  * zip / unzip
  * gzip / gunzip
  * bzip2 / bunzip2 (壓縮效率較佳)
  * xz / unxz (壓縮效率更好)
  * 範例
    * #壓縮後生成file1.xz，並刪除原始檔
    ```
    xz file1
    ```
    * 壓縮後生成file1.xz，但保留原始檔
    ```
    xz -k file1
    ```
    * 解壓縮，並刪除壓縮檔
    ```
    xz -d file1.xz
    ```
* tar
  * 用於將多個檔案合併為一個檔案，以利備份和壓縮
  * 範例
    * 將dir1下所有檔案合併到test.tar
    ```
    tar -cf test.tar dir1
    ```
    * 再用gzip產生test.tar.gz
    ```
    gzip test.tar
    ```
    
| 副檔名   | 說明                                 |
| -------- | ------------------------------------ |
| *.tar    | 以 tar 程式打包的檔案，未壓縮        |
| *.tar.gz | 以 tar 程式打包的檔案，並以gzip壓縮  | 
| .tar.bz2 | 以 tar 程式打包的檔案，並以bzip2壓縮 |
| *.tar.xz | 以 tar 程式打包的檔案，並以xz壓縮    |

| 選項        | 說明               |
|:-----------:| ------------------ |
| -c          | 建立檔案           |
| -x          | 解開檔案           | 
| -v          | 顯示過程           |
| -t          | 查看內容           |
| -f 檔名     | 要被處理的檔案名稱 |
| -z          | 由gzip處理         | 
| -j          | 由bzip2處理        |
| -J          | 由xz處理           |
| -C 目的路徑 | 指定目的地路徑     |
  * tar配合壓縮範例
    * 把dir1打包，然後壓縮成不同的壓縮檔格式<br>
  ```tar -zcf test.tar.gz dir1```<br>
  ```tar -zcf test.tgz dir1 ```<br>
  ```tar -jcf test.tar.bz2 dir1```<br>
  ```tar -Jcf test.tar.xz dir1```
    * 檢視tar檔的內容<br>
    ```tar -tvf test.tar.gz```　(只顯示內容物，未真實解開)
    * 解開tar壓縮檔<br>
    ```tar -zxf test.tar.gz```<br>
    ```tar -zxf test.tgz```<br>
    ```tar -zxf test.tar.gz -C /tmp``` (解開來放到/tmp/下)<br>
    ```tar -jxf test.tar.bz2```<br>
    ```tar -Jxf test.tar.xz```

## 帳號與群組管理
* 帳號(User)
  * 帳號名稱是唯一的、不可重複，且大小寫有別
  * 帳號編號(UID)
    * 每個帳號會對應一個不重複的編號(User ID，簡稱UID)
    
    | UID        | 身分         | 帳號範例                      |
    | ---------- | ------------ | ----------------------------- |
    | 0          | root         | root                          |
    | 1~999      | 系統服務帳號 | cdrom、daemon                 |
    | 1000~65535 | 一般使用者   | user1 (1000)<br> user2 (1001) |
* 群組(Group)
  * 群組編號(GID)
    * 每個群組會對應一個不重複的編號(Group ID，簡稱GID)
    
    | GID        | 群組身分     | 帳號範例                      |
    | ---------- | ------------ | ----------------------------- |
    | 0          | root群組     | root                          |
    | 1~999      | 系統服務群組 | cdrom、daemon                 |
    | 1000~65535 | 一般群組     | user1 (1000)<br> user2 (1001) |
* 主要群組與次要群組
  * 一個帳號只能擁有一個主要群組
  * 帳號若沒有主要群組，則該帳號無法登入
  * 新增帳號時，預設會指定一個與帳號同名的主要群組
  * 一個帳號可以擁有0至多個次要群組
* 帳號群組相關的設定檔
  * /etc/passwd　(每行代表一個帳號，以：分隔以下欄位，預設任何人皆可檢視此檔案內容)
    * 1.使用者帳號，1到32字元內
    * 2.密碼，顯示x表示已改存於/etc/shadow
    * 3.帳號UID
    * 4.帳號GID
    * 5.此帳號的備註
    * 6.家目錄路徑
    * 7.使用者登入後預設的shell
  * /etc/shadow (每行代表一個帳號，以：分隔以下欄位，預設root或shadow群組的帳號才可以檢視)
    * 1.帳號名稱
    * 2.加密後的密碼
    * 3.密碼最後改變的日期 (從1970年1月1日開始算)
    * 4.密碼不可被更動的天數 (相對於第3欄)
    * 5.這組密碼還有多久會過期 (相對於第3欄)
    * 6.警告更改密碼間隔天數 (相對於第5欄)
    * 7.密碼過期後帳號還有多久會解除 (相對於第5欄)
    * 8.帳號還有多久會過期(從1970年1月1日開始算，如果是空的，代表此帳號不會過期)
    * 9.保留欄位
  * /etc/group　(一行代表一個群組，以：分隔以下欄位，預設任何人皆可檢視此檔案內容)
    * 1.群組名稱
    * 2.群組密碼，顯示x表示已改存於/etc/gshadow
    * 3.GID
    * 4.這個群組的會員
  * /etc/gshadow
    * 一行代表一個群組，以：分隔以下欄位，預設root或shadow群組的帳號才可以檢視
    * 1.群組名稱
    * 2.加密後的群組密碼
    * 3.群組管理員帳號
    * 4.這個群組的會員
* 切換帳號(su)
  * su [帳號] 
  * 用於切換目前使用的帳號，需輸入新帳號的密碼
  * 預設會切換成 root
  * 切換後會產生子Shell
  * 要返回原帳號可使用 exit
* sudo
  * sudo 指令
  * 暫時用root權限執行該指令
  * 使用時必須輸入目前帳號的密碼
  * 每次密碼可維持5分鐘內不需再輸入密碼
  * 只有寫於/etc/sudoers設定檔內的帳號才可以使用 sudo
  * 讓user2 擁有使用sudo的權力:
    * 以root權限執行visudo
    ```
    ....(前面省略)....
    root ALL=(ALL) ALL <-先找到這一行
    user2 ALL=(ALL) ALL <-新增這一行
    ....(底下省略)....
    ```
  * wheel群組成員也可以使用sudo
    * 雖然/etc/sudoers沒有設定user1的權力，但是藉由設定了wheel群組的權力，<br>而wheel是user1的次要群組，所以user1可以使用sudo
    ```
    ## Allows people in group wheel to run all commands
    %wheel  ALL=(ALL)       ALL
    ```
    * 執行 sudo usermod -G wheel user3　將user3次要群組設定為wheel <- user3就能使用sudo
  * 切換成root帳號也可以使用sudo -i 只需輸入原帳號的密碼

## 帳號設定
* 更改帳號的密碼(passwd)
  * ```passwd [帳號] ```
  * 不指定帳號則預設會更改目前帳號的密碼
  * 以root權限更改其他帳號的密碼，就不需輸入原始密碼 ```sudo passwd [帳號]```
* 更改帳號的密碼(chpasswd)
  * ```echo 帳號:密碼 | chpasswd```
  * 適合用於自動化腳本，可批量設定密碼
  * 範例：以root身分將user2的密碼改為12345
  ```
  echo user2:12345 | sudo chpasswd
  ```
* 新增帳號(useradd)
  * ```useradd 帳號名稱```
  * 需root權限
  * 會自動新增一個同名的群組
  * 但不會自動建立密碼
  ```
  sudo useradd user3 #建立帳號後會自動建立同名群組
   sudo passwd user3 #建立密碼
  ```
* 修改帳號(usermod)
  * ```usermod 帳號``` 
  * 需root權限
  
| 選項 | 說明         |
|:----:| ------------ |
| -u   | 設定新UID    |
| -d   | 設定家目錄   | 
| -g   | 設定主要群組 |
| -G   | 設定次要群組 |
| -a   | 附加次要群組 |
| -L   | 鎖定帳號     | 
| -U   | 解鎖帳號     |
* 刪除帳號(userdel)
  * ```userdel 帳號```
  * 需用root權限
  * ```-f``` 強制移除帳號
  * ```-r``` 刪除家目錄及其他檔案(例如信箱或工作排程)
  * 強制刪除user3 ```sudo userdel -r -f user3```
* 查詢帳號資訊
  * ```users``` 顯示目前登入的帳號，資訊較簡略
  * ```who``` 顯示目前登入的帳號，較詳細
  * ```w``` 只顯示目前入的指定帳號，資訊最完整
* 查詢帳號是屬於哪個群組 (id或groups)
  * ```groups [帳號]``` 查詢該帳號所屬的群組
  * ```id [帳號]``` 印出帳號群組相關資訊
  * ```lastlog``` 列出每個帳號最近登入時間
  * 顯示系統登入紀錄 (last)
    * ```last -n 3``` 顯示最近3筆紀錄
    * ```last user1``` #只顯示user1的登入紀錄
    * ```last reboot``` 顯示重開機的紀錄
    
## 檔案權限管理
* 檢視檔案資訊

```
　　　　　　連結數　　　　群組　　　檔案最後存取日期
-rwxrw---- 　1 　test 　test 　0 　Feb 1 19:23 　file1.txt
檔案屬性　　　　　擁有者 　　　檔案大小　　　　　　　　檔名
```
*  -rwxrwxrwx
  * 第1個位元代表檔案(目錄)類型
    * -表示為一般檔案
    * d表示為目錄
    * l表示為Soft link
  * 後9個位元為權限位元
    * r 表示read權限
    * w 表示write權限
    * x 表示excute權限
  * 前3個rwx為檔案擁有者屬性(可讀可寫可執行)
  * 中間3個rwx為檔案所屬群組之屬性
  * 後3個rwx為其他人對此檔案之屬性
* 權限說明
    | 權限       | 對於檔案     | 對於目錄                      |
    |:----------:| ------------ | ----------------------------- |
    | 讀取<br> r | 檢視檔案內文<br> cat、tac、less、more、tail、head     | 檢視目錄的內容物<br>ls |
    | 寫入<br> w | 修改內容後，可存檔保留變更<br>vim、gedit、joe、nano | 新增/修改/刪除檔案及子目錄<br>touch、mkdir、rmdir、rm、mv |
    | 執行<br> x | 將檔案當成程式來執行<br>./file1     | 允許進入到該目錄內<br>cd |
* 變更檔案權限(chmod)
  * 檔案的擁有者可以更改檔案權限
  
| 指令範例                   | 說明                   |
| -------------------------- | ---------------------- |
| chmod u=rwx,g=rx,o=r file1 | 權限會變成 rwxr-xr--   |
| chmod o= file1             | others的所有權限都關掉 | 
| chmod a=rw file1           | 所有人設定為可讀可寫   |
| chmod a+x dir1             | 所有人都加上執行權限   |
| chmod o-x file1            | 關掉others的執行權限   |
* chmod 數字設定
  * ```chmod 權限數字 [-R] 檔案或目錄```
    * r=4，w=2，x=1， -=0 
    * ```chmod 740 file1``` 權限會變成rwxr-----
    * ```chmod -R 700 dir1/*``` dir1內所有檔案及子目錄的權限皆變成rwx------
    
## 套件管理機制
* yum 指令用法 (CentOS)
  * yum search “subversion”
 
| 用法                  | 說明                 |
| --------------------- | -------------------- |
| yum install 套件名    | 安裝套件             |
| yum -y install 套件名 | 安裝時預設回答yes    | 
| yum remove 套件名     | 移除該套件           |
| yum update            | 更新已安裝的所有套件 |
| yum update 套件名     | 更新該套件           |
| yum list installed    | 列出所有已安裝的套件 |
| yum list update       | 列出所有可更新的套件 |
| yum info 套件名       | 以套件名查詢相關資訊 |

* APT 指令用法 (ubuntu)
  * sudo apt-get install subversion
  
| 用法                      | 說明                         |
| ------------------------- | ---------------------------- |
| apt-get install 套件名    | 安裝套件                     |
| apt-get -y install 套件名 | 安裝時預設回答yes            | 
| apt-get remove 套件名     | 移除該套件                   |
| apt-get update            | 更新套件清單                 |
| apt-get upgrade           | 逐一升級所有有新版的軟體套件 |
| apt-cache search 字串     | 搜尋可用套件                 |
