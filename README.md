# video-rephotography

**原片锁定多机位重摄影**：为已有视频设计新机位、补拍视角和完整的 video-to-video 提示词，适用于 Codex 中的影视创作工作流。

把原片看作已经完成的表演，重新决定观众从哪里看：保留动作、对白、口型、视线和时间节奏，通过机位、焦段、构图、景深、运镜与切镜增加画面信息和情绪层次。

## 效果对比

[查看或下载「上下同步对比」视频](examples/上下同步对比.mp4)

用户提供的上下同步对比演示，时长约 13.10 秒，画面尺寸 992×960。视频按原文件上传，保留画面与音轨。上下拼接用于展示对比，不代表重摄影输出需要分屏；进行新任务时，应单独提供对应的原视频母版。

## 能做什么

- 根据原视频或用户提供的可信分析，建立源事件时间表，区分实测、用户提供、估计和未知信息。
- 设计覆盖原片时间轴的多机位剪辑，包括双人镜头、过肩、反应、动作和道具特写。
- 将人物、道具及不同方向的背景参考分工绑定，检查动作、视线与空间连续性。
- 默认中文解释、英文提示词，也支持完整中文提示词及中英双版。
- 对用户明确追加的对白、动作或背景修改，列明解除的锁定项，避免同时承诺“原片完全不变”。

这是一套分析与提示词技能，不自带视频生成服务。需要原片的新视角任务适用；无原片的新剧情、普通文生视频、图片转视频及单独改写表演不属于默认范围。

## 安装

本仓库根目录就是技能目录，包含 `SKILL.md`、`agents/` 和 `references/`。将仓库克隆或完整复制到 Codex 的技能目录，并将文件夹命名为 `video-rephotography`。

Windows PowerShell 示例（已安装 Git；若目标已存在，先保留已有版本，不直接覆盖）：

```powershell
$skillRoot = if ($env:CODEX_HOME) {
    Join-Path $env:CODEX_HOME 'skills'
} else {
    Join-Path $HOME '.codex\skills'
}
New-Item -ItemType Directory -Path $skillRoot -Force | Out-Null
git clone https://github.com/pencil102411-cell/video-rephotography.git (Join-Path $skillRoot 'video-rephotography')
```

安装后在新任务中确认技能可用，再通过 `$video-rephotography` 调用。

## 使用示例

```text
使用 $video-rephotography 分析我提供的原视频。
保留原片表演、对白、动作、视线和时间轴，设计一条多机位剪辑。
重点突出两人之间的调侃，增加双向过肩和道具特写。
先给源事件表与机位表，再输出完整中文、英文两版可复制提示词。
图片只用于指定的人物、道具和背景参考；缺少依据的区域请明确说明。
```

提供原视频，以及希望突出的情绪或信息。对白原文、角色图、场景正反方向图和道具图可帮助澄清参考关系，但不要求每次都备齐同一套素材。

默认交付一条按时间切换机位的单画面视频提示词。若需要各机位独立的全长版本，请明确提出。镜头数、画幅、时长与输出语言遵循当前素材和用户要求，不套用固定的九镜或十三镜方案。

## 文件说明

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](SKILL.md) | 适用边界、表演锁定契约、摄影设计与交付规则 |
| [agents/openai.yaml](agents/openai.yaml) | Codex 显示名称及默认调用提示 |
| [references/prompt-template.md](references/prompt-template.md) | 完整生成提示词模板 |
| [references/timeline-and-qa.md](references/timeline-and-qa.md) | 源事件表、镜头记录与验收依据 |
| [references/platform-notes.md](references/platform-notes.md) | 带核对日期的平台适配记录 |
| [references/scenario-case.md](references/scenario-case.md) | Scenario 案例分析、来源与复用边界 |
| [references/scenario-original-prompt.txt](references/scenario-original-prompt.txt) | 用户提供的上游提示词原文副本 |
| [examples/上下同步对比.mp4](examples/上下同步对比.mp4) | 用户提供的上下同步对比演示视频 |

## 来源与验证边界

方法参考 [Scenario 的公开演示](https://x.com/Scenario_gg/status/2102365054389899695/video/1)、[作者提示词回复](https://x.com/Scenario_gg/status/2102365314562294250)及用户提供的原文，来源资料保留归属，不将上游原文标为本仓库原创。具体观察及尚未核对的内容记录在案例说明中。

平台设置记录有核对日期，提交生成前应检查当前入口。技能文件完整和提示词自洽不代表成片必然保持逐帧一致；只有实际生成并检查过的视频，才能报告成片验收结果。
