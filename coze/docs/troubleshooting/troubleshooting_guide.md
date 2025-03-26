# 扣子平台故障排除指南

## 一、常见错误类型

### 1. 节点配置错误
#### 症状
- 节点显示红色警告
- 无法保存配置
- 运行时报错

#### 解决方案
1. 检查必填参数
   - 查看错误提示
   - 补充缺失参数
   - 确认参数类型

2. 验证参数格式
   - 检查JSON格式
   - 确认数值范围
   - 验证字符串格式

3. 常见示例
```json
// 错误示例
{
    "temperature": "0.7",  // 应该是数字类型
    "max_tokens": -1      // 不能是负数
}

// 正确示例
{
    "temperature": 0.7,
    "max_tokens": 1000
}
```

### 2. 变量传递问题
#### 症状
- 节点无法获取上游数据
- 变量undefined错误
- 类型不匹配错误

#### 解决方案
1. 检查变量定义
```json
// 正确的变量定义
{
    "variables": [
        {
            "name": "user_input",
            "type": "string",
            "required": true
        }
    ]
}
```

2. 验证变量映射
```json
// 正确的变量映射
{
    "connections": [
        {
            "from": "node1",
            "to": "node2",
            "mapping": {
                "output_var": "input_var"
            }
        }
    ]
}
```

3. 类型转换处理
```json
{
    "type": "transform",
    "config": {
        "conversions": [
            {
                "from": "string",
                "to": "number",
                "method": "parse_float"
            }
        ]
    }
}
```

### 3. 性能问题
#### 症状
- 响应时间过长
- 内存占用过高
- CPU使用率高

#### 解决方案
1. 优化节点配置
```json
{
    "cache_config": {
        "enabled": true,
        "ttl": 3600
    },
    "batch_size": 10,
    "timeout": 5000
}
```

2. 添加性能监控
```json
{
    "monitor_config": {
        "metrics": ["latency", "memory", "cpu"],
        "threshold": {
            "latency_ms": 1000,
            "memory_mb": 500
        }
    }
}
```

## 二、调试技巧

### 1. 使用日志节点
```json
{
    "type": "logger",
    "config": {
        "level": "debug",
        "format": "detailed",
        "output": ["console", "file"]
    }
}
```

### 2. 断点调试
1. 设置断点节点
2. 查看中间结果
3. 单步执行

### 3. 测试数据
```json
{
    "test_cases": [
        {
            "input": {"query": "测试问题"},
            "expected": {"type": "string", "length": ">0"}
        }
    ]
}
```

## 三、常见场景问题

### 1. 知识库检索失败
#### 问题描述
- 无法找到相关内容
- 相似度得分过低
- 检索结果不准确

#### 解决方法
1. 检查知识库配置
```json
{
    "knowledge_base": {
        "index_method": "semantic",
        "threshold": 0.7,
        "top_k": 3
    }
}
```

2. 优化检索参数
3. 更新知识库内容

### 2. LLM响应问题
#### 问题描述
- 响应不相关
- 格式不正确
- token超限

#### 解决方法
1. 优化提示词
```json
{
    "prompt_template": {
        "system": "你是专业的助手",
        "format": "markdown",
        "constraints": ["简洁", "准确"]
    }
}
```

2. 调整模型参数
3. 处理长文本

### 3. 多轮对话问题
#### 问题描述
- 上下文丢失
- 回复不连贯
- 记忆混乱

#### 解决方法
1. 配置上下文管理
```json
{
    "context_manager": {
        "max_turns": 5,
        "strategy": "sliding_window",
        "memory_key": "chat_history"
    }
}
```

2. 优化记忆机制
3. 清理无用上下文

## 四、系统维护

### 1. 日常检查
- 监控关键指标
- 检查错误日志
- 验证功能正常

### 2. 定期维护
- 更新知识库
- 优化配置
- 清理缓存

### 3. 应急处理
1. 问题定位
2. 临时方案
3. 根本解决

## 五、最佳实践

### 1. 开发建议
- 使用版本控制
- 做好备份
- 编写测试用例

### 2. 运维建议
- 设置监控告警
- 制定备份策略
- 记录问题处理

### 3. 优化建议
- 定期评估性能
- 收集用户反馈
- 持续改进

## 附录：常用调试命令

### 1. 查看日志
```bash
tail -f logs/app.log | grep ERROR
```

### 2. 性能分析
```bash
top -p $(pgrep -f app_name)
```

### 3. 配置检查
```bash
json_verify < config.json
``` 