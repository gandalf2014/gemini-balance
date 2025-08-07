# Gemini Balance 模型使用指南

## 🤖 支持的模型列表

### Gemini 2.5 系列 (推荐使用)

#### `gemini-2.5-pro`
- **特点**: 最先进的推理模型，具有最高响应准确性
- **适用场景**: 复杂推理、高级编程、数学问题、STEM分析
- **限制**: 5 RPM, 250K TPM, 100 RPD
- **推荐用途**: 需要最高质量输出的任务

#### `gemini-2.5-flash` ⭐ 推荐
- **特点**: 最佳性价比模型，具有完整功能
- **适用场景**: 大规模处理、低延迟任务、日常对话
- **限制**: 10 RPM, 250K TPM, 250 RPD
- **推荐用途**: 大多数应用场景的首选

#### `gemini-2.5-flash-lite`
- **特点**: 成本优化模型，高吞吐量
- **适用场景**: 实时应用、成本敏感场景、高频任务
- **限制**: 15 RPM, 250K TPM, 400 RPD
- **推荐用途**: 需要高并发的应用

### Gemini 2.0 系列 (最新功能)

#### `gemini-2.0-flash`
- **特点**: 最新功能和速度，原生工具使用
- **适用场景**: 体验最新功能、工具调用
- **限制**: 8 RPM, 250K TPM, 200 RPD
- **推荐用途**: 需要最新功能的应用

#### `gemini-2.0-flash-lite`
- **特点**: 2.0轻量版，成本效率优化
- **适用场景**: 成本敏感的2.0功能使用
- **限制**: 12 RPM, 250K TPM, 300 RPD
- **推荐用途**: 预算有限但需要2.0功能

### Gemini 1.5 系列 (兼容性保留)

#### `gemini-1.5-flash`
- **特点**: 快速多模态模型
- **适用场景**: 图像、视频、音频处理
- **限制**: 10 RPM, 250K TPM, 250 RPD
- **状态**: 2025年9月停用

#### `gemini-1.5-flash-8b`
- **特点**: 小型模型，适合高频任务
- **适用场景**: 简单任务、高并发场景
- **限制**: 20 RPM, 250K TPM, 500 RPD (最高限制)
- **状态**: 2025年9月停用

#### `gemini-1.5-pro`
- **特点**: 中型多模态模型，复杂推理
- **适用场景**: 复杂分析、长文档处理
- **限制**: 3 RPM, 250K TPM, 50 RPD (最严格限制)
- **状态**: 2025年9月停用

## 📊 模型选择建议

### 按使用场景选择

| 场景 | 推荐模型 | 原因 |
|------|----------|------|
| 日常对话 | `gemini-2.5-flash` | 性价比最佳 |
| 复杂推理 | `gemini-2.5-pro` | 最高准确性 |
| 高并发应用 | `gemini-2.5-flash-lite` | 最高限制 |
| 成本敏感 | `gemini-2.5-flash-lite` | 成本优化 |
| 最新功能 | `gemini-2.0-flash` | 最新特性 |
| 简单任务 | `gemini-1.5-flash-8b` | 高频处理 |

### 按性能需求选择

| 需求 | 推荐模型 | 备注 |
|------|----------|------|
| 最高质量 | `gemini-2.5-pro` | 准确性优先 |
| 最佳平衡 | `gemini-2.5-flash` | 质量与速度平衡 |
| 最高速度 | `gemini-2.5-flash-lite` | 速度优先 |
| 最低成本 | `gemini-1.5-flash-8b` | 成本优先 |

## 🔧 使用示例

### Python 示例
```python
import openai

client = openai.OpenAI(
    api_key="your-user-key",
    base_url="https://your-worker.workers.dev/v1"
)

# 使用推荐的性价比模型
response = client.chat.completions.create(
    model="gemini-2.5-flash",
    messages=[
        {"role": "user", "content": "Hello, how are you?"}
    ]
)

# 使用最高质量模型
response = client.chat.completions.create(
    model="gemini-2.5-pro",
    messages=[
        {"role": "user", "content": "Solve this complex math problem..."}
    ]
)
```

### JavaScript 示例
```javascript
const response = await fetch('https://your-worker.workers.dev/v1/chat/completions', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer your-user-key',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    model: 'gemini-2.5-flash',
    messages: [
      { role: 'user', content: 'Hello!' }
    ]
  })
});
```

## ⚠️ 重要说明

1. **模型停用**: Gemini 1.5 系列将在2025年9月停用，建议迁移到2.5系列
2. **限制说明**: RPM=每分钟请求数, TPM=每分钟Token数, RPD=每日请求数
3. **推荐使用**: `gemini-2.5-flash` 是大多数场景的最佳选择
4. **成本优化**: 对于高频应用，使用 `gemini-2.5-flash-lite`
5. **质量优先**: 对于复杂任务，使用 `gemini-2.5-pro`

## 🔄 迁移建议

### 从 1.5 系列迁移
- `gemini-1.5-flash` → `gemini-2.5-flash`
- `gemini-1.5-pro` → `gemini-2.5-pro`
- `gemini-1.5-flash-8b` → `gemini-2.5-flash-lite`

### 性能提升
- 2.5 系列具有更好的推理能力
- 2.0 系列提供最新功能
- 所有新模型都支持更多语言和更好的多模态处理
