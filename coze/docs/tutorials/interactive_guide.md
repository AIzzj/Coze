# 扣子平台互动式教程

## 实战练习一：创建简单问答机器人

### 步骤 1：创建工作流
1. 点击"新建工作流"
2. 输入名称："my_first_bot"
3. 选择模板："空白模板"

### 步骤 2：添加开始节点
1. 从左侧工具栏拖入"开始节点"
2. 配置节点参数：
```json
{
    "input_params": [
        {
            "name": "user_question",
            "type": "string",
            "description": "用户提问"
        }
    ]
}
```

### 步骤 3：添加LLM节点
1. 拖入"LLM节点"
2. 配置参数：
```json
{
    "model": "gpt-4",
    "temperature": 0.7,
    "system_prompt": "你是一个友好的助手"
}
```

### 步骤 4：连接节点
1. 点击开始节点的输出点
2. 拖动到LLM节点的输入点
3. 配置变量映射：
   - user_question -> input_text

### 步骤 5：测试工作流
1. 点击"调试"按钮
2. 输入测试问题
3. 查看响应结果

## 实战练习二：添加知识库功能

### 步骤 1：准备知识库
1. 创建知识库文件
2. 上传文档内容
3. 配置检索参数

### 步骤 2：添加知识库节点
```json
{
    "type": "knowledge_base",
    "config": {
        "database": "my_kb",
        "search_method": "semantic",
        "top_k": 3
    }
}
```

### 步骤 3：修改节点连接
1. 开始节点 -> 知识库节点
2. 知识库节点 -> LLM节点
3. 配置变量传递：
```json
{
    "connections": [
        {
            "from": "start",
            "to": "knowledge_base",
            "variables": ["user_question"]
        },
        {
            "from": "knowledge_base",
            "to": "llm",
            "variables": ["search_results"]
        }
    ]
}
```

## 实战练习三：添加意图识别

### 步骤 1：配置意图类别
```json
{
    "intents": [
        "问题咨询",
        "闲聊对话",
        "任务执行"
    ]
}
```

### 步骤 2：添加条件分支
```json
{
    "type": "condition",
    "config": {
        "rules": [
            {
                "if": "intent == '问题咨询'",
                "then": "knowledge_path"
            },
            {
                "if": "intent == '闲聊对话'",
                "then": "chat_path"
            }
        ]
    }
}
```

### 步骤 3：测试不同场景
1. 测试问题咨询
   - 输入："产品价格是多少？"
   - 预期：走知识库路径

2. 测试闲聊对话
   - 输入："今天天气真好"
   - 预期：走对话路径

## 实战练习四：优化响应质量

### 步骤 1：添加上下文管理
```json
{
    "type": "context",
    "config": {
        "max_turns": 5,
        "memory_key": "chat_history"
    }
}
```

### 步骤 2：配置提示词模板
```json
{
    "type": "prompt",
    "config": {
        "template": "基于以下信息回答问题：\n知识库：{knowledge}\n历史对话：{history}\n问题：{question}"
    }
}
```

### 步骤 3：添加后处理
```json
{
    "type": "post_process",
    "config": {
        "operations": [
            "格式化",
            "敏感词过滤",
            "情感调整"
        ]
    }
}
```

## 实战练习五：添加监控和日志

### 步骤 1：配置日志节点
```json
{
    "type": "logger",
    "config": {
        "level": "info",
        "fields": [
            "timestamp",
            "node_id",
            "input",
            "output"
        ]
    }
}
```

### 步骤 2：添加性能监控
```json
{
    "type": "monitor",
    "config": {
        "metrics": [
            "response_time",
            "success_rate",
            "token_usage"
        ]
    }
}
```

### 步骤 3：设置告警规则
```json
{
    "type": "alert",
    "config": {
        "rules": [
            {
                "metric": "response_time",
                "threshold": 2000,
                "action": "notify"
            }
        ]
    }
}
```

## 作业练习

1. 基础作业：
   - 创建一个简单问答机器人
   - 添加至少3个不同类型的节点
   - 实现基本的对话功能

2. 进阶作业：
   - 添加知识库功能
   - 实现多轮对话
   - 添加意图识别

3. 挑战作业：
   - 实现完整的客服系统
   - 添加多模态处理
   - 优化响应质量

## 常见问题解答

1. Q: 节点之间无法连接？
   A: 检查节点的输入输出类型是否匹配

2. Q: 变量传递失败？
   A: 确认变量名称和类型是否正确定义

3. Q: 响应很慢？
   A: 检查是否有不必要的节点或操作

## 进阶提示

1. 使用模板加速开发
2. 注意添加错误处理
3. 定期备份工作流
4. 测试不同场景
5. 收集用户反馈 