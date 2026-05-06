# ai-interview
智能 AI 面试系统

本项目是一个基于本地大模型与语音技术运行的 AI 面试系统。用户可通过语音与 AI 面试官互动，AI 面试官能够根据候选人情况进行提问、追问、总结与评分，并通过 TTS（文本转语音）输出声音。前端页面提供可视化界面与 Live2D 虚拟形象展示。

## 🛠 技术栈

- **LLM（大语言模型）**: Qwen3.5-4B
- **ASR（语音识别）**: FunASR-nano-2512
- **TTS（语音合成）**: Fun-CosyVoice3-0.5B-2512
- **Frontend（前端展示）**: Streamlit
- **Avatar（虚拟数字人）**: Live2D

## 📁 项目结构

```text
ai-interview/
├── assets/         # 静态资源（图片、样式、Live2D模型等）
├── config/         # 全局配置文件 (如 config.yaml)
├── data/           # 数据存储
│   └── sessions/   # 每次面试的会话数据与报告 (meta.json, conversation.jsonl, report.json)
├── docs/           # 项目文档总览与架构设计
│   ├── 01-architecture/         # 系统设计和模块契约
│   ├── 02-llm-module/           # LLM组文档
│   ├── 03-voice-interaction/    # 语音交互组文档
│   ├── 04-frontend-integration/ # 页面集成组文档
│   └── 05-collaboration/        # 开发协作和里程碑管理
├── logs/           # 系统运行日志输出目录
├── models/         # 本地模型文件存储目录（Qwen、FunASR、CosyVoice等）
├── src/            # 核心源代码
│   ├── app.py      # Streamlit 前端页面与系统入口文件
│   ├── asr/        # 语音识别模块 (FunASR)
│   ├── interview/  # 面试业务逻辑控制
│   ├── live2d/     # 虚拟人集成与渲染
│   ├── llm/        # 大模型交互与提示词工程 (Qwen)
│   ├── schemas/    # 统一定义各模块交互的数据结构 (如 Pydantic Models)
│   ├── tts/        # 语音合成模块 (CosyVoice)
│   └── utils/      # 公用工具模块 (日志、音频处理、文件读写等)
├── test/           # 单元测试与集成测试脚本
├── .env.example    # 环境变量配置模板
├── requirements.txt# 项目 Python 依赖列表
└── README.md       # 项目说明文档
```

## 🧩 核心模块

系统分为三大核心模块：

### 1. LLM 模块 (`src/llm` & `src/interview`)
- 负责面试官的人设控制、问题生成、多轮追问、面试总结以及对候选人表现的综合评分。

### 2. 语音交互模块 (`src/asr` & `src/tts`)
- 负责实时麦克风输入与输出流处理。
- 使用 FunASR 进行语音到文本的精准转换。
- 使用 Fun-CosyVoice3 将 AI 面试官的文本回复转换为语音。

### 3. 页面集成模块 (`src/app.py` & `src/live2d`)
- 采用 Streamlit 搭建交互式 Web 页面，展示对话历史与录音状态。
- 集成 Live2D，实现虚拟角色的动作与音频口型同步联动。

## 🔄 核心数据流

1. **用户说话** -> 前端采集音频
2. **ASR转文字** -> 解析候选人回答
3. **LLM生成回复** -> 判断当前面试阶段并生成面试官话术
4. **TTS转语音** -> 将回复文本合成语音
5. **前端播放音频** -> Live2D同步动作/口型展示

## 👥 团队分工

- **LLM组（2人）**：负责内容生成、提示词设计、面试流程控制、评分逻辑。
- **语音交互组（2人）**：负责语音输入输出，包括 ASR、TTS、音频流处理、断句与播报控制。
- **页面集成组（2人）**：负责 Streamlit 页面、Live2D 集成、前后端模块联调与演示效果。

## 🚀 快速开始

*(运行步骤待完善)*

1. 克隆项目到本地
2. 复制 `.env.example` 并重命名为 `.env`，根据需要配置环境变量
3. 安装环境依赖：`pip install -r requirements.txt`
4. 下载相关模型并放置于 `models/` 目录下
5. 启动系统：`streamlit run src/app.py`
