# 鸭嘴兽 (Platypus) 插件文档

## 插件描述

鸭嘴兽插件是一个强大的自然语言处理工具，可以帮助用户进行文本分析、情感识别和语义理解。

## 参数配置

| 参数名称 | 参数描述 | 来源 |
|---------|----------|------|
| query | 用户的查询文本，插件将对此文本进行分析 | 默认参数 |
| mode | 分析模式，可选值：'basic'(基础分析)、'advanced'(高级分析)、'sentiment'(情感分析) | 默认参数 |
| language | 文本语言，默认为'auto'(自动检测)，也可指定具体语言如'zh'(中文)、'en'(英文) | 默认参数 |
| max_tokens | 返回结果的最大token数量，默认为1000 | 默认参数 |

## API端点

- https://api.coze.com/v1/plugins/platypus/analyze (来源: API模板)

## 响应格式

### 格式示例 (来源: 响应模板)

```json
{
  "result": {
    "analysis": "这是一段表达积极情感的文本，情感倾向分值为0.87（范围-1到1）。",
    "sentiment": "positive",
    "score": 0.87,
    "keywords": ["开心", "礼物", "意外"]
  },
  "status": "success"
}
```

## 使用场景

1. 文本情感分析
2. 关键信息提取
3. 主题识别
4. 语义理解
5. 内容摘要生成

## 使用示例

### 示例 1 (来源: 示例模板)

```json
{
  "query": "分析这段文本的情感倾向：我今天非常开心，因为我收到了一份意外的礼物。",
  "mode": "sentiment",
  "language": "zh"
}
```

### 示例 2 (来源: 示例模板)

```json
{
  "query": "What is the main topic of this text: AI technology has been rapidly evolving in recent years.",
  "mode": "basic",
  "language": "en"
}
```

