# youtube-vers-agent

一种 Claude Code 技能，通过双源验证（本地 Claude + Gemini）和规格交叉验证将 YouTube 教程转换为 Claude Code 技能。

## 描述

此技能通过以下方式将 YouTube 教程内容转换为结构化的 Claude Code 技能：
1. 从视频转录中提取关键概念和程序
2. 通过双源验证（视频 + 文档）验证信息
3. 创建符合 Claude Code 约定的正确格式的 SKILL.md 文件
4. 通过交叉参考确保准确性和完整性

## 何时使用

在以下情况下使用此技能：
- 将教育性 YouTube 内容转换为可重用的 Claude Code 技能
- 基于关于开发工具、框架或方法论的教学视频创建技能
- 通过与官方文档核对来确保技能的准确性
- 从视频学习资源构建验证过的技能库

## 技能工作流程

### 1. 视频分析阶段
- 使用 watch 技能处理 YouTube 视频以提取转录和关键帧
- 识别视频中呈现的主要主题、程序和代码示例
- 构建学习目标和成果

### 2. 双源验证
- 对于每个关键概念/程序，使用 context7-mcp 或 find-docs 技能咨询官方文档
- 将视频内容与权威来源交叉参照
- 注意任何差异或版本差异
- 验证代码示例按演示方式工作

### 3. 技能创建
- 生成符合 Claude Code 约定的正确格式的 SKILL.md 文件
- 包含清晰的描述、使用指南和逐步工作流程
- 引用用于验证的视频来源和文档来源
- 添加基于验证程序的适当工具推荐

### 4. 质量保证
- 测试提及的代码示例或程序
- 验证技能是否遵循 Claude Code 技能格式标准
- 确保技能提供可操作且可验证的指导

## 输出

在适当的 .claude/skills/ 目录中生成一个完整的 SKILL.md 文件，该文件：
- 清晰定义技能的目的和适用性
- 提供特定的使用指南
- 概述可验证的工作流程
- 引用用于双源验证的来源
- 遵循 Claude Code 技能约定

## 所需工具

- watch：用于处理 YouTube 视频内容
- context7-mcp 或 find-docs：用于双源验证相对于官方文档
- Bash：用于文件操作和技能创建

## 安装

1. 克隆此仓库：
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. 将技能复制到您的 Claude Code 技能目录：
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. 重新加载插件：
   ```bash
   /reload-plugins
   ```

## 使用

安装后，您可以通过提供 YouTube URL 和指定要构建的内容来使用此技能：

```
/youtube-vers-agent [YouTube URL] [要提取的内容] [要构建的内容]
```

示例：
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo 整个项目 一项 Claude Code 技能
```

## 使用示例

将关于创建 React 组件的 YouTube 教程转换为 Claude Code 技能：
1. 使用 watch 技能提取视频转录和关键点
2. 使用 context7-mcp 将 React 组件创建模式与官方 React 文档进行核对
3. 创建包含在 Claude Code 中创建 React 组件的验证程序的 SKILL.md
4. 包含对所使用的 YouTube 教程和 React 文档的引用

## 验证标准

所有创建的技能必须：
- 引用至少两个独立来源（视频 + 文档）
- 包含具体且可操作的步骤
- 提供清晰的使用指南
- 遵循既定的 Claude Code 技能格式
- 包含可测试的可验证程序

## 许可证

MIT 许可证 - 请参阅 [LICENSE](LICENSE) 文件了解详细信息。