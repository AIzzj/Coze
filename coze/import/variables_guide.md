# 扣子平台变量使用指南

## 一、变量类型

### 1. 系统变量
```json
{
    "系统变量": {
        "环境变量": {
            "NODE_ENV": "运行环境",
            "API_VERSION": "API版本",
            "DEBUG_MODE": "调试模式"
        },
        "上下文变量": {
            "CONTEXT_ID": "会话上下文ID",
            "USER_ID": "用户标识",
            "SESSION_ID": "会话标识"
        },
        "配置变量": {
            "CONFIG_PATH": "配置文件路径",
            "LOG_LEVEL": "日志级别",
            "TIMEOUT": "超时设置"
        }
    }
}
```

### 2. 自定义变量
```json
{
    "变量定义": {
        "命名规范": {
            "规则": "使用小写字母和下划线",
            "前缀": "根据用途添加适当前缀",
            "示例": ["user_input", "process_result", "output_data"]
        },
        "作用域": {
            "全局作用域": "整个工作流可用",
            "节点作用域": "仅在特定节点中可用",
            "临时作用域": "临时存储中间结果"
        }
    }
}
```

## 二、变量使用

### 1. 变量声明
```json
{
    "声明方式": {
        "直接声明": "在节点配置中直接定义",
        "动态声明": "通过代码动态创建",
        "批量声明": "通过配置文件批量定义"
    },
    "数据类型": {
        "基本类型": ["字符串", "数字", "布尔值"],
        "复杂类型": ["数组", "对象", "函数"]
    }
}
```

### 2. 变量传递
```json
{
    "传递方式": {
        "节点间传递": {
            "直接传递": "通过连线传递",
            "全局共享": "通过全局变量共享",
            "事件传递": "通过事件机制传递"
        },
        "作用域传递": {
            "向下传递": "父节点到子节点",
            "向上传递": "子节点到父节点",
            "平级传递": "同级节点之间"
        }
    }
}
```

## 三、最佳实践

### 1. 命名规范
- **变量命名**
  - 使用有意义的名称
  - 遵循一致的命名风格
  - 添加适当的注释
  - 避免使用保留字

### 2. 作用域管理
- **全局变量**
  - 谨慎使用全局变量
  - 明确变量生命周期
  - 及时清理无用变量
  - 避免命名冲突

### 3. 性能优化
```json
{
    "优化建议": {
        "内存管理": {
            "及时释放": "不再使用的变量及时释放",
            "避免泄露": "防止内存泄露",
            "合理使用": "避免过度使用全局变量"
        },
        "访问优化": {
            "缓存优化": "合理使用变量缓存",
            "作用域优化": "优化变量作用域",
            "读写优化": "减少不必要的读写操作"
        }
    }
}
```

## 四、错误处理

### 1. 常见错误
```json
{
    "错误类型": {
        "未定义错误": {
            "原因": "变量未声明就使用",
            "解决方案": "使用前先声明或检查"
        },
        "类型错误": {
            "原因": "变量类型不匹配",
            "解决方案": "进行类型检查或转换"
        },
        "作用域错误": {
            "原因": "访问超出作用域的变量",
            "解决方案": "正确管理变量作用域"
        }
    }
}
```

### 2. 调试技巧
- **变量监控**
  - 使用日志记录
  - 设置断点调试
  - 变量状态追踪
  - 错误信息收集 