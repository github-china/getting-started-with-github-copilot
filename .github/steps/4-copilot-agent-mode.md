## Step 4: Copilot 智能体模式 🚀

### 📖 什么是 Copilot 智能体模式(Agent Mode)?

Copilot [Agent Mode](https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode) 是AI编程助理的最新进化形态。它能独立思考，感知环境，自主规划并完成任务。

在该模式下，Copilot 不仅能自动响应编译和语法错误，还会实时监控终端与测试输出，并在出现问题时自动修复，持续循环，直到任务完成。

#### 编辑模式 vs 智能体模式

| 对比维度      | ✏️ Edit 模式  | 👩‍🚀 Agent 模式                                  |
| ------------ | ----------- | ------------------------------------------------|
| **上下文范围** | 仅限你明确添加的文件  | 可根据任务需要自动读取或修改更多文件           |
| **自我校验**  | 基本无（需你手动迭代） | 内置反馈与自动重试机制                       |
| **修改范围**  | 精准、局部性强     | 可影响多个相关层面以保持一致性                    |
| **适用场景**  | 你明确知道要改什么   | 任务较模糊、需要探索或推理                      |
| **工具调用**  | 无（需手动执行命令）  | 可调用工具（读取/修改文件、运行命令、查看测试输出） |

#### 🧰 工具调用

在处理用户请求时，智能体模式会调用不同的工具来完成目标任务，例如：

* 查找与任务相关的文件
* 获取网页内容
* 运行测试或执行命令

> [!TIP]
> 除了 VS Code 内置的工具外，你还可以通过 **MCP（Model Context Protocol）** 调用更多工具。
>
> 了解更多请阅读 [MCP servers](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) 以及 [GitHub MCP Server](https://github.com/github/github-mcp-server)

下面我们开始体验一下 **智能体模式** 吧！👩‍🚀

### :keyboard: 实操环节: 使用 Agent 模式增加“取消报名”按钮

1. 打开 **Copilot 聊天面板**，通过下拉菜单切换到 **Agent 模式**。

   <img width="250" alt="agent mode" src="https://github.com/user-attachments/assets/9bb85530-77a1-4d47-86b2-99769ce197db" />

1. 点击 **工具（Tools）图标**，浏览当前 Agent 模式可用的所有工具。

   <img width="250"  alt="tools icon" src="https://github.com/user-attachments/assets/8f73400a-2647-4b28-b52b-721b8cf348d8" />


1. 准备测试！请 Copilot 帮你添加删除报名者的功能：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > #codebase Please add a delete icon next to each participant and hide the bullet points.
   > When clicked, it will unregister that participant from the activity.
   > ```

   其中的 `#codebase` 工具会帮助 Copilot 定位到相关文件和代码块，以便更准确地执行任务。

   > 🪧 **Note:** 本课程中我们显式添加了 `#codebase` 来确保输出结果稳定。
   > 你也可以尝试去掉它，看看 Agent 模式是否会自动扩展上下文范围。

1. Copilot 完成修改后，重启调试器，预览网页效果。如果结果满意，点击 **Keep** 按钮保存更改。如果不满意，可直接给出反馈，让 Copilot 进一步改进。

1. 还有一个注册时的小问题需要 Copilot 修复

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > I've noticed there seems to be a bug.
   > When a participant is registered, the page must be refreshed to see the change on the activity.
   > ```

1. Copilot 完成后需要审查结果。满意就按 **Keep**，不满意就反馈给 Copilot 继续优化。

### :keyboard: 实操环节：使用 Agent 模式编写测试 🧑‍🚀

现在后端功能越来越完善，但还缺少测试覆盖。 这一步，我们将使用 **Agent 模式** 来自动添加测试依赖、生成测试代码并运行。

1. 在 **Agent 模式** 下向 Copilot 输入以下提示词：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-placeholder?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Add fastapi tests using pytest in a new tests directory and run them.
   > Make sure to add any new dependencies to requirements.txt
   > ```

1. 在 Copilot 执行过程中，部分工具可能需要你手动确认。

   **🎯 目标: 让所有测试通过（显示绿色）—— 追求一次性成功！✅**

   > 🪧 **提示:** Copilot 可能一次就完成任务，也可能需要你补充说明。

1. 所有测试通过后，**提交并推送**修改到你的 `accelerate-with-copilot` 分支。
   🎉 快完成了！进入最后一步吧！