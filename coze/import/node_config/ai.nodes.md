# AI 节点文档

## 1. 大模型节点
### 功能描述
- 调用大型语言模型
- 支持多种模型选择
- 可配置系统提示词

### 关键参数
- model: 模型选择（如豆包-L5-Pro）
- temperature: 温度参数（0-1）
- system_prompt: 系统提示词
- max_tokens: 最大输出长度

### 使用场景
- 文本生成
- 对话交互
- 内容创作

### 配置示例
```json
{
  "model": "豆包-L5-Pro",
  "temperature": 0.7,
  "system_prompt": "你是一个专业的助手",
  "max_tokens": 2000
}
```

## 2. 意图识别节点
### 功能描述
- 识别用户输入意图
- 分类用户请求
- 提取关键信息

### 关键参数
- input_text: 输入文本
- intent_types: 意图类型列表
- confidence_threshold: 置信度阈值

### 使用场景
- 用户需求分类
- 对话场景识别
- 任务分发

## 3. 知识库节点
### 功能描述
- 知识库检索
- 相似度匹配
- 答案生成

### 关键参数
- query: 检索查询
- top_k: 返回结果数量
- similarity_threshold: 相似度阈值

### 使用场景
- 智能问答
- 知识检索
- 文档查询

## 4. 图像生成节点
### 功能描述
- AI 图像生成
- 图像风格转换
- 图像编辑

### 关键参数
- prompt: 图像描述
- style: 风格设置
- size: 图像尺寸
- negative_prompt: 负面提示词

### 使用场景
- 创意设计
- 内容制作
- 视觉展示

## 5. 语音处理节点
### 功能描述
- 语音识别
- 语音合成
- 音色克隆

### 关键参数
- audio_input: 音频输入
- voice_id: 音色ID
- language: 语言设置
- speed: 语速调节

### 使用场景
- 语音交互
- 音频处理
- 多模态应用

# AI节点模型信息

## 模型列表

### Moonshot系列（由月之暗面提供）

#### Kimi 8K
- 模型ID: moonshot-v1-8k
- 上下文窗口: 8K
- 输出格式: Json输出、functionCall
- 特点: Kimi大模型与"Kimi智能助手"为同款模型
- 使用场景: 限额使用，适合性价比场景

#### Kimi 32K
- 模型ID: moonshot-v1-32k
- 上下文窗口: 32K
- 输出格式: Json输出、functionCall
- 特点: Kimi大模型与"Kimi智能助手"为同款模型
- 使用场景: 限额使用，适合性价比场景

#### Kimi 128K
- 模型ID: moonshot-v1-128k
- 上下文窗口: 128K
- 输出格式: Json输出、functionCall
- 特点: Kimi大模型与"Kimi智能助手"为同款模型
- 使用场景: 限额使用，适合长文本处理

### 百川系列（由百川智能提供）

#### 百川·4
- 模型ID: Baichuan4
- 上下文窗口: 32K
- 输出格式: Json输出、functionCall
- 特点: 百川智能最新第4代基座大模型
- 使用场景: 限额使用，旗舰级性能

### 豆包系列（由字节跳动提供）

#### 豆包·工具调用
- 模型ID: ep-20250103114050-hgnz5
- 上下文窗口: 32K
- 输出格式: 支持微调、functionCall
- 特点: Doubao-pro-32k/241215，主力模型，适合处理复杂任务，在各类场景下表现优异

#### 豆包·1.5·Pro·32k
- 模型ID: ep-20250122125445-ck9wp
- 上下文窗口: 32K
- 输出格式: functionCall
- 特点: Doubao-1.5-pro-32k，全新一代主力模型，性能全面升级
- 使用场景: 旗舰级性能

#### 豆包·1.5·Pro·256k
- 模型ID: ep-20250123120326-whd2h
- 上下文窗口: 256K
- 输出格式: Json输出、functionCall
- 特点: Doubao-1.5-pro-256k基于Doubao-1.5-Pro全面升级版，整体性能更强
- 使用场景: 高级、长文本、旗舰级性能

#### 豆包·视觉理解·Pro
- 模型ID: ep-20241213110738-6svsb
- 上下文窗口: 32K
- 输出格式: 图片理解
- 特点: Doubao-vision-pro-32k/241028，具备强大的图片理解与推理能力
- 使用场景: 图片理解

#### 豆包·视觉理解·Lite
- 模型ID: ep-20250212163522-t6br7
- 上下文窗口: 32K
- 输出格式: 图片理解
- 特点: Doubao-vision-lite-32k/241015，具备强大的图片理解与推理能力
- 使用场景: 高速、图片理解

#### 豆包·通用模型·Lite
- 模型ID: ep-20241010173045-24s99
- 上下文窗口: 32K
- 输出格式: 支持微调、functionCall
- 特点: Doubao-lite-32k/240828，响应速度更快
- 使用场景: 高速

#### 豆包·通用模型·Lite·128k
- 模型ID: ep-20250212162939-tkhp8
- 上下文窗口: 128K
- 输出格式: functionCall
- 特点: Doubao-lite-128k/240828，拥有极致的响应速度，更好的性价比
- 使用场景: 高速

#### 豆包·通用模型·Pro
- 模型ID: ep-20241010172728-279wq
- 上下文窗口: 32K
- 输出格式: 支持微调、functionCall
- 特点: Doubao-pro-32k/240828，在参考问答、总结摘要、创作、文本处理等场景表现优异
- 使用场景: 旗舰级性能

#### 豆包·通用模型·Pro·256k
- 模型ID: ep-20250212162000-zkfh8
- 上下文窗口: 256K
- 输出格式: 长文本
- 特点: Doubao-pro-256k，主力模型，适合处理复杂任务
- 使用场景: 高级、长文本

#### 豆包·角色扮演·Pro
- 模型ID: ep-20250115160924-2mlxr
- 上下文窗口: 32K
- 输出格式: 角色扮演
- 特点: Doubao-pro-32k/character-241215，角色扮演效果更优秀
- 使用场景: 角色扮演

#### 豆包·角色扮演
- 模型ID: seed_strong_character
- 上下文窗口: 32K
- 输出格式: 角色扮演
- 特点: Seed-strong-character，通过深入分析用户的输入和行为，制定更加精准的角色扮演策略
- 使用场景: 限额使用，角色扮演

### 阶跃星辰系列

#### 阶跃星辰·1.5v·视频理解
- 模型ID: step-1.5v-mini
- 上下文窗口: 32K
- 输出格式: 图片理解、视频理解
- 特点: 强大视频理解能力
- 使用场景: 限额使用，视频理解

#### 阶跃星辰·1v·图片理解
- 模型ID: step-1v-8k
- 上下文窗口: 8K
- 输出格式: 图片理解
- 特点: 优秀图像理解能力
- 使用场景: 限额使用，图片理解

### 通义千问系列（由阿里巴巴提供）

#### 通义千问·Max
- 模型ID: qwen-max
- 上下文窗口: 8K
- 输出格式: functionCall、Json输出
- 特点: 通义千问系列中最强的模型
- 使用场景: 限额使用，旗舰级性能

### 智谱系列（由智谱提供）

#### 智谱·4
- 模型ID: glm-4-0520
- 上下文窗口: 128K
- 输出格式: Json输出、functionCall
- 特点: 智谱AI最新大模型
- 使用场景: 限额使用，旗舰级性能

### abab系列（由Minimax提供）

#### abab6.5s
- 模型ID: abab6.5s-chat-pro
- 上下文窗口: 245K
- 输出格式: Json输出、functionCall
- 特点: 245k超长上下文
- 使用场景: 限额使用，长文本

#### abab6.5
- 模型ID: abab6.5-chat-pro
- 上下文窗口: 8K
- 输出格式: Json输出、functionCall
- 特点: 即将下线，尽快迁移
- 使用场景: 限额使用

### DeepSeek系列（由深度求索提供）

#### DeepSeek-V3
- 模型ID: ep-20250204211414-ckw8d
- 上下文窗口: 64K
- 输出格式: MoE模型
- 特点: V3 functionCall 版本，支持在Single-Agent模式下调用各类工具
- 使用场景: 工具调用，Beta版本

#### DeepSeek-R1-Distill-Qwen-7B
- 模型ID: ep-20250206162353-cf5kf
- 上下文窗口: 64K
- 输出格式: CoT（思维链）
- 特点: 通过DeepSeek-R1 660B模型的推理蒸馏技术打造，在数学推理、逻辑推理等方面表现优异
- 使用场景: 深度思考，复杂推理

#### DeepSeek-R1-Distill-Qwen-32B
- 模型ID: ep-20250206162425-t5m5w
- 上下文窗口: 64K
- 输出格式: CoT（思维链）
- 特点: 通过DeepSeek-R1 660B模型的推理蒸馏技术打造，在数学推理、逻辑推理等方面表现优异
- 使用场景: 深度思考，复杂推理

#### DeepSeek·3
- 模型ID: deepseek-chat
- 上下文窗口: 31K
- 输出格式: Json输出、functionCall
- 特点: 当前使用人数较多，服务不稳定，若遇到调用失败等问题可切换其他模型
- 使用场景: 限额使用，代码专精

#### DeepSeek-R1
- 模型ID: ep-20250204211352-q625s
- 上下文窗口: 64K
- 输出格式: CoT（思维链）
- 特点: DeepSeek-reasoner，在输出最终回答之前，模型会先输出一段推理过程
- 使用场景: 深度思考

#### DeepSeek-R1·工具调用
- 模型ID: ep-20250204211352-q625s
- 上下文窗口: 64K
- 输出格式: 工具调用，Beta版本
- 特点: R1 functionCall 版本，支持在Single-Agent模式下调用各类工具
- 使用场景: 工具调用，深度思考

## 大模型节点配置

### 大模型节点
```json
{
  "type": "large_model",
  "config": {
    "model_id": "moonshot-v1-8k",
    "temperature": 0.7,
    "system_prompt": "你是一个专业的助手",
    "max_tokens": 2000,
    "top_p": 0.95,
    "top_k": 50,
    "presence_penalty": 0,
    "frequency_penalty": 0
  },
  "input": {
    "prompt": "${input}"
  },
  "output": {
    "result": "output"
  }
}
```

#### 参数说明
- **model_id**: 模型ID，可选择上述列表中的模型
- **temperature**: 温度参数，控制生成随机性，范围0-1
- **system_prompt**: 系统提示词，设定模型的角色和行为
- **max_tokens**: 最大生成token数
- **top_p**: 累计概率截断，范围0-1
- **top_k**: 保留概率最高的k个token
- **presence_penalty**: 重复主题惩罚
- **frequency_penalty**: 重复度惩罚

### 输入输出配置
- **输入参数名**: 默认为"input"，类型为字符串
- **系统提示词**: 可使用变量引用输入参数中的变量
- **用户提示词**: 可使用变量引用输入参数中的变量
- **输出格式**: 支持文本、Markdown、JSON
- **异常忽略**: 可选择是否忽略异常并在异常发生时使用默认输出替代
