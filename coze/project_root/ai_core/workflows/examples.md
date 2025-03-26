# 扣子平台工作流示例

## 一、基础工作流

### 1. 基础问答工作流
```json
{
    "name": "基础问答工作流",
    "description": "简单的问答交互工作流",
    "nodes": [
        {
            "id": "start",
            "type": "start",
            "next": "intent_recognition",
            "config": {
                "input_params": {
                    "user_input": {
                        "type": "string",
                        "required": true,
                        "description": "用户输入的问题"
                    }
                }
            }
        },
        {
            "id": "intent_recognition",
            "type": "llm",
            "config": {
                "task": "意图识别",
                "model": "gpt-3.5-turbo"
            },
            "next": "response_generation"
        },
        {
            "id": "response_generation",
            "type": "llm",
            "config": {
                "task": "回答生成",
                "model": "gpt-3.5-turbo"
            },
            "next": "end"
        },
        {
            "id": "end",
            "type": "end"
        }
    ]
}
```

### 2. 条件判断工作流
```json
{
    "name": "条件判断工作流",
    "description": "包含条件判断的基础工作流",
    "nodes": [
        {
            "id": "start",
            "type": "start",
            "next": "condition"
        },
        {
            "id": "condition",
            "type": "condition",
            "config": {
                "conditions": [
                    {
                        "field": "user_input",
                        "operator": "contains",
                        "value": "帮助",
                        "next": "help_branch"
                    },
                    {
                        "field": "user_input",
                        "operator": "contains",
                        "value": "问题",
                        "next": "question_branch"
                    }
                ],
                "default_next": "default_branch"
            }
        },
        {
            "id": "help_branch",
            "type": "llm",
            "config": {
                "task": "帮助信息生成",
                "model": "gpt-3.5-turbo"
            },
            "next": "end"
        },
        {
            "id": "question_branch",
            "type": "llm",
            "config": {
                "task": "问题解答",
                "model": "gpt-3.5-turbo"
            },
            "next": "end"
        },
        {
            "id": "default_branch",
            "type": "llm",
            "config": {
                "task": "默认回复",
                "model": "gpt-3.5-turbo"
            },
            "next": "end"
        },
        {
            "id": "end",
            "type": "end"
        }
    ]
}
```

## 二、高级工作流

### 1. 智能客服工作流
```json
{
    "name": "智能客服工作流",
    "description": "专业的客服场景工作流",
    "nodes": [
        {
            "id": "start",
            "type": "start",
            "next": "intent_recognition"
        },
        {
            "id": "intent_recognition",
            "type": "llm",
            "config": {
                "task": "意图识别",
                "model": "gpt-4",
                "system_prompt": "你是客服意图识别专家"
            },
            "next": "knowledge_search"
        },
        {
            "id": "knowledge_search",
            "type": "knowledge_base",
            "config": {
                "search_type": "semantic",
                "top_k": 3,
                "threshold": 0.7
            },
            "next": "context_management"
        },
        {
            "id": "context_management",
            "type": "context",
            "config": {
                "max_turns": 5,
                "memory_key": "chat_history"
            },
            "next": "response_generation"
        },
        {
            "id": "response_generation",
            "type": "llm",
            "config": {
                "task": "回答生成",
                "model": "gpt-4",
                "system_prompt": "你是专业的客服代表"
            },
            "next": "end"
        },
        {
            "id": "end",
            "type": "end"
        }
    ]
}
```

### 2. 图文创作工作流
```json
{
    "name": "图文创作工作流",
    "description": "自动生成图文内容的工作流",
    "nodes": [
        {
            "id": "start",
            "type": "start",
            "next": "topic_analysis"
        },
        {
            "id": "topic_analysis",
            "type": "llm",
            "config": {
                "task": "主题分析",
                "model": "gpt-4"
            },
            "next": "content_generation"
        },
        {
            "id": "content_generation",
            "type": "llm",
            "config": {
                "task": "内容生成",
                "model": "gpt-4"
            },
            "next": ["image_generation", "text_polish"]
        },
        {
            "id": "image_generation",
            "type": "image",
            "config": {
                "model": "dall-e-3",
                "size": "1024x1024"
            },
            "next": "content_combination"
        },
        {
            "id": "text_polish",
            "type": "llm",
            "config": {
                "task": "文本优化",
                "model": "gpt-4"
            },
            "next": "content_combination"
        },
        {
            "id": "content_combination",
            "type": "process",
            "config": {
                "task": "内容组合"
            },
            "next": "end"
        },
        {
            "id": "end",
            "type": "end"
        }
    ]
}
```

### 3. 深度搜索工作流
```json
{
    "name": "深度搜索工作流",
    "description": "用于深度信息搜索和验证的工作流",
    "nodes": [
        {
            "id": "start",
            "type": "start",
            "next": "query_generation"
        },
        {
            "id": "query_generation",
            "type": "llm",
            "config": {
                "task": "搜索词生成",
                "model": "gpt-4"
            },
            "next": "search"
        },
        {
            "id": "search",
            "type": "search",
            "config": {
                "engine": "bing",
                "max_results": 5,
                "time_range": "month"
            },
            "next": "result_analysis"
        },
        {
            "id": "result_analysis",
            "type": "llm",
            "config": {
                "task": "结果分析",
                "model": "gpt-4"
            },
            "next": "report_generation"
        },
        {
            "id": "report_generation",
            "type": "llm",
            "config": {
                "task": "报告生成",
                "model": "gpt-4"
            },
            "next": "end"
        },
        {
            "id": "end",
            "type": "end"
        }
    ]
}
```

## 三、最佳实践

### 1. 工作流设计原则
- 模块化：功能独立，便于维护
- 可扩展：支持功能扩展
- 错误处理：完善的异常处理机制
- 性能优化：合理的资源利用

### 2. 开发建议
- 先搭建基础框架
- 逐步添加功能
- 注重测试验证
- 持续优化改进

### 3. 常见问题
- 上下文管理
- 错误处理
- 性能优化
- 成本控制 