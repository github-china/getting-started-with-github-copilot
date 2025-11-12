## Step 1: Hello Copilot

欢迎来到 **“GitHub Copilot 入门”** 课程! :robot:

在本课程中，你将和 GitHub Copilot 一起动手参与一个真实项目 —— 帮助优化 Mergington 高中的学生课外活动报名网站。🎻 ⚽️ ♟️

<img width="600" alt="Mergington High School 网站截图" src="https://github.com/user-attachments/assets/472398fd-1aa1-4084-b443-4e242deb30d9" />  

### 📖 认识 GitHub Copilot

<img width="150" align="right" alt="copilot logo" src="https://github.com/user-attachments/assets/4d22496d-850b-4785-aafe-11cba03cd5f2" />

GitHub Copilot 是一款由 AI 驱动的编程助手，可以帮助你更快、更高效地编写代码，让你能把精力集中在问题分析和协作上。

研究证明，GitHub Copilot 能显著提升开发者的生产力，加快软件开发节奏。
更多研究细节可参考 [GitHub 博客：量化 Copilot 对开发者效率与幸福感的影响](https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/)。

你可以通过以下几种方式在 IDE 中与 Copilot 交互：

| 交互模式                           | 📝 功能说明                                                     | 🎯 适用场景             |
|--------------------------------| -------------------------------------------------------------- | ------------------- |
| **⚡ 内联建议（Inline Suggestions）** | 当你输入代码时，Copilot 会实时给出基于上下文的智能补全，从单行到整段函数。 | 补全当前代码行或快速生成新代码块    |
| **💬 问答模式（Ask Mode）**          | 用于回答关于代码、项目结构或技术概念的问题。                            | 理解代码逻辑、头脑风暴、技术提问    |
| **✏️ 编辑模式（Edit Mode）**         | 支持跨文件修改，VS Code 会直接在编辑器中应用修改供你审查。               | 明确知道要修改的功能或文件时使用    |
| **🤖 智能体模式（Agent Mode）**       | Copilot 会在多个文件间自主完成修改，甚至执行命令行任务。                | 任务定义较模糊、可能涉及运行工具的情况 |
| **💭 内联对话（Inline Chat）**       | 针对当前文件或代码选区的互动聊天，可提问或请求修改。                     | 代码解释、调试、优化局部功能      |

除了 VS Code，Copilot 还可在 `github.com`、JetBrains、Xcode 等环境中使用。
本次课程我们将在基于 VS Code 的云端开发环境 —— [GitHub Codespace](https://github.com/features/codespaces) 中进行实战练习。

> [!TIP]
> 想了解更多功能？请参考 [GitHub Copilot 功能文档](https://docs.github.com/en/copilot/about-github-copilot/github-copilot-features)

### :keyboard: 实操环节: 通过 Copilot Chat 了解项目概况

接下来，我们将启动开发环境，通过 Copilot 来了解项目概况，并实际运行项目。

1. 点击下方按钮，在新标签页中打开 **Create Codespace** 页面，保持默认配置。

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

2. 确认 **Repository** 显示的是你自己练习的仓库，而不是原始仓库，然后点击绿色的 **Create Codespace** 按钮。

   - ✅ 你的: `/{{full_repo_name}}`
   - ❌ 原始: `/skills/getting-started-with-github-copilot`

3. 等待 VS Code 在浏览器中加载完成。

4. 打开左边栏的扩展（Extensions）菜单，确认 `GitHub Copilot` 和 `Python` 插件均已安装并启用。

   <img width="350" alt="copilot extension for VS Code" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" />

   <img width="350" alt="python extension for VS Code" src="https://github.com/user-attachments/assets/3040c0f5-1658-47e2-a439-20504a384f77" />

5. 点击 VS Code 顶部的 **Toggle Chat 图标**，打开 Copilot 聊天侧边栏。

   <img width="150" alt="image" src="https://github.com/user-attachments/assets/abf584e9-ef68-4725-8b22-4803805e6d55" />

   > 🪧 **Note:** If this is your first time using GitHub Copilot, you will need to accept the usage terms to continue.

6. 确认当前处于 **Ask Mode（问答模式）**。

   <img width="350" alt="screenshot showing Ask Mode selection in Copilot Chat" src="https://github.com/user-attachments/assets/fb1d7cac-2d39-4199-b5d9-0f3dfcfb3bcd" />
7. 输入以下提示词，请 Copilot 简要介绍项目结构和运行方式：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace Please briefly explain the structure of this project.
   > What should I do to run it?
   > ```

   > 🪧 **提示:** 无需完全照做 Copilot 的建议，我们已为你准备好完整环境。

   <details>
   <summary>@workspace 是什么?</summary>
 
   它是一个特殊的[聊天参与者](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants)。
   能够提供有关工作区中代码的上下文信息。 当希望 Copilot 考虑项目的结构，参考项目中不同文件之间的关系时请使用 @workspace。

   </details>

8. 了解完项目后，让我们实际运行一下！点击左侧边栏的 **Run and Debug** 菜单，然后按下 **Start Debugging** 图标。

   <img width="300" alt="image" src="https://github.com/user-attachments/assets/50b27f2a-5eab-4827-9343-ab5bce62357e" />

9. 想在浏览器中访问网页，我们需要找到访问地址和端口。在底部面板中找到 **Ports** tab页。 找到端口号 `8000`，将鼠标悬停在其链接上，点击 **Open in browser（在浏览器中打开）**。

   ![image](https://github.com/user-attachments/assets/92d5642e-ce99-4a66-850c-2d311a673596)

### :keyboard: 实操环节: 使用 Copilot 执行 git 命令 🙋

网站已成功运行起来了。接下来，让 Copilot 帮我们创建一个分支，用来做个小改动。

1. 在 VS Code 底部面板中，切换到 **Terminal** 标签页，然后点击右上角的 “+” 号，打开一个新终端窗口。
2. 在新终端中，按下快捷键 `Ctrl + I`（Windows）或 `Cmd + I`（Mac），调出 **Copilot 的终端内联聊天窗口**。

3. 假设我们需要新建一个分支并把它推送到到远程仓库，但我们忘记了命令，我们可以这样对Copilot说：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Hey copilot, how can I create and publish a new Git branch called "accelerate-with-copilot"?
   > ```

   > 💡 **提示:** 如果 Copilot 的回答不太准确，可以继续补充说明，它会记住上下文进行调整。

4. 然后点击 `Run` 按钮，Copilot 会直接执行命令，无需手动复制粘贴。

5. 稍等片刻后查看 VS Code 左下角状态栏，当前分支应显示为 `accelerate-with-copilot`。若已切换成功，说明你完成了此步骤！

6. 分支推送到 GitHub 后，Mona 会自动开始检查你的任务。稍等片刻，她会在评论中回复进度与下一步任务。

<details>
<summary>遇到问题? 🤷</summary><br/>

若未收到反馈，请检查以下事项：

- 确认分支名称是否为 `accelerate-with-copilot`。
- 确认分支是否成功推送到你的仓库中。

</details>
