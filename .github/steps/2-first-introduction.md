## Step 2: 借助 Copilot 快速完成任务

在上一步中，GitHub Copilot 已经帮助我们顺利上手项目。这本身就节省了大量时间，但现在是时候真正开始干活了！

:bug: **糟糕，网站上出现了一个 BUG** :bug:

我们发现报名流程有点问题：学生竟然可以重复报名同一个活动！😱
考验 Copilot 的时候到了，看它能否帮助我们找出问题来源并修复。

开始前，先简单了解一下 Copilot 的工作原理。🧑‍🚀

### 📖 Copilot 工作原理

简单来说，可以把 Copilot 想成一个“专家级的同事”。想让它帮你高效的完成工作，就得给它足够的背景信息（context）和清晰的指令（prompt）。而不同的模型（model）就像不同的同事，有各自的强项。

* **如何提供上下文?:** 在开发环境，Copilot 会自动参考你周围的代码和打开的文件；如果你用聊天功能，还可以直接引用文件。
* **选择模型：** 本次练习中选哪个模型不是我们关注的焦点，可以自行尝试，体会不同模型的特点与效果。🤖
* **如何写提示词（prompt）：** 指令要清楚明确，这样 Copilot 才能给出最贴切的结果；当然，你也可以随时补充说明，它能理解上下文继续帮你完善。

> [!TIP]
> 你还可以通过 [聊天参与者](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants)、[聊天变量](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-variables)、[斜杠命令](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#slash-commands-1) 和 [MCP 工具](https://code.visualstudio.com/docs/copilot/chat/mcp-servers) 等方式进一步增强 Copilot 的能力。

### :keyboard: 实操环节: 使用 Copilot 修复 bug :bug:

1. 首先让 Copilot 定位 bug 的来源。打开 **Copilot Chat 面板**，选择 **Ask 模式**，然后输入：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace Students are able to register twice for an activity.
   > Where could this bug be coming from?
   > ```

2. Copilot 会告诉你问题出在 `src/app.py` 文件的 `signup_for_activity` 方法中。接下来我们按它的建议手动修复。

   1. 打开 VS Code 找到并打开 `src/app.py` 文件。

   2. 滚动到文件底部附近，找到 `signup_for_activity` 方法。

   3. 找到那条 “Add student” 的注释，在它上方添加注册校验逻辑。

   4. 输入下面这行注释后按下回车，稍等片刻，你会看到 Copilot 自动出现代码建议：

      ```python
      # Validate student is not already signed up
      ```

   5. 按下 `Tab` 键接受建议并生成代码。

   <details>
   <summary>参考示例代码</summary><br/>

   注意：Copilot 每天都在不断进步，因此生成的结果可能会有所不同。
   如果你对当前的建议不太满意，可以参考我们给出的示例结果，用它来继续完成后续步骤。

   ```python
   @app.post("/activities/{activity_name}/signup")
   def signup_for_activity(activity_name: str, email: str):
      """Sign up a student for an activity"""
      # Validate activity exists
      if activity_name not in activities:
         raise HTTPException(status_code=404, detail="Activity not found")

      # Get the activity
      activity = activities[activity_name]

      # Validate student is not already signed up
      if email in activity["participants"]:
        raise HTTPException(status_code=400, detail="Student is already signed up")

      # Add student
      activity["participants"].append(email)
      return {"message": f"Signed up {email} for {activity_name}"}
   ```

   </details>

### :keyboard: 实操环节: 用 Copilot 生成示例数据 📋

开发新项目时，经常需要生成用于测试的模拟数据。Copilot 在这方面非常强！我们可以在 `src/app.py` 文件顶部（大约第 23 行）找到 `activities` 变量，在这里让 Copilot 帮我们生成更多示例活动。

1. 点击 `activities` 的任意一行，按下快捷键 `Ctrl + I`（Windows）或 `Cmd + I`（Mac）打开 **Inline Chat**。
2. 输入以下提示词并回车：

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Add 2 more sports related activities, 2 more artistic
   > activities, and 2 more intellectual activities.
   > ```

3. Copilot 会直接在原来的基础上修改代码，你可以查看修改后点击 **Accept** 接受建议。

   <details>
   <summary>示例结果</summary><br/>

   如果你对当前的建议不太满意，可参考下面的完整样例

   ```python
   # In-memory activity database
   activities = {
      "Chess Club": {
         "description": "Learn strategies and compete in chess tournaments",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 12,
         "participants": ["michael@mergington.edu", "daniel@mergington.edu"]
      },
      "Programming Class": {
         "description": "Learn programming fundamentals and build software projects",
         "schedule": "Tuesdays and Thursdays, 3:30 PM - 4:30 PM",
         "max_participants": 20,
         "participants": ["emma@mergington.edu", "sophia@mergington.edu"]
      },
      "Gym Class": {
         "description": "Physical education and sports activities",
         "schedule": "Mondays, Wednesdays, Fridays, 2:00 PM - 3:00 PM",
         "max_participants": 30,
         "participants": ["john@mergington.edu", "olivia@mergington.edu"]
      },
      "Basketball Team": {
         "description": "Competitive basketball training and games",
         "schedule": "Tuesdays and Thursdays, 4:00 PM - 6:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Swimming Club": {
         "description": "Swimming training and water sports",
         "schedule": "Mondays and Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      },
      "Art Studio": {
         "description": "Express creativity through painting and drawing",
         "schedule": "Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Drama Club": {
         "description": "Theater arts and performance training",
         "schedule": "Tuesdays, 4:00 PM - 6:00 PM",
         "max_participants": 25,
         "participants": []
      },
      "Debate Team": {
         "description": "Learn public speaking and argumentation skills",
         "schedule": "Thursdays, 3:30 PM - 5:00 PM",
         "max_participants": 16,
         "participants": []
      },
      "Science Club": {
         "description": "Hands-on experiments and scientific exploration",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      }
   }
   ```

   </details>

### :keyboard: 实操环节: 用 Copilot 生成提交说明 💬

Bug 修复成功，示例数据也造好了，现在可以提交修改并推送到 GitHub 远程仓库！

1. 在左侧边栏选择 **Source Control**（源代码管理）。
2. 找到 `app.py` 文件，点击旁边的 `+` 将改动暂存。
3. 不要手动输入提交信息，而是点击消息框右边的 ✨ **Generate Commit Message** 按钮，让 Copilot 自动生成说明。
4. 点击 **Commit** 按钮提交，然后点击 **Sync Changes** 推送到 GitHub。
5. 稍等片刻，Mona 会检查你的工作并给出下一步反馈。

<details>
<summary>遇到问题? 🤷</summary><br/>

如果没有收到反馈，请确认:

- 是否将 `src/app.py` 文件的修改推送到了 `accelerate-with-copilot` 分支。

</details>
