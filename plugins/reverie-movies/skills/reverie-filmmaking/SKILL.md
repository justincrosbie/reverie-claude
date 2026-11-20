---
name: reverie-filmmaking
description: Make a short film, music video or other AI video with Reverie Movies. Covers which tools to call in what order, keeping characters and objects consistent across shots, continuous camera moves, checking each shot before building on it, scoring the film with original music, choosing models, and getting the user's OK before anything costs credits. Use when the user wants to make, continue or fix a film with Reverie.
---

# AI filmmaking with Reverie Movies

Reverie Movies turns an idea, a script or a song into a finished film. The film is planned as scenes and shots, rendered shot by shot with AI video models, and exported as one video. Everything happens in the user's Reverie account, so they can keep editing at reveriemovies.com. Planning and editing are free; anything that spends credits is quoted first.

## The plan: every film, step by step

Every film follows the same plan, whatever kind it is. Most people here have never made a film: they don't know the steps, so you lead them through. Know which step you're on (from what's in the project and what's been said), never redo a finished one, and at every step do the free work yourself, then end by saying where they are in the plan, what comes next, and one question they can answer in a word, with the likely answers offered as choices. Never hand them a form, and never ask them for prompts, shot lists, timings or models: those are yours.

1. **What they have.** A song, a script, an idea, or nothing yet. If what they've said doesn't make it clear, ask, with those four as the choices. It decides the kind of film (below).
2. **The source.** It's their film: plan nothing until they've given or chosen an idea.
   - A song: have them send it, listen to it, and say in two sentences what you hear: the mood, the tempo, where it lifts, and where the singing is.
   - A script: have them paste or send it, read it, and say back in a line what you found: who's in it, where it happens, whether people speak, and about how long it runs.
   - An idea: take it in their words, however short ("me floating through sci-fi worlds" is enough).
   - Nothing yet (or "a music video for my song", which isn't an idea): ask whether they have an idea or would like some. When they want some, pitch three, A, B and C, one line each (drawn from their song when there is one), and let them pick one, mix them or change one.
3. **The shape.** Propose it all at once, from the source, as one line they can change: how long (a song or a script's lines set it), widescreen or vertical (vertical for a phone or social post), whether people speak, and the look and genre ("about 90 seconds, widescreen, two speaking parts, a moody thriller: change anything?"). Their yes settles it. When they've said to just make it, or what they've sent settles it already ("a two-minute film", a script with its times marked), decide the rest yourself, say it in a line, and go straight on.
4. **The cast.** Everyone who appears, from the script or the idea: don't ask for what the script already says. A real person ("me", "my sister") needs a clear photo of their face before any picture is made, or every picture shows a stranger. Someone you make up: say in a line how they'll look, so they can change it, and give them a portrait before any still, so they look the same in every shot. If nobody's in it, say so and move on.
5. **The voices** (only when people speak). Every speaking part has its voice before any line is voiced. Offer both: they send a clip of 5 to 30 seconds of just that person speaking (ask once whose voice it is: theirs, or someone who's agreed), or you make one from a described voice ("a warm, gravelly old sailor"), about 30 words of their lines so it runs 8 to 15 seconds, and play it to them. Ask which first, with a button for each, and quote nothing yet; once they've picked, put a line for every speaker on one card. Give it to the character, so they speak in it in every shot.
6. **The sound** (not for a music video: the song is its sound). Ask how it should sound, with a button for each and what the film costs each way (set_film_plan gives the prices), and record their answer (set_film_plan sound): music composed for it ("score": quote generate_music for its length now, on its own card), the sound of each scene recorded with its video ("scene": rain, footsteps, the sea; it costs more), or silent for now ("silent": music can be added later). When people speak, their voices are there either way: the question is what's under them. Never make a film silent without asking: a silent sample was a surprise.
7. **The plan**, once the cast and the sound are settled (and their voices, when people speak). A portrait still being made counts: plan while it's made, in the same turn, rather than waiting for it. Every scene, then every shot, to the film's end, in one go (planning is free), timed to what drives the film (below). Then say in a line how many shots, how long they run, and one line per scene.
8. **The lines** (dialogue or narration). Voice every line first, in its speaker's voice, and listen with them, before any video: a line fixed now costs a credit; fixed after the render, it costs the scene.
9. **A sample.** A short stretch made start to finish on one yes (the first scene; for a music video its best 25 to 30 seconds, usually the chorus), so they see it working before paying for it all. Say what the whole film costs against their credits.
10. **The rest of the film**, on one yes, once they've seen the sample and have the credits.
11. **The finished film.** Put it together, check it end to end, and give it to them to watch and download. Then offer to redo any shot they don't like.

**Kinds of film.** The kind is what drives the film, and it changes some steps. Genre (action, comedy, horror…) is part of the look, not the kind.
- **Music video**: from their song, which sets the length and the cuts (on the beat). No voices or lines steps: shots sung on camera get lip-sync to the song, on the same card as their videos, without being asked.
- **Story with dialogue** (a drama, a comedy, two people talking): from a script or an idea. The lines drive it, so the voices and the lines come before any video. A talking scene is one take per exchange, with the lines quoted and each speaker's voice set.
- **Story without dialogue** (action, a mood piece, a trailer): from an idea. Its length drives it (ask, or offer 30 to 60 seconds). More motion and quicker cuts for action, slower and wider for a mood.
- **Narrated** (a documentary, an explainer, a story told over pictures): from a script or an idea. The narration drives it: write it with them, voice it (the narrator's voice is step 5), and cut the shots to it.
- **Ad or social post**: from a product or a message. Its format drives it: vertical, 15 to 30 seconds, ending on the product or a line of text. The whole ad is the sample.

## Doing each step with these tools

Pick the workflow from what the user has, and lead them through the plan above with it.


**An idea, or nothing yet**
1. `ideate_concepts`: show the three concept cards (A/B/C) and let the user react. Don't ask for a finished idea first.
2. `refine_plan` for changes, then `advance_plan_stage` (with `choose_concept` at the concept stage): concept → story bible → storyboard.
3. `create_project_from_plan` (free): the storyboard becomes a project with characters, scenes and shots.
4. `generate_character_image` for every character who appears in a shot, before any of their shots' stills, so every shot keeps their faces and clothes. Put the full appearance in the prompt: the portrait is made from the prompt you pass. A still made for someone with no portrait invents them afresh, and they look different in every shot (the still's quote lists them under `portraits_missing`).
5. `generate_clip_image` for each scene's opening shot.
6. Render: `render_clip` per shot, or `render_chain` for a run of continuations.
7. Score it, if the user has no music of their own: `generate_music` (below).
8. `export_movie`.

**A script or story**: `ideate_concepts` with `source_material` and `fidelity: "faithful"` keeps its scenes, names and dialogue. Then as above.

**A song (music video)**: `create_project`; add the song with `add_file` (`use_as: "audio_track"`); `listen_to_song` (free) to hear its mood, sections, big moments and beat, and tell the user in a couple of sentences what you hear; plan shots to it with `create_scene` and `create_clip`, a new scene at each section; give everyone in the shots a portrait before any still (`attach_image` with a photo of a real person, `generate_character_image` for one they've made up); render; `fit_cuts_to_music` so every cut lands on the beat; then `lip_sync_clip` each singing shot **last**, because lip-sync is matched to the shot's place in the song; `export_movie`. A whole song costs more than most users have at first: start with a sample (below).

**A scene with dialogue**: settle the lines first. Voice each with `generate_voice_over` in the voice the character will have, and listen with the user. Set each speaker's voice from a 5–30 second sample (`set_character_voice`), then render the exchange on `kling-4.0` with the lines quoted in the prompt. See *Lessons from finished films* below.

**An existing film**: `list_projects` → `get_project`, then edit, render what's missing, or export.

## A sample first

Most users can't pay for a whole film before they've seen any of it, and a new account's credits don't cover a whole song. Show them part of it first:

1. Plan the whole film (free), then quote the first 20–30 seconds of shots on the preview model and say what the whole film would cost against their credits.
2. Render those shots and check each with `view_shot_frames`.
3. `export_movie`: a partly rendered film exports as a sample, the rendered shots with their stretch of the song. Give the user the finished `video_url` to watch.
4. Then quote the rest. If it's more than they have, say once which credit pack covers it.

Make the musical and technical calls yourself (where cuts land, which model, how long each shot runs) and tell the user what you chose. Don't ask them to check beat grids or timelines.

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
- **When the user reacts to a shot** ("love it", "her face changed", "there are strangers in it"), record it with `rate_shot` (free). For a problem it returns the usual fix: offer it in a sentence. A render it leads to is quoted like any other.
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
- Looking at a shot with characters (looking at its frames or its still) also returns `faces`: whether each character still matches their portrait, and what differs. On drift, fix the still (or make it again with the characters set) before rendering from it or continuing from the shot. It's reliable on clothes, hair and accessories; for subtle face changes, look yourself as well.
- Set the shot's characters before making its still, so the still is made from their portraits. A still like that carried their faces through the shot on every model we tested, even when someone left the frame and came back.
- Only kling-4.0 uses the still and the portraits together. On Veo and Wan, naming characters for a render swaps the still for a new picture made from the portraits; leave them out to keep the still.
- Characters that must stay identical across many shots need a premium model such as kling-4.0. On a free account, Wan 3.0 from a still made with the characters does best.
- Someone who enters partway through a continuation (not in its first frame) gets an invented face and clothes. Whenever a prompt brings a person in partway through, offer an end frame showing them in the same reply as the render's quote.

**Sound**
- Shots with their own sound keep it in the export, mixed with the music and voice tracks. Mute a shot's own sound (update_clip with audio_muted) where a track replaces it.
- Keep a score low (about 0.2–0.3 volume) under dialogue, and let it stop or thin out for silences.

**Before calling it finished**
- Export and watch the whole film: every join, every line. Problems that hide in single shots show up in the cut.

## Music

`generate_music` composes an original score (or a song, with `instrumental: false`) and adds it as an audio track. Set `duration_seconds` to the film's runtime; a longer piece is cut to length with a fade. Write the brief like a composer's cue sheet: genre, instruments and mood, with sections timed to the film's moments from `get_project`'s shot start times: "[0:00-0:15] solo felt piano, curious. [0:15-0:35] pizzicato strings join, playful. [0:35-0:50] timpani and swelling strings, the plunge." Describe the sound; it refuses named artists and copyrighted lyrics. If the user has their own song, use it instead (`start_upload` + `add_file`).

Uploading the user's files: `start_upload` returns an `upload_url` to PUT the bytes to. If you can't send bytes yourself, give the user its `upload_page_url` as a link: it opens a page where they choose the file, with no sign-in. Give only that link. Where the chat app passes attached files to tools (ChatGPT does), a file the user attached goes straight to `add_file` as `file`, or to `attach_image` as `image`, with no upload page. When they say it's done, call `add_file`. Ask for one file at a time, saying which it is ("your song", "a photo of you").

## Shape and sound

- **Set the shape when you create the project**: `create_project` with `aspect_ratio: "9:16"` for TikTok, Reels and Shorts. It defaults to 16:9 landscape. Quotes state each shot's shape and whether it has sound.
- **Shots are silent unless you pass `with_audio: true`** (50% more). Ask whether the user wants sound before quoting.

## Keeping a character identical

For a real person, a costume or a mascot that must never change:

1. Give them a reference: a clean, front-on, full-body image, ideally a real photo, as the character's portrait (`attach_image`).
2. Set the shot's characters (`create_clip` with `characters`) before making its still: the still is then made from their portraits, and it carries their faces into the video on any model, even when someone leaves the frame and comes back.
3. Render on **kling-4.0**, the only model that uses the still and the portraits together. On Veo and Wan, naming `characters` in `render_clip` renders from a new picture made from the portraits instead of the still (the still stays on the shot); to render from the still, leave them out. The quote's `notes` say which will happen.
4. A continuation starts from the shot before and sends no portraits (except on kling-4.0), so any drift carries forward. Give continuations an end frame showing the character.
5. Keep them large in frame, describe the costume the same way in every prompt, and spell out what must not change ("he never speaks, his mouth never moves").
6. Check each shot with `view_shot_frames` before building on it.

## Choosing a model for the shot

Leave `model` out unless the user asks, or the shot is one of these. When you pick one, say why in a line, with the price from the quote.

| The shot | Use | Why |
|---|---|---|
| People talking | `kling-4.0` | Each character keeps their face and speaks in their own voice. 3–30 s, sound always on. |
| Characters who must look identical across many shots | `kling-4.0` | It uses the shot's still and the portraits together. |
| Characters, on a free account | `wan-3.0` from a still made with the shot's characters, without naming them in the render | Included at 480p and 720p, 2–30 s, sound at no extra cost. The still carries their faces; named, Wan swaps the still for a weaker likeness. |
| A character with no still yet | `veo-3.1-generate-001` with `characters` | The best likeness from portraits alone, though it invents the setting. |
| A wide shot of a group | Kling | Veo adds strangers to groups. |
| Children | Kling | Veo refuses to render children. |
| An end frame framed unlike the start | Kling | Veo blends the two into a double exposure. |
| A single subject in similar framing, cheaply | `veo-3.1-lite-generate-001` | The cheapest; it takes no portraits, so start from a good still. |
| A long take without dialogue | `wan-3.0`, `kling-4.0`, or `seedance-2.5` for anything but real people | Up to 30 s. Seedance turns photorealistic people away. |

How each model uses characters (tested on the same shot, November 2026): **kling-4.0** keeps the still and adds the portraits. **veo-3.1-generate-001** (best likeness), **veo-3.1-fast-generate-001** and **wan-3.0** (weakest likeness) use the portraits *instead of* the still when you name characters. **kling-3.0**, **veo-3.1-lite** and **MiniMax** take no portraits: the still carries the faces.

Free accounts render on the included models; `get_credit_balance` reports `premium_unlocked`. Say plainly, once, that characters identical across shots need a premium model such as Kling 4, and recommend Wan 3.0 from a still for the rest. Never press.

## Spending

Renders, images, enhancements, extensions, voice-overs, character voices, music, new transitions and export each work in two calls:

1. Call without `confirm`. Nothing is spent; you get a quote (`credits_required`, `what`, `quote_id`).
2. Tell the user what it is and what it costs, and wait for a clear yes.
3. Call again with the same arguments plus `confirm: true` and the `quote_id`.

A quote covers only the call it was made for, lasts an hour and works once. If a confirm is refused with `quote_required`, quote again. Never confirm on your own judgment. A render is charged only when it finishes; a blocked or failed one costs nothing. If a suitable image is already in the conversation, offer `attach_image` (free) before quoting a generated one.

Renders take minutes. Poll `get_render_job_status` with all outstanding job ids at once, and don't say a shot is done until its job is. When a shot or an export is done, give the user its `video_url` so they can watch it right there.

## What Reverie can't do

Say so without calling tools: buying credits (bought at reveriemovies.com), publishing to YouTube or social media (export, then the user uploads), or controlling desktop editors.
