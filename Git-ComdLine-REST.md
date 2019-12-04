# Git/RESTful API/命令行

## Git

#### Git 常用命令
- ```git clone```
- ```git remote add origin```
- ```git push -u origin master```
- ```git log```
- ```git status```
- ```git diff```
- ```git add *```
- ```git commit -m "message"```
- ```git push```
- ```git pull```

#### Git 撤销与回滚
- **暂存区**：```git add```之后commit之前存在的区域；**工作区**：```git commit```之后存在的区域；**远程仓库**：```git push```之后；
- 作了修改，但还没```git add```，撤销到上一次提交：```git checkout --filename```；```git checkout --.```
- 作了修改，并且已经```git add```，但还没```git commit```：
    - 先将暂存区的修改撤销：```git reset HEAD filename```/```git reset HEAD```；此时修改只存在于工作区，变为了 "unstaged changes"；
    - 再利用上面的checkout命令从工作区撤销修改
- ```git add```之后，作了修改，想丢弃这次修改：```git checkout --filename```会回到最近一次```git add```
- 作了修改，并且已经```git commit```了，想撤销这次的修改：
    - ```git revert commitID```. 其实，```git revert```可以用来撤销任意一次的修改，不一定要是最近一次
    - ```git reset --hard commitID```/```git reset --hard HEAD^```（HEAD表示当前版本，几个^表示倒数第几个版本，倒数第100个版本可以用HEAD~100）；参数```--hard```：强制将暂存区和工作区都同步到指定的版本
    - ```git reset```和```git revert```的区别是：reset是用来回滚的，将HEAD的指针指向了想要回滚的版本，作为最新的版本，而后面的版本也都没有了；而revert只是用来撤销某一次更改，对之后的更改并没有影响
    - 然后再用```git push -f```提交到远程仓库

#### Git 分支管理

## RESTful API

### 参考
- [Git教程 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/896043488029600)
- [GitHub - jlevy/the-art-of-command-line: Master the command line, in one page](https://github.com/jlevy/the-art-of-command-line/blob/master/README-zh.md)