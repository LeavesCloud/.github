# Git多人协作

## 一、 注意事项



### 1. 流程图制作



#### 1.1 什么时候绘制流程图

(1) 当负责项目需要制作一个新的系统则应该绘制流程图方便协作者了解整个系统

(2) 当项目整体复杂度达到一定程度则应该绘制流程图以分析并处理重复或不必要的处理逻辑



#### 1.2 流程图规范

> 没有



### 2. 代码注释

(1) 当编写代码时觉得可能产生歧义的代码应该带有注释指明多者之间的区别。

(2) 当变量名无法直接表明其作用应该使用注释指明其作用。

(3) 当产生了新的方法则应该使用方法注释指明传递参数及方法作用，方便其他协作者阅读编写



### 3. 技术文档

#### 1. 什么时候写技术文档



## 二、Git规范



### 1. Git分支

分支暂定使用 `master` 。

协作者应 `fork` 个人代码副本，提交代码应创建 `pr` 请求代码合并，避免直接推送导致错误代码混淆。

#### 1.1 Fork 及 pr 提交操作步骤:

(1) 进入项目主页 → 点击 `Fork` → 创建个人副本；克隆个人副本到本地。

(2) 设置原始仓库

```
git remote add upstream https://github.com/LeavesCloud/[仓库名称]
```

(3) 提交 `pr`

```bash
git fetch upstream # 拉取最新代码
git pull upstream master # 同步原始仓库 master 代码
git checkout -b [类型表述(feat/fix...)]/[代码内容大概描述(任意)] # 创建本地分支
```

修改代码需要推送到个人备份仓库中，此处不做过多演示。

代码提交完毕后需要前往副本仓库根据目标仓库及分支创建 `pr` 请求。

❗需要保持分支与原仓库同步

```bash
git fetch upstream
git rebase upstream/master
git push origin [分支名称] --force #强制推送
```

(4) 清理代码

```bash
git checkout master
git pull upstream master
git branch -D [分支名称] # 删除本地分支
git push origin --delete [分支名称] # 删除远程分支=
```

### 2. Commit 提交

> commit 提交应该按照不同操作进行区分，以方便协作者快速定位

提交格式: `<type>: <subject>`

● type -> 提交的类型

● subject -> 提交的内容概括

| **Type** | **描述**                                     |
| -------- | -------------------------------------------- |
| feat     | 新功能或新方法                               |
| fix      | 修复 bug                                     |
| refactor | 重构                                         |
| docx     | 修改文档                                     |
| style    | 通常是对无用代码进行删除或修改代码的排版样式 |
| test     | 测试相关的代码                               |
| build    | 与 build 相关的代码                          |
