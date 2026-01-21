# Google Antigravity 文档创建技能配置指南

本文档将指导你如何在 Google Antigravity IDE 中配置和启用 Anthropic 官方提供的 5 个核心文档创建技能 (Doc Creation Skills)。配置完成后，你的 Agent 将具备创建 Word、PPT、Excel 和 PDF 文档的能力。

## 1. 技能列表

我们将安装以下 5 个官方技能：

1.  **docx**: 创建、编辑和分析 Word 文档
2.  **pptx**: 创建、编辑和分析 PowerPoint 演示文稿
3.  **xlsx**: 创建、编辑和分析 Excel 电子表格
4.  **pdf**: 提取文本、创建 PDF 和处理表单
5.  **doc-coauthoring**: 协作文档编辑和共同创作

## 2. 自动安装 (推荐)

在你的终端中运行以下脚本，即可一键完成安装。

### 步骤说明

该脚本会执行以下操作：
1.  确保 Antigravity 的全局技能目录存在 (`~/.gemini/antigravity/skills/`)。
2.  克隆官方 `anthropics/skills` 仓库到临时目录。
3.  将 5 个目标技能文件夹复制到 Antigravity 的全局目录中。
4.  清理临时文件。

### 安装脚本

```bash
# 1. 创建 Antigravity 全局技能目录
mkdir -p ~/.gemini/antigravity/skills

# 2. 创建一个临时目录用于下载
mkdir -p /tmp/claude_skills_temp
cd /tmp/claude_skills_temp

# 3. 克隆 Anthropic 官方技能仓库
echo "正在克隆官方技能仓库..."
git clone https://github.com/anthropics/skills.git .

# 4. 复制 5 个文档相关的技能到 Antigravity 目录
echo "正在安装文档技能..."
cp -r skills/docx ~/.gemini/antigravity/skills/
cp -r skills/doc-coauthoring ~/.gemini/antigravity/skills/
cp -r skills/pptx ~/.gemini/antigravity/skills/
cp -r skills/xlsx ~/.gemini/antigravity/skills/
cp -r skills/pdf ~/.gemini/antigravity/skills/

# 5. 清理临时文件
cd ~
rm -rf /tmp/claude_skills_temp

echo "✅ 安装完成！技能已部署到 ~/.gemini/antigravity/skills/"
```

## 3. 安装依赖库

为了让 Agent 能够执行这些技能中的 Python 脚本，你需要安装相应的 Python 依赖库。

```bash
pip install python-docx openpyxl pandas pypdf reportlab python-pptx
```

*注意：如果你的 Agent 运行在特定的虚拟环境中，请确保在该环境中安装上述库。*

## 4. 验证与使用

安装完成后，建议重启 Antigravity IDE 或重新加载 Agent Manager。你无需手动开启这些技能，只需在对话中提出相关需求，Agent 会自动识别并调用。

### 测试指令示例

*   **Word 文档**:
    > "帮我写一份关于 2024 年 Q3 季度项目总结的 Word 文档，包含‘项目概况’、‘主要成果’和‘下一步计划’三个章节。"

*   **PPT 演示文稿**:
    > "创建一个 5 页的 PPT，介绍 Antigravity 的核心功能，风格要简洁专业。"

*   **Excel 表格**:
    > "生成一个 Excel 表格，列出 2025 年每月的预算规划示例，包含‘收入’、‘支出’和‘结余’列。"

*   **PDF 处理**:
    > "读取这个 PDF 文件 (path/to/file.pdf) 的内容，并总结其核心观点。"

## 5. 常见问题 (FAQ)

**Q: 技能没有触发怎么办？**
A: 请检查 `~/.gemini/antigravity/skills/` 目录下是否存在对应的文件夹（如 `docx`），且文件夹内包含 `SKILL.md` 文件。如果目录正确，尝试更明确地描述你的需求，例如明确提到“创建 Word 文档”。

**Q: 执行时报错 "ModuleNotFoundError"？**
A: 这通常是因为缺少 Python 依赖。请查看报错信息中缺少的库名，使用 `pip install <库名>` 进行安装。

**Q: 我可以只在特定项目中使用吗？**
A: 可以。将脚本中的目标路径从 `~/.gemini/antigravity/skills/` 改为你项目根目录下的 `.agent/skills/` 即可。

---
**相关链接**
- [Awesome Claude Skills](https://github.com/VoltAgent/awesome-claude-skills)
- [Antigravity Documentation](https://antigravity.google/docs)
