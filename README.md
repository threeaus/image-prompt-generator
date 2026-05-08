# image-prompt-generator

## 中文

`image-prompt-generator` 是一个给 coding agent 使用的图片提示词生成 skill 。

它适合处理很短的画面描述，并把抽象想法转换成观众能直接看到的画面细节。输出包含中文维度拆解和可直接用于 AI 画图工具的英文 prompt。

### 功能

- 将抽象描述转换成具体可见的画面元素
- 自动补全主题、动作、环境、构图、光影、风格、文字等维度
- 避免依赖否定词和空泛概念
- 输出中文拆解和完整英文 prompt
- 可被多种 coding agent 作为 skill、规则文件或自定义指令使用

### 安装方式

#### 通用安装

1. 下载或复制 `SKILL.md`。
2. 放到你的 coding agent 支持的 skills、rules、instructions 或 prompts 目录中。
3. 按照对应工具的要求重新加载、重启，或开启一个新会话。
4. 如果你的工具没有固定目录，可以把 `SKILL.md` 内容作为自定义指令添加。

下载文件：

```bash
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o SKILL.md
```

克隆仓库：

```bash
git clone https://github.com/threeaus/image-prompt-generator.git
```

#### Codex 示例

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o ~/.codex/skills/image-prompt-generator/SKILL.md
```

如果已经克隆仓库：

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
cp SKILL.md ~/.codex/skills/image-prompt-generator/SKILL.md
```

安装后，重新打开对应 agent 或开始一个新会话，让它加载这个 skill。

### 使用方式

在你的 coding agent 中直接提出画图相关需求，例如：

```text
帮我画一张赛博朋克风格的东京街头
```

或：

```text
生成一张适合做公众号封面的图片 prompt，主题是独立开发者的夜晚工作台
```

当请求包含“画图”“生成图片”“帮我画”“做张图”“image prompt”“画一张”等表达时，这个 skill 可以指导 agent 生成更完整的图片 prompt。

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

`image-prompt-generator` is an image prompt generation skill file for coding agents.

It turns short or abstract image ideas into visible scene details. The output includes a Chinese dimension breakdown and a complete English prompt ready for image generation.

### Features

- Converts abstract ideas into concrete visible details
- Fills in subject, action, environment, composition, lighting, style, and text
- Reduces vague concepts and negative phrasing
- Outputs both a Chinese breakdown and a complete English prompt
- Can be used by different coding agents as a skill, rules file, or custom instruction

### Installation

#### Generic installation

1. Download or copy `SKILL.md`.
2. Put it in the skills, rules, instructions, or prompts location supported by your coding agent.
3. Reload, restart, or start a new session according to your agent's requirements.
4. If your agent has no fixed directory, paste the content of `SKILL.md` as a custom instruction.

Download the file:

```bash
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o SKILL.md
```

Clone the repository:

```bash
git clone https://github.com/threeaus/image-prompt-generator.git
```

#### Codex example

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
curl -L https://raw.githubusercontent.com/threeaus/image-prompt-generator/main/SKILL.md -o ~/.codex/skills/image-prompt-generator/SKILL.md
```

If you already cloned this repository:

```bash
mkdir -p ~/.codex/skills/image-prompt-generator
cp SKILL.md ~/.codex/skills/image-prompt-generator/SKILL.md
```

After installation, restart the relevant agent or start a new session so it can load the skill.

### Usage

Ask your coding agent for an image prompt, for example:

```text
Create an image prompt for a cyberpunk street in Tokyo.
```

Or:

```text
Generate an image prompt for a newsletter cover about an indie developer working late at night.
```

This skill is intended for requests such as "draw an image", "generate an image", "help me draw", "make an image", "image prompt", and similar image-generation requests.

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
