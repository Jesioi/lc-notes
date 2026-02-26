# GitHub Notes
git status
git add .
git commit -m "add 144 preorder traversal note" // 提交到本地仓库，存一个版本
git push // 推送到github
git pull // 从github拉取最新代码
cd // 切换目录
ls // 列出当前目录下的文件

git rebase // 把好几个commit合并，保持提交历史整洁，把当前分支的提交“挪到”另一个分支后面，不可编辑
git rebase -i Head~3 // 交互式rebase，可以编辑提交历史，修改提交信息，合并提交等,Head~3 表示最近的3次提交


git clone // 克隆远程仓库到本地
git log // 查看提交历史
git diff // 查看修改内容
git stash // 暂存当前修改

git reset --hard HEAD~1 // 回退到上一个提交 // 慎用，会丢失修改！！！
git restore --staged // 取消暂存
git restore // 恢复工作区修改

git checkout -b new-branch // 创建并切换到新分支
git branch // 查看分支
git checkout // 切换分支
git merge // 合并分支
git checkout master // 切换回master分支


pwd current location