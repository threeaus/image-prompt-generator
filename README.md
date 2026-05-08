# image-prompt-generator

## 中文

`image-prompt-generator` 是一个用于生成 AI 画图提示词的 Codex skill。

它适合处理很短的画面描述，并把抽象想法转换成观众能直接看到的画面细节。输出包含中文维度拆解和可直接用于 AI 画图工具的英文 prompt。

### 功能

- 将抽象描述转换成具体可见的画面元素
- 自动补全主题、动作、环境、构图、光影、风格、文字等维度
- 避免依赖否定词和空泛概念
- 输出中文拆解和完整英文 prompt

### 安装

下载 `SKILL.md` 到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o ~/.codex/skills/image-prompt-generator/SKILL.md
```

如果你已经克隆了这个仓库，也可以复制文件：

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
cp SKILL.md ~/.codex/skills/image-prompt-generator/SKILL.md
```

安装后，重新打开 Codex 或开始一个新会话，让 skill 被加载。

### 使用方式

在 Codex 中直接提出画图相关需求，例如：

```text
帮我画一张赛博朋克风格的东京街头
```

或：

```text
生成一张适合做公众号封面的图片 prompt，主题是独立开发者的夜晚工作台
```

当请求包含“画图”“生成图片”“帮我画”“做张图”“image prompt”“画一张”等表达时，这个 skill 会被使用。

### 输出形式

```text
=== 维度拆解 ===
- 主题: ...
- 动作: ...
- 环境: ...
- 构图: ...
- 光影: ...
- 风格: ...
- 文字: ...

=== 完整 Prompt ===
...
```

## English

`image-prompt-generator` is a Codex skill for generating image prompts for AI image tools.

It turns short or abstract image ideas into visible scene details. The output includes a Chinese dimension breakdown and a complete English prompt ready for image generation.

### Features

- Converts abstract ideas into concrete visible details
- Fills in subject, action, environment, composition, lighting, style, and text
- Reduces vague concepts and negative phrasing
- Outputs both a Chinese breakdown and a complete English prompt

### Installation

Download `SKILL.md` into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o ~/.codex/skills/image-prompt-generator/SKILL.md
```

If you already cloned this repository, you can copy the file instead:

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
cp SKILL.md ~/.codex/skills/image-prompt-generator/SKILL.md
```

After installation, restart Codex or start a new session so the skill can be loaded.

### Usage

Ask Codex for an image prompt, for example:

```text
Create an image prompt for a cyberpunk street in Tokyo.
```

Or:

```text
Generate an image prompt for a newsletter cover about an indie developer working late at night.
```

This skill is intended for requests such as “draw an image”, “generate an image”, “help me draw”, “make an image”, “image prompt”, and similar image-generation requests.

### Output Format

```text
=== 维度拆解 ===
- 主题: ...
- 动作: ...
- 环境: ...
- 构图: ...
- 光影: ...
- 风格: ...
- 文字: ...

=== 完整 Prompt ===
...
```
