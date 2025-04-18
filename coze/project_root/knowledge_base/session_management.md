# 扣子平台会话管理指南

## 一、基础概念

### 1. 会话定义
- **会话（Conversation）**：用户与智能体之间的一段问答交互
- **消息（Message）**：单条的用户输入或智能体回复
- **对话（Chat）**：会话中的一次调用过程

### 2. 会话特性
- 支持多轮对话
- 自动处理上下文
- 消息保存180天
- 支持多种内容类型

## 二、会话操作

### 1. 创建会话
```json
{
    "输入参数": {
        "conversationName": "会话名称（String，必选）"
    },
    "输出参数": {
        "isSuccess": "是否成功（Boolean）",
        "isExisted": "是否已存在（Boolean）",
        "conversationId": "会话ID（String）"
    }
}
```

### 2. 清除上下文
```json
{
    "输入参数": {
        "conversationName": "会话名称（String，必选）"
    },
    "输出参数": {
        "isSuccess": "是否成功（Boolean）"
    }
}
```

### 3. 查询消息列表
```json
{
    "输入参数": {
        "conversationName": "会话名称（String，必选）",
        "limit": "返回消息数量（Integer，1-50）",
        "beforeId": "指定位置之前的消息（String）",
        "afterId": "指定位置之后的消息（String）"
    },
    "输出参数": {
        "messageList": [
            {
                "messageId": "消息ID",
                "role": "发送者角色（user/assistant）",
                "content_type": "内容类型（1:文本，2:多模态）",
                "content": "消息内容"
            }
        ],
        "first_id": "第一条消息ID",
        "last_id": "最后一条消息ID",
        "has_more": "是否有更多消息"
    }
}
```

## 三、上下文管理

### 1. 上下文特性
- 影响模型性能和生成效果
- 支持多轮对话记忆
- 可动态清除和更新
- 支持语义连贯性

### 2. 使用场景
- **保持上下文**：
  - 连续对话
  - 主题延续
  - 个性化回复

- **清除上下文**：
  - 话题切换
  - 重新开始
  - 避免干扰

### 3. 最佳实践
- 合理控制上下文长度
- 及时清理无关上下文
- 保持对话连贯性
- 优化记忆管理

## 四、注意事项

### 1. 使用限制
- 会话节点仅支持应用使用
- 试运行仅能操作测试数据
- 消息保存期限180天
- 上下文窗口大小限制

### 2. 性能优化
- 合理使用消息查询
- 及时清理无用上下文
- 优化数据存储结构
- 控制会话数量

### 3. 安全建议
- 定期备份重要会话
- 控制访问权限
- 保护敏感信息
- 监控异常行为 