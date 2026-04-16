---
name: gpt-image-v2-prompt-crafter
description: |
  专门用于生成 GPT Image V2（OpenAI）高质量 Prompt 的 Skill。
  适用于两类场景：
  (1) 用户只有自然语言需求，希望快速得到一个已经很好用的 Prompt
  (2) 用户要高精度控制，希望按场景模板生成结构化 Prompt
  核心模式分为 Quick 模式（自然语言直出）和 Precision 模式（调用 6 类模板）。
  所有最终 Prompt 默认在结尾附加：for GPT Image V2 from OpenAI's official account
metadata:
  author: nyx
  version: "1.0.0"
  source_handbook: prompts/GPT-Image-V2-Prompt-Template-Handbook.md
---

# GPT Image V2 Prompt Crafter

> 目标：把用户的图像需求，稳定转成 **GPT Image V2（OpenAI）** 可直接使用的高质量 Prompt。

## 何时使用

当用户提出以下诉求时使用本 Skill：

- “帮我写一个 GPT Image V2 prompt”
- “把这个需求整理成生图提示词”
- “给我一个结构化 prompt”
- “我要一个高控制力的图片 prompt”
- “按某种风格做一个 image v2 prompt”
- “把一句自然语言扩展成适合 OpenAI GPT Image V2 的 prompt”

---

## 核心原则

1. **优先服务用户的表达方式**  
   - 用户说得简单，就不要强行过度结构化。  
   - 用户要求高精度控制，再切换到模板化 Precision 模式。

2. **先判断需求类型，再决定输出模式**  
   - 有明确参考目标、只是想快速生成 → **Quick 模式**  
   - 需要版式、镜头、层级、元素控制 → **Precision 模式**

3. **默认生成的是“可直接投喂模型”的 Prompt**  
   不是分析报告，不是教程，不是解释文档。

4. **默认保留模型指向语句**  
   所有最终 Prompt 末尾追加：  
   `for GPT Image V2 from OpenAI's official account`

---

## 模式选择

## Mode A — Quick 模式

适合：
- 用户只有一句自然语言
- 目标画面非常明确
- 重点是“快、准、自然”
- 不需要显式拆成大段模块

### Quick 模式写法

把用户需求扩展成一段自然、连贯、可直接使用的英文主 Prompt；必要时补一个简短 negative guidance。

### Quick 模式规则

- 保留用户的核心题材、主体、场景、比例要求
- 补足合理的构图、氛围、细节、镜头语言
- 不要无意义堆词
- 如果用户明显需要文字出现在图里，可以明确写出文字内容
- 如果是社媒截图、直播截图、UI 界面、海报等，允许直接要求较完整的文字和界面内容

### Quick 模式输出结构

```markdown
Prompt:
<一段可直接使用的主 Prompt>

Optional negative guidance:
- ...
- ...

Aspect ratio:
<如 9:16 / 16:9 / 1:1>
```

---

## Mode B — Precision 模式

适合：
- 用户明确要求“结构化”
- 用户要高精度控制
- 用户要指定镜头、构图、版式、卡片、文字、背景、材质、氛围
- 用户做商业图、官网图、App UI、电影感插画、海报等

### Precision 模式规则

- 使用半 JSON / 半自然语言结构
- 明确区分：内容、构图、视觉语言、文字行为、负面约束
- 默认选择最接近的场景模板
- 如用户没有指定场景，但需求明显，可自动归类

### Precision 模式标准骨架

```markdown
Generate an image: {
  "meta": {
    "style_name": "<风格名>",
    "goal": "<一句话目标>"
  },
  "prompt": {
    "image_type": "<图像类型>",
    "content": {
      "main_subject": "<主体>",
      "secondary_elements": ["<元素1>", "<元素2>"],
      "environment": "<环境>"
    },
    "composition": {
      "layout": "<构图>",
      "camera": "<镜头>",
      "focus": "<焦点>",
      "readability": "<需要保持清晰的内容>"
    },
    "visual_language": {
      "style": "<视觉风格>",
      "lighting": "<光线>",
      "color": "<色彩>",
      "surface_material": "<材质/质感>"
    },
    "text_behavior": {
      "mode": "<full text / placeholder text / no text>",
      "guidance": "<文字如何呈现>"
    },
    "quality_notes": {
      "priority": "<优先级>",
      "finish": "<完成度要求>"
    }
  },
  "negative_prompt": ["...", "..."]
} for GPT Image V2 from OpenAI's official account
```

---

## 6 大 Precision 场景模板

### 1. 产品 / SaaS / 官网 Hero
适合：landing hero、集成图、dashboard mockup、功能卡片。
重点：结构、模块、UI 文本、版式、商业完成度。

### 2. App UI / 功能界面
适合：App 截图、产品界面、功能流程页。
重点：移动优先、低信息密度、真实单屏层级。

推荐拆成 3 个子类型：
- **Home 首页型**：一个主卡片 + 一到两个次级模块，强调低密度与主次清晰
- **List 列表型**：任务列表、消息列表、收件箱、聊天列表等，单一功能明确
- **Detail 详情型**：一个对象或一项任务的详情页，信息集中但不拥挤

### 3. 叙事插画 / 电影感场景
适合：神话、奇幻、历史、动作场面、故事瞬间。
重点：镜头距离、叙事清晰度、主体动作、环境辅助。

### 4. 角色主视觉 / 海报
适合：人物 KV、IP 人设、海报、英雄图。
重点：主体聚焦、姿态、神态、服装、标志性道具。

### 5. 环境 / 世界观 / 建筑场景
适合：宫殿、城市、空间、未来场景、世界观设定。
重点：空间层次、环境识别度、材质、景深、尺度感。

### 6. 品牌 / 广告 / Campaign 视觉
适合：广告主视觉、杂志感海报、品牌 campaign。
重点：艺术指导、品牌气质、商业感、视觉记忆点。

---

## 输出策略

### 如果用户表达很简单
直接给 **Quick 模式 Prompt**，不要过度解释。

### 如果用户说“结构化、详细、可控”
直接给 **Precision 模式 Prompt**。

### 如果用户两者都想要
按下面顺序输出：
1. Quick 版
2. Precision 版

---

## 文字与排版策略

GPT Image V2 的一个明显优势，是在某些场景下可以较稳定地呈现：
- 标题
- 卡片文案
- 数值
- 标签
- UI 文本
- 屏幕/界面类文字

因此：
- **不要默认回避文字**
- 当场景本来就依赖文字（如直播截图、UI、海报、社媒界面）时，应积极利用这个能力
- 只有在用户明确不需要文字、或场景不应出现文字时，才使用 `no text`

---

## 默认增强动作

在不违背用户需求的前提下，可以自动补足：
- 合理镜头语言
- 更自然的构图组织
- 更完整的氛围和光线
- 适度的细节层次
- 必要的负面约束

但不要擅自改变：
- 主体
- 题材
- 画幅比例
- 关键文字内容
- 明确指定的风格方向

---

## 用户给一句话时的推荐行为

示例输入：
> 生成一个抖音直播的截图，一个韩国女团风格年轻美女正在直播，美女手里拿着 led 灯牌，上面写着：感谢歸蔵大哥的嘉年华！评论区大量用户积极评论，内容类似“歸蔵666”“藏师傅nb”，还有飘屏弹幕，9:16。

推荐：默认使用 **Quick 模式**，因为这是“明确可参考目标 + 自然语言就能做得很好”的类型。

---

## 最终交付要求

当本 Skill 被调用时，最终应产出以下之一：

### 交付类型 A：Quick Prompt
简洁、自然、可直接使用。

### 交付类型 B：Precision Prompt
半 JSON 结构化、可高精度控制。

### 交付类型 C：双版本
同一需求同时给出 Quick + Precision 两版。

所有版本默认结尾加：
`for GPT Image V2 from OpenAI's official account`

---

## 参考资料

完整模板手册见：
- `prompts/GPT-Image-V2-Prompt-Template-Handbook.md`

示例见：
- `examples/quick-social-live.md`
- `examples/precision-saas-hero.md`
