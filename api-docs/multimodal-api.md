# Multimodal API Documentation

## Introduction

Multimodal APIs are designed to handle multiple types of input data, such as text and images, to perform various tasks like generating captions for images or listing available models. These APIs enable the integration of different data modalities to enhance the capabilities of applications.

## Endpoints

### `POST /api/caption`

Generates a caption for an image.

- **Endpoint**: `/api/caption`
- **Method**: `POST`
- **Description**: Generates a caption for an image.
- **Implementation**: Refer to the implementation in `src/endpoints/caption.js`.

### `POST /api/openai/caption-image`

Generates a caption for an image using OpenAI.

- **Endpoint**: `/api/openai/caption-image`
- **Method**: `POST`
- **Description**: Generates a caption for an image using OpenAI.
- **Implementation**: Refer to the implementation in `src/endpoints/openai.js`.

### `POST /api/openrouter/models/multimodal`

Lists available multimodal models from OpenRouter.

- **Endpoint**: `/api/openrouter/models/multimodal`
- **Method**: `POST`
- **Description**: Lists available multimodal models from OpenRouter.
- **Implementation**: Refer to the implementation in `src/endpoints/openrouter.js`.

## Request and Response Examples

### `POST /api/caption`

**Request**:
```json
{
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...",
  "prompt": "Describe the image"
}
```

**Response**:
```json
{
  "caption": "A beautiful sunset over the mountains."
}
```

### `POST /api/openai/caption-image`

**Request**:
```json
{
  "image": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...",
  "prompt": "Describe the image",
  "api": "openai",
  "model": "gpt-4-turbo"
}
```

**Response**:
```json
{
  "caption": "A beautiful sunset over the mountains."
}
```

### `POST /api/openrouter/models/multimodal`

**Request**:
```json
{
  "api_key": "your_api_key"
}
```

**Response**:
```json
{
  "models": [
    "model1",
    "model2",
    "model3"
  ]
}
```

## Error Handling

### Common Error Scenarios

1. **Invalid Image Format**:
   - **Description**: The provided image format is not supported.
   - **Response**:
     ```json
     {
       "error": "Invalid image format. Supported formats are JPEG and PNG."
     }
     ```

2. **Missing API Key**:
   - **Description**: The API key is missing or invalid.
   - **Response**:
     ```json
     {
       "error": "Missing or invalid API key."
     }
     ```

3. **Internal Server Error**:
   - **Description**: An unexpected error occurred on the server.
   - **Response**:
     ```json
     {
       "error": "Internal server error. Please try again later."
     }
     ```

## Authentication

### API Key

Some endpoints require an API key for authentication. The API key should be included in the request headers as follows:

```http
Authorization: Bearer your_api_key
```

Ensure that you have a valid API key before making requests to these endpoints.
