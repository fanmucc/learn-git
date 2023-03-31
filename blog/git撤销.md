## Git 后悔药

> 远程撤销 和 被本地撤销

#### 远程撤销

- `git revert`

> 如果发现自己已经 push 到远程仓库，但是其中有错误内容，可以使用该命令进行撤销提交记录并重新 push 到远程

1. `git revert commitid 或 commitid1 commitid2 下同` // 重置相关的 commit 可能会出现冲突，进行解决后可以再次提交， 没有冲突的时候会自动打开 commit，填写提交信息，进行 push。注： 产生新的提交

2. `git revert commitid --no-edit` // 不填写 commit 信息，使用 git 自动生成的提交信息 注： 产生新的提交

3. `git revert commitid --no-commit` // 不进行 commit 提交，只抵消暂存区和工作区的文件变化。 注：产生新的提交。

需要注意的是，如果撤销的记录不是最新提交的，可能会需要解决冲突才能，继续`commit`和`push`

#### 本地撤销

- `git reset`

> 撤销本地记录，已经`commit`，但是不是自己想要的信息，可以通过`git reset`进行撤销

##### 简单实用

1. `git reset --hard commitid 或 多个` // 回退版本 并销毁 暂存区和工作区的修改 注：产生新的提交记录
2. `git reset --sort commitid 或 多个` // 回退版本 保存暂存区和工作区的修改 注：撤销后重新提交，则会重置掉回退时的 commit 信息
3. `git reset --mixed commitid 或 多个` // 回退版本 将工作区的文件修改未暂存状态

如果是跨几个 commit 版本进行撤销并重新`commit`，相关的`commit`信息会重置集合成最新提交的

##### 扩展 待补充

#### 替代上一次 commit 信息

`git commit --amend -m "Fixes bug #42"`

直接使用，可以修改上一次的提交信息，其实就是新的提交代替上次旧的提交

#### 移除暂存区的文件

- `git restore --staged 文件名`

#### 撤销当前分支修改

开发到错误分支

1. 基于错误分支创建一个新分支
2. 通过`git reset`撤销相关`commit`提交
3. 进入新分支继续开发

#### 回退撤销

- `git reflog` // 查看修改 HEAD 指针的修改记录

![gif reflog展示]('/assets/git_reflog.png')

回退:
`git reset --hard commitid`
