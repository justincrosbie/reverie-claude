---
name: reverie-filmmaking
description: Make a short film, music video or other AI video with Reverie Movies. Covers which tools to call in what order, keeping characters and objects consistent across shots, continuous camera moves, checking each shot before building on it, scoring the film with original music, choosing models, and getting the user's OK before anything costs credits. Use when the user wants to make, continue or fix a film with Reverie.
---

# AI filmmaking with Reverie Movies

Reverie Movies turns an idea, a script or a song into a finished film. The film is planned as scenes and shots, rendered shot by shot with AI video models, and exported as one video. Everything happens in the user's Reverie account, so they can keep editing at reveriemovies.com. Planning and editing are free; anything that spends credits is quoted first.

## Pick the workflow from what the user has

**An idea, or nothing yet**
1. `ideate_concepts`: show the three concept cards (A/B/C) and let the user react. Don't ask for a finished idea first.
2. `refine_plan` for changes, then `advance_plan_stage` (with `choose_concept` at the concept stage): concept → story bible → storyboard.
3. `create_project_from_plan` (free): the storyboard becomes a project with characters, scenes and shots.
4. `generate_character_image` for the main characters, so later shots keep their faces and clothes. Put the full appearance in the prompt: the portrait is made from the prompt you pass.
5. `generate_clip_image` for each scene's opening shot.
6. Render: `render_clip` per shot, or `render_chain` for a run of continuations.
7. Score it, if the user has no music of their own: `generate_music` (below).
8. `export_movie`.

**A script or story**: `ideate_concepts` with `source_material` and `fidelity: "faithful"` keeps its scenes, names and dialogue. Then as above.

**A song (music video)**: `create_project`; add the song with `start_upload` + `add_file` (`use_as: "audio_track"`); plan shots to its length with `create_scene` and `create_clip`; render; trim with `update_clip` (`trim_end_seconds`) so cuts land on the beat; then `lip_sync_clip` each singing shot **last**, because lip-sync is matched to the shot's place in the song; `export_movie`.

**An existing film**: `list_projects` → `get_project`, then edit, render what's missing, or export.

## Continuity

| The user wants to… | Use |
|---|---|
| Continue the action in a new shot | `create_clip` with `clip_type: "continuation"`. It starts on the previous shot's last frame, so it needs no still. |
| Render a run of continuations in one go | `render_chain`: one quote for the run; each shot starts when the one before finishes. |
| Make a rendered shot longer | `extend_clip` |
| End a shot on a particular picture | `set_end_frame` (another shot's frame or an image take), or `generate_clip_image` with `use_as: "end_frame"` |
| Soften a cut | `set_transition` |

Write each continuation so its camera keeps the direction and speed of the shot before. A shot that plunges down followed by one that "rises" makes a visible bounce at the cut.

## Shot craft (learned making real films)

- **Look at every shot before building on it.** Call `view_shot_frames` when a render finishes. Check the characters and objects, that nothing unexpected has appeared, and that a continuation picks up where the shot before ended.
- **Someone entering partway through a continuation** gets invented unless you give that shot an end frame showing them (`generate_clip_image` with `use_as: "end_frame"`).
- **A small subject that ends a shot as a blur** (a paper boat lost in a waterfall) gets reinvented by the next shot, sometimes as something else entirely. Give the next shot an end frame made from the subject's portrait, and prompt the camera to find the subject first.
- **Keep small subjects large in the frame**: "the camera stays close behind so the boat stays large in the foreground". Wide shots lose them.
- **Restate a recurring object's look** in every prompt where it appears, especially when it wasn't in the previous shot's last frame.

## Music

`generate_music` composes an original score (or a song, with `instrumental: false`) and adds it as an audio track. Set `duration_seconds` to the film's runtime; a longer piece is cut to length with a fade. Write the brief like a composer's cue sheet: genre, instruments and mood, with sections timed to the film's moments from `get_project`'s shot start times: "[0:00-0:15] solo felt piano, curious. [0:15-0:35] pizzicato strings join, playful. [0:35-0:50] timpani and swelling strings, the plunge." Describe the sound; it refuses named artists and copyrighted lyrics. If the user has their own song, use it instead (`start_upload` + `add_file`).

## Choosing models

- Leave `model` out unless the user asks; the quality tier picks one.
- **Kling** holds people, groups and continuity best. Use it for shots with people, wide group shots, and shots whose end framing differs from their start.
- **Veo** models are cheaper, but they add strangers to wide group shots, blend very different framings into a double exposure, lose small subjects in wide shots, and refuse to render children. Veo 3.1 Lite is good for single subjects that stay in a similar framing.
- Free accounts render on the included models. `get_credit_balance` reports `premium_unlocked`. Mention a premium model at most once, and only when it would clearly serve the shot.

## Spending

Renders, images, enhancements, extensions, voice-overs, music, new transitions and export each work in two calls:

1. Call without `confirm`. Nothing is spent; you get a quote (`credits_required`, `what`, `quote_id`).
2. Tell the user what it is and what it costs, and wait for a clear yes.
3. Call again with the same arguments plus `confirm: true` and the `quote_id`.

A quote covers only the call it was made for, lasts an hour and works once. If a confirm is refused with `quote_required`, quote again. Never confirm on your own judgment. A render is charged only when it finishes; a blocked or failed one costs nothing. If a suitable image is already in the conversation, offer `attach_image` (free) before quoting a generated one.

Renders take minutes. Poll `get_render_job_status` with all outstanding job ids at once, and don't say a shot is done until its job is.

## What Reverie can't do

Say so without calling tools: buying credits (bought at reveriemovies.com), publishing to YouTube or social media (export, then the user uploads), or controlling desktop editors.
