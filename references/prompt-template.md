# 提示词模板

`{{...}}` 是编写时的变量，不是平台参数。按当前原片替换；没有证据的字段不能填假数。无台词、无抛接、无慢动作的素材删除相关例外。用户只提供文字分析时说明数据来源，不能标为独立测量。

默认整段生成一条剪辑成片，镜头按时间硬切。若用户指定另一个交付形态，相应改写 OUTPUT，不保留互相冲突的说明。

```text
ONE FINISHED PERFORMANCE, RE-PHOTOGRAPHED

SOURCE AND OUTPUT
{{SOURCE_TAG}} is the timeline master: {{source description}}, duration {{T}} seconds, with {{audio status}}. The performance has already happened. Re-photograph that same event from the camera positions below. Do not restage, re-perform, reinterpret or re-time it.
Create ONE full-frame edited video covering 0.00–{{T}} seconds. Cut between the specified views at their boundaries, following one continuous source timeline. Do not create a split-screen, collage, or simultaneous views. At output time t, show the event occurring at source time t. End at {{T}}; do not pad the ending.

LOCKED PERFORMANCE AND WORLD
Preserve identity, body pose, head angle, original eyeline, microexpressions, blink timing, lip movement, hands, contact with objects, object count, action paths and event timings from the source. Keep wardrobe, props, set layout, light direction and softness, exposure, white balance and colour grade.
Only camera position, orientation, focal-length intention, framing, focus, depth of field, camera movement and the listed cuts may change. Perspective, parallax, occlusion and reflections must change naturally with viewpoint. Never move the actor or a prop to improve a new composition.

AUDIO AND SPEECH WINDOWS
Preserve the original dialogue, voice, pauses, ambience and sound events, synchronized to the source timeline. Do not rewrite, dub, regenerate a new performance, or add music or sound effects.
{{speaker identity}} SPEAKING: {{verified or user-supplied intervals}}.
{{speaker identity}} NO SPOKEN WORDS: {{complementary intervals with actual nonverbal mouth actions}}.
Repeat the speaker-specific map only if more speakers are present.
Whenever the mouth is visible during speech, its movements follow the original speech, even when the person looks down, appears in profile or is out of focus. When the mouth is hidden, the original audio continues. No spoken words does not mean a frozen or necessarily closed mouth: preserve the source breathing, drinking, chewing and other nonverbal movement. Do not mute ambience in these intervals.

EYELINE
The original performance is directed toward {{original camera/person/object and spatial location}}. Preserve its time-varying gaze targets: {{source glances and returns}}.
The subject does not turn toward, search for, or greet a new camera. {{geometry-specific instructions for side/rear/on-axis views}}. Lens contact occurs only where the source gaze and the new lens position naturally align at that same instant.

PLAYBACK TEMPO
Match the playback of the source 1:1. No new slow motion, speed ramps, freeze frames, time remapping, repeated actions or temporal skips.
{{If present: source-embedded slow passage and exact or qualified interval; retain it as recorded, without slowing or extending it further.}}

EVENT ANCHORS
{{For each fast or contact-critical action: time before action and object state; release/contact/start; trajectory or action phase; catch/end/contact; state afterward.}}
Camera movement may follow these events but may not change their timing, path, duration or outcome. The same object remains the same object across all cuts.

NEWLY REVEALED AREAS
{{For each relevant view: evidence-backed visible background; areas to keep out of frame; specific content that must not be invented.}}
Maintain a coherent space across views. Do not fill unseen areas with unsupported salient people, architecture, signage or props.

CAMERA PLAN
[{{start}}–{{end}}] {{camera position relative to subject and world, height and angle}}; {{shot size, focal-length feel}}, {{one dominant camera move with direction/end position}}, {{focus target and depth of field}}. Show the source action at this interval: {{action, head/gaze and object state}}. {{mouth visibility and intersecting speech/non-speech intervals}}. {{known foreground/background and required continuity}}.
{{Repeat for the remaining consecutive intervals, ending exactly at T.}}

SUBJECT AND SET CONTINUITY
{{Subject identity and distinctive details; wardrobe and hair; prop identities/counts/locations; scene geometry; lighting and colour anchors, all derived from this source.}}

NO ADDITIONS
No added people, actions, dialogue, object duplicates, unrequested set changes, captions or comparison labels. Preserve source-native details that belong to the scene. {{Any task-specific exclusions.}}
```

## 信息不足时

- 时长已知、语音窗口未知：仍可写“逐时跟随源音轨与口型”，并把窗口精确表列为待核对；不编造说话时间。需要精确窗口的交付暂标草稿。
- 只有一张截图：能写视觉锁定与摄影方向，不能完成原片时间表。
- 用户提供精确事件表但无法查看原片：可以据此输出完整提示词，注明“按用户时间表编写，原片未独立核对”，不要用 `measured` 冒充实测。
- 需裁剪或独立全长机位时：统一修改 SOURCE AND OUTPUT 与每段时间映射。不能只改总时长而留下旧锚点。

音轨原样保留是交付要求。若平台生成音轨有变化或不带音轨，应在剪辑中回贴原音并验同步，不能靠追加一句提示词就宣称无损通过。
