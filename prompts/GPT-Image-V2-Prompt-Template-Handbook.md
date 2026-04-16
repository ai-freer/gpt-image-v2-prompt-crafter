# GPT Image V2（OpenAI）Prompt 模板手册

> 本文档用于提炼 **GPT Image V2（OpenAI）** 在高质量生图中的有效 Prompt 写法，沉淀为可复用模板。  
> 写法采用 **半 JSON / 半自然语言** 结构：既方便阅读，也方便后续修改与扩展。

---

## 文档目标

- 归纳 GPT Image V2 已表现出的能力优势
- 按核心生图场景分类
- 为每类场景提供基础 Prompt 模板
- 保留较高控制力、较高完成度、较强结构表达能力
- 在模板结尾保留激活语句：  
  **`for GPT Image V2 from OpenAI's official account`**

---

## 一、GPT Image V2 的能力特点

从当前已验证的出图效果来看，GPT Image V2 的优势主要体现在：

- **结构理解更强**：能更好地理解分层、分块、模块化描述
- **复杂画面整合能力更强**：能同时处理主体、环境、版式、细节、文案
- **文本呈现能力更强**：标题、卡片内容、数字、标签、界面文字可较稳定落地
- **构图控制更强**：对居中、对称、分层、镜头距离等有更好的服从度
- **整体完成度更高**：更适合直接生成接近成品级的视觉

因此，这一代 Prompt 不应只写零散关键词，而更适合写成：

- 这是什么图
- 主体是什么
- 配体是什么
- 环境是什么
- 构图如何组织
- 风格如何定义
- 文字如何出现
- 哪些问题需要避免

---

## 二、推荐的通用 Prompt 结构

下面是一套适合 GPT Image V2 的通用母模板。

```md
Generate an image: {
  "meta": {
    "style_name": "<风格名称>",
    "goal": "<一句话说明这张图要完成什么>"
  },

  "prompt": {
    "image_type": "<图像类型，例如 SaaS hero / app UI / cinematic scene / poster / environment concept>",

    "content": {
      "main_subject": "<核心主体>",
      "secondary_elements": [
        "<辅助元素 1>",
        "<辅助元素 2>",
        "<辅助元素 3>"
      ],
      "environment": "<环境、空间、背景、世界观信息>"
    },

    "composition": {
      "layout": "<构图方式，例如 centered / symmetrical / layered / cinematic framing>",
      "camera": "<镜头距离或视角，例如 close-up / medium shot / wide shot / isometric>",
      "focus": "<画面焦点是什么>",
      "readability": "<强调什么需要清晰：文字、动作、层级、结构、主体轮廓等>"
    },

    "visual_language": {
      "style": "<整体视觉语言>",
      "lighting": "<光线氛围>",
      "color": "<色彩系统>",
      "surface_material": "<材质、边缘、阴影、质感等>"
    },

    "text_behavior": {
      "mode": "<full text / placeholder text / no text>",
      "guidance": "<说明文字如何表现>"
    },

    "quality_notes": {
      "priority": "<最优先保证的内容>",
      "finish": "<完成度要求，例如 high fidelity / polished / commercial-grade>"
    }
  },

  "negative_prompt": [
    "<不要出现的问题 1>",
    "<不要出现的问题 2>",
    "<不要出现的问题 3>"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

## 三、核心生图场景分类

建议将常见需求分成以下 6 类：

1. **产品 / SaaS / 官网 Hero**
2. **App UI / 功能界面**
3. **叙事插画 / 电影感场景**
4. **角色主视觉 / 海报**
5. **环境 / 世界观 / 建筑场景**
6. **品牌 / 广告 / Campaign 视觉**

---

## 四、基础模板

---

### 1）产品 / SaaS / 官网 Hero 模板

```md
Generate an image: {
  "meta": {
    "style_name": "premium SaaS landing hero",
    "goal": "Create a polished product marketing hero visual with strong structure, premium interface aesthetics, and excellent text/render fidelity."
  },

  "prompt": {
    "image_type": "Modern SaaS landing page hero section",

    "content": {
      "main_subject": "A central product module, integration hub, or hero interface element that anchors the composition.",
      "secondary_elements": [
        "Feature cards arranged around or below the main subject",
        "Mini dashboards, charts, labels, badges, or supporting UI modules",
        "Optional connector lines, status blocks, metrics, or integration elements"
      ],
      "environment": "A clean digital product space with soft background treatment and carefully controlled negative space."
    },

    "composition": {
      "layout": "Centered or grid-based composition with strong alignment and clear hierarchy.",
      "camera": "Front-facing product presentation with a stable, slightly elevated or neutral perspective.",
      "focus": "The main product or integration structure should read first.",
      "readability": "Layout clarity, card hierarchy, UI spacing, text placement, and overall polish should feel intentional."
    },

    "visual_language": {
      "style": "Premium software aesthetic, polished UI mockup, calm and modern.",
      "lighting": "Soft studio-style lighting with gentle highlights and controlled shadows.",
      "color": "Pastel, neutral, or brand-led palette with restrained contrast.",
      "surface_material": "Crisp panels, refined shadows, subtle depth, optional glassmorphism or layered surfaces."
    },

    "text_behavior": {
      "mode": "full text",
      "guidance": "Headlines, labels, values, and interface copy can be fully integrated and should feel natural, clean, and well typeset."
    },

    "quality_notes": {
      "priority": "Prioritize structure, text fidelity, UI hierarchy, and overall polish.",
      "finish": "High-fidelity, commercial-grade product visual."
    }
  },

  "negative_prompt": [
    "cluttered layout",
    "broken UI structure",
    "messy spacing",
    "garbled text",
    "random logos",
    "harsh contrast"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

### 2）App UI / 功能界面模板

```md
Generate an image: {
  "meta": {
    "style_name": "high-fidelity app interface visual",
    "goal": "Generate a polished product interface scene with strong feature clarity, readable text, and realistic UI composition."
  },

  "prompt": {
    "image_type": "Mobile app UI or desktop product interface",

    "content": {
      "main_subject": "A specific app screen, feature workflow, or interface state.",
      "secondary_elements": [
        "Navigation bars, tabs, panels, lists, buttons, and cards",
        "Charts, avatars, inputs, filters, toggles, or status indicators",
        "Optional device framing if needed"
      ],
      "environment": "The image should feel like a product design visualization rather than a lifestyle photo."
    },

    "composition": {
      "layout": "Clean screen-centered composition with intuitive structure and balanced information density.",
      "camera": "Straight-on or slightly angled interface presentation.",
      "focus": "The feature flow and interaction logic should feel immediately understandable.",
      "readability": "UI copy, panel grouping, and data structure should remain coherent and legible."
    },

    "visual_language": {
      "style": "Modern interface design, elegant and system-driven.",
      "lighting": "Soft and controlled, enough to add depth without distracting from the content.",
      "color": "Brand-aligned or interface-oriented palette.",
      "surface_material": "Clean digital surfaces, refined shadows, subtle elevation between layers."
    },

    "text_behavior": {
      "mode": "full text",
      "guidance": "UI labels, values, buttons, and section titles should appear stable, readable, and naturally integrated."
    },

    "quality_notes": {
      "priority": "Prioritize interface realism, feature clarity, and typographic cleanliness.",
      "finish": "Highly polished and presentation-ready."
    }
  },

  "negative_prompt": [
    "unreadable interface text",
    "chaotic layout",
    "generic fake app look",
    "overdecorated effects",
    "broken hierarchy"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

### 3）叙事插画 / 电影感场景模板

```md
Generate an image: {
  "meta": {
    "style_name": "cinematic narrative scene",
    "goal": "Capture a dramatic and readable moment with strong storytelling, clear focal emphasis, and high scene coherence."
  },

  "prompt": {
    "image_type": "Narrative illustration or cinematic action frame",

    "content": {
      "main_subject": "The central character, confrontation, or story moment that defines the image.",
      "secondary_elements": [
        "Supporting characters or opposing forces",
        "Atmospheric effects such as smoke, sparks, debris, weather, or magical energy",
        "Architecture, landscape, or setting cues that reinforce the scene"
      ],
      "environment": "A setting that clearly establishes place and tone without overwhelming the main dramatic action."
    },

    "composition": {
      "layout": "Character-centered composition with clear directional energy and strong foreground-background separation.",
      "camera": "Explicitly define the shot distance — close-up, medium shot, or wide shot.",
      "focus": "The viewer should immediately understand who is acting, what is happening, and where the emotional center is.",
      "readability": "Action clarity, subject silhouette, and scene logic should remain readable even when the image is visually rich."
    },

    "visual_language": {
      "style": "Cinematic, dramatic, cohesive, emotionally charged.",
      "lighting": "Controlled dramatic lighting with atmosphere and depth.",
      "color": "Scene-appropriate palette that supports mood and focus.",
      "surface_material": "Detailed but disciplined rendering; effects should support the narrative rather than dominate it."
    },

    "text_behavior": {
      "mode": "no text",
      "guidance": "No visible typography unless explicitly requested."
    },

    "quality_notes": {
      "priority": "Prioritize storytelling clarity, subject focus, and cinematic coherence.",
      "finish": "High-detail, illustration-grade or film-frame-grade."
    }
  },

  "negative_prompt": [
    "confusing action",
    "cluttered crowd scene",
    "unclear subject focus",
    "modern visual intrusions",
    "weak camera logic"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

### 4）角色主视觉 / 海报模板

```md
Generate an image: {
  "meta": {
    "style_name": "character key visual",
    "goal": "Create a high-control hero image centered on a character with strong identity, presence, and visual clarity."
  },

  "prompt": {
    "image_type": "Character poster, hero portrait, or key visual",

    "content": {
      "main_subject": "A single character or tightly controlled group, defined by pose, expression, outfit, and signature traits.",
      "secondary_elements": [
        "Props, costume details, insignia, symbolic motifs",
        "Atmospheric effects or subtle background framing",
        "Optional supporting visual elements that reinforce identity"
      ],
      "environment": "A background that supports the character’s presence without competing for attention."
    },

    "composition": {
      "layout": "Clear focal composition with strong silhouette separation.",
      "camera": "Portrait, half-body, three-quarter, or full-body depending on the use case.",
      "focus": "The character should dominate the image immediately.",
      "readability": "Pose, anatomy, costume design, and expression should all read clearly."
    },

    "visual_language": {
      "style": "Premium, cinematic or illustrative, identity-driven.",
      "lighting": "Directional, elegant, and supportive of facial and costume definition.",
      "color": "Character-led palette that reinforces role and mood.",
      "surface_material": "Well-resolved costume materials, clean edges, detailed but controlled rendering."
    },

    "text_behavior": {
      "mode": "optional",
      "guidance": "No text unless poster typography is specifically needed."
    },

    "quality_notes": {
      "priority": "Prioritize character presence, silhouette, and iconic readability.",
      "finish": "Poster-grade, hero-grade visual finish."
    }
  },

  "negative_prompt": [
    "muddy silhouette",
    "generic outfit design",
    "weak focal hierarchy",
    "off-style anatomy",
    "busy background"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

### 5）环境 / 世界观 / 建筑场景模板

```md
Generate an image: {
  "meta": {
    "style_name": "environment concept visual",
    "goal": "Generate a setting-focused image with strong worldbuilding, spatial readability, and immersive atmosphere."
  },

  "prompt": {
    "image_type": "Environment concept art, architecture scene, or worldbuilding image",

    "content": {
      "main_subject": "The location itself — a city, palace, temple, room, landscape, or designed environment.",
      "secondary_elements": [
        "Pathways, structures, props, lighting sources, vegetation, weather, or storytelling details",
        "Optional scale references such as figures, vehicles, statues, or objects",
        "Foreground, midground, and background layers that define depth"
      ],
      "environment": "The setting should feel coherent, intentional, and rich in identity."
    },

    "composition": {
      "layout": "Wide or medium-wide framing with strong depth cues and a readable focal structure.",
      "camera": "Environmental camera placement that emphasizes scale and space logic.",
      "focus": "The viewer should immediately understand the nature and mood of the place.",
      "readability": "Architecture, pathways, atmospheric depth, and scene hierarchy should be easy to parse."
    },

    "visual_language": {
      "style": "Immersive, art-directed, atmospheric, and spatially clear.",
      "lighting": "Lighting should define form, mood, and depth.",
      "color": "A setting-led palette that supports tone and material identity.",
      "surface_material": "Clear material differentiation across stone, metal, fabric, vegetation, glass, or other surfaces."
    },

    "text_behavior": {
      "mode": "no text or minimal signage",
      "guidance": "Avoid visible typography unless signs or labels are intentionally part of the world."
    },

    "quality_notes": {
      "priority": "Prioritize environment identity, depth, and world logic.",
      "finish": "High-detail concept art or premium scene rendering."
    }
  },

  "negative_prompt": [
    "chaotic architecture",
    "weak sense of scale",
    "flat depth",
    "inconsistent worldbuilding",
    "overstuffed detail"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

### 6）品牌 / 广告 / Campaign 视觉模板

```md
Generate an image: {
  "meta": {
    "style_name": "premium brand campaign visual",
    "goal": "Create a highly art-directed commercial image with strong brand tone, visual control, and memorable impact."
  },

  "prompt": {
    "image_type": "Brand visual, campaign key visual, or editorial advertising image",

    "content": {
      "main_subject": "The product, symbol, scene, or figure that carries the campaign message.",
      "secondary_elements": [
        "Brand motifs, controlled props, texture layers, framing elements, or supporting design cues",
        "Optional environmental styling that reinforces the campaign mood",
        "Selective visual accents that enhance memorability"
      ],
      "environment": "The setting should serve the brand story and feel cohesive rather than generic."
    },

    "composition": {
      "layout": "Bold and highly intentional, with strong focal emphasis and elegant negative space where appropriate.",
      "camera": "Chosen based on campaign need — intimate, dramatic, product-centric, or scene-led.",
      "focus": "The key visual message should land instantly.",
      "readability": "Even if stylized, the image should remain compositionally clear and commercially usable."
    },

    "visual_language": {
      "style": "Premium, editorial, commercial, memorable, and cohesive.",
      "lighting": "Strong art-directed lighting that supports the brand mood.",
      "color": "Brand-led palette or campaign-specific palette with intentional emphasis.",
      "surface_material": "Controlled finish, rich but selective detail, and polished visual impact."
    },

    "text_behavior": {
      "mode": "optional",
      "guidance": "Text can be included if the campaign layout requires it, but it should feel integrated rather than pasted on."
    },

    "quality_notes": {
      "priority": "Prioritize brand tone, impact, and aesthetic consistency.",
      "finish": "Commercial-grade campaign finish."
    }
  },

  "negative_prompt": [
    "generic stock-ad feeling",
    "weak art direction",
    "low-end commercial styling",
    "cluttered composition",
    "mismatched tone"
  ]
} for GPT Image V2 from OpenAI's official account
```

---

## 五、可选增强模块

### 1）文本强化模块

```md
"text_behavior": {
  "mode": "full text",
  "guidance": "Titles, labels, values, card text, and interface copy should be rendered clearly, naturally, and with stable typographic structure."
}
```

### 2）高结构控制模块

```md
"composition": {
  "layout": "Strict grid alignment, modular spacing, and deliberate visual zones.",
  "focus": "Each section should occupy a clear role within the composition.",
  "readability": "The image should maintain strong structure and hierarchy even when multiple modules are present."
}
```

### 3）高完成度商业渲染模块

```md
"quality_notes": {
  "priority": "Preserve control, coherence, and fine detail across the full image.",
  "finish": "High-fidelity, highly polished, commercially usable, and presentation-ready."
}
```

### 4）电影感镜头控制模块

```md
"composition": {
  "camera": "A clearly defined cinematic shot distance with intentional framing.",
  "focus": "The central narrative beat should read instantly.",
  "readability": "Action, gesture, subject silhouette, and spatial logic should remain clear."
}
```

---

## 六、变量占位建议

为了方便后续复用，可以把模板参数化。

### 通用变量
- `{style_name}`
- `{goal}`
- `{image_type}`
- `{main_subject}`
- `{secondary_elements}`
- `{environment}`
- `{layout}`
- `{camera}`
- `{focus}`
- `{readability}`
- `{style}`
- `{lighting}`
- `{color}`
- `{surface_material}`
- `{text_mode}`
- `{text_guidance}`
- `{priority}`
- `{finish}`

### UI / SaaS 类变量
- `{product_type}`
- `{layout_type}`
- `{card_count}`
- `{dashboard_density}`
- `{text_density}`
- `{brand_tone}`
- `{background_palette}`

### 叙事 / 插画类变量
- `{subject}`
- `{moment}`
- `{opponent_or_support}`
- `{camera_distance}`
- `{environment_type}`
- `{lighting_mood}`

### 角色类变量
- `{character_name_or_archetype}`
- `{pose}`
- `{expression}`
- `{costume_style}`
- `{signature_prop}`
- `{framing_type}`

### 环境类变量
- `{location_type}`
- `{world_style}`
- `{time_of_day}`
- `{weather}`
- `{scale_reference}`
- `{architectural_language}`

---

## 七、使用建议

建议按以下流程使用模板：

1. **先判断场景类型**  
   是产品图、UI 图、叙事图、角色图、环境图还是品牌广告图。

2. **选择对应母模板**  
   用最接近的一套作为基础。

3. **替换关键变量**  
   重点替换主体、构图、环境、视觉语言、文字策略。

4. **补充负面约束**  
   写明你最不希望出现的问题。

5. **保留尾部语句**  
   在当前实践中建议保留：  
   **`for GPT Image V2 from OpenAI's official account`**

---

## 八、结论

GPT Image V2 更适合用一种 **结构化、模块化、但保留自然语言弹性** 的方式来描述完整画面系统。

高质量 Prompt 的核心不是堆关键词，而是清楚表达：

- 这是什么图
- 画面主体是什么
- 环境与配体是什么
- 构图如何组织
- 哪些内容必须清晰
- 风格与完成度是什么
- 哪些问题需要避免
