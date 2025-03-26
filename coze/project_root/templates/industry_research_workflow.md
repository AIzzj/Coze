# 5分钟深度行业研究工作流详解

## 📊 完整工作流结构

### 1. 基础流程
```
[开始节点] → [消息] → [create_document] → [变量聚合] → [代码] → ...
```

### 2. 主要分析流程
```
[代码] → [行业概览关键词提取] → [行业概览分析] → [概述写入文档] → [输出]
        ↓
[4P分析关键词提取] → [4P分析] → [4P分析写入文档] → [输出]
        ↓
[行业特征分析关键词提取] → [行业特征分析] → [特征分析写入文档] → [输出]
        ↓
[竞争分析关键词提取] → [竞争分析] → [竞争分析写入文档] → [输出]
```

## 🔄 节点详细配置

### 1. 开始节点
- 输入参数：`BOT_USER_INPUT`（用户输入的行业名称）
- 输出连接：连接到消息节点

### 2. 消息节点
- 输入：来自开始节点的行业名称
- 功能：确认开始分析
- 输出：连接到create_document节点

### 3. create_document节点
输入参数：
- `content`：文档内容
- `title`：文档标题
- `folder_token`：文件夹标识
输出参数：
- `errorMessage`
- `errorCode`

### 4. 变量聚合节点
功能：对create_document的输出进行处理
Group1配置：
- `create_document.errorMessage`
- `create_document.errorCode`

### 5. 代码节点
功能：处理错误信息和授权验证
输入：
- `input`：来自变量聚合的结果
输出：
- `key0`：处理结果

### 6. 分析循环结构
每个分析模块包含4个关键节点：
1. 关键词提取节点：
   - 输入：`keywords`
   - 输出：`output`

2. 必应搜索节点：
   - 输入参数：
     - `query`：搜索关键词
     - `count`：结果数量
     - `freshness`：时间范围
     - `offset`：偏移量

3. 分析写入节点：
   - 输入：
     - `content`：分析内容
     - `document_id`：文档ID
     - `position`：插入位置

4. 结果输出节点：
   - 功能：确认内容写入完成
   - 输出：写入状态

## 🔗 变量传递说明

### 1. 文档创建阶段
```
BOT_USER_INPUT → 消息节点
↓
create_document(content, title, folder_token)
↓
变量聚合(errorMessage, errorCode)
↓
代码处理(input → key0)
```

### 2. 分析循环阶段
每个分析模块的变量传递：
```
关键词提取(keywords → output)
↓
必应搜索(query, count, freshness → search_results)
↓
内容分析(content, document_id, position)
↓
结果确认(status)
```

## ⚙️ 特殊节点配置

### 1. 必应搜索节点
标准配置：
- `count`: 5
- `market`: "zh-CN"
- `freshness`: "Month"

### 2. 文档写入节点
位置控制：
- 使用`position`参数控制内容插入位置
- 确保内容按正确顺序写入

## 💡 优化建议

1. 并行处理
- 4个分析模块可以并行执行
- 使用变量聚合节点汇总结果

2. 错误处理
- 每个模块都有错误捕获
- 使用代码节点处理异常

3. 性能优化
- 合理设置搜索结果数量
- 控制API调用频率

## 🔍 调试要点

1. 文档创建
- 检查授权状态
- 验证文档创建权限

2. 搜索模块
- 监控API限制
- 检查关键词质量

3. 内容写入
- 确认文档ID正确
- 验证写入权限 