# Live2D 集成说明

## 1. 目标
将面试官以虚拟角色形式展示，并在说话时触发口型和简单动作。

## 2. 最低可行实现
- 页面中嵌入 Live2D canvas
- 默认 idle 动作循环
- 播放音频时触发 speaking 状态

## 3. 口型同步方案
初期建议采用简单方案：
- 音频播放中 -> mouth_open = true
- 音频结束 -> mouth_open = false

后续可升级：
- 根据音频能量驱动嘴型开合程度

## 4. 风险点
- Streamlit 原生不擅长复杂前端动画
- 需要通过 iframe / custom component 集成