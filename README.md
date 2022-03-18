![Alt text](https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg "Hello git")

<img src="http://static.runoob.com/images/runoob-logo.png" width="50%">


Git 基本操作
============

初始本地數據庫時，預設的分支名稱就是 master
-------------------------------------------

![GITHUB]( https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_12.57.25ni0zk.png "圖片名稱")

利用分支來創造各產品線的又能保持 master 分支發展
------------------------------------------------

>git branch dev

<img src="https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_13.12.21o0tmv.png">

切換分支各產品線的程式
----------------------

>git checkout dev

<img src="https://w3c.hexschool.com/img/%E8%9E%A2%E5%B9%95%E6%88%AA%E5%9C%96_2019-11-19_13.12.21o0tmv.png">

所有修改檔案提交記錄
--------------------

git add . 

提交到本地端的檔案庫
--------------------

git commit -m "Update messges"

本地端的檔案庫同步回遠端檔案庫
------------------------------

git push 

列出不同檔案與檔案庫
--------------------

git add . 

輕量級標籤
----------

git tag -a 2532X001 9fceb02
           標籤     版本GUID前八碼
           
註解的標籤
----------

git tag -a 2532X001 9fceb02 -m "Update messges"
                            加入註解訊息
                            
查詢所有標籤
------------

git tag


查詢標籤修改
------------

git show XXXX

查詢提交版本GUID
----------------

git log --pretty=oneline


檢出標籤
--------

git checkout -b version2 v2.0.0


Git 設定 SSH
------------

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

>第一步：設定原作的遠端節點
>
>舉例來說，這是 Fork 過來的專案：

$ git remote -v
origin	https://github.com/eddiekao/dummy-git.git (fetch)
origin	https://github.com/eddiekao/dummy-git.git (push)


git remote 指令加上 -v 參數後可以看到更完整的資訊。從這裡可以看得出來目前這個專案只有設定一個遠端節點 origin。接下來我要幫它加上另一個遠端節點，這個遠端節點指的位置就是原作的專案：

$ git remote add dummy-kao https://github.com/kaochenlong/dummy-git.git


其實大部份的資料都會教你使用 upstream 做為原作遠端節點的名字，但為避免大家跟之前在「Push 上傳到 GitHub」章節介紹的 upstream 搞混，所以這裡我故意使用 dummy-kao 做為指向原作的遠端節點。這時候在這個專案應該就有 2 個遠端節點了，一個是原來的 origin，一個是原作的 dummy-kao：

$ git remote -v

dummy-kao	https://github.com/kaochenlong/dummy-git.git (fetch)

dummy-kao	https://github.com/kaochenlong/dummy-git.git (push)

origin	https://github.com/eddiekao/dummy-git.git (fetch)

origin	https://github.com/eddiekao/dummy-git.git (push)

>第二步：抓取原作專案的內容
>接下來，就是使用 Fetch 指令來取得原作專案最新版的內容：

$ git fetch dummy-kao

remote: Counting objects: 4, done.

remote: Compressing objects: 100% (2/2), done.

remote: Total 4 (delta 1), reused 3 (delta 1), pack-reused 1

Unpacking objects: 100% (4/4), done.

From https://github.com/kaochenlong/dummy-git

 * [new branch]      features/mailer      -> dummy-kao/features/mailer
 * [new branch]      features/mailer-plus -> dummy-kao/features/mailer-plus
 * [new branch]      features/mailer_pro  -> dummy-kao/features/mailer_pro
 * [new branch]      features/member      -> dummy-kao/features/member
 * [new branch]      master               -> dummy-kao/master


$ git merge dummy-kao/master

Updating ac341ae..689b015

Fast-forward

 contact.html | 2 ++

 1 file changed, 2 insertions(+)
 

 
> 第三步：推回自己的專案
這個步驟要不要做就看你自己決定了，畢竟在你電腦上已經是最新版本了，如果你希望你在 GitHub 上那個 Fork 的專案也跟到最新版，只要推上去就行了：


$ git push origin master

Counting objects: 4, done.

Delta compression using up to 4 threads.

Compressing objects: 100% (4/4), done.

Writing objects: 100% (4/4), 596 bytes | 596.00 KiB/s, done.

Total 4 (delta 1), reused 0 (delta 0)

remote: Resolving deltas: 100% (1/1), completed with 1 local object.

To https://github.com/eddiekao/dummy-git.git

   ac341ae..689b015  master -> master


