## 1.git commit --amend
	当我们想要对上一次的提交进行修改时，我们可以使用git commit –amend命令。git commit –amend既可以对上次提交的内容进行修改，也可以修改提交说明。git commit --amend 修改上一次提交，将两次提交合并为一次提交。
## 2.git push -f
	-f  f是force的意思，参数强行覆盖仓库，会导致别人辛辛苦苦编写的代码付之一炬。因此该操作只在自己的git项目上使用，尽量不要使用这个项目。
## 3.github PR 建议
	及时回复Review
	改动太多
	无意义的修改
	标题无意义或者不对
	不必要的修改
## 4.upStream 操作
+ 1.配置当前当前fork的仓库的原仓库地址
	> $git remote add upstream https://gitlab.jiuxia.com/pilot/java-automation-test.git
+ 2.查看remote
	> $ git remote -v
	>origin  https://gitlab.jiuxia.com/qa/java-automation-test.git (fetch)
origin  https://gitlab.jiuxia.com/qa/java-automation-test.git (push)
upstream        https://gitlab.jiuxia.com/pilot/java-automation-test.git (fetch)
upstream        https://gitlab.jiuxia.com/pilot/java-automation-test.git (push)`
+ 3.从源也就是upstream获取最新代码
	>$ git fetch upstream
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From https://gitlab.jiuxia.com/pilot/java-automation-test
   93bdbaf..fdbc850  master     -> upstream/master

+ 合并从源拉下来的代码。在merge之前本地是看不到拉下来的代码的，默认是保存在了upstream/master
>	$ git merge upstream/master
Updating d41ded3..fdbc850
Fast-forward
 README.md | 1 +
 testme.py | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 testme.py

+ 查看日志，本地看不到更新
> $ git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean

+ 查看日志，可以看到源上的更新“Add new file”和“Update README.md”
> $ git log
commit fdbc85003969b0b2964ad0f20bc07b817fe52b56 (HEAD -> master, upstream/master)
Date:   Thu Apr 25 09:31:42 2019 +0000
    Add new file
>
commit 93bdbafd49fa354aaa7b7e972f108ed19e41c81b
Date:   Thu Apr 25 09:27:59 2019 +0000
    Update README.md
>
commit d41ded37b71d4067c13b47df20a61e48ff725b2c (origin/master, origin/HEAD)
Date:   Mon Apr 8 18:10:10 2019 +0800
    initial

+ 推送更新到代码库。代码同步完成。
>$ git push
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 511 bytes | 511.00 KiB/s, done.
Total 6 (delta 3), reused 0 (delta 0)
To https://gitlab.jiuxia.com/qa/java-automation-test.git
   d41ded3..fdbc850  master -> master
