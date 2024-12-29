# 多模态API文档

## 介绍

多模态API旨在处理多种类型的输入数据，如文本和图像，以执行各种任务，如生成图像的标题或列出可用的模型。这些API使应用程序能够集成不同的数据模态，以增强其功能。

## 端点

### `POST /api/caption`

生成图像的标题。

- **端点**: `/api/caption`
- **方法**: `POST`
- **描述**: 生成图像的标题。
- **实现**: 参考`src/endpoints/caption.js`中的实现。

### `POST /api/openai/caption-image`

使用OpenAI生成图像的标题。

- **端点**: `/api/openai/caption-image`
- **方法**: `POST`
- **描述**: 使用OpenAI生成图像的标题。
- **实现**: 参考`src/endpoints/openai.js`中的实现。

### `POST /api/openrouter/models/multimodal`

列出OpenRouter中可用的多模态模型。

- **端点**: `/api/openrouter/models/multimodal`
- **方法**: `POST`
- **描述**: 列出OpenRouter中可用的多模态模型。
- **实现**: 参考`src/endpoints/openrouter.js`中的实现。

## 请求和响应示例

### `POST /api/caption`

**请求**:
```json
{
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...",
  "prompt": "描述图像"
}
```

**响应**:
```json
{
  "caption": "山脉上美丽的日落。"
}
```

### `POST /api/openai/caption-image`

**请求**:
```json
{
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...",
  "prompt": "描述图像",
  "api": "openai",
  "model": "gpt-4-turbo"
}
```

**响应**:
```json
{
  "caption": "山脉上美丽的日落。"
}
```

### `POST /api/openrouter/models/multimodal`

**请求**:
```json
{
  "api_key": "your_api_key"
}
```

**响应**:
```json
{
  "models": [
    "model1",
    "model2",
    "model3"
  ]
}
```

## 错误处理

### 常见错误场景

1. **无效的图像格式**:
   - **描述**: 提供的图像格式不受支持。
   - **响应**:
     ```json
     {
       "error": "无效的图像格式。支持的格式为JPEG和PNG。"
     }
     ```

2. **缺少API密钥**:
   - **描述**: API密钥缺失或无效。
   - **响应**:
     ```json
     {
       "error": "缺少或无效的API密钥。"
     }
     ```

3. **内部服务器错误**:
   - **描述**: 服务器发生意外错误。
   - **响应**:
     ```json
     {
       "error": "内部服务器错误。请稍后再试。"
     }
     ```

## 认证

### API密钥

某些端点需要API密钥进行认证。API密钥应包含在请求头中，如下所示：

```http
Authorization: Bearer your_api_key
```

在发出这些端点的请求之前，请确保您拥有有效的API密钥。
