# 遇到的經典問題 : 如何使用 Git

## [Git 無法在 Cmder 執行](https://blog.csdn.net/hfuter2016212862/article/details/109622540)
- Cmder 本身就有內建好的 Git，只需去設定接好。
- 解決方式具體如下:
  - Settings -> Startup -> Tasks -> 新增一個項目並命名(git)
    - Task Paramters
      - `/icon "C:\xxx\cmder\vendor\git-for-windows\usr\share\git\git.ico"`
    - 底下白色大框
      - `C:\xxx\cmder\vendor\git-for-windows\bin\sh.exe`

## [變更 Cmder 起始路徑](https://albert-kuo.blogspot.com/2019/01/tools-cmder-cmder.html)
- Settings -> Startup -> Tasks -> {cmd:Cmder}
  - 於白色大框內容中改寫 `cmd /k ""%ConEmuDir%\..\init.bat" " -new_console:d:C:\Users\xxx\xxx`
- Save settings

## [如何在 Cmder 登入 Git](https://ithelp.ithome.com.tw/articles/10308140?sc=rss.iron)
- 打開 Cmder 輸入
  - ssh-keygen -t ed25519 -C `your_git_email@example.com`
  - 去使用者找 .ssh目錄，並將用記事本將.pub打開 (將內容複製下來)
    - `C:\Users\xxx\.ssh`
- 打開 GitHub
  - 點擊右上角的小頭像，並點擊倒數第二個 `settings`。
  - 點擊左邊選擇列的 SSH and GPG keys。
  - 點擊 SSH keys 的 `New SSH key`。
  - 將剛剛複製的內容放至 Key 裡面，並點擊 `Add SSH Key`。
  - 在表單上會看到你新增的SSH key圖示。
- 開啟 Cmder 並輸入 `ssh -T git@github.com`
  - 輸入 yes 之後你會看到 Hi... 就代表創建成功 !

</br></br>
# 基本指令
## 創建版本庫 (每個專案都常要創建一次)
```
git init
```
## Clone 克隆
```
git clone git@github.com:.../...git
```
## Status 狀態
```
git status
```
## Push 推
#將本地內容推至 遠端資料庫指定的大/小分支</br>
#push <資料庫大分支> <資料庫分支> (新的分支會自行創建)</br>
```
git push <origin> <master>   
```
## Pull 拉
#將遠端資料庫 指定的大/小分支內容拉下來</br>
#pull <資料庫大分支> <資料庫分支> (新的分支會自行創建)</br>
```
git pull <origin> <master>
```
## Log 查看操作歷史紀錄
```
git log
```
## Add 新增檔案
#只是先新增到本地的版本庫 但尚未更新至遠端庫</br>
可以指定檔案(要寫副檔名) `git add xxx.xxx` </br>
將路徑中所有檔案提交出去 `git add *`

## Commit 提交
Commit 出去後還尚未完成，Push 才是結束 </br>
`git commit -m "...."`

## [Branch](https://blog.csdn.net/sirria1/article/details/102552684)
查看本地與遠端的大小分支</br>
`git branch -a`

## Merge
#合併本地與遠端的內容</br>
#test為要合併的分支</br>
`git merge <test>`

## [Checkout -b 新建並切換到新分支](https://git-scm.com/book/zh-tw/v2/%E4%BD%BF%E7%94%A8-Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E5%92%8C%E5%90%88%E4%BD%B5%E7%9A%84%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95)
新建並切換到新分支 test `git checkout -b test`</br>
相當於下面兩指令 :
- 新建分支 test `git branch test`
- 切換至分支 test `git checkout test`

</br></br>
# 情境模擬
### 第一次提交檔案至 Git
- 創建庫 `git init`
- 當前git狀態 `git status`
- 將路徑中所有檔案提交出去/可以指定檔案(要寫副檔名) `git add *` `git add xxx.xxx` 
- 這次事件的註解內容  `git commit -m "..."` 
- 查看操作歷史紀錄 `git log`
- 接下來我們要去 github創建遠端版本庫
- 創建完畢可以看到底下有給了指令 選擇這行
- `git remote add <origin> git@<github.com:.../...git>`
  - #選擇怎麼呼叫這個大分支 `origin`
  - #你的專案網址 `git@github.com:.../...git`
- `git push <origin> <master>`
  - #push <資料庫大分支> <資料庫分支> (新的分支會自行創建)

### 第二次以上提交至 Git
- `git status`
- `git add *`
- `git commit -m "..."`
- `git log`
- `git push <origin> <master>`

## fatal: refusing to merge unrelated histories.
#**Git 版控判斷方式，是看檔案更新前後時間點。**
- 遇到本地有檔案，先去建立 Git 上的專案，但卻順便建立了README.md (意味著本地少了該檔)。
- 這時候要將本地檔案 push 上去就會噴錯，就算要 pull 下來也噴錯 (整個懷疑人生)。
  - 噴錯內容會說與歷史完全不符 `fatal: refusing to merge unrelated histories.`
- 解決方法 : 直接用 `git pull origin main --allow-unrelated-histories`
  - 選定大/小分支名稱，後面一定要加上 --allow-unrelated-histories (允許不相關的歷史記錄)。
  - 如此一來可以直接抓下來合併 !
- 這樣本地就跟上 Git 的進度，因此可以直接 `git push origin main` 出去，就全部都同步啦 !

## [hint: Updates were rejected because the tip of your current branch is behind.](https://blog.csdn.net/weixin_43770545/article/details/103822377)
- 這可以暴力強制提交 `git push -u <origin> <main> -f`

## [Git Pull or Merge 的問題](https://blog.csdn.net/qq_20801369/article/details/73290373)
錯誤內容如下:
```
error: You have not concluded your merge (MERGE_HEAD exists). 
hint: Please, commit your changes before merging. 
fatal: Exiting because of unfinished merge.
```
- 方法.1 
  - 先 `git commit -m "commit info"`
  - 就可以拉下來 `git pull origin main`
- 方法.2　放棄本地修改，直接拉取
- `git reset --hard`
- `git pull`

## [合併 commit 內容之方法](https://gitbook.tw/chapters/rewrite-history/merge-multiple-commits-to-one-commit)
- 具體流程
  - 查看目前所有提交內容 (由新到舊排序 / q 可以退出查看) `git log --oneline`
  - `git rebase -i bb0c9c2` 指定打開 bb0c9c2 該次提交 (由舊到新排序 / 可以去 git UI 看或是 cmd 瀏覽)
  - 將要合併的內容 由 `pick` 改成 `squash` 之語法
    1. 再次編輯的語法 `git rebase --edit-todo`
    1. 若分支呈現紅色的，需先將方才更動內容加入進來 `git add *`
    1. 接著更改 commit 內容 (若是全合併成一個，只須留一個commit) `git rebase --continue`
       - 若是 `git rebase --continue` 指令修改完後無法通過，則再次輸入，因為還有需要待改內容。
  - 若都無噴錯，即直接 push 更新上去 (這邊要強制推出) `git push -u origin master -f`

## [修改歷史 commit 內容](https://docs.github.com/zh/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/changing-a-commit-message)
- 與合併歷史做法一樣，叫出 `git rebase -i`
- 但 `squash` 改成 `reword`
- 編輯完後一樣使用強制提交才確實完成更改。

## [Cmd 修改檔案之常見語法](https://blog.csdn.net/zmzhangcsdn/article/details/107298516)
- 插入 a / s
- 不儲存退出 / 強制不儲存退出 : :q / :q!
- 儲存退出 / 強制儲存退出 : :wq / :wq!
- 取消動作 esc

## [更改最後一次 commit 內容](https://gitbook.tw/chapters/using-git/amend-commit1)
- `git commit --amend -m "..."`
- `git push -u origin main -f`


## [恢復到指定版本](https://zhuanlan.zhihu.com/p/35078876?utm_id=0)
#先去搜尋該專案要指定的版本
- `git reset --hard <版本>`
- `git push origin HEAD --force`
- 查看 Git 倉庫即可看到已完成恢復版本。


## [Git 個人頁面新增花樣](https://blog.csdn.net/weixin_41804512/article/details/134440056)
