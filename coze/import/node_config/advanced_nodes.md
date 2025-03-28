# 高级节点信息

## 知识库&数据库

### 知识库写入
![知识库写入](../assets/icons/kb_write.png)

知识库写入节点用于向知识库中添加或更新内容。

**功能**：
- 向知识库添加新内容
- 更新现有知识库内容
- 支持多种格式的知识导入

### 知识库检索
![知识库检索](../assets/icons/kb_search.png)

知识库检索节点用于从知识库中检索相关信息。

**功能**：
- 语义化检索知识库内容
- 支持相似度匹配
- 可配置检索结果数量和相似度阈值

### 长期记忆
![长期记忆](../assets/icons/long_term_memory.png)

长期记忆节点用于存储和检索长期对话历史和关键信息。

**功能**：
- 存储重要对话内容
- 检索历史交互信息
- 维护用户长期上下文

### 变量赋值
![变量赋值](../assets/icons/variable_assign.png)

变量赋值节点用于设置和管理工作流中的变量值。

**功能**：
- 设置变量值
- 支持多种数据类型
- 可用于状态管理和数据传递

## 图像处理

### 图像生成
![图像生成](../assets/icons/image_generation.png)

图像生成节点用于创建AI生成的图像。

**功能**：
- 基于文本描述生成图像
- 支持多种风格和尺寸
- 可配置生成参数

**配置示例**：
```json
{
  "type": "image_generation",
  "config": {
    "model": "stable-diffusion",
    "prompt": "${image_description}",
    "negative_prompt": "低质量, 模糊",
    "size": "1024x1024",
    "style": "写实风格"
  },
  "input": {
    "image_description": "${input}"
  },
  "output": {
    "image_url": "generated_image"
  }
}
```

### 画板
![画板](../assets/icons/canvas.png)

画板节点提供图像编辑和绘制功能。

**功能**：
- 编辑和修改图像
- 添加文本和图形元素
- 支持图层和混合模式

### 报图
![报图](../assets/icons/chart.png)

报图节点用于生成数据可视化图表。

**功能**：
- 将数据转换为可视化图表
- 支持多种图表类型（柱状图、折线图、饼图等）
- 可自定义图表样式和布局

### 提示词优化
![提示词优化](../assets/icons/prompt_optimization.png)

提示词优化节点用于改进图像生成的提示词。

**功能**：
- 分析和优化图像生成提示词
- 增强提示词的描述性和精确性
- 提高生成图像的质量和相关性

### 画质提升
![画质提升](../assets/icons/image_enhancement.png)

画质提升节点用于提高图像的质量和清晰度。

**功能**：
- 提高图像分辨率
- 减少噪点和模糊
- 增强细节和对比度

## 组件

### 问答
![问答](../assets/icons/qa.png)

问答组件节点用于构建问答系统。

**功能**：
- 处理用户问题
- 生成相关答案
- 支持知识库集成

### 文本处理
![文本处理](../assets/icons/text_processing.png)

文本处理节点用于执行各种文本操作。

**功能**：
- 文本分析和提取
- 格式转换和规范化
- 内容摘要和分类

### HTTP请求
![HTTP请求](../assets/icons/http_request.png)

HTTP请求节点用于与外部API和服务进行交互。

**功能**：
- 发送HTTP请求（GET、POST、PUT、DELETE等）
- 处理API响应
- 支持认证和自定义头部

**配置示例**：
```json
{
  "type": "http_request",
  "config": {
    "method": "POST",
    "url": "https://api.example.com/data",
    "headers": {
      "Content-Type": "application/json",
      "Authorization": "Bearer ${token}"
    }
  },
  "input": {
    "body": "${request_data}",
    "token": "${auth_token}"
  },
  "output": {
    "response": "api_response",
    "status": "status_code"
  }
}
```

## 节点配置通用参数

### 输入参数
- **参数名**: 定义输入参数的名称
- **变量类型**: 支持字符串、数字、布尔值、对象、数组等类型
- **默认值**: 当未提供输入时使用的值

### 输出配置
- **变量名**: 定义输出变量的名称
- **输出格式**: 可选择文本、JSON、二进制等
- **异常忽略**: 可配置是否忽略异常并提供默认输出

### 异常处理
- **忽略异常**: 当设置为开启时，节点执行出错不会中断工作流
- **替代输出**: 当异常被忽略时，可以配置替代的输出值

# Coze平台高级节点配置示例

本文档提供Coze平台中高级节点的详细配置示例和使用方法，帮助开发者更好地理解和使用这些节点。

## 1. 代码节点详解

代码节点允许您编写自定义代码来处理输入数据并生成输出结果。

### 配置示例

```javascript
// 在这里，您可以通过 'params' 获取输入参数
// 'params' 和 'ret' 已经被正确地注入
// 下面是一个示例，获取名为input的参数
// const input = params.input;
// 下面是一个示例，输出一个包含多种数据类型的对象
// const ret = { "name": "小明", "hobby": "读书" };

async function main({ params }: Args) {
  // 构建输出对象
  const result = {
    text: params.input + " 已处理",
    count: params.input.length,
    processed: true,
    details: {
      timestamp: new Date().toISOString(),
      source: "代码节点"
    }
  };
  
  return result;
}
```

### 输入参数配置

| 参数名 | 参数类型 | 说明 |
|--------|---------|------|
| input  | str     | 输入文本 |

### 输出参数配置

| 变量名 | 变量类型 | 说明 |
|--------|---------|------|
| key0   | str.String | 处理后的文本 |
| key1   | [].Array   | 数组类型输出 |
| key2   | {}.Object  | 对象类型输出 |
| key21  | str.String | 对象内的字符串属性 |

### 高级用法

1. **异步处理**：
```javascript
async function main({ params }: Args) {
  // 异步操作示例
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return { result: data };
}
```

2. **错误处理**：
```javascript
async function main({ params }: Args) {
  try {
    // 可能出错的代码
    const result = processData(params.input);
    return { success: true, data: result };
  } catch (error) {
    return { success: false, error: error.message };
  }
}
```

3. **数据转换**：
```javascript
async function main({ params }: Args) {
  // 将JSON字符串转换为对象
  const data = JSON.parse(params.input);
  // 处理数据
  const processed = data.items.map(item => ({
    id: item.id,
    name: item.name.toUpperCase(),
    value: item.value * 2
  }));
  return { processed };
}
```

## 2. 选择器节点详解

选择器节点用于根据条件选择不同的执行路径，实现条件分支逻辑。

### 配置示例

#### 基本条件判断

```
如果 [请选择] [str.] [输入或引用参数值] [新增]

否则
```

#### 多条件判断

```
如果 [用户输入] [包含] [帮助]
如果 [用户分数] [大于] [80]
如果 [用户状态] [等于] [活跃]

否则
```

### 使用技巧

1. **条件优先级**：条件按从上到下的顺序评估，一旦满足某个条件，就会执行对应分支
2. **复合条件**：可以使用代码节点预处理复杂条件，然后在选择器中使用处理结果
3. **默认路径**：始终设置"否则"分支作为默认路径，确保所有情况都有处理方式

### 应用场景

1. **用户意图分流**：根据用户输入内容选择不同的处理流程
2. **数据验证分支**：根据数据验证结果选择成功或失败处理路径
3. **多级决策树**：构建复杂的决策树结构，实现智能决策

## 3. 意图识别节点详解

意图识别节点用于分析用户输入，识别其意图并进行分类。

### 配置示例

#### 输入配置
```
参数名: query
参数值: str. [输入或引用参数值]
```

#### 意图匹配配置
```
[请输入用户意图的描述，如星座问题等] [删除]
其他意图
```

#### 输出配置
```
classificationId: Integer
```

### 使用技巧

1. **意图描述优化**：
   - 使用清晰、具体的描述
   - 包含可能的用户表达方式
   - 避免过于宽泛的描述

2. **多意图处理**：
   - 为每个意图创建专门的处理流程
   - 使用选择器节点根据classificationId路由到对应处理流程

3. **未识别意图处理**：
   - 为"其他意图"设置合适的处理流程
   - 考虑使用反馈机制收集未识别的意图

### 应用场景

1. **智能客服**：识别用户咨询类型，路由到相应的处理流程
2. **多功能助手**：根据用户需求提供不同服务
3. **用户意图分析**：收集和分析用户意图数据

## 4. 循环节点详解

循环节点用于重复执行特定操作，处理数组数据或实现迭代逻辑。

### 配置示例

#### 循环设置
```
循环类型: 使用数组循环
```

#### 循环数据
```
参数名: input
参数值: [str] [输入或引用参数值]
```

#### 中间变量
```
参数名: [自定义变量名]
参数值: [变量类型] [值]
```

#### 输出配置
```
参数名: output
参数值: str. [引用参数值] [新数据]
```

### 使用技巧

1. **数组循环优化**：
   - 预处理数组数据，移除不需要处理的元素
   - 使用中间变量存储累积结果
   - 考虑使用批处理节点替代大型数组的循环

2. **循环控制**：
   - 设置明确的循环终止条件
   - 使用计数器防止无限循环
   - 考虑提前退出机制

3. **数据聚合**：
   - 使用中间变量收集循环处理结果
   - 在循环后使用代码节点处理聚合数据

### 应用场景

1. **批量数据处理**：处理用户提交的多条数据
2. **迭代优化**：通过多次迭代改进结果
3. **分页数据获取**：循环获取多页数据

## 5. 批处理节点详解

批处理节点用于并行处理多个任务，提高处理效率。

### 配置示例

#### 批处理设置
```
并行运行数量: int. 10
批处理次数上限: int. 100
```

#### 输入配置
```
参数名: input
参数值: [str] [输入或引用参数值]
```

#### 输出配置
```
参数名: output
参数值: str. [引用参数值] [新数据]
```

### 使用技巧

1. **并行度优化**：
   - 根据任务复杂度和资源限制调整并行数量
   - 对于IO密集型任务，可以使用更高的并行度
   - 对于计算密集型任务，适当降低并行度

2. **错误处理**：
   - 实现单个任务的错误处理机制
   - 考虑部分失败情况下的整体处理策略
   - 使用日志记录失败任务信息

3. **资源管理**：
   - 监控资源使用情况
   - 避免过高的并行度导致资源耗尽
   - 考虑使用批次处理大量数据

### 应用场景

1. **大规模数据处理**：并行处理大量数据记录
2. **多API并行调用**：同时调用多个外部服务
3. **性能优化**：提高处理吞吐量

## 节点组合最佳实践

### 数据预处理 + 批处理模式

```
输入节点 → 代码节点(数据分割) → 批处理节点 → 代码节点(结果合并) → 输出节点
```

这种模式适用于处理大量数据，先将数据分割成小批次，然后并行处理，最后合并结果。

### 意图识别 + 选择器模式

```
输入节点 → 意图识别节点 → 选择器节点 → 多个专门处理节点 → 输出节点
```

这种模式适用于构建多功能机器人，根据用户意图选择不同的处理流程。

### 循环 + 条件退出模式

```
输入节点 → 代码节点(初始化) → 循环节点 → 代码节点(处理) → 选择器节点(检查退出条件) → 输出节点
```

这种模式适用于需要迭代处理直到满足特定条件的场景。

### 批处理 + 错误重试模式

```
输入节点 → 批处理节点 → 选择器节点(检查成功/失败) → 代码节点(重试失败项) → 输出节点
```

这种模式适用于需要确保所有任务都成功完成的场景，对失败的任务进行重试。 