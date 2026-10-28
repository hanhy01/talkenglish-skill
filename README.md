# talkenglish-skill

专四（TEM-4）口语思辨陪练 Skill。AI 一轮一轮给出英文思辨话题和正反参考句型，用户参考后口头作答；AI 再做原样转写、一版地道化改写（改动处加粗）和中文简短点评，重点纠正中式英语（Chinglish）。

## 项目解决什么问题

专四口语即席问答最常见的备考痛点：

- 自己练题时没有反馈，不知道自己说的英文哪里不地道；
- 中式英语（中文语序直译、中式搭配、逻辑断层）自己听不出来；
- 口语 App 多是跟读模板或背素材，不针对"思辨问答"做即席输出训练；
- 练完一轮不知道接下来该怎么递进追问。

本 Skill 把这个流程收敛成一个轻量文字陪练：出题 → 给正反句型支架 → 你口头作答 → 原样转写 + 一版地道改写 + 中文点评，并支持就同一话题层层追问或重答。

## 主要功能

- **出题**：一轮一个 TEM-4 难度的英文思辨话题，覆盖教育、科技与媒体、环境、社会现象、个人成长、文化、人际关系等领域。
- **句型支架**：每轮配 Pro / Con 两句纯英文参考句型，完整可套用，不附中文翻译。
- **原样转写**：【我的原句】保留用户口述中的所有错误、卡顿和自我纠正，不做"善意补全"。
- **地道改写**：【优化句】只给一版，优先修中式语序、中式搭配、逻辑断层、母语负迁移，拒绝浅层同义词替换；核心改动用 `**加粗**` 标出，保持口语长度。
- **中文点评**：【简短点评】1–3 句，点出本次最典型的 Chinglish 问题，并评价逻辑清晰度和用词句式地道度。
- **分支推进**：【继续】就当前话题深度追问（反方视角、观点局限、举例）再练一轮；【重新回答】不换话题，重摆提示后等待重答。
- **纯提示词**：不含脚本、无第三方依赖、不联网抓网页、不处理 PDF、不提供图形界面、不生成音频。

## 安装方法

无需构建、无需安装依赖。

1. 把整个 `talkenglish-skill/` 目录复制到你的 Agent 平台约定的技能目录（例如 Doubao 的 `.user_skills/` 目录，或其他平台的 skills 根目录）。
2. 目录内需保留两个文件：`SKILL.md` 和 `agents/openai.yaml`，其余不需要。
3. 刷新或重启 Agent 会话后，即可通过触发词调用。
4. 若使用 OpenAI Agents SDK 类运行时，`agents/openai.yaml` 已提供 `model`、`temperature`、`max_tokens` 和 `system_prompt` 配置，可直接加载或按需调整模型名。

## 使用方法

加载 Skill 后，直接对 AI 说一句即可开始，例如：

- "练口语"
- "专四口语思辨陪练"
- "daily oral practice"

训练按轮次自动进行：

1. AI 先给出一个英文 Topic 和两句纯英文参考句型（Pro / Con 各一句），然后停下等你作答。
2. 你用英文口头作答（直接打字转述你会说的话即可）。
3. AI 依次输出三段：【我的原句】原样转写 →【优化句】一版改写、改动处加粗 →【简短点评】中文点评。
4. 反馈结束后选下一步：【继续】同话题深度追问再练一轮；【重新回答】不换话题重答一次，直到满意。

## 输入输出示例

**AI（新话题一轮）：**

```
Topic: Should college students be required to attend every class?

Pro: Regular contact with teachers and peers deepens understanding that
     self-study alone cannot provide.
Con: Mandatory attendance may discourage independent learners, who often
     benefit more from flexible schedules than from sitting through lectures.
```

**用户作答：**

```
I think college students should not require to attend all class. Because going
to class means waking up early, it make you very tired. And some teacher's class
is boring, we can learn knowledge by ourselves, so why must we sit there?
```

**AI 反馈：**

```
【我的原句】
I think college students should not require to attend all class. Because going
to class means waking up early, it make you very tired. And some teacher's class
is boring, we can learn knowledge by ourselves, so why must we sit there?

【优化句】
I think college students **should not be required to attend every class**,
because waking up early for lectures **often leaves them exhausted**. Besides,
some teachers' classes are boring, and we can **study the material on our own**,
so why must we sit there?

【简短点评】
典型中式问题：被动语态漏用（should not require 应为 be required）；learn
knowledge 是中式搭配，英文说 study the material。逻辑上"早起疲惫→不该强制"
跳跃了一步，把疲惫和听课效率挂钩会更有说服力；整体口语自然度尚可。

请选择下一步：
【继续】— 就当前话题深度追问，再练一轮
【重新回答】— 不换话题，你重新答一次
```
