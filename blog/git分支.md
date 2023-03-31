## 分支Gig

> 查看分支，切换分支，删除分支，远程分支

- 查看分支
  - `git branch` // 查看本地分支
  - `git branch -r` 或 `git branch --remote` // 查看远程分支
  - `git branch -a` 或 `git branch --all` // 查看所有分支
  - `git branch -l` 或 `git branch --list` // 查看所有的本地分支

- 创建和切换分支
  - `git branch 分支名`  // 创建分支
  - `git checkout 分支名`  // 切换分支
  - `git checkout -b 分支名`  // 上面两步的结合，创建并切换分支
- 合并分支
  - `git merge 分支名`  // 将分支名的分支合并到当前所在的分支
- 删除分支
  - `git branch -d 分支名` 既 `git branch -delete 分支名`  // 删除完全合并的分支
  - `git brabch -D 分支名`  // 删除分支 即使没有合并
- `git branch -m 新分支名` 或 `git branch -move` // 重命名，修改之前的commit的内容会自动变更到新分支名
- `git branch -c`或`git branch -copy` // 复制分支 复制一个分支及其reflog
  - `git branch -C` // 复制分支，即使目标存在 分支上的提交信息会变更到重复分支上

- `git branch --show-current`  // 显示当前分支名称

  

  #### 远程分支

  `git fetch` 更新远程分支， 如果别人`push`了一个新分支到远程，可以根据此命令更新获取到最新的远程分支和提交

  ##### 跟踪分支

  从远程分支检出一个本地分支，并跟踪远程分支，远程分支有变可以通过`git pull`来更新最新代码

  `git checkout -b remote orgin/remote`  即 `git checkout -b 本地分支名 origin/远程分支名` 本地分支名可以不与远程分支名一致

  或

  `git checkout --track origin/远程分支名`

  

   ##### 本地分支跟踪远程分支

   `git branch --set=upstream-to 远程分支名` 本地分支建立与远程分支的个跟踪