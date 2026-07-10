# Dance Comparison Workflow

## Preconditions

Use FFmpeg/FFprobe for inspection and rendering. Prefer the project-local FFmpeg when available; otherwise use the system command. If neither is available, stop before editing and clearly state that rendering cannot start until an FFmpeg tool is available.

Both inputs must show enough of the dancer to judge movement. A reference downloaded by the user through the official client is acceptable; do not fetch or download platform media.

When an input has multiple dancers, require the user to identify the relevant person by position and clothing. Require both the user and the reference dancer when both clips are multi-person. Do not guess an identity from a group formation.

## Alignment

1. Identify the first shared movement landmark automatically: first counted step, arm opening, body drop, or clear musical hit.
2. Set independent start offsets so that landmark occurs at output `00:00:00.000` in both clips.
3. Check a second landmark around the first transition and a third at a high-amplitude move.
4. If drift remains small and steady, apply a modest speed correction only when it keeps the teacher audio natural. If drift is large or variable, do not force it; request a better source or a manual start cue.
5. Trim both clips to their common aligned dance length.
6. Re-encode at 30 fps after offsets and any approved correction. Avoid frame dropping that changes movement order.

## Direction Check

Make left-right direction consistent before evaluating form:

1. Inspect the shared start, one one-sided arm/head action, and one stepping or turning action.
2. Compare the teacher's original direction and an `hflip` candidate against the user's unmirrored video.
3. Keep the candidate whose corresponding arm, foot, turn, and travel direction match the user. When the mirrored candidate wins, mirror the teacher.
4. Never mirror the user's video automatically.
5. If the reference direction cannot be inferred because of a group formation, obstruction, or symmetric moves, render a 3-5 second proof and ask for a precise reference-dancer identity or start cue before the full export.

## Composition

Use a 1080x960 canvas with two 540x960 panels. Keep the teacher in the left panel and the user in the right panel.

- Use the teacher direction selected by the Direction Check. Mirror only the teacher when the mirrored candidate produces matching left-right actions. Keep the user unmirrored.
- Reframe the user more tightly than the source when possible, but leave room for raised hands, steps, and head movement.
- Match perceived dancer size between panels without distorting aspect ratio.
- Use teacher audio only. Do not mix, duck, or retain the user's audio.
- Burn each action prompt in white Chinese text inside the user's panel, with a subtle dark translucent background for legibility. Time prompts to the relevant action, keep them to one or two short lines, and do not obscure the user's head, hands, or feet.

## Verification

Before full delivery, inspect beginning, middle, and late output frames. Confirm:

- Same first shared movement and beat placement.
- Teacher is on the left and its left-right direction matches the user at the checked asymmetric landmarks.
- User is on the right, enlarged, and not visibly cropped at key movements.
- No user audio stream remains in the export.
- Output is 1080x960, 30 fps, H.264 video with AAC teacher audio.

## Feedback Format

Use five to ten entries, ordered by learning impact. Each entry must have a directly visible basis in the aligned video.

```markdown
# 动作对比重点

1. `00:12.40`｜右臂与肩线
   差距：老师右臂抬到肩线后停得更稳；你的手肘略低，落点提前。
   练习：对着镜子先做四次“抬到肩线—停半拍—落下”，再接回音乐。
```

Use plain, supportive language. A useful note is specific enough to practice once, but never presents a camera-angle guess as a fact.

## Stop Conditions

Pause and ask the user for a replacement reference or manual start instruction when:

- The choreography is not the same.
- Either dancer's hands, feet, or trunk are repeatedly outside the frame.
- The image is too blurry or obstructed to compare.
- Beat and movement landmarks disagree after the proof segment.
- Teacher orientation cannot be safely inferred.
