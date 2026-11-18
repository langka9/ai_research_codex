`.gitignore`是用来登记什么文件不上传到云端 github 的，通常是一些临时文件、编译生成的文件、日志文件、密钥等。“*”表示任意的意思。

看一下`todo_task\6_skill_memo.md`里关于各大厂家模型的介绍。

尝试完成以下任务，就基本掌握了工具的使用了：参考本项目，新建一个项目，逐步搭建 AI 工作流
1. 注册 github，安装 git，使用 git 将本地电脑关联自己的 github
2. 使用 VS Code ，并在插件中安装 Claude Code、Codex、CodeBuddy 插件。
3. 打开一个空的文件夹，命名为`ai_research_copy`。
4. 使用 CodeBuddy 插件作为 AI，进行以下任务，现在 CodeBuddy 可以免费使用 Hy4 模型
5. 初始化`CLAUDE.md`和`AGENTS.md`
6. 让 CodeBuddy 帮你把项目上传到你的 github 上，且作为私有项目
7. 新建一个分支`test1`（从现有来源创建新分支），然后发布分支（新建分支是在本地的，发布分支是发布到云端）
8. 在`test1`分支上，在 todo_task 目录下新建一个任务文件，并使用 CodeBuddy 完成它
9. 完成后的任务，将任务文件归档到`archived_task`中，并且在任务文件末尾记录产物有哪些
10. 在`test1`分支上，将内容进行提交（commit），并推送（push）到云端 github 上
11. 切换到`main`分支，合并`test1`分支到`main`分支中，合并后推送`main`分支
12. 合并分支之后，删除本地的`test1`分支和远程的`test1`分支（在 VSCode 里操作 git 的界面的右上角“···”中，“分支”中，有“删除分支”，“删除远程分支”）

恭喜你完成入门的 git 管理功能。

进阶任务：
1. 使用 CC Switch 管理不同厂商的模型，使用 CC Switch 进行模型切换和管理（在 CC Switch 的 Claude Code 中）
2. 使用 VS Code 中的 Claude Code 作为 AI 工具。
3. 使用 skill-manage 管理 skill