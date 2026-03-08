# 主流Agent平台部署教程（零基础/轻量开发）
本技能体系基于**关键词触发+固定流程+纯文字输出+对话式交互**开发，适配所有主流AI Agent/大模型平台，以下为核心平台的**快速部署方法**，分「零基础部署」（无开发能力）和「轻量开发」（少量代码/配置）。

## 一、国内商用智能助手（零基础部署，推荐个人/新手）
### 1. 字节跳动豆包
1. 打开豆包，进入「我的→指令库→新建指令」；
2. 指令名称：短视频提示词创作Agent；
3. 指令内容：复制本仓库`core-skills/video-prompt-skill/trigger-words.md`和`core-skills/video-prompt-skill/guide-steps.md`的核心内容；
4. 触发方式：选择「关键词触发」，录入12个核心触发关键词；
5. 保存后，输入任意触发关键词即可调用技能。

### 2. 阿里通义千问
1. 打开千问，进入「技能→自定义技能→新建场景对话」；
2. 场景名称：短视频提示词创作；
3. 对话流程：按`guide-steps.md`的对话引导流程，设置「用户输入（数字）→机器人回复」的交互节点；
4. 技能规则：录入12个触发关键词及对应功能，参考`trigger-words.md`；
5. 保存后，输入「引导」即可开启分步创作。

### 3. 百度文心一言
1. 打开文心一言，进入「定制→定制问答→新增问答」；
2. 批量录入12个触发关键词作为「问题」，对应功能/流程作为「答案」；
3. 进入「技能广场→我的技能」，将定制问答设为「启用」；
4. 输入触发关键词即可一键调用。

### 4. 科大讯飞星火
1. 打开星火，进入「我的→指令模板→新建模板」；
2. 模板名称：短视频提示词创作技能；
3. 模板内容：复制本仓库`core-skills/video-prompt-skill/core-skills-detail.md`的核心内容；
4. 触发关键词：录入12个核心触发关键词；
5. 保存后，输入关键词即可调用模板。

## 二、海外商用Agent（零基础/轻量开发，推荐个人/小团队）
### 1. OpenAI ChatGPT/GPTs（零基础搭建专属GPT）
1. 打开ChatGPT，进入「Explore→Create a GPT」；
2. **Configure**页：
   - Name：Video Prompt Creator Agent
   - Description：高效生成合规可过审的短视频提示词，支持关键词触发、对话引导；
   - Instructions：复制本仓库`core-skills/video-prompt-skill/trigger-words.md`和`core-skills/video-prompt-skill/core-skills-detail.md`的核心内容；
3. **Capabilities**：关闭「Web browsing」「DALL·E」「Code interpreter」（仅保留文本能力）；
4. **Save**：选择「For yourself」/「Public」，生成专属GPT；
5. 直接在专属GPT中输入触发关键词即可使用。

### 2. OpenAI Assistant API（轻量开发，企业/团队）
1. 进入OpenAI平台，创建新的Assistant；
2. 配置Assistant：
   - Name：Video Prompt Skill Assistant
   - Instructions：录入6大核心技能的流程和过审检测规则；
   - Tools：无需添加工具，仅保留「Code Interpreter」（可选）；
3. 将12个触发关键词封装为**API调用参数**，对应不同的技能执行逻辑；
4. 调用Assistant API，传入触发关键词/用户需求，即可自动返回结果。

## 三、开源Agent框架（轻量开发，技术爱好者/团队）
### 1. LangChain（主流推荐）
1. 将6大核心技能封装为**LangChain Tools**，每个Skill对应一个Tool函数；
2. 将12个触发关键词设为**Tool触发词**，通过Prompt工程实现关键词匹配；
3. 将`guide-steps.md`的对话流程封装为**LangChain ConversationChain**，实现多轮对话引导；
4. 结合本地大模型（如Qwen/LLaMA 3）或云端大模型，部署私有化Agent；
5. 输入触发关键词，自动调用对应Tool，执行技能流程。

### 2. LLaMA Index
1. 将本仓库的所有技能内容导入LLaMA Index的**Document Store**；
2. 创建**Query Engine**，设置关键词匹配规则，关联触发词与技能内容；
3. 将6大核心技能封装为**Functions**，实现技能的自动化调用；
4. 部署后，输入用户需求/触发关键词，即可返回对应的提示词/技能结果。

## 四、企业级Agent平台（企业/团队，私有化部署）
### 1. 字节跳动火山方舟
1. 进入火山方舟平台，选择「自定义Agent→新建Agent」；
2. 选择基础大模型（如豆包大模型）；
3. 配置Agent：录入12个触发关键词、6大核心技能流程、对话引导步骤；
4. 将Skill 6的过审检测规则封装为**自定义插件**；
5. 发布为企业内部专属Agent，团队成员可直接调用。

### 2. 百度文心千帆/阿里通义灵码
1. 将6大核心技能封装为**REST API**，每个技能对应一个API接口；
2. 在文心千帆/通义灵码平台，创建新的Agent，关联API接口；
3. 设置关键词触发规则，录入12个核心触发关键词；
4. 部署为企业级Agent，支持团队批量调用、接口对接。

## 五、部署核心原则
1. **保留核心逻辑**：无论哪种平台，均需保留12个触发关键词、6大技能流程、对话引导顺序；
2. **纯文本输出**：关闭所有图片/视频生成功能，仅保留文本输出能力；
3. **合规优先**：将Skill 6的过审检测规则作为核心配置，确保输出内容合规；
4. **简化交互**：所有引导选项均为数字，降低用户使用成本。