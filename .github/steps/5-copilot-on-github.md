## Step 5: 在 Pull Request 中使用 Copilot

恭喜你！🎉 到这里，你已经完成了本次课程的所有编码环节。
接下来，我们需要将把成果合并到主分支中。

### 📖 理论: 在 Pull Request 中使用 Copilot

#### Copilot 自动生成 PR 摘要

在之前的课程中，我们创建 Pull Request 时，我们通常会根据备注和提交信息手动撰写摘要。但如果提交记录不够规范或缺少注释，这一步往往就比较耗时。
好消息是，**Copilot** 可以自动阅读 PR 中的所有更改，帮你生成一份包含重点变更与引用的专业摘要。

#### Copilot 代码审查

在合并代码前，多一双“眼睛”总是好事。我们可以请 **Copilot** 先进行一次初步审查，再进入人工代码评审环节。
Copilot 擅长发现常见的小问题，并给出简单的修改建议。不过要记住——它只是辅助工具，最终判断仍需由开发者完成。

> [!NOTE]
> 这些功能仅对 **GitHub Copilot 付费用户**开放。[官方文档](https://docs.github.com/en/copilot/get-started/plans)

### :keyboard: 实操环节：使用 Copilot 生成摘要并审查 PR

**Copilot PR 摘要**和**Copilot 代码审查**目前属于受限功能，如果你没有访问权限，可以跳过对应步骤。

1. 打开浏览器，进入你的练习项目仓库。

2. 你可能会看到一个提示横幅，建议你创建新的 Pull Request。点击它，或前往顶部的 **Pull Requests** 标签页，新建一个 PR，参数如下：

   * **base 分支：** `main`
   * **compare 分支：** `accelerate-with-copilot`
   * **标题：** `Improve student activity registration system`

3. （可选）在 PR 描述编辑栏点击 **Copilot 图标**，选择 **Summary** 操作。稍等片刻，Copilot 会自动生成一段基于代码更改的摘要说明。📝

   <img alt="Copilot summarize button " width="450px" src="https://github.com/user-attachments/assets/7a712d8b-484d-41df-9353-bc2b397fc1e0">

4. （可选）在右侧信息面板顶部的 **Reviewers** 区域，点击 **Copilot 图标旁的 Request 按钮**。等待片刻，Copilot 会自动在你的 PR 下留下审查意见。

   <img alt="Copilot review button" width="300px" src="https://github.com/user-attachments/assets/39b15002-a235-4c25-b09d-6a8097e27b62">

   > 💡 **提示：** 你可以在日志中看到“已请求 Copilot 审查”的记录。

5. 最后，点击底部的 **Merge pull request** 按钮。干得漂亮！🎉 你已经完成所有步骤！

6. 稍等片刻，Mona 会自动检查你的成果，并在评论区留下最终反馈。