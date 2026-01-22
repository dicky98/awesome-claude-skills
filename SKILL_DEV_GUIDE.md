# Agent Skill 开发与原理指南

本文档深入解析 Agent Skill 的本质、开发方法以及 AI 工具（如 Claude Code, Antigravity）如何调用这些技能。

## 1. Skill 的本质

**Skill = 可执行程序 + 给 AI 看的自然语言说明书**

普通的脚本工具是“电钻”，而 Skill 是“电钻 + 《使用指南》”。Skill 通过在代码外层包裹自然语言描述，将死板的 API 接口转化为 AI 可以理解和决策的**认知接口**。

| 特性 | 普通程序 (Script) | Agent Skill |
| :--- | :--- | :--- |
| **调用者** | 人类 / 硬编码脚本 | AI Agent 自动决策 |
| **触发方式** | 精确命令 (`python run.py -a 1`) | 自然语言意图 ("帮我查天气") |
| **接口类型** | 严格的参数类型 | 弹性的语义理解 |
| **上下文** | 需要人工管理 | AI 按需自动加载 (Progressive Disclosure) |

---

## 2. 如何开发一个 Skill？

一个标准的 Skill 通常是一个独立文件夹，包含核心的 `SKILL.md` 和实现功能的脚本。

### 示例场景：天气查询 (Weather Checker)

假设我们要创建一个查询天气的 Skill。

#### 2.1 目录结构

```bash
.claude/skills/weather-checker/
├── SKILL.md           # [大脑] 给 AI 看的说明书
└── get_weather.py     # [手脚] 实际执行逻辑的脚本
```

#### 2.2 编写“手脚” (`get_weather.py`)

这是一个标准的 Python 脚本，负责具体的数据获取。

```python
import sys
import json

# 模拟 API 调用逻辑
def get_weather(city):
    # 实际场景可替换为 requests.get(...)
    mock_data = {
        "Beijing": {"temp": 25, "condition": "Sunny"},
        "Shanghai": {"temp": 28, "condition": "Rainy"}
    }
    return mock_data.get(city, {"error": "City not found"})

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print(json.dumps({"error": "No city provided"}))
        sys.exit(1)
    city = sys.argv[1]
    print(json.dumps(get_weather(city)))
```

#### 2.3 编写“大脑” (`SKILL.md`)

这是 Skill 的核心。你需要用 YAML Frontmatter 定义元数据，用 Markdown 编写 AI 指令。

```markdown
---
name: weather-checker
description: Query real-time weather information for a specific city.
---

# Weather Checker Skill

## When to use this skill
Use this skill when the user asks about the weather conditions, temperature, or forecast of a specific city.
(e.g., "What's the weather in Beijing?", "Is it raining in Shanghai?")

## How to use
To get the weather, you must execute the python script located in this skill's directory.

1.  **Extract the city name** from the user's prompt.
2.  **Run the script**: `python get_weather.py <CityName>`
3.  **Interpret the JSON output** and answer the user in natural language.

## Error Handling
- If the output contains "error", apologize to the user and ask for a valid city name.
- If the script fails to run, inform the user about the technical issue.
```

---

## 3. AI 工具是如何使用 Skill 的？

当你在 Claude Code 或 Antigravity 中输入 *"Is it raining in Shanghai today?"* 时，后台经历了以下三个阶段：

### 阶段一：意图识别 (Router)
1.  **扫描**: AI 工具启动时，扫描 Skill 目录（如 `~/.claude/skills/`）。
2.  **索引**: 读取所有 `SKILL.md` 顶部的 `description` 字段。
3.  **匹配**: AI 分析用户意图，发现 `weather-checker` 的描述 "Query real-time weather..." 与请求高度匹配。

### 阶段二：上下文注入 (Context Injection)
1.  **加载**: AI 将匹配到的 `SKILL.md` 的**全部内容**（Instruction 部分）动态注入到当前的对话 Prompt 中。
2.  **认知**: 此时 AI 获得了“新技能”，知道要通过运行脚本来获取天气，而不是胡编乱造。

### 阶段三：执行与反馈 (Execution)
1.  **推理**: 根据 Skill 指令，AI 提取出参数 `Shanghai`。
2.  **行动**: AI 在终端自动执行命令：
    ```bash
    python .claude/skills/weather-checker/get_weather.py Shanghai
    ```
3.  **观察**: 捕获脚本输出的 JSON：`{"temp": 28, "condition": "Rainy"}`。
4.  **回答**: AI 根据 Skill 的指示，将 JSON 翻译为自然语言回答用户。

---

## 4. 最佳实践

1.  **原子化**: 每个 Skill 最好只做一件事（如“查询天气”和“预订机票”应分开）。
2.  **描述清晰**: `description` 字段决定了 AI 是否会加载该 Skill，务必准确简洁。
3.  **鲁棒性**: 在 `SKILL.md` 中明确告诉 AI 如何处理错误（如脚本报错、参数缺失）。
4.  **无状态**: 脚本最好是无状态的，或者状态由外部（如文件/数据库）管理，方便 AI 反复调用。

---

## 5. 环境依赖与跨平台挑战

正如你所观察到的，Skill 的执行极度依赖宿主机的系统环境。这在涉及本地应用交互（如 PowerPoint, Word）时尤为明显。

### 为什么会不同？

Skill 本质上是在终端执行命令，因此它继承了所有操作系统的差异性：

*   **系统命令差异**: Windows 使用 `dir` 和 `type`，而 macOS/Linux 使用 `ls` 和 `cat`。
*   **文件路径格式**: Windows 使用反斜杠 `\`，macOS/Linux 使用正斜杠 `/`。
*   **应用接口 (API)**:
    *   **Windows**: Microsoft Office 提供了强大的 **COM/OLE 自动化接口**，Python 库如 `pywin32` 可以深度控制 Word/PPT。
    *   **macOS**: Office 自动化通常依赖 **AppleScript**，功能覆盖率不如 Windows 的 COM 接口全面。
    *   **Linux**: 通常没有原生 Office，可能需要调用 LibreOffice 的无头模式 (Headless Mode) 或使用纯 Python 库（如 `python-docx`, `python-pptx`）直接操作文件二进制，而不是操作运行中的 App。

### 解决方案

在开发 Skill 时，你有三种策略来应对这种差异：

#### 策略 A：纯 Python 库（推荐）
尽量不依赖已安装的 App，而是直接操作文件。
*   *场景*: 生成一个 PPT。
*   *做法*: 使用 `python-pptx` 库生成 `.pptx` 文件。
*   *优点*: 跨平台兼容性极好（Win/Mac/Linux 都能跑），无需安装 Office。

#### 策略 B：环境检测
在脚本中判断当前系统，执行不同的逻辑。

```python
import platform

system = platform.system()
if system == "Windows":
    # 使用 pywin32 调用 COM 接口
    pass
elif system == "Darwin": # macOS
    # 使用 osascript 调用 AppleScript
    pass
else:
    print("Error: This skill does not support Linux.")
```

#### 策略 C：明确声明依赖
如果你的 Skill 必须依赖特定平台的特性（例如“控制当前正在播放的 PPT 翻页”），请在 `SKILL.md` 中明确标注。

```markdown
# PowerPoint Controller
> **Warning**: This skill requires Windows 10/11 and Microsoft PowerPoint installed.
```

