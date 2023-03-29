## Git 的基础操作

> 暂存 提交到本地仓库 提交到远程仓库, 查看修改的文件

#### 获取状态

```
git status  // 获取变更文件状态, 包含具体的信息
git status -s // 获取变更文件状态，简单信息
git status --short // 获取变更文件状态，简单信息
```

#### 暂存

每次修改完代码,可以通过 `git status` 来查看文件的状态的。

```
git status
// On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

// 这样提示，没有任何更新

// 有更新的操作
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        blog/git基础操作.md   // 更新的文件，在终端中是红色字体，提示这个文件为已经编辑过得文件

nothing added to commit but untracked files present (use "git add" to track)
```

- 跟踪与暂存 `git add`

这个时候可以通过 `git add`的操作来暂存已经修改的文件

```
git add . // 暂存所有已修改的文件
git add <具体文件名>  // 跟踪并暂存具体内容

// 通过git add 命令来进行跟踪和暂存后，再查看此时的状态 git status 此时修改的内容为绿色
```

> 当修改一个已经暂存过的文件，查看状态是，会出现两条几率，一个已经暂存的，一个 modified 状态修改后的文件，这次修改的文件，还没进行跟踪和暂存，此时为红色字体状态，这个时候可以再次通过 git add 来进行暂存

> 注：，Git 只不过暂存了你运行 git add 命令时的版本。 如果你现在提交，修改的文件是你最后一次运行 git add 命令时的那个版本，而不是你运行 git commit 时，在工作目录中的当前版本。 所以，运行了 git add 之后又作了修订的文件，需要重新运行 git add 把最新版本重新暂存起来。 既提交到本次仓库是以最后一次 git add 为准，而不是修改的文件。

#### 查看已暂存和为暂存的的内容

- git diff

```
git diff
// 会将修改的内容进行展示
// 展示出来所有信息，暂存未提交的 和 需改未暂存的

// 暂存未提交的 头部信息展示
diff --git a/blog/git基础操作.md b/blog/git基础操作.md
index 55921a6..9553f86 100644
--- a/blog/git基础操作.md
+++ b/blog/git基础操作.md
@@ -2,6 +2,14 @@
具体内容

// 未暂存的修改
@@ -33,4 +41,17 @@ nothing added to commit but untracked files present (use "git add" to track)
git add . // 暂存所有已修改的文件
git add <具体文件名> // 跟踪并暂存具体内容
```

- git diff --staged

比对已暂存文件与最后一次提交的文件差异, 上一次 `commit` 和 这次最后一次 `git add` 之间的差异

- git diff --cached

查看已经暂存起来的变化, 已经`git add`暂存后的变化，修改未暂存的不显示

#### commit 提交更新到本地仓库

```
git commit // 提交，这个时候让你通过vim的形式创建提交信息
git commit -m "提交信息"  // 提交，通过 -m 将提交信息保持在同一行
git commit -a -m "将已经暂存过得文件一起提交，跳过git add 步骤" // 这里的意思是，如果你有已经git add 过的内容，如果再次修改并未重新git add, 如果使用-a -m 进行提交则会直接将未暂存的文件暂存，然后提交，省略git add 步骤
```

总结

- git status // 查看文件状态
  - git status -s // 查看文件状态 简略信息
  - git status -short // 查看文件状态 简略信息
- git add // 跟踪·暂存文件
  - git add . // 跟踪·暂存全部
  - git add <文件并> // 跟踪具体文件
- git diff // 查看相关文件修改
  - git diff --staged // 查看 上一次 `commit`和最后一次 `git add` 暂存后的文件变化
  - git diff --cached // 查看 已经暂存起来的变化，最后一次 `git add`暂存后的变化，未暂存的不展示
- git commit // 提交更新到本地仓库
  - git commit -m "提交信息"
  - git commit -a -m "提交信息" // 会将已经暂存，并又再次修改的文件直接再次暂存后提交。
