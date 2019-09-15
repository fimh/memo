Nothing sepcial, just record some daily used git commands here.

Git使用相关的命令以及概念的理解记录在这里边。

## 常用命令
写开发日志(commit message)注意事项

> ***第一行一定要是少于50字的开发概括信息，而且第二行务必是空行，第三行开始才可以开始细致描述开发信息。这是因为很多版本服务系统中的email机制都会选取log中的第一行为邮件题目。***


### 克隆远程repo

```
$ git clone [url]
```

### 查看分支

```
# 查看所有本地分支
$ git branch

# 查看所有远程分支
$ git branch -r

# 查看所有分支(本地+远程)
$ git branch -a
```

### 新建分支

```
# 基于base_branch创建一个新分支new_branch，并切换过去
$ git checkout -b [new_branch] [base_branch]
```

### 切换分支

```
$ git checkout [existed_branch]
```

### 修改分支名

```
$ git branch -m [old_branch] [new_branch]
```

### 删除分支

```
# 注意，existed_branch不能是目前所在的分支
$ git branch -d [existed_branch]
```

### 删除Remote分支

```
$ git push origin --delete [old_branch]
```

### 查看变更

```
$ git status
```

查看当前分支的所有版本历史
```
$ git log
```

### 还原变更
如果未添加到暂存区

```
$ git checkout --${file_to_be_reverted}
```

如果已提交到暂存区，需要先将其取消暂存，然后再执行上面的命令

```
$ git reset HEAD --${file_to_be_reverted}
$ git checkout --${file_to_be_reverted}
```

### Revert one or more existing commits
Record some new commits to reverse the effect of some earlier commits

```
$ git revert ${commit_id}
```

For details, refer to [git-revert - Revert some existing commits](https://git-scm.com/docs/git-revert.html)

### Remove Untracked File
Check which files will be deleted

```
$ git clean -n
```

Delete the files for real

```
$ git clean -f
```

### 添加文件

```
# 将当前目录及子目录下的所有新增文件都添加到暂存区
$ git add .

# 添加指定的文件到暂存区
$ git add [file1] [file2] ...

# 删除文件，并将删除操作保存到暂存区
$ git rm [file1] [file2] ...
```

### 提交代码

```
# 将暂存区里的所有更改提交
$ git commit -m [message]

# 提交暂存区里的指定文件改动
$ git commit [file1] [file2] ... -m [message]
```

### 修改最后一次提交的修改
经常会发生commit之后，发现有些修改并没有提交上去，比如忘记添加文件，删除某行代码等等。
这个时候你并不需要再提交一个commit，而是可以修改最后的一个commit。

```
$ git add. [some file to be commit]
$ git commit --amend
```

### 代码合并
#### merge
```
# 将develop分支中的改动合并到当前分支(比如当前分支为master)
$ git merge --no-ff develop # --no-ff 不使用fast forward模式，即会创建一个commit节点
$ git merge develop ## 如果不加参数，默认就是--ff，即不会创建commit节点
```

> `fast-forward` merge keeps the changesets in a linear history, making it easier to use other tools (log, blame, bisect).  While `no fast-forward` merge always create a commit to log this merge action.

#### rebase
```
# 将master分支中的改动合并到当前分支(比如当前分支为develop)
$ git checkout master
$ git pull
$ git checkout develop
$ git rebase master
```
该命令主要用于多人协同开发时，将服务器上的主分支(master)上的改动合并到本地开发分支当中，完成之后再通过Pull Request等方式最终merge到master中。
通过这种方式操作，master分支上的commit会比较清晰，就像没有经过任何合并一样。

#### merge与rebase的区别
以分支master到develop为例

merge是将master中的commit按照时间顺序合并到develop中，这时，你原来开发过的commit会在历史中乱掉。

rebase是将master中的commit先合并到develop中，然后将develop之前的commit以patch的形式以此应用到develop中。此时你所做的修改会全部在master中最新commit的后边，无论它们之间的时间先后。此时，你将develop分支再合并到master中，就像同一个人之后又开发了一个新的feature一样，十分清晰。

具体可以参考：[git merge 和 git rebase 小结](http://blog.csdn.net/wh_19910525/article/details/7554489#reply)

### 提交本地的分支到服务器

```
# 创建一个新分支test
$ git branch test

# 切换到分之test
$ git checkout test

# 将test分支推到服务器(之前没有)
$ git push --set-upstream origin test
```

### 全局或者局部设置用户名与邮箱
全局设置如下

```
$ git config --global user.email abc@123.com
$ git config --global user.name "User Name"
```

在一个单独的git repo中

```
$ git config user.email abc@123.com
$ git config user.name "User Name"
```

### 将服务器的变动更新到本地(commit)
使用`git pull`命令来进行操作，使用起来稍微有些复杂。
先参考这篇文章 [git pull](http://www.yiibai.com/git/git_pull.html)

### 将服务器的变动更新到本地(branch)
使用`git fetch`命令来进行操作，比如服务器删除了某些分支，如何将其同步到本地repo呢？直接

```
$ git fetch
```
这个命令还有其它几种用法，具体可以参考[Git 真正理解 git fetch, git pull 以及 FETCH_HEAD](http://ruby-china.org/topics/4768)

### 修改远程地址

```
$ git remote set-url origin [url]
```

### 删除远端仓库信息
```
$ git remote remove origin
```

### 差异对比
做了改动之后，如果查看具体的改动，可以使用git内置的diff工具

```
$ git diff ${branch_a}..${branch_b}
// or
$ git diff ${branch_a}...${branch_b}
// or compare branch_b with current branch
$ git diff ..${branch_b}
```

详情参考：[Git学习教程（七） Git差异比对](http://fsjoy.blog.51cto.com/318484/245465/), [Git "range" or "dot" syntax](https://wincent.com/wiki/Git_%22range%22_or_%22dot%22_syntax)

### 创建tag并提交remote
创建tag

```
$ git tag -a {tag_name} -m “tag_comment″
```

push到remote服务器

```
$ git push origin --tags
```

更多内容，参考[Git打Tag相关操作](http://www.jianshu.com/p/dab7da2a0721)

### 查看Tag并查看对应的message

```
$ git tag -n 9 -l
```
上述命令为显示Tag，并最多显示9行Message的内容

### 根据commit message在log里搜索commit
假如要在所有分支里边搜索包含"Build 1200"字符串的commit，命令如下：

```
$ git log --all --grep='Build 1200'
```

更多内容，参考[How to search a Git repository by commit message?](http://stackoverflow.com/a/7124949)

### 查看指定commit的变更
两种命令，

```
$ git show $COMMIT
```
或者

```
$ git diff ${COMMIT}^!
```

更多内容，参考[How to diff a commit with its parent?](http://stackoverflow.com/a/436368)

### 暂存Stash

`$ git stash`命令常用的几个参数如下：

 - `save ${MESSAGE}`，将当前暂存区的修改作为一条stash存储，并还原workspace。注意，最新的一条stash的index为0，即stash队列是后进先出。
 - `list`，查看所有的stash
 - `clear`，删除所有stash
 - `show`，
	 - `$ git stash show -p ${STASH_INDEX}` 查看指定stash与当前workspace的差别(相当于执行diff之后的效果)
 - `apply ${STASH_INDEX}`，将指定的stash还原到当前workspace。`${STASH_INDEX}`为可选参数，默认值为0。
 - `pop ${STASH_INDEX}`，作用于`apply`相同，但是会删除对应的stash。可以对比数据结构`Stack`中的`pop`操作。

更多内容，参考[Git stash用法](https://gist.github.com/subchen/3409a16cb46327ca7691) 和 [Git 基础再学习之：git checkout -- file](https://www.cnblogs.com/Calvino/p/5930656.html)

### cherry-pick
`cherry-pick`可pick一个或多个连续的commit，用法如下
`$ git cherry-pick ${option} -x`

 - `${COMMIT_ID}`
 - `${START_COMMIT_ID}^..${END_COMMIT_ID}`，注意`^`表示包含`${START_COMMIT_ID}`，即为闭区间；没有的话则不包含，即为左开右闭
 - `-x` - will append a line that says "cherry picked from commit ..." which can be usefull when cherry-picking between two publicly visible branches

如果有冲突，需要手动以此解决。然后可以执行以下相应的操作
`$ git cherry-pick `

 - `--continue`
 - `--quit`
 - `--abort`

更多内容，参考[git cherry-pick 使用指南](https://www.jianshu.com/p/08c3f1804b36)

### solving conflicts
first we can identify merge conflict files via the following command,

```
$ git status
```

print a list of commits that conflict between the merging branches

```
$ git log --merge
```

resolve easy/obvious conflicts
```
// solution is to accept local/our version
$ git checkout --ours ${path_to_file}
// solution is to accept remote/other-branch version
$ git checkout --theirs ${path_to_file}
```

find the base commit for two branches
```
$ git merge-base ${branch_1} ${branch_2}
```

### git submodule
#### adding a git submodule into current git

```
$ git submodule add -b [git_submodule_branch] [git_submodule_url] [check_to_local_path]
```
The above command will generate a config file `.gitmodules` under current git root directory.

```
$ git submodule init [module_a] [module_b] [...]	 //  initialize the specified modules or all modules if no module specified
$ git submodule update
$ git submodule update --remote		// --remote will tell git to fetch the latest commit on the branch in the module
```
More information, please refer to [How can I specify a branch/tag when adding a Git submodule?](https://stackoverflow.com/a/18797720)

#### remove a git submodule
Removing a submodule takes more steps than creating a new one.
Please refer to [Git submodule add: “a git directory is found locally” issue](https://stackoverflow.com/a/35778105) for how to achieve this.

#### clone a git with submodules
The following command will clone specified branch in a remote git and download all submodules resided in that git automatically.

```
$ git clone -b [git_branch] --recurse-submodules [git_url]
```

## 分支管理
不同公司根据自己的业务需求会指定不同的分支使用规范。这里列一个网上流传比较广泛的Git分支使用模型：[A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)。

有热心的人根据这个模型做了一个Git扩展，可以非常快速地按照上述的规范来使用Git: [nvie/gitflow](https://github.com/nvie/gitflow)。

其实[Git之分支创建策略](http://www.cnblogs.com/lee0oo0/archive/2013/06/29/3161883.html) 这篇文章就是根据这个模型来写的。

## 概念理解
HEAD是什么意思？
> HEAD is a ref (reference) to the currently checked out commit. In normal states, it's actually a symbolic ref to the branch you have checked out - if you look at the contents of .git/HEAD you'll see something like "ref: refs/heads/master". The branch itself is a reference to the commit at the tip of the branch.

Hot fixes是什么意思？
> When a critical bug in a production version must be resolved immediately, a hotfix branch may be branched off from the corresponding tag on the master branch that marks the production version. 

Feature branches是什么？
> 这类分支只存在于开发者本地的repo中。
>
> 它一般用于开发新特性/功能(包括实验性质的，尚未确定是否最终会发布的特性/功能)。

git submodule机制是什么，如何使用？
> submodule的信息都存储在repo根目录的".gitmodules"文件中
> 
> 执行
> `$ git submodule init`
> 会将module的git地址与注册到本机的指定路径
> 
> 然后执行
> `$ git submodule update`
> 会对每个module执行clone操作

## 常见问题
### SSL certificate problem: Unable to get local issuer certificate
This error occurs when a self-signed certificate cannot be verified. 
**Workaround**
1. Tell git to not perform the validation of the certificate using the global option:

```
git config --global http.sslVerify false
```
2. Disable TLS/SSL verification for a single git command

```
$ git -c http.sslVerify=false clone [url]
```

## 参考
 1. [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
 2. [nvie/gitflow](https://github.com/nvie/gitflow)
 3. [3.3 Git 分支 - 分支的管理](https://git-scm.com/book/zh/v1/Git-分支-分支的管理)
 4. [Review code with pull requests](https://www.visualstudio.com/da-dk/docs/git/pull-requests)
 5. [常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
 6. [git 查看远程分支、本地分支、创建分支、把分支推到远程repository、删除本地分支](http://blog.csdn.net/arkblue/article/details/9568249/)
 7. [芒果iOS开发之Merge branch 'master' of XXX Please enter a commit message to explain why this merge](http://blog.csdn.net/crazyzhang1990/article/details/50412934)
 8. [Git之分支创建策略](http://www.cnblogs.com/lee0oo0/archive/2013/06/29/3161883.html)
 9. [如何使用git创建项目，创建分支](http://blog.csdn.net/wfdtxz/article/details/7973608)
 10. [git 有用却易忘的知识与命令](https://www.zybuluo.com/yangfch3/note/159758)
 11. [GUI Clients](https://git-scm.com/download/gui/linux)
 12. [Make an existing Git branch track a remote branch?](http://stackoverflow.com/questions/520650/make-an-existing-git-branch-track-a-remote-branch)
 13. [How do you create a remote Git branch?](http://stackoverflow.com/questions/1519006/how-do-you-create-a-remote-git-branch)
 14. [2.6 Git Basics - Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
 15. [github创建tag](http://caibaojian.com/github-create-tag.html)
 16. [git pull](http://www.yiibai.com/git/git_pull.html)
 17. [git修改远程仓库地址](http://blog.csdn.net/tanningzhong/article/details/52873566)
 18. [Git学习教程（七） Git差异比对](http://fsjoy.blog.51cto.com/318484/245465/)
 19. [Git打Tag相关操作](http://www.jianshu.com/p/dab7da2a0721)
 20. [Git 真正理解 git fetch, git pull 以及 FETCH_HEAD](http://ruby-china.org/topics/4768)
 21. [How to search a Git repository by commit message?](http://stackoverflow.com/a/7124949)
 22. [How to diff a commit with its parent?](http://stackoverflow.com/a/436368)
 23. [Git Submodule使用完整教程](http://www.kafeitu.me/git/2012/03/27/git-submodule.html)
 24. [git恢复被修改的文件](http://blog.csdn.net/awj3584/article/details/26567735)
 25. [rename git branch locally and remotely](https://gist.github.com/lttlrck/9628955)
 26. [git merge 和 git rebase 小结](http://blog.csdn.net/wh_19910525/article/details/7554489#reply)
 27. [git-merge完全解析](http://www.jianshu.com/p/58a166f24c81)
 28. [SSL certificate problem: Unable to get local issuer certificate](https://confluence.atlassian.com/bitbucketserverkb/ssl-certificate-problem-unable-to-get-local-issuer-certificate-816521128.html)
 29. [Unable to resolve “unable to get local issuer certificate” using git on Windows with self-signed certificate](https://stackoverflow.com/a/34049063)
 30. [How to remove local untracked files from the current Git branch](https://koukia.ca/how-to-remove-local-untracked-files-from-the-current-git-branch-571c6ce9b6b1)
 31. [Git merge conflicts](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)
 32. [Git – Resolve Merge Conflicts](https://easyengine.io/tutorials/git/git-resolve-merge-conflicts/)
 33. [How to resolve merge conflicts in Git](https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-git)
 34. [https://stackoverflow.com/questions/1191282/how-to-see-the-changes-between-two-commits-without-commits-in-between](https://stackoverflow.com/questions/1191282/how-to-see-the-changes-between-two-commits-without-commits-in-between)
 35. [git merge-base 与 show-branch 命令](https://blog.csdn.net/icbm/article/details/78332448)
 36. [Whatʼs a Fast Forward Merge?](https://sandofsky.com/images/fast_forward.pdf)
 37. [Fast-Forward Git Merge](https://ariya.io/2013/09/fast-forward-git-merge)
