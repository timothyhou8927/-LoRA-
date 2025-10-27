一、项目简介 | Project Overview

“追星星的AI”项目致力于通过 大模型与多模态生成技术，为孤独症儿童及其家庭提供 可个性化生成的视觉绘本工具。
项目以 Qwen-Image 系列模型 为基座，训练特定风格的 LoRA（Low-Rank Adaptation）模型，用于生成符合孤独症儿童视觉认知特征的绘本插图。

目标是让特教教师与家长能够低成本、高效率地创建 简洁、连贯、温和且具教育意义 的个性化故事绘本，帮助孩子更好地理解日常社交、情绪与常识场景。

🧩 二、公益价值 | Social Impact

🎨 个性化支持：针对每位孤独症儿童不同的兴趣、认知水平与感官偏好，定制故事内容与视觉表现。

🤝 减轻教师负担：AI 自动生成绘本素材，大幅降低特教机构手工绘制耗时（3-5小时/本 → 数分钟）。

💬 促进亲子互动：父母可通过自然语言与AI共同生成故事，促进情感交流。

🌍 推动教育普惠：项目模型与工具开放至魔搭社区，助力公益教育资源共享。

⚙️ 三、技术方案 | Technical Architecture

*模型基础*

基模（Base Model）：Qwen-Image 系列

微调方式：LoRA Fine-tuning（低秩适配）

训练平台：魔搭社区 AIGC、模型训练专区（ModelScope AIGC）



*数据来源*

故事文本数据集：Starlight-AI Test Set

专业知识包：《孤独症儿童绘本相关资料包》

绘本生成流程基线：绘本生成Baseline工作流


🧠 四、LoRA 训练细节 | LoRA Training Details
项目	内容
训练模型	Qwen-Image
微调方法	LoRA (rank=8, alpha=16)
优化目标	保持人物与场景一致性、强化视觉焦点、减少背景干扰
数据类型	四类功能绘本（常识认知、社交礼仪、心智解读、趣味故事）
输出格式	图像 + Prompt 组合，形成完整故事绘本场景
Prompt 设计要点

指定人物名称、服装、场景关键词，保持风格一致。

控制构图（单主体、背景简洁）。

明确色彩方案（高饱和、纯色对比）。

指令示例：

Prompt: A little boy with blue T-shirt smiles and waves to his friend at the playground.
Style: bright color blocks, flat illustration, simple background, autism-friendly visual.

🖼️ 五、作品展示 | Output Showcase

本项目提交至少 8 组绘本样例，涵盖 4 种功能类型：

功能类型	示例主题	画风特点
常识认知	认识交通工具	写实简练，清晰主体
社交礼仪	学会说谢谢	表情明确，情境单一
心智解读	小熊的情绪色彩	温暖色调，情绪导向
趣味故事	小兔找月亮	连贯构图，柔和线条

所有图片均由训练后的 LoRA 模型生成，保持主角与风格一致性。

💡 六、技术亮点 | Technical Highlights

多模态协同生成：结合文本理解与图像生成，使AI能根据故事语义自动优化画面。

LoRA轻量化训练：参数高效复用，仅需少量计算资源即可实现特定绘本风格迁移。

视觉认知适配：基于孤独症儿童视觉心理特征（低干扰、高对比度、简洁背景）定向优化。

开放式工作流：集成绘本生成、prompt管理与图像一致性检测于一体的流程化工具。

🚀 七、使用说明 | How to Use

1.模型加载
在 ModelScope 或魔搭社区中下载本项目 LoRA 模型。

from modelscope import pipeline
pipe = pipeline('text-to-image', model='Qwen/Qwen-Image', lora='username/AutismStorybook-LoRA')


2.输入故事文本
使用官方故事集文本，或自定义故事输入。

3.生成插图

images = pipe("A boy learns to share his toy with friends, autism-friendly style.")
images[0].save("storybook_page1.png")

4.导出绘本
将生成的图像按故事顺序组合输出，即可形成完整电子绘本。

🌱 八、未来展望 | Future Directions

🧩 LoRA风格扩展：为不同儿童偏好（如动物、交通工具、自然景象）创建更多可复用风格包。

🗣️ 语音阅读支持：结合语音合成技术，为绘本添加温柔语音解说。

🌐 家庭端生成器：构建Web端交互界面，让家长可一键生成并打印个性化绘本。

🤖 情绪识别反馈：通过视觉与语音分析，让系统自动推荐适配的故事类型。

📎 九、文件结构 | File Structure
├── README.md
├── models/
│   └── AutismStorybook-LoRA (LoRA weights)

├── prompts/
│   ├── cognition_prompts.json
│   ├── social_prompts.json
│   ├── emotion_prompts.json
│   └── story_prompts.json

├── outputs/
│   ├── story_1/
│   │   ├── image_1.png
│   │   └── prompt.txt
│   └── story_8/
└── scripts/
    ├── generate_storybook.py
    └── evaluate_style_consistency.ipynb
