# 模块接口契约

本文件定义 LLM、语音交互、页面集成三组之间的接口格式。

---

## 1. ASR 输出给 LLM 的格式

```json
{
  "text": "我之前做过一个推荐系统项目",
  "is_final": true,
  "timestamp_ms": 1723456789
}
```
字段说明：

text: ASR识别后的文本
is_final: 是否是最终结果
timestamp_ms: 时间戳

## 2. LLM 输入格式
```json

{
  "role": "candidate",
  "text": "我之前做过一个推荐系统项目",
  "stage": "technical",
  "history": [
    {"role": "interviewer", "text": "请做一个自我介绍"},
    {"role": "candidate", "text": "我是一名后端开发工程师"}
  ]
}
```
## 3. LLM 输出格式
```json

{
  "reply_text": "你刚才提到推荐系统项目，请详细介绍一下你负责的部分。",
  "stage": "technical",
  "follow_up": true,
  "end_interview": false,
  "score": null
}
```
字段说明：

reply_text: 面试官回复
stage: 当前阶段
follow_up: 是否继续追问
end_interview: 是否结束面试
score: 若结束时可输出评分对象，否则为 null
## 4. TTS 输入格式
```json

{
  "text": "你刚才提到推荐系统项目，请详细介绍一下你负责的部分。",
  "speaker": "default_female",
  "speed": 1.0
}
```
## 5. TTS 输出格式
```json

{
  "audio_path": "./temp/tts_001.wav",
  "sample_rate": 24000,
  "duration_sec": 3.2
}
```
## 6. 前端状态对象格式
```json

{
  "session_id": "user_001",
  "interview_stage": "technical",
  "is_recording": false,
  "is_speaking": true,
  "current_text": "你刚才提到推荐系统项目，请详细介绍一下你负责的部分。"
}
```
## 7. 错误码约定


ASR_LOAD_ERROR
ASR_INFERENCE_ERROR
LLM_LOAD_ERROR
LLM_GENERATE_ERROR
TTS_LOAD_ERROR
TTS_INFERENCE_ERROR
FRONTEND_RENDER_ERROR
错误统一返回格式：

```json

{
  "code": "TTS_INFERENCE_ERROR",
  "message": "语音合成失败",
  "detail": "speaker not found"
}
```    