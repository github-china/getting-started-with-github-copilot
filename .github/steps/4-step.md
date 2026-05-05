## 步骤 4: 使用 Plan Agent 设计你的实现 🧭

在上一步中，Agent Mode 帮助我们快速完成了功能开发，让迭代速度大幅提升。 🚀

这一步我们换一种更“工程化”的方式：先设计方案，再执行实现。就像架构师一样，先把路径规划清楚，再交给开发去落地，这样可以减少不确定性，让结果更稳定、结构更清晰 🧪

### 📖 理论: 什么是 Copilot Plan Agent?

Copilot [Plan Agent](https://code.visualstudio.com/docs/copilot/agents/planning) 用于在真正修改代码之前，先帮助你设计完整的解决方案。

它不会一上来就改代码，而是会：

- 分析你的需求
- 主动提出澄清问题
- 生成可执行的实现计划
- 根据你的反馈不断优化方案

#### Plan Agent 一览

| 方面    | 🧭 Plan Agent 表现                                  |
| ----- | ------------------------------------------------- |
| 目标    | 在编码前生成结构化实现方案                                     |
| 上下文获取 | 以只读方式分析代码与需求                                      |
| 协作方式  | 提问 + 迭代优化计划                                       |
| 迭代能力  | 支持多轮方案调整                                          |
| 安全机制  | 在你确认前不会修改任何文件                                     |
| 执行切换  | 点击 **Start implementation** 后交由 Agent Mode 执行代码实现 |


> [!TIP]
> 你可以先提出一个高层需求，然后逐步补充约束条件，让计划越来越完善。

### ⌨️ 实操环节: 使用 Plan Agent 设计并实现后端测试

目前我们的后端还没有任何测试覆盖，现在我们用 **Plan Agent** 来设计一套测试方案，并最终自动实现它。

1. 打开 **Copilot Chat** 面板，将模式切换为 **Plan Agent（规划模式）**。

   <img width="350" alt="image" src="../images/plan-mode-dropdown.png" />


1. 我们先提出初始需求，让 Copilot 帮我们补充细节：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > I want to add backend FastAPI tests in a separate tests directory.
   > ```

1. 请等待 Copilot 生成初步方案。如果它向您提出任何问题，请您尽可能回答。 

   > 🪧 **注意:** 不需要一次就完美实现，可以逐步完善方案

1. 你可以继续补充约束，让方案更专业，例如：

   例如下面：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Let's use the AAA (Arrange-Act-Assert) testing pattern to structure our tests
   > ```

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Make sure we use `pytest` and add it to `requirements.txt` file
   > ```


1. 当你对方案满意后，点击 **Start implementation** 开始真正干活。

   <img width="350" alt="image" src="../images/plan-mode-start-implementation.png" />

   请注意，点击该按钮后，模式已从 **Plan** 切换到了 **Agent Mode**。从此刻起，Copilot 即可像往常一样编辑您的代码库。

1. 观察 Copilot 执行，执行过程中可能会请求某些权限（例如，执行命令或创建虚拟环境）。请批准这些权限，以便它能继续工作。

1. 查看本次代码修改，并确认测试已成功运行。如果需要，可以继续引导 Copilot 调整，直到实现全部完成。

   **🎯 目标: 确保所有测试运行成功，并显示为绿色通过状态 ✅**

   > 🪧 **注意:** 任务可能一次性就通过，也可能需要你通过后续提示进行进一步引导和调整

1. 完成后提交代码并推送到 `accelerate-with-copilot` 分支。

1. 提交完成后，Mona 会自动检查你的测试实现，并给出下一步指引

<details>
<summary>遇到问题? 🤷</summary><br/>

- 如果测试没有运行，可以让 Copilot 帮你执行测试命令
- 确认 `pytest` 已添加到 `requirements.txt` 文件中，并且项目中已创建 `tests/` 目录

</details>
