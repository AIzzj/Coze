# 扣子平台节点配置指南

## 一、LLM节点

### 1. 基础配置
```json
{
    "llm_config": {
        "model": {
            "type": "string",
            "enum": ["gpt-3.5-turbo", "gpt-4"],
            "description": "选择使用的语言模型"
        },
        "temperature": {
            "type": "number",
            "minimum": 0,
            "maximum": 2,
            "default": 0.7,
            "description": "控制输出的随机性"
        },
        "max_tokens": {
            "type": "integer",
            "minimum": 1,
            "maximum": 4096,
            "default": 1024,
            "description": "输出的最大token数"
        }
    }
}
```

### 2. 高级配置
```json
{
    "llm_advanced_config": {
        "system_prompt": {
            "type": "string",
            "description": "系统提示词"
        },
        "stop_sequences": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "description": "停止序列"
        },
        "presence_penalty": {
            "type": "number",
            "minimum": -2,
            "maximum": 2,
            "default": 0,
            "description": "重复惩罚因子"
        }
    }
}
```

## 二、知识库节点

### 1. 基础配置
```json
{
    "knowledge_base_config": {
        "search_type": {
            "type": "string",
            "enum": ["semantic", "keyword"],
            "default": "semantic",
            "description": "搜索类型"
        },
        "top_k": {
            "type": "integer",
            "minimum": 1,
            "maximum": 10,
            "default": 3,
            "description": "返回结果数量"
        },
        "threshold": {
            "type": "number",
            "minimum": 0,
            "maximum": 1,
            "default": 0.7,
            "description": "相似度阈值"
        }
    }
}
```

### 2. 高级配置
```json
{
    "knowledge_base_advanced_config": {
        "index_type": {
            "type": "string",
            "enum": ["faiss", "milvus"],
            "default": "faiss",
            "description": "索引类型"
        },
        "chunk_size": {
            "type": "integer",
            "minimum": 100,
            "maximum": 1000,
            "default": 500,
            "description": "文本分块大小"
        },
        "overlap": {
            "type": "integer",
            "minimum": 0,
            "maximum": 100,
            "default": 50,
            "description": "分块重叠大小"
        }
    }
}
```

## 三、图像节点

### 1. 基础配置
```json
{
    "image_config": {
        "model": {
            "type": "string",
            "enum": ["dall-e-2", "dall-e-3"],
            "default": "dall-e-3",
            "description": "图像模型"
        },
        "size": {
            "type": "string",
            "enum": ["256x256", "512x512", "1024x1024"],
            "default": "1024x1024",
            "description": "图像尺寸"
        },
        "quality": {
            "type": "string",
            "enum": ["standard", "hd"],
            "default": "standard",
            "description": "图像质量"
        }
    }
}
```

### 2. 高级配置
```json
{
    "image_advanced_config": {
        "style": {
            "type": "string",
            "enum": ["natural", "vivid"],
            "default": "natural",
            "description": "图像风格"
        },
        "num_images": {
            "type": "integer",
            "minimum": 1,
            "maximum": 4,
            "default": 1,
            "description": "生成图像数量"
        }
    }
}
```

## 四、数据处理节点

### 1. 基础配置
```json
{
    "data_config": {
        "source": {
            "type": "string",
            "enum": ["database", "api", "file"],
            "description": "数据来源"
        },
        "format": {
            "type": "string",
            "enum": ["json", "csv", "xml"],
            "default": "json",
            "description": "数据格式"
        },
        "batch_size": {
            "type": "integer",
            "minimum": 1,
            "maximum": 1000,
            "default": 100,
            "description": "批处理大小"
        }
    }
}
```

### 2. 高级配置
```json
{
    "data_advanced_config": {
        "preprocessing": {
            "type": "array",
            "items": {
                "type": "string",
                "enum": ["清洗", "转换", "标准化"]
            },
            "description": "预处理步骤"
        },
        "validation": {
            "type": "object",
            "properties": {
                "schema": "数据模式",
                "rules": "验证规则"
            },
            "description": "数据验证"
        }
    }
}
```

## 五、配置最佳实践

### 1. 性能优化
- 合理设置批处理大小
- 优化索引配置
- 缓存常用数据

### 2. 成本控制
- 选择合适的模型
- 控制token使用量
- 优化API调用

### 3. 质量保证
- 完善的错误处理
- 数据验证和清洗
- 结果评估机制

### 4. 安全考虑
- 访问权限控制
- 数据加密存储
- 日志记录和审计 