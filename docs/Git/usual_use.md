# 一般使用方法

## 专业名词
* Workspace：工作区
* Index / Stage：暂存区
* Repository：仓库区（或本地仓库）
* Remote：远程仓库

## 初始化本地仓库，并和远程仓库建立连接

1. 在GitHub上建立自己的仓库，建议不要先初始化README, license, 或者gitignore文件。
2. 初始化本地仓库并添加文件
        
        # 进入到本地仓库目录
        cd ${本地仓库目录}
        
        # 初始化
        git init
        
        # 添加全部文件
        git add . 
        
        # 添加注释
        git commit -m 'your commit message'
        
3. 和远程仓库建立连接

        # 添加远程仓库到本地仓库
        git remote add ${远程仓库代号} ${远程仓库地址URL}
        # 一般可以写成
        git remote add origin ${远程仓库地址URL}
        
        # 验证远程仓库URL
        git remote -v
        
4. 提交代码

        git push (-u) ${远程仓库代号}  ${分支名称}
        # 一般可以写成（本地建立完分支，默认是在master分支上）
        git push origin master
        
5. 关于远程仓库地址问题

    指令结尾是git的仓库地址，可使用SSH连接方式，如

    git@XX.XX.XX.12:gyjia/hotcodeserver.git 
    
    或http连接方法

    使用SSH可能出现以下的问题

    > git@gitee.com: Permission denied (publickey).

    > fatal: Could not read from remote repository.

    > Please make sure you have the correct access rights

    > and the repository exists.

    需要将本电脑的SSH钥匙提交到GitHub上，具体根据电脑类型查询使用方法
        

## 日常提交代码的方法

### 提交到本分支

        # 如果和远程仓库有版本上的不同，需要先同步文件
        git pull
        
        # 添加全部文件
        git add . 
        
        # 添加注释
        git commit -m 'your commit message'
        
        # 提交代码
        git push


### 提交到新的分支

        # 建立本地的新分支
        git branch ${新分支的名称}
        
        # 切换到该分支上
        git checkout ${新分支的名称}
        
        # 添加全部文件
        git add . 
        
        # 添加注释
        git commit -m 'your commit message'
        
        # 提交代码
        git push ${远程仓库代号}  ${新分支的名称}
        # 一般可以写成
        git push origin ${新分支的名称}

## 其他命令
请看参考文献Git常用命令

<https://www.cnblogs.com/chenwolong/p/GIT.html>
