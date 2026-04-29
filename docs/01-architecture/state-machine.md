# 面试流程状态机

## 1. 面试阶段定义

- `opening`：开场欢迎
- `self_intro`：自我介绍
- `technical`：技术问答
- `project`：项目追问
- `behavioral`：行为问题
- `candidate_questions`：候选人反问
- `summary`：总结反馈
- `finished`：结束

---

## 2. 状态迁移逻辑

### opening
系统介绍流程，并进入 self_intro

### self_intro
候选人完成自我介绍后，根据内容转入 technical 或 project

### technical
根据岗位问题库提问技术问题，若候选人提到项目细节可进入 project

### project
深入追问项目背景、技术选型、问题处理和结果

### behavioral
询问沟通协作、冲突处理、压力应对等问题

### candidate_questions
允许候选人提问

### summary
生成总结和评分

### finished
停止进一步问答

---

## 3. 状态切换触发条件

- 回答包含项目经历 -> 进入 project
- 技术问题轮数超过阈值 -> 进入 behavioral
- 总问题数达到阈值 -> 进入 summary
- 用户明确表示结束 -> 进入 summary