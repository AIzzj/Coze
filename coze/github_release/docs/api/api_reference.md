# Coze平台API参考

## API概述

Coze平台提供了一组RESTful API，允许开发者以编程方式创建、管理和执行工作流。本文档提供了API端点的详细说明和示例。

## 认证

所有API请求都需要使用API密钥进行认证。在HTTP请求头中添加以下内容：

```
Authorization: Bearer YOUR_API_KEY
```

## 基础端点

### 工作流管理

#### 创建工作流

```
POST /api/v1/workflows
```

请求体示例：

```json
{
  "name": "my_workflow",
  "description": "示例工作流",
  "nodes": [
    {
      "id": "start_node",
      "type": "start",
      "config": {
        "input_params": [
          {
            "name": "user_input",
            "type": "string"
          }
        ]
      }
    },
    {
      "id": "response_node",
      "type": "response",
      "config": {
        "model": "gpt-4",
        "system_prompt": "简洁回答用户问题"
      }
    }
  ],
  "connections": [
    {
      "from": "start_node",
      "to": "response_node"
    }
  ]
}
```

响应示例：

```json
{
  "workflow_id": "wf_123456",
  "status": "created",
  "created_at": "2023-01-01T12:00:00Z"
}
```

#### 获取工作流

```
GET /api/v1/workflows/{workflow_id}
```

响应示例：

```json
{
  "workflow_id": "wf_123456",
  "name": "my_workflow",
  "description": "示例工作流",
  "status": "active",
  "created_at": "2023-01-01T12:00:00Z",
  "updated_at": "2023-01-01T12:00:00Z",
  "nodes": [...],
  "connections": [...]
}
```

#### 执行工作流

```
POST /api/v1/workflows/{workflow_id}/execute
```

请求体示例：

```json
{
  "inputs": {
    "user_input": "如何使用Coze平台?"
  },
  "session_id": "optional_session_id"
}
```

响应示例：

```json
{
  "execution_id": "exec_123456",
  "status": "completed",
  "result": {
    "content": "Coze平台是一个AI工作流编排工具，您可以..."
  },
  "start_time": "2023-01-01T12:01:00Z",
  "end_time": "2023-01-01T12:01:02Z"
}
```

## 错误处理

所有API错误都会返回适当的HTTP状态码和错误详情：

```json
{
  "error": {
    "code": "invalid_workflow",
    "message": "工作流结构无效",
    "details": "节点 'node_id' 缺少必要的配置"
  }
}
```

## 速率限制

API请求受到速率限制，免费账户每分钟最多10个请求，付费账户有更高的限制。您可以通过响应头查看剩余配额：

```
X-Rate-Limit-Remaining: 8
X-Rate-Limit-Reset: 1640995200
```

## 示例代码

### Python

```python
import requests

api_key = "your_api_key"
headers = {
    "Authorization": f"Bearer {api_key}",
    "Content-Type": "application/json"
}

# 执行工作流
workflow_id = "wf_123456"
url = f"https://api.coze.cn/api/v1/workflows/{workflow_id}/execute"
data = {
    "inputs": {
        "user_input": "如何使用Coze平台?"
    }
}

response = requests.post(url, json=data, headers=headers)
result = response.json()
print(result)
```

### JavaScript

```javascript
const axios = require('axios');

const apiKey = 'your_api_key';
const workflowId = 'wf_123456';

async function executeWorkflow() {
  try {
    const response = await axios.post(
      `https://api.coze.cn/api/v1/workflows/${workflowId}/execute`,
      {
        inputs: {
          user_input: '如何使用Coze平台?'
        }
      },
      {
        headers: {
          'Authorization': `Bearer ${apiKey}`,
          'Content-Type': 'application/json'
        }
      }
    );
    
    console.log(response.data);
  } catch (error) {
    console.error('Error:', error.response?.data || error.message);
  }
}

executeWorkflow();
``` 