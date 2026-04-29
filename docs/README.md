# AI Interview 文档总览

本项目是一个本地运行的 AI 面试系统，技术栈如下：

- LLM: Qwen3.5-4B
- ASR: FunASR-nano-2512
- TTS: Fun-CosyVoice3-0.5B-2512
- Frontend: Streamlit
- Avatar: Live2D

## 团队分工

### 1. LLM组（2人）
负责内容生成、提示词设计、面试流程控制、评分逻辑。

### 2. 语音交互组（2人）
负责语音输入输出，包括 ASR、TTS、音频流处理、断句与播报控制。

### 3. 页面集成组（2人）
负责 Streamlit 页面、Live2D 集成、前后端模块联调与演示效果。

## 文档结构

- `01-architecture/`：系统设计和模块契约
- `02-llm-module/`：LLM组文档
- `03-voice-interaction/`：语音交互组文档
- `04-frontend-integration/`：页面集成组文档
- `05-collaboration/`：开发协作和里程碑管理

## 开发原则

1. 所有模块先定义接口，再开发实现
2. 各组优先完成独立可测试版本
3. 联调统一基于 interface contracts
4. 每次合并代码前同步更新模块 README 和测试状态