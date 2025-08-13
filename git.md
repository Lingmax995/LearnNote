初始化一个Git仓库，使用`git init`命令。



添加文件到Git仓库，分两步：

1. 使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m <message>`，完成。
举例
```
git add file1.txt
git add file2.txt file3.txt
git commit -m "add 3 files."
简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。
````

- 要随时掌握工作区的状态，使用`git status`命令。
- 如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容。
- `git log`命令显示从最近到最远的提交日志
	- 如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数

- 版本回退
	`--hard`会回退到上个版本的已提交状态，而`--soft`会回退到上个版本的未提交状态，`--mixed`会回退到上个版本已添加但未提交的状态
```
git reset --hard HEAD^  //退回上一个版本
git reset --hard 1094a  //退回“1094a”版本号的版本
```

- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本


	 查看文件内容 cat file.txt

- `git checkout -- file`可以丢弃工作区的修改

- 用命令`git reset HEAD <file>`可以把暂存区的修改撤销掉（unstage），重新放回工作区

- 确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`
- `git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
```
git checkout -- test.txt

```

- github推送内容 `git push`
```
git push -u origin main
```