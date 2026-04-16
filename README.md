# GPT Image V2 Prompt Crafter

一个面向 **GPT Image V2（OpenAI）** 的 Prompt 生成 Skill。  
A prompt-crafting skill for **GPT Image V2 (OpenAI)**.

---

## 简介 / Overview

这个 Skill 专门用于把用户的图像需求整理成高质量、可直接使用的 **GPT Image V2 Prompt**。  
This skill turns user image requests into high-quality, directly usable **GPT Image V2 prompts**.

它支持两种主要模式：  
It supports two main modes:

- **Quick 模式 / Quick Mode**：适合一句话需求、自然语言直出、快速得到效果很好的 prompt  
- **Precision 模式 / Precision Mode**：适合高控制、结构化、需要明确构图/镜头/版式/文字策略的场景

---

## 适用场景 / Use Cases

- 帮用户把一句自然语言扩展成 GPT Image V2 prompt  
  Expand a simple natural-language request into a GPT Image V2 prompt
- 为商业视觉、官网 Hero、UI 界面、叙事插画、角色海报生成高控制 prompt  
  Generate high-control prompts for commercial visuals, website heroes, UI scenes, narrative illustrations, and character posters
- 根据不同场景自动选择“自然语言 prompt”或“半 JSON 结构化 prompt”  
  Automatically choose between a natural-language prompt and a semi-JSON structured prompt

---

## 包含内容 / Contents

- `SKILL.md`：Skill 主说明  
  Main skill definition and usage guidance
- `prompts/GPT-Image-V2-Prompt-Template-Handbook.md`：完整模板手册  
  Full template handbook
- `examples/quick-social-live.md`：Quick 模式示例  
  Quick mode example
- `examples/precision-saas-hero.md`：Precision 模式示例  
  Precision mode example

---

## 使用方式 / How It Works

### Quick 模式 / Quick Mode

适合目标明确、可以直接描述清楚的需求。  
Best for requests that are already clear and can be expressed directly.

输出通常是：  
Output is usually:

- 一段自然、连贯、可直接使用的主 Prompt  
  A natural, fluent, directly usable main prompt
- 可选的 negative guidance  
  Optional negative guidance
- 画幅比例提示（如有）  
  Aspect ratio guidance when needed

### Precision 模式 / Precision Mode

适合需要高精度控制的场景。  
Best for high-control scenarios.

输出通常是半 JSON / 半自然语言结构，分块定义：  
Output usually uses a semi-JSON / semi-natural-language structure with blocks for:

- 内容 / content
- 构图 / composition
- 视觉语言 / visual language
- 文字行为 / text behavior
- 质量要求 / quality notes
- 负面约束 / negative prompt

---

## 核心模板场景 / Core Template Categories

本 Skill 默认覆盖以下几类高频场景：  
This skill covers the following core prompt categories by default:

1. **产品 / SaaS / 官网 Hero**  
   Product / SaaS / website hero
2. **App UI / 功能界面**  
   App UI / product interface
3. **叙事插画 / 电影感场景**  
   Narrative illustration / cinematic scene
4. **角色主视觉 / 海报**  
   Character key visual / poster
5. **环境 / 世界观 / 建筑场景**  
   Environment / worldbuilding / architectural scene
6. **品牌 / 广告 / Campaign 视觉**  
   Brand / advertising / campaign visual

---

## 默认约定 / Default Convention

所有最终 Prompt 默认在结尾附加：  
All final prompts append the following line by default:

`for GPT Image V2 from OpenAI's official account`

---

## 设计目标 / Design Goal

不是简单堆关键词，而是让 Prompt 更像一份可执行的视觉说明。  
The goal is not to stack random keywords, but to make the prompt behave more like an executable visual spec.

重点是：  
The priorities are:

- 更高质量 / higher quality
- 更高控制力 / higher control
- 更高完成度 / higher completion
- 更适合 GPT Image V2 的能力特点 / better aligned with GPT Image V2 strengths

---

## Repository

GitHub: https://github.com/ai-freer/gpt-image-v2-prompt-crafter
