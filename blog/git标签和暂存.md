## Git标签与暂存

> 标签 和 暂存

#### 标签

- 标签 用于功能跟新和版本迭代
- 查看标签
  1. `git tag` 或 `git tag --list` 查看所有标签
  2. `git tag -l "v1.0*"` 列举出所有tag标签为v1.0.*的所有tag标签
- 添加标签 
  - 附注标签
    1. `git tag -a v1.0.0 -m "版本v1.0.0"`  给当前`commit`添加标签
    2. `git show v1.0.0` 查看标签信息和与之对应的提交信息
  - 轻量标签
    1. `git tag v1.0.2` 轻量标签没有相关信息
- 追加标签
  1. `git tag -a v1.2 commitid` 给相关的提交打上对应的标签
  2. `git push origin v.1.0.1` 将本地tag标签同步到远程
  3. `git push orign --tags` 将本地所有tag标签同步到远程
- 删除标签
  1. `git tag -d 标签名` 删除本地标签
  2. `git push origin --delete 标签名` 删除远程标签
  3. `git push origin :ref/tags/标签名`  删除远程标签

#### 暂存

> 需要将编辑的内容保存在暂存区后才能进行暂存，既`git add .`
>
> 使用暂存，所有文件都处于编辑区

- `git stash list` 查看所有暂存

- `git stash` 把暂存区的内容进行暂存

- `git stash -m "暂存描述"` 给暂存添加描述方便查找

- `git statsh apply 暂存hash值` hash: stash@{0} 使用此暂存，但不删除此暂存

- `git stash pop`  使用上一次暂存，并删除此暂存

- `git stash pop 暂存hash值` hash: stash@{0} 使用此暂存，并且删除此暂存

- `git stash clear` 清空所有暂存

  