# Streamlit 页面架构

## 1. 页面组成

- 顶部：标题和项目介绍
- 左侧：Live2D角色展示
- 中间：对话记录区
- 底部：录音按钮 / 输入按钮 / 状态栏

## 2. 状态管理

建议在 session_state 中维护：
- chat_history
- current_stage
- is_recording
- is_speaking
- current_audio_path

## 3. 页面交互流程

点击录音
-> 用户说话
-> 音频上传/保存
-> 调用ASR
-> 展示识别文本
-> 调用LLM
-> 展示回复文本
-> 调用TTS
-> 播放音频