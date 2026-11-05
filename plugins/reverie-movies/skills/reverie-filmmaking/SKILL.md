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

**A scene with dialogue**: settle the lines first. Voice each with `generate_voice_over` in the voice the character will have, and listen with the user. Set each speaker's voice from a 5–30 second sample (`set_character_voice`), then render the exchange on `kling-4.0` with the lines quoted in the prompt. See *Lessons from finished films* below.

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

## Lessons from finished films

Learned making real films here, most of them from what those films wasted.

**Before you spend**
- Settle the script before any video. For dialogue, voice the lines first (a voice-over for each, in the voice the character will have, about a credit a line) and listen with the user. A line that doesn't land costs a credit to fix now and a whole scene's render later.
- Prove a doubtful idea with the cheapest thing that shows it: a still before a render, a short render before a long one. A continuation is the exception: it starts from the shot before and never needs a still.
- Decide which shots continue which before rendering. Two shots in a row that start from the same still jump at the cut: make the second a continuation, so it starts on the first one's last frame.

**Dialogue**
- For people talking, use kling-4.0 with each speaker's voice set from a 5–30 second sample (set_character_voice). Render the exchange as one take of up to 30 seconds, with the lines quoted in the prompt and who says each. It cuts to close-ups and inserts on its own, which plays far less stiffly than a locked two-shot.
- Kling 4 keeps the cast and their voices on continuations too, so a long scene can run as a chain of takes.
- Direct the delivery sparingly: one or two specific pauses where they matter. Asking for long pauses everywhere makes every line slow and wooden.
- Lip-syncing a silent shot to a recorded line is the fallback for other models: the heads stay still and it rarely looks seamless. If you use it, render the speaker listening with a closed mouth, and check the lip-synced version is the one in use before exporting.
- An exact repeat (a loop, a callback, a glitch) has to reuse the same take. A new generation never says it the same way twice.

**Keeping it consistent**
- Check every new still against the characters' portraits and the shots either side: clothes, hair, props. A wardrobe change between two stills shows as a costume change at the cut.
- Name the characters for each render, or set them on the shot, so their portraits guide it.

**Sound**
- Shots with their own sound keep it in the export, mixed with the music and voice tracks. Mute a shot's own sound (update_clip with audio_muted) where a track replaces it.
- Keep a score low (about 0.2–0.3 volume) under dialogue, and let it stop or thin out for silences.

**Before calling it finished**
- Export and watch the whole film: every join, every line. Problems that hide in single shots show up in the cut.

## Music

`generate_music` composes an original score (or a song, with `instrumental: false`) and adds it as an audio track. Set `duration_seconds` to the film's runtime; a longer piece is cut to length with a fade. Write the brief like a composer's cue sheet: genre, instruments and mood, with sections timed to the film's moments from `get_project`'s shot start times: "[0:00-0:15] solo felt piano, curious. [0:15-0:35] pizzicato strings join, playful. [0:35-0:50] timpani and swelling strings, the plunge." Describe the sound; it refuses named artists and copyrighted lyrics. If the user has their own song, use it instead (`start_upload` + `add_file`).

## Shape and sound

- **Set the shape when you create the project**: `create_project` with `aspect_ratio: "9:16"` for TikTok, Reels and Shorts. It defaults to 16:9 landscape. Quotes state each shot's shape and whether it has sound.
- **Shots are silent unless you pass `with_audio: true`** (50% more). Ask whether the user wants sound before quoting.

## Keeping a character identical

For a real person, a costume or a mascot that must never change:

1. Give them a reference: a clean, front-on, full-body image, ideally a real photo, as the character's portrait (`attach_image`).
2. Render on a model that takes character references: **kling-4.0** or **veo-3.1-generate-001**. Kling 3.0 Pro and the Veo Fast and Lite models ignore them. The quote's `notes` say when references won't be used.
3. A continuation starts from the shot before and sends no references (except on kling-4.0), so any drift carries forward. Give continuations an end frame showing the character.
4. Keep them large in frame, describe the costume the same way in every prompt, and spell out what must not change ("he never speaks, his mouth never moves").
5. Check each shot with `view_shot_frames` before building on it.

## Choosing models

- Leave `model` out unless the user asks; the quality tier picks one.
- **Kling 4** (`kling-4.0`, 3–30 seconds, sound always on) is the model for people talking: each character keeps their face and speaks in their own voice, and it cuts within a take on its own.
- **Kling** holds people, groups and continuity best. Use it for shots with people, wide group shots, and shots whose end framing differs from their start.
- **Veo** models are cheaper, but they add strangers to wide group shots, blend very different framings into a double exposure, lose small subjects in wide shots, and refuse to render children. Veo 3.1 Lite is good for single subjects that stay in a similar framing.
- Free accounts render on the included models. `get_credit_balance` reports `premium_unlocked`. Mention a premium model at most once, and only when it would clearly serve the shot.

## Spending

Renders, images, enhancements, extensions, voice-overs, character voices, music, new transitions and export each work in two calls:

1. Call without `confirm`. Nothing is spent; you get a quote (`credits_required`, `what`, `quote_id`).
2. Tell the user what it is and what it costs, and wait for a clear yes.
3. Call again with the same arguments plus `confirm: true` and the `quote_id`.

A quote covers only the call it was made for, lasts an hour and works once. If a confirm is refused with `quote_required`, quote again. Never confirm on your own judgment. A render is charged only when it finishes; a blocked or failed one costs nothing. If a suitable image is already in the conversation, offer `attach_image` (free) before quoting a generated one.

Renders take minutes. Poll `get_render_job_status` with all outstanding job ids at once, and don't say a shot is done until its job is.

## What Reverie can't do

Say so without calling tools: buying credits (bought at reveriemovies.com), publishing to YouTube or social media (export, then the user uploads), or controlling desktop editors.
