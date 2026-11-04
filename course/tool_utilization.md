# 科研开发工具准备与使用：课堂口播稿

> **使用说明：** 本稿面向第一次配置科研开发工具的 Windows 用户，正文可直接讲授；以“演示提示”标注的部分用于配合屏幕操作，不必朗读。操作说明以 2026 年 11 月 4 日查阅的厂商和项目文档为依据。软件界面、登录方式、价格、额度和可用模型会变化，授课前请按链接核对当前页面。仓库已准备的安装包清单见“仓库内安装包”一节；其中个别文件来自第三方镜像，按表中说明辨别来源。

## 本节目标

学完本节后，大家可以完成三件事：建立 GitHub 账号并在 VS Code 中打开一个项目；理解 Codex、Claude Code、桌面 Agent、Jego、Clash Verge 和 CC Switch 各自负责什么；使用 Git 保存和检查一次 AI 辅助修改，并将项目推送到自己的远程仓库。

## 开场：先把工具放进一条工作流

大家好，今天我们来准备一套可以用于科研项目的开发工具。我们会了解每个工具在工作流中承担的任务，以及怎样让它们安全地衔接起来。

先看一条最常见的工作流：Git 在本机保存文件的改动历史；GitHub 托管远程仓库，方便分享和协作；VS Code 用来打开、编辑和运行项目；Codex 或 Claude Code 在项目上下文中协助阅读和修改文件。WorkBuddy 和 Marvis 属于桌面 AI 助手，可以在授权范围内处理本地任务。Jego 与 Clash Verge 负责不同范围的网络代理配置。CC Switch 管理一些 AI 工具所使用的模型服务和接口配置。

每个工具承担的职责不同：CC Switch 管理模型服务连接配置，实际模型和额度由服务商及账号提供；Git 在本机记录版本历史，GitHub 托管远程仓库并提供协作能力。把这些关系理清楚，安装时就不容易把账号、模型、接口和项目文件混在一起。

## 第一部分：注册 GitHub，安装 Git 和 VS Code

### 1.1 注册并保护 GitHub 账号

打开 [GitHub 注册页面](https://github.com/signup)，按提示填写邮箱、用户名和密码，并完成邮箱验证。用户名会成为公开的个人标识，建议选择一个长期使用、便于辨认的名字。注册完成后，建议开启双重验证，并妥善保存恢复方式。GitHub 的账户说明也建议验证邮箱并设置双重验证。

GitHub 账号用来登录 GitHub 网站、授权 VS Code 和访问有权限的仓库。它不会自动替你保存本机文件；文件只有在提交之后推送到远程仓库，远程仓库里才会出现。

> **【演示提示】** 展示 GitHub 注册入口、邮箱验证和账号安全设置页面。屏幕上不要展示个人密码、恢复码或验证码。

### 1.2 安装 Git for Windows 并设置提交身份

Git 是安装在电脑上的版本控制工具。请从 [Git for Windows 官方安装页](https://git-scm.com/install/windows)下载适合电脑架构的 Standalone Installer。仓库的工具准备目录也放了一份 Git 安装包，文件名和版本记录在后面的清单里；课堂操作以官网提供的当前版本为准。

安装完成后，打开 PowerShell 或 VS Code 终端，输入下面的命令，确认系统能找到 Git：

    git --version

Git 需要知道应该把谁记录为一次提交的作者。请设置提交显示名称和邮箱：

    git config --global user.name "你的名字"
    git config --global user.email "你的邮箱或 GitHub 提供的 noreply 邮箱"

可以用下面的命令检查结果：

    git config --global --list

这里的 name 和 email 会写入提交历史，作为提交作者信息。网页登录和仓库操作授权由浏览器及 Git Credential Manager 处理；推送 GitHub 仓库时，Git Credential Manager 会打开浏览器让你完成授权，Git for Windows 通常已经包含它。请跟随浏览器授权流程，不要把 GitHub 密码或访问令牌写进命令、脚本或项目文件。[GitHub 的凭据缓存说明](https://docs.github.com/en/get-started/git-basics/caching-your-github-credentials-in-git?platform=windows)

### 1.3 安装 VS Code 并登录 GitHub

到 [VS Code 官方下载页](https://code.visualstudio.com/download)下载 Windows User Installer。大多数个人电脑使用 User Setup 即可，不需要管理员权限。安装后打开 VS Code，在左下角的账户菜单中选择 GitHub 登录，可以启用设置同步等账户功能。

要区分 VS Code 界面里的账号登录和 Git 操作的认证。克隆私有仓库或向 GitHub 推送时，VS Code 可能另行弹出授权流程；完成之后，Git Credential Manager 会保存授权信息。作者邮箱仍由前一步的 Git 配置决定。VS Code 对 GitHub 的说明和 Git 快速入门分别介绍了这两类操作：[GitHub 集成](https://code.visualstudio.com/docs/sourcecontrol/github)；[VS Code Git 快速入门](https://code.visualstudio.com/docs/sourcecontrol/quickstart)。

> **【演示提示】** 安装 Git 后重新打开 VS Code，在终端运行 git --version。再从账户菜单登录 GitHub，并说明这一步与后续 Git 推送时可能出现的浏览器授权各自负责什么。

## 第二部分：认识并安装桌面 AI 工具

### 2.1 Codex 桌面端

Codex 桌面端是 OpenAI 面向编程任务的独立应用。它可以围绕一个项目处理代码工作。Windows 安装入口请从 [OpenAI Codex 页面](https://openai.com/codex/)或 [ChatGPT 官方下载页](https://chatgpt.com/download/)进入，再按当前页面的指引安装和登录。登录方式和使用额度以当前账号及官方页面说明为准。

第一次使用时，先打开一个专门的练习项目，向它提一个范围很小的要求，例如：“请阅读这个项目的 README，用三点说明项目用途，暂时不要修改文件。”熟悉它能看到哪些文件、在哪里显示改动之后，再尝试让它修改一个简单的示例文件。OpenAI 也提供 Codex 的 [VS Code IDE 扩展说明](https://developers.openai.com/codex/ide)；桌面应用和 IDE 插件是不同入口，后面会分别介绍。

### 2.2 Claude Desktop 与 Claude Code

Claude Desktop 是 Claude 的桌面聊天应用，适合开展一般问答和文档讨论。请从 [Anthropic 官方下载页面](https://www.anthropic.com/claude)选择 Windows 版本，安装后按页面提示登录。可以从一个不含隐私数据的摘要或公开论文开始，要求它整理研究问题、方法和结论，再回到原文核对。

Claude Code 是面向代码项目的编程 Agent，可在终端或受支持的 IDE 中工作。Claude Desktop 面向一般问答和文档讨论，Claude Code 面向项目代码操作。我们这节重点使用 VS Code 中由 Anthropic 发布的 Claude Code 扩展；安装和使用说明见 [Claude Code in VS Code 官方文档](https://code.claude.com/docs/en/ide-integrations)。仓库中名为 Claude-win-x64.msix 的包在旧 README 中被描述为“Claude Code 桌面版”，与 Anthropic 当前产品名称可能不一致；下载时请核对产品名称、发布者和官方安装方式。

### 2.3 WorkBuddy 和 Marvis

WorkBuddy 和 Marvis 可以用自然语言处理一些桌面任务。它们的权限可能包括读取或修改本地文件，部分操作还会涉及电脑设置。安装时使用厂商当前下载页：[腾讯 WorkBuddy](https://cloud.tencent.com/product/workbuddy)；[腾讯 Marvis](https://marvis.qq.com/)。登录和可用功能以软件当前提供的方式为准。

初次使用时，请建立一个不含敏感材料的练习文件夹，只授权这个文件夹。先让 Agent 列出它准备查看或修改的内容，再决定是否允许执行。Marvis 官网介绍了效率模式和本地模式；如果要处理敏感文件，应先确认当前模式、数据是否会上传，以及本地运行的功能范围。不要因为工具能自动操作电脑，就默认授权整个磁盘或自动同意所有修改。

如果用 Agent 协助检查网络配置，先让它说明准备读取和修改哪些配置，保存原有配置，再由用户逐项确认。涉及学校网络或受管理设备时，先按学校规定处理网络问题。

> **【演示提示】** 用练习目录中的一个公开或虚构文本文件演示“先阅读并说明计划，再执行小范围操作”。避免使用私人论文、未公开数据、真实密钥或学校网络配置作为演示材料。

## 第三部分：Jego 和 Clash Verge 的基本配置

Jego（无忧行）提供浏览器插件和订阅服务两类使用方式。浏览器插件只处理安装了插件的浏览器；订阅服务则通过兼容客户端供其他应用使用。初次安装请按[无忧行浏览器插件安装说明](https://help.jegovpn.com/guide/installation)从 Chrome Web Store 或 Microsoft Edge 扩展商店添加，再登录并按页面提示选择使用方式。无忧行帮助文档说明，订阅地址可在登录后的控制面板“订阅节点”页面查看；订阅链接可能包含账号凭据，应像密码一样保管。[无忧行订阅说明](https://help.jegovpn.com/subscription/)

课堂演示可以按下面的顺序进行：先从 Jego 官方入口安装浏览器插件并按其页面说明登录；如果需要在桌面客户端中使用，再确认账号当前拥有适用的订阅服务，然后在控制面板找到对应订阅地址并复制。价格、权益和可用节点会变化，购买前以控制面板显示为准。

Clash Verge Rev 是管理代理配置和配置文件的桌面客户端。请从 [Clash Verge Rev 项目页面](https://github.com/clash-verge-rev/clash-verge-rev)及其文档进入当前下载渠道。安装后，在配置或 Profiles 页面选择“从订阅链接导入”一类入口，粘贴刚才复制的订阅地址，保存并等待配置下载完成。随后选择新配置文件，按客户端文档选择连接模式和可用策略组。订阅导入方式见 [Clash Verge Rev 官方说明](https://www.clashverge.dev/guide/profile.html)。

如果导入失败，先检查链接是否复制完整、订阅是否有效、网络是否可连接，再查客户端文档和服务商帮助页。不要把订阅地址发到群聊、公开仓库或截图中。请遵循当地规定、学校网络管理要求和服务条款；学校网络出现连接问题时，使用学校允许的排查途径。

> **【演示提示】** 演示时可用测试订阅或遮盖敏感部分的截图，展示“控制面板复制链接—客户端导入—选择配置—查看连接状态”的流程。不要把真实订阅地址留在课件、录屏或聊天记录里。

## 第四部分：CC Switch、模型服务与兼容接口

### 4.1 CC Switch 负责什么

CC Switch 是一个配置管理工具，可以为 Codex、Claude Code 等客户端管理不同的服务商配置。常见字段包括服务商、API 地址、模型名称和 API Key。模型推理服务、API 额度和计费由你配置的平台提供。当前功能和支持的工具以 [CC Switch 官方文档](https://ccswitch.io/en/docs)为准。

有些客户端只能有一个当前生效的服务商配置；CC Switch 可以帮助在不同配置之间切换，省去手动修改多个配置文件。先选择要配置的应用，再添加服务商预设或自定义配置，核对服务商给出的 Base URL、API Key、模型 ID 和接口格式，保存后启用。服务商提供预设时，优先从预设开始；手动填写时照着服务商自己的 API 文档逐项核对。

### 4.2 OpenAI 兼容接口和 Claude 兼容接口

可以把 API 接口格式想成一份约定好的“点单表格”：客户端按约定填写模型名称、输入内容和工具调用要求，服务端按同一约定接收并返回结果。所谓 OpenAI 兼容，是服务商支持某一种 OpenAI API 请求格式；所谓 Claude 或 Anthropic 兼容，是服务商支持 Anthropic Messages 请求格式。

“兼容”描述请求格式是否匹配。不同服务商提供的模型和功能仍有差异，具体还要核对接口路径、模型 ID、流式输出、工具调用、上下文限制、费用和隐私政策。即使两个平台都写着 OpenAI compatible，它们支持的 OpenAI 接口类型也可能不同。

当前 CC Switch 文档将 Codex 的原生请求格式说明为 OpenAI Responses API，将 Claude Code 的原生请求格式说明为 Anthropic Messages。OpenAI Chat Completions、Responses 和 Anthropic Messages 是不同的接口格式。服务商若只支持其中另一种格式，通常需要由兼容路由转换；转换能否保留所需功能，要看客户端、CC Switch 和服务商的具体支持。[CC Switch 上游格式说明](https://ccswitch.io/en/docs?item=add&section=providers)；[本地路由说明](https://ccswitch.io/en/docs?item=service&section=proxy)。

### 4.3 什么时候需要路由

如果客户端与服务商提供相同的接口格式，通常可以直接连接。如果格式不同，例如 Claude Code 使用 Anthropic Messages，但服务商只开放 OpenAI Chat Completions，就可以在 CC Switch 中配置本地路由，让请求先经过本机的 CC Switch，再转换成服务商支持的格式。

使用路由时，需要在 CC Switch 中启动对应应用的路由，并让本地路由服务保持运行。切回直连配置后，客户端会直接访问服务商。接口转换会带来额外的兼容条件，所以遇到模型列表为空或工具调用失败时，检查模型 ID、API 地址、密钥和格式配置，并确认服务商实际支持相应功能。

API Key 具有调用账号服务的权限。只在可信的客户端和服务商中配置，不要放进 README、代码、截图、公开仓库或课堂录屏。使用第三方模型服务前，先确认费用规则和数据处理方式。演示时用占位符，不展示真实密钥。

> **【演示提示】** 在 CC Switch 中展示 Codex 与 Claude Code 两个配置页的字段差异。可以用虚构 API 地址、虚构模型名和“此处填写自己的 API Key”作为示例，演示直连和路由开关，不实际公开任何账号信息。

## 第五部分：在 VS Code 中使用 Codex 和 Claude Code

打开 VS Code 的扩展视图，搜索官方扩展名称和发布者。Codex 扩展应核对发布者为 OpenAI；Claude Code 扩展应核对发布者为 Anthropic。安装完成后，按扩展提示登录并打开一个本地项目文件夹。扩展市场中名称相近的第三方工具很多，先确认发布者再安装。

这类编程 Agent 会参考当前项目中的文件，也可能提出修改或运行命令。第一次不要让它“改好整个项目”。可以先提出范围明确的任务，例如：“先阅读 README 和 src 目录，概括项目结构；只给我一份修改计划，不要改文件。”确认它理解了项目之后，再给一个可检查的小任务，例如“在 README 中增加一段运行环境说明，完成后列出改动文件”。

模型菜单会显示当前账号或已配置服务商提供的可用选项。Codex 扩展中的模型选择入口由扩展当前界面提供；Claude Code 可以通过当前模型选择菜单或 /model 命令查看可用选项。列表里的模型受账号权限、服务商配置和接口支持限制。CC Switch 用于切换客户端连接的服务商和模型配置。使用路由时，需要保证 CC Switch 路由服务正常运行；更改配置后若扩展仍使用旧状态，按工具文档重新载入或重启对应会话。

给编程 Agent 下任务时，尽量交代四件事：要完成什么、相关文件在哪里、哪些行为不要做、完成后怎样检查。例如：“请修改练习项目的 README，补充 Windows 安装步骤；先检查现有内容，保留原有章节，不要运行外部安装脚本；修改后说明差异。”执行之后逐项查看差异，再决定是否保留。

> **【演示提示】** 在 VS Code 扩展面板中演示查找并确认 OpenAI 和 Anthropic 发布者、安装插件、完成登录、打开项目、查看模型菜单和一次小型修改。模型名称和按钮位置以当前插件版本界面为准。

## 第六部分：用 Git 管理项目并与 GitHub 同步

现在我们把刚才使用的练习项目交给 Git 管理。Git 会先在本机记录版本。GitHub 负责保存远程仓库并提供协作功能。VS Code 的 Source Control 视图和命令行 Git 操作的是同一个仓库。

在 VS Code 中打开练习项目文件夹，选择 Source Control（源代码管理）视图，再选择 Initialize Repository（初始化仓库）。如果习惯使用终端，也可以在项目文件夹运行：

    git init
    git status

修改文件后，先在 Source Control 里查看改动，再选择要保存的文件并 Stage（暂存）。输入清楚的提交说明，例如“Add Windows setup notes”，然后 Commit（提交）。对应的命令行操作大致是：

    git add README.md
    git commit -m "Add Windows setup notes"

这里可以记住一条顺序：工作区中的修改先经过暂存，再形成一个本地提交。提交说明帮助你以后理解这一版改了什么。提交本身只保存在本机。

分支可以理解成一条独立的改动路线。要尝试一个新功能时，先从状态栏的分支菜单新建分支，或在终端使用：

    git switch -c demo/first-change

在这个分支上修改、检查并提交。确认结果后，再按项目需要合并到主分支。这样可以把实验性改动与主线分开，也方便回到先前提交。

要把项目放到 GitHub，可以使用 VS Code 命令面板里的 Publish to GitHub，或先在 GitHub 创建仓库，再按提示设置 remote 并推送。第一次课堂练习建议创建仅自己可见的私有仓库。推送成功后，检查 GitHub 网页上的文件和提交记录。已有远程仓库的项目可以使用 Pull 下载远程更新，用 Push 上传本地提交；操作之前先确认当前分支和状态，尤其不要在不了解差异时反复执行同步或强制覆盖。

Git 提交历史不包含尚未提交或被忽略的文件。推送到 GitHub 能增加一份远程副本，但远程仓库也可能被误删、权限变更或错误覆盖；重要研究数据和论文材料仍应依照课题组的数据管理要求做独立备份。推送前检查 .gitignore，确认密钥、个人数据、未公开研究数据和大型原始数据没有被误加到仓库。

> **【演示提示】** 用练习目录演示初始化仓库、修改一个文件、查看差异、暂存、提交、创建分支、推送到私有 GitHub 仓库并查看提交历史。演示期间可用 git status 和 git log --oneline 检查本地状态与历史。

## 第七部分：仓库内安装包

下面列出 tool_preparation/README.md 中与本课相关的 Windows 安装包。表中版本来自文件名或 README；这些文件名不代表目前最新版本，本稿也未独立验证本地文件的数字签名。对桌面 Agent 和模型客户端，课堂安装以对应厂商的官方页面为准；安装本地备包前先核对发布者、来源和当前版本。

| 工具 | 仓库内文件 | README 所列来源或注意事项 |
|---|---|---|
| Git for Windows | Git-2.56.0.4-64-bit.exe | Git 官方 Windows 安装页 |
| VS Code | VSCodeSetup-x64-1.144.1.exe | VS Code 官方下载页 |
| Clash Verge Rev | Clash.Verge_2.5.9_x64-setup.exe | Clash Verge Rev 项目仓库 |
| Codex | Codex-Windows-x64.msix | README 指向 Wangnov/codex-app-mirror，属于第三方镜像来源；优先从 OpenAI 官方入口安装 |
| Claude 桌面应用 | Claude-win-x64.msix | README 指向 Wangnov/claude-app-mirror；核对 Anthropic 当前产品名称、发布者和官方安装方法 |
| WorkBuddy | WorkBuddy-win32-x64-user-5.9.3.42398134-d4692421.exe | README 指向 WorkBuddy 网站；当前安装入口以腾讯 WorkBuddy 官方页面为准 |
| Marvis | marvis_9cb66bd5b7eee38b.exe | README 指向 Marvis 官方网站；按官网当前版本核对 |
| Jego | JegoV1.5.12.zip | README 未注明该 ZIP 的来源；使用 Jego 官方帮助页和浏览器商店链接核对 |
| CC Switch | CC-Switch-v4.0.25-Windows.msi | README 指向 CC Switch 官方网站；按当前文档确认版本和功能 |

完整软件包说明和链接见 [tool_preparation/README.md](../tool_preparation/README.md)。

## 结尾：把 AI 改动纳入可检查的研究流程

今天我们从 GitHub 账号开始，安装 Git 和 VS Code，认识 Codex、Claude Desktop、WorkBuddy、Marvis、Jego、Clash Verge 和 CC Switch，再把 Codex 与 Claude Code 放进 VS Code。最后，我们用 Git 保存一次改动，并把项目同步到 GitHub。

请记住三个习惯：第一，授权 AI 之前先确认它要访问的文件和要执行的操作；第二，模型服务的 API Key、订阅地址和研究数据都要妥善保管；第三，AI 改完文件后先检查差异，再提交和推送。工具可以帮我们减少重复劳动，研究者仍然要对数据、代码和研究结论负责。

## 社区补充阅读

本教程也检索了知乎和 CSDN 的操作经验文章，用于了解初学者常遇到的配置问题。社区文章可能对应较旧版本、第三方服务或不同账号方案；涉及安装来源、认证、费用和接口格式时，请以工具厂商及项目官方文档为准。

- 知乎：[用 CC Switch 管理 Claude Code 和 Codex 的模型服务配置](https://zhuanlan.zhihu.com/p/2048779842519294952)
- CSDN：[Codex 在 VS Code 中的使用指南](https://blog.csdn.net/Interview_TC/article/details/158500825)
