# 扣子平台工作流搭建完全指南

## 第一章：基础概念

### 1.1 什么是工作流
工作流是由多个节点组成的处理流程，就像搭积木一样，每个节点都有特定的功能，通过连接这些节点，我们可以实现复杂的功能。

### 1.2 节点类型介绍
1. 开始节点（Start Node）
   - 作用：接收用户输入
   - 特点：每个工作流必须有一个开始节点

2. 处理节点（Process Node）
   - 文本处理
   - 图像处理
   - 数据分析等

3. 输出节点（Output Node）
   - 返回结果
   - 保存数据等

## 第二章：开始搭建第一个工作流

### 2.1 准备工作
1. 登录扣子平台
2. 创建新的工作流项目
3. 熟悉界面布局

### 2.2 创建简单对话工作流
让我们创建一个简单的问答机器人：

```json
{
    "name": "simple_chat",
    "nodes": [
        {
            "id": "user_input",
            "type": "start",
            "config": {
                "input_params": [
                    {
                        "name": "message",
                        "type": "string"
                    }
                ]
            }
        },
        {
            "id": "chat_response",
            "type": "llm",
            "config": {
                "model": "gpt-4",
                "temperature": 0.7
            }
        }
    ],
    "connections": [
        {
            "from": "user_input",
            "to": "chat_response"
        }
    ]
}
```

#### 步骤说明：
1. 创建开始节点
2. 添加LLM响应节点
3. 连接节点
4. 设置参数

## 第三章：变量传递详解

### 3.1 变量基础
变量是在节点之间传递数据的容器。每个变量都有：
- 名称：用于识别变量
- 类型：如string、number、object等
- 作用域：在哪些节点间可用

### 3.2 变量传递示例
以智能客服模板为例：

```json
{
    "variables": [
        {
            "name": "user_query",
            "type": "string",
            "description": "用户输入的问题"
        },
        {
            "name": "intent",
            "type": "object",
            "description": "识别出的意图"
        }
    ],
    "nodes": [
        {
            "id": "input",
            "outputs": ["user_query"]
        },
        {
            "id": "intent_recognition",
            "inputs": ["user_query"],
            "outputs": ["intent"]
        }
    ]
}
```

#### 变量传递流程：
1. 用户输入 -> user_query
2. user_query -> 意图识别
3. 意图识别 -> intent
4. intent -> 后续处理

## 第四章：高级工作流搭建

### 4.1 条件分支
示例：根据意图分流处理

```json
{
    "nodes": [
        {
            "id": "condition",
            "type": "condition",
            "config": {
                "conditions": [
                    {
                        "if": "intent.type == 'question'",
                        "then": "qa_node"
                    },
                    {
                        "if": "intent.type == 'chat'",
                        "then": "chat_node"
                    }
                ]
            }
        }
    ]
}
```

### 4.2 循环处理
示例：批量处理数据

```json
{
    "nodes": [
        {
            "id": "loop",
            "type": "loop",
            "config": {
                "iterator": "data_list",
                "max_iterations": 10
            }
        }
    ]
}
```

## 第五章：调试与优化

### 5.1 调试技巧
1. 使用日志节点
2. 检查变量值
3. 单节点测试

### 5.2 常见问题解决
1. 变量未定义
   - 检查变量名称
   - 确认变量作用域

2. 节点连接错误
   - 验证输入输出
   - 检查数据类型

3. 性能优化
   - 减少不必要的节点
   - 优化循环结构

## 第六章：最佳实践

### 6.1 工作流设计原则
1. 简单性：保持工作流结构清晰
2. 模块化：相似功能封装为子流程
3. 可维护性：添加注释和文档

### 6.2 示例工作流
智能客服完整示例：

```json
{
    "name": "customer_service",
    "description": "智能客服工作流示例",
    "nodes": [
        {
            "id": "input",
            "type": "start",
            "comment": "接收用户问题",
            "config": {
                "input_params": [
                    {
                        "name": "question",
                        "type": "string"
                    }
                ]
            }
        },
        {
            "id": "intent",
            "type": "nlp",
            "comment": "识别用户意图",
            "config": {
                "model": "gpt-4"
            }
        },
        {
            "id": "knowledge",
            "type": "knowledge_base",
            "comment": "查询知识库",
            "config": {
                "threshold": 0.8
            }
        },
        {
            "id": "response",
            "type": "llm",
            "comment": "生成回复",
            "config": {
                "model": "gpt-4",
                "temperature": 0.7
            }
        }
    ],
    "variables": [
        {
            "name": "user_question",
            "type": "string"
        },
        {
            "name": "user_intent",
            "type": "object"
        },
        {
            "name": "knowledge_result",
            "type": "array"
        },
        {
            "name": "final_response",
            "type": "string"
        }
    ],
    "connections": [
        {
            "from": "input",
            "to": "intent",
            "variables": ["user_question"]
        },
        {
            "from": "intent",
            "to": "knowledge",
            "variables": ["user_intent"]
        },
        {
            "from": "knowledge",
            "to": "response",
            "variables": ["knowledge_result"]
        }
    ]
}
```

## 第七章：进阶主题

### 7.1 错误处理
1. 添加错误处理节点
2. 设置重试策略
3. 定义回退方案

### 7.2 监控与日志
1. 添加监控节点
2. 配置日志级别
3. 设置告警规则

## 附录：常用节点参考

### A. 文本处理节点
```json
{
    "type": "text_process",
    "config": {
        "operations": ["分词", "实体识别", "情感分析"]
    }
}
```

### B. 知识库节点
```json
{
    "type": "knowledge_base",
    "config": {
        "search_method": "semantic",
        "top_k": 3
    }
}
```

### C. LLM节点
```json
{
    "type": "llm",
    "config": {
        "model": "gpt-4",
        "temperature": 0.7,
        "max_tokens": 1000
    }
}
``` 