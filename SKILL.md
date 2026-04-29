---
name: fable-generator-generic
description: "生成寓意故事（Fable）来解释概念。用户输入一个主题，AI 生成一个富有启发性的寓言故事。支持图片卡片和 Markdown 文件输出。"
metadata:
  openclaw:
    emoji: "📖"
    version: "1.0.0"
    author: "Generic Version"
    requires:
      os: ["darwin", "linux"]
    tags: ["storytelling", "fable", "ai-brain", "markdown"]
  visibility: public
---

# Fable Generator (通用版)

## 概念

**Fable Generator** 使用 AI 生成寓意故事来解释抽象概念或主题。每个故事都包含：
- 一个生动的叙事
- 一个清晰的寓意（Moral）
- 适合分享的图片卡片格式

## 依赖 Skills

| Skill | 用途 | 安装命令 |
|-------|------|----------|
| `markdown-to-image` | 将 Markdown 转换为图片卡片 | `openclaw skill install ReffWu/markdown-to-image` |

### 自动检测与安装

此 skill 会在执行时自动检测依赖是否已安装：

```
执行前检查:
├── 检查 markdown-to-image 是否存在
│   ├── ✅ 已存在 → 继续执行
│   └── ❌ 不存在 → 提示用户运行: openclaw skill install ReffWu/markdown-to-image
```

## 使用场景

| 触发词 | 说明 |
|--------|------|
| "给我讲个寓言" | 随机生成一个寓意故事 |
| "生成一个关于 X 的寓言" | 基于指定主题生成故事 |
| "fable about X" | 英文版本 |
| "生成寓言到文件" | 只输出 Markdown 文件，不生成图片 |

## 执行流程

```
1. 解析用户输入的主题
2. 生成富有教育意义的寓言故事 (Markdown 格式)
3. 检查 output_mode 配置:
   ├── image → 调用 markdown-to-image 生成图片卡片
   ├── file → 保存为 .md 文件
   └── all → 同时生成图片 + 文件
4. 返回结果给用户
```

## 配置选项

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| `output_mode` | `image` | 输出模式: `image`, `file`, `all` |
| `language` | `auto` | 语言: `auto`, `zh`, `en` |
| `style` | `storytelling` | 风格: `storytelling`, `philosophical`, `humorous` |
| `card_theme` | `default` | 卡片主题 (传给 markdown-to-image) |

## 示例

### 基本用法

```
用户: 给我一个关于"坚持"的寓言
AI: [生成故事 + 图片卡片]
```

### 指定输出为文件

```
用户: 生成一个关于"诚信"的寓言，输出到文件
AI: [生成故事，保存为 fable-integrity.md]
```

## 输出格式

### Markdown 格式

```markdown
# 📖 寓言：坚持的种子

## 故事

很久以前，有一个小男孩...

## 寓意

坚持就像种子，只有不断浇灌才能发芽成长。

---
*由 Fable Generator 生成*
```

### 图片卡片

调用 `markdown-to-image` skill 生成可分享的图片卡片。

## 注意事项

1. **首次使用**：请先安装依赖: `openclaw skill install ReffWu/markdown-to-image`
2. **图片主题**：可以通过 `card_theme` 参数自定义卡片样式

## 错误处理

| 错误 | 解决方法 |
|------|----------|
| "markdown-to-image skill 未安装" | 运行 `openclaw skill install ReffWu/markdown-to-image` |
| "故事生成失败" | 尝试简化主题或使用英文 |

---

*此为通用版本，不强制依赖任何单一平台。*
