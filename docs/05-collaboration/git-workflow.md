# Git协作规范

## 分支策略
- `main`：稳定版本
- `dev`：开发集成分支
- `feature/xxx`：个人功能分支

## 命名示例
- feature/llm-prompt
- feature/asr-test
- feature/tts-test
- feature/streamlit-ui
- feature/live2d-basic

## 提交流程
1. 从 dev 拉新分支
2. 在功能分支开发
3. 提交 PR 到 dev
4. 代码评审通过后合并

## Commit 规范
- feat: 新功能
- fix: 修复问题
- docs: 文档更新
- refactor: 重构
- test: 测试代码