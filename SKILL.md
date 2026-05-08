---
name: image-prompt-generator
description: 画图提示词生成器 — 用户描述想要的画面，基于"视觉代偿"方法论自动补全维度，输出可直接用于 AI 画图工具的完整 prompt。
version: 2.0
---

# Image Prompt Generator (v2 - 视觉代偿版)

## 核心原则

写提示词时，不要想"我要表达什么概念"，要想"**观众究竟能看到什么**"。

## 6 条铁律

1. **少写概念，多写可见物** -- 把抽象意图拆成观众能直接看到的视觉特征
2. **少用否定，多用正向替代** -- 不写"不要X"，直接写"要Y"
3. **少写抽象动作，多写画面关系** -- "望向"不如把目标物放在人物前方
4. **少用主题标签，多写姿态和环境线索** -- "打游戏"换成"双手横向握着手机"
5. **少靠镜头词，多靠细节密度控制远近** -- 想近景就堆面部/缝线/反光细节
6. **不要只说表达什么，要说观众会看到什么**

## 触发条件

当用户说"画图"、"生成图片"、"帮我画"、"做张图"、"image prompt"、"画一张"等与图片生成相关的请求时使用。

## 工作流程

### Step 1: 收集用户意图

用户会给出一个画面描述（可能很简短）。先理解核心主题、风格、用途。

### Step 2: 视觉代偿转换

对用户描述中的每一个抽象概念，执行以下转换：

**触发词替换**
- 某些词会激活模型的整套场景联想（护士帽→医院，安全帽→工地，厨师帽→厨房）
- 如果不需要那套联想，直接绕开这个词，描述你真正想要的画面
- 例如：不要写"一个不戴护士帽的人"，写"一个穿日常便装的人，短发，无头饰"

**否定转正向**
- "不要帽子" → 直接描述无帽造型："短发露出前额，头顶无任何头饰"
- "不要夸张" → "姿势自然放松，日常抓拍感"
- "不要反着拿手机" → "双手横向握着手机，拇指朝上"

**概念拆解为视觉特征**
- "帅气" → "面部轮廓清晰，下颌线分明，眉骨略高"
- "精英感" → "合身深色西装，袖口露出一厘米白衬衫，发型整洁"
- "温馨" → "暖色调台灯，毛毯搭在沙发扶手上，桌面冒着热气的马克杯"
- "打游戏" → "双手横向握着手机，低头看向手中的屏幕"
- "修图" → "身体微微前倾注视显示器，右手握着鼠标，桌面摆着数位板"

**镜头词转细节密度**
- 不写"特写"，写"画面聚焦在头盔面罩反光、胸前生命支持系统、宇航服缝线、金属接口和表面微小划痕上"
- 不写"全景"，写"人物全身出现在广阔表面上，脚下灰白色尘土延伸到远方，远处是低矮山丘和巨大的天空"
- 不写"俯视角"，写"从上方向下看，能看到头顶、肩膀顶部和上方轮廓，下方是遥远的背景"

### Step 3: 补全 7 个维度

对转换后的视觉描述，按以下维度补全细节。缺失的用合理默认值填充，但仍遵守视觉代偿原则：

**1. 主题 (Subject)**
- 写具体视觉特征，不写抽象标签
- 人物：面部特征、体型轮廓、发色发型、肤色
- 物体：材质、颜色、大小比例、表面纹理

**2. 动作/姿态 (Action)**
- 写观众能看到的身体姿态和手部位置
- 不写概念（"思考"），写姿态（"单手托腮，目光落在远处"）

**3. 地点/环境 (Location)**
- 写环境中的可见物：地面材质、墙面、家具、窗外景物
- 不写"咖啡店"，写"木质桌面，白色瓷杯，窗外透入暖光，吧台后方可见咖啡机"

**4. 构图与画幅 (Composition & Aspect Ratio)**
- 根据用途推画幅：海报/手机壁纸→9:16，网页 banner→16:9，头像→1:1，电影感→2.39:1
- 通过细节密度控制远近，不靠"特写/中景/全景"
- 描述主体在画面中的位置关系

**5. 镜头与光影 (Camera & Lighting)**
- 光源要具体：侧窗自然光、头顶直射硬光、屏幕冷光反射在脸上
- 阴影要具体：面部一半明一半暗、地面拉长的影子
- 镜头焦段可选：广角(24mm)、标准(50mm)、长焦(85mm+)

**6. 风格 (Style)**
- 明确画风：水彩、油画、摄影、3D渲染、赛博朋克、吉卜力等
- 可指定风格参考："in the style of..."

**7. 长宽比与文字 (Aspect Ratio & Text)**
- 如需文字：写明内容、字体风格、颜色、位置
- 如不需要："No text in the image"

### Step 4: 输出格式

先输出**中文维度拆解**（方便用户确认），再输出**完整英文 prompt**。

```
=== 维度拆解 ===
- 主题: [具体视觉特征]
- 动作: [可见的姿态和手部位置]
- 环境: [环境中的可见物]
- 构图: [画幅 + 主体位置 + 细节密度描述]
- 光影: [具体光源 + 阴影效果]
- 风格: [画风/参考]
- 文字: [有/无，有的话具体描述]

=== 完整 Prompt ===
[英文 prompt，一段式或分段式均可]
```

### Step 5: 迭代

询问用户对哪个维度不满意，针对性调整。调整时仍遵守视觉代偿原则。

## 示例

**用户输入**: "帮我画一张赛博朋克风格的东京街头"

**输出**:

=== 维度拆解 ===
- 主题: 一条狭窄的城市街道，两侧建筑外墙密集排列着发光招牌和全息广告屏
- 动作: 一个穿深色风衣的人背对镜头走在街道中央，衣摆被风吹起
- 环境: 雨后湿滑的沥青路面反射着粉紫色和青色的霓虹光，地面有积水坑，远处建筑群延伸至雾气中
- 构图: 9:16竖版，人物位于画面中下三分之一处，两侧建筑向天空收窄形成透视，前景地面倒影占画面下方四分之一
- 光影: 霓虹招牌发出粉紫色和青色的光打在湿路面上，人物轮廓边缘有一圈微弱的逆光，上方隐约透出月光的冷蓝调
- 风格: 电影摄影感，Blade Runner 2049 色调，高对比度，赛博朋克
- 文字: 招牌上有日文假名和汉字，内容为虚构店名，发光效果

=== 完整 Prompt ===
A narrow city street in cyberpunk Tokyo at night after rain, dense buildings on both sides covered in glowing signs and holographic ad screens. A figure in a dark long coat walks away from the camera down the center of the street, coat hem lifted by wind. Wet asphalt reflects pink-purple and cyan neon light, puddles on the ground mirror the signs above, distant building clusters fade into fog. 9:16 vertical format, figure in the lower third, buildings narrowing upward into perspective, ground reflections filling the bottom quarter. Neon signs cast pink-purple and cyan light on wet pavement, faint rim light on the figure's silhouette, cold blue moonlight from above. Japanese katakana and kanji on signs showing fictional shop names with glow effect. Cinematic photography feel, Blade Runner 2049 color palette, high contrast, cyberpunk aesthetic. No additional text.

需要调整哪个维度？
