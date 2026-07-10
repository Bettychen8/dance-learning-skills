---
name: dance-comparison-coach
description: Create a direction-correct synchronized side-by-side dance comparison with burned-in action prompts from a user's dance video and a locally saved teacher/reference video. Use when Codex needs to identify dancers in multi-person clips, automatically align two performances by start movement and music, choose whether to mirror the teacher, enlarge and reframe the user's body, keep teacher audio only, trim to the common dance length, and export a frame-clear MP4 with concise Chinese movement guidance burned into the user's panel.
---

# Dance Comparison Coach

Turn a user's dance practice video and an officially saved local reference video into a reliable, frame-clear learning comparison. Default to teacher on the left, user on the right, automatic direction correction, teacher audio only, common-length trimming, white Chinese action prompts burned into the user's panel, and 30 fps.

## Required Inputs

Require two local videos:

1. The user's original dance video.
2. The teacher/reference dance video saved by the user through the official platform client.

When either video contains more than one dancer, require identification for every relevant person before editing. The user must give both a position and clothing description, for example: `我：画面中间，绿色上衣黑裤子；参考：中间，白上衣蓝裤子`.

Do not ask for mirror, start-time, duration, or prompt-style settings. Determine them automatically.

## Workflow

1. Inspect both videos before editing.
   - Check duration, resolution, rotation, frame rate, and audio streams.
   - Inspect representative frames to confirm full-body visibility, direction, and matching choreography.
   - Compare the teacher's original direction and a mirrored-teacher candidate at the shared start and at least two asymmetric motions, such as a one-sided arm, head turn, or stepping foot. Keep the candidate whose left-right actions match the unmirrored user. Never mirror the user's video automatically.
   - Read [references/comparison-workflow.md](references/comparison-workflow.md) before selecting offsets or rendering.

2. Align performance timing.
   - Find the first shared movement automatically, not merely the first decoded frame.
   - Use beat and visible movement landmarks to test timing at the beginning, a transition, and a large-amplitude move.
   - Trim both clips to their common aligned dance length.
   - Render an internal 3-5 second proof segment. Continue to the full export only when all three checks are coherent.
   - If the two clips are different choreography, lack enough visible body, are too blurry, or cannot be aligned or direction-checked confidently, explain the specific limitation and ask for a replacement clip or a precise identity/start cue.

3. Build the comparison export.
   - Place teacher left and user right in a 1080x960 landscape frame at 30 fps.
   - Use the direction-checked teacher candidate. When correction is needed, mirror the teacher horizontally; otherwise retain its original direction. Keep the user unmirrored.
   - Crop and scale the user into a direct-camera-like full-body view; preserve head, hands, and feet across key moves.
   - Use only the teacher audio; remove the user audio.
   - Burn 5-10 concise Chinese action prompts into the user's right-side panel at their relevant moments. Use white text with a subtle dark translucent background, keep each prompt to one or two short lines, and avoid covering the user's head, hands, or feet.
   - Export a playable H.264/AAC MP4 with no source modification and verify its streams, duration, frame rate, and early/middle/late frames.

4. Deliver learning evidence.
   - Export a keyframe sheet covering 5-10 high-value moments; label each with the aligned time.
   - Write the same concise Chinese coaching notes to a companion file. Use the format in the reference file.
   - Describe only visible differences such as timing, direction, range, height, weight shift, limb line, and stability. Do not claim medical, anatomical, or body-measurement precision. Do not score ambiguous angles, occlusion, or camera-perspective artifacts.

## Deliverables

Place exports in the requested output folder, using descriptive names:

- `dance_compare_<name>.mp4`
- `dance_compare_<name>_keyframes.jpg`
- `dance_compare_<name>_feedback.md`

Report any alignment limitation before presenting the feedback as reliable.
