---
layout: post
title: "Git-Bash常用命令"
---

# Git-Bash常用命令

目录：
- [Git-Bash常用命令](#git-bash常用命令)
  - [1.建立仓库](#1建立仓库)
  - [2.初始化仓库](#2初始化仓库)
  - [3.添加文件到版本库](#3添加文件到版本库)
  - [4.查看仓库变更情况](#4查看仓库变更情况)
  - [5.查看文件变更明细](#5查看文件变更明细)
  - [6.修改文件内容，提交到到版本库](#6修改文件内容提交到到版本库)
    - [6.1.撤销修改](#61撤销修改)
  - [7.查看版本记录](#7查看版本记录)
  - [8.版本回退](#8版本回退)
  - [9.查看历史命令记录](#9查看历史命令记录)
  - [10.删除文件](#10删除文件)
  - [11.远程仓库](#11远程仓库)
  - [12.远程库克隆](#12远程库克隆)
  - [13.远程仓库的变更与提交](#13远程仓库的变更与提交)
  - [14.分支管理](#14分支管理)

## 1.建立仓库
```
mkdir 仓库目录路径
```

## 2.初始化仓库
```
cd 仓库路径
git init
```

## 3.添加文件到版本库
1. 文件要保留在仓库根目录或子目录下  
2. 提交文件需要两步：  
   - 用git add告诉Git要添加文件了
   - 用git commit -m 告诉Git要提交文件了。其中-m是为本次提交附加说明。强烈建议追加-m
	
示例：

```
git add readme.txt
git commit -m "add a readme.txt file"
```
	
## 4.查看仓库变更情况

```
git status
```

## 5.查看文件变更明细

```
git diff 文件名
```

## 6.修改文件内容，提交到到版本库
等同添加文件到版本库，先  `git add`  ，再  `git commit -m`  。
### 6.1.撤销修改

`git checkout -- filename`  将没有提交的修改内容从"暂存区"撤销。这样，git add命令添加的文件数据就会消失，等待下次  `git add`  新的内容到缓存区再  `git commit`  。
示例：

```
git checkout -- readme.txt
```

## 7.查看版本记录

`git log`  或  `git log -pretty=oneline`  

## 8.版本回退

  `git reset --hard HEAD~迭代次(1-N)`  或  `git reset --hard commitid`

## 9.查看历史命令记录

`git reflog`  

(*ps：显示内容从上到下是按时间降序的*)
	
## 10.删除文件

1. 先确认删除 
    
    ```
    git rm filename
    ```
    
2. 再提交  
   
    ```
    git commit -m "remove a filename file"
    ```
    
3. 若删错了，不要执行第2步的commit，用checkout还原
    
    ```
    git checkout -- filename
    ```
	
## 11.远程仓库
1. 显示远程仓库  
    
    ```
    git remote -v
    ```
    
2. 添加建立与远程仓库的连接  
    
    ```
    git remote add origin 仓库地址
    ```
    
3. 第一次把本地库的所有内容推送到远程仓库上  
    
    ```
    git push -u origin main
    ```
    
4. 推送最新修改到仓库 (3)步骤完成后  
    
    ```
    git push origin main
    ```
    

## 12.远程库克隆
1. 将远程仓库克隆到本地仓库  
   
    ```
    git clone 仓库地址
    ```
    
2. 克隆成功后切换到目标仓库  
    
    ```
    cd 项目名
    ```
    
3. 在项目仓库上做的任何变更 推送回远程仓库
   - 先添加变更到本地仓库暂存区  
        ```
        git add 变更文件
        ```
   - 在实际提交变更到本地仓库  
        ```
        git commit -m "提交说明"
        ```
   - 推送更新到远程仓库  
        ```
        git push origin main
        ```
			
## 13.远程仓库的变更与提交
1. 先与远程库关联  
    ```
    git remote add origin 仓库地址
    ```
2. 若远程库不为空，拉取远程库文件  
    ```
    git pull origin main
    ```

3. 将本地变更文件`git add`到暂存区
4. 将本地变更文件提交到本地仓库`git commit -m "提交说明"`
5. 将本地仓库内容推送到`git push`远端
		
## 14.分支管理

如果没有仓库，需要先建立创库或仓库克隆。

- 查看分支
  查看本地分支使用命令：  

  ```
  git branch 
  ```
  
  查看远程分支使用命令：
  
  ```
  git branch -a
  ```

- 拉取远程分支并同时创建对应的本地分支。  
  
    ```
    git checkout -b 本地分支名x origin/远程分支名x 
    ```
    
- 切换分支。  
   ```
   git checkout 本地分支名
   或
   git switch 本地分支名
   ```
- 提交代码到远程分支。  
  在目前切换的分支下进行`git add --all`;`git commit -m ""`等操作后再`git push`即可。
