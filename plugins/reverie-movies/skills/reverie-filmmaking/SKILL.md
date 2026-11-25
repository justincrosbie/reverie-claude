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
3. **The cast**, locked in before anything else is planned. Everyone who appears, from the script or the idea: don't ask for what the script already says. A real person ("me", "my sister") needs a clear photo of their face before any picture is made, or every picture shows a stranger. For each character, settle and save on them (create_character / update_character): how they look, their role (protagonist, antagonist, supporting or minor), what they're like, what they want, and how they change (personality, motivations, arc). Someone you make up: say in a line how they'll look and who they are, so they can change it, and give them a portrait before any still, so they look the same in every shot. Their cards are in Current state every turn: read a character's card whenever you use them, and describe them the same way in every prompt. One person playing several parts (clones, twins, a one-man band) is a character for each part, named for it, each with the same photo and their own clothes, so every shot's cast says exactly who and how many are in it; name them in the prompt, never "a second clone". A character's appearance is only how they look, never a place or an action. If nobody's in it, say so (set_film_plan nobody_in_it) and move on.
4. **The voices** (only when people speak). Every speaking part has its voice before any line is voiced. Offer both: they send a clip of 5 to 30 seconds of just that person speaking (ask once whose voice it is: theirs, or someone who's agreed), or you make one from a described voice ("a warm, gravelly old sailor"), about 30 words of their lines so it runs 8 to 15 seconds (generate_voice_over, then set_character_voice with its track: a sample isn't their voice until it's set), and play it to them. Ask which first, with a button for each, and quote nothing yet; once they've picked, put a line for every speaker on one card. Give it to the character, so they speak in it in every shot.
5. **Format and style**, for every kind of film, a music video too. Propose it all at once, from the source, in two or three short lines they can change:
   - how long (a song or a script's lines set it; otherwise ask, offering 30 to 60 seconds);
   - the format: vertical 9:16 for phones and social, or widescreen 16:9 for a computer, TV or YouTube; and 720p, or 1080p for a big screen;
   - whether people speak;
   - the look: the theme and genre, naming the world exactly ("a 1960s Star Trek starship", not "sci-fi"); how it's shot (film stock, light); its colours; how the camera moves; and any film, show or director it should feel like (ask whether they have one in mind, and offer one that fits).
   ("About 90 seconds, widescreen 16:9 for YouTube, two speaking parts. A moody rain-soaked thriller, shot on grainy 35mm in neon and shadow, slow push-ins, in the spirit of Blade Runner: change anything?") On their yes, record it all (set_film_plan length_seconds, aspect_ratio, resolution, look, visual_style, color_palette, camera_language, references). When they've said to just make it, or what they've sent settles it already ("a two-minute film", a script with its times marked), decide the rest yourself, say it in a line, record it, and go straight on.
6. **The sound** (not for a music video: the song is its sound). Ask how it should sound, with a button for each and what the film costs each way (set_film_plan gives the prices), and record their answer (set_film_plan sound): music composed for it, scene by scene ("score": the usual choice for a film, and the one to recommend; it's composed at its own step once the shots are planned, so quote no music yet), the sound of each scene recorded with its video ("scene": rain, footsteps, the sea; it costs more), or silent for now ("silent": music can be added later). When people speak, their voices are there either way: the question is what's under them. Never make a film silent without asking: a silent sample was a surprise.
7. **The scenes**, outlined, no shots yet (planning is free). Break the film into scenes from what happens in it, each with its setting and its time (create_scene), to the film's end:
   - Every scene gets its setting (create_scene setting): where it is and how it looks, in the brief's world, named exactly ("the command deck of a 1960s starship: curved consoles, gold, blue and red uniforms", never just "the bridge"). It goes into every picture and video in that scene, so the scenes stay in one world.
   - Every scene gets its time. A music video's scenes are the saved song map's sections (starts_at_seconds, ends_at_seconds, section). Any other film splits its length into a budget per scene (seconds) that adds up to the whole, from what happens in the script or the idea.
   Say them one line each with their times.
8. **The brief**, once the scenes are outlined. Sum up everything agreed in a short list they can check at a glance: the idea; who's in it and what they're about; how long; the format; the look, the shooting style, the colours, the camera and the references; the sound or the song's shape; and the scenes, one line each with their times. Ask what they'd change. Change what they ask in the step it belongs to (recording it with set_film_plan, update_character or update_scene) and show it again; on their yes, record it (set_film_plan brief_confirmed true). A message that changes the brief is never its yes: show it again and ask. When they've said to just make it, say the brief in two lines, record it, and go on. The brief is in Current state every turn: plan and make every scene and shot from it, never from memory, and when they change something in it later, record the change before anything is made.
9. **The shots**, on the confirmed brief, scene by scene: read each scene's setting, cast and time and each character's card, and fill its time with shots, to the film's end, in one go, timed to what drives the film (below). A portrait still being made counts: plan while it's made, in the same turn, rather than waiting for it.
   - A music video's shots land on its singing, its instrument entries and its big moments.
   - Each scene's shots fill its time; Current state flags a scene whose shots run short or over, or that has no setting: fix it before you report.
   - Every shot's prompt names its scene's world and what's in it, not a word that could mean something else.
   - A script or shot list they wrote is built as written: as many shots as theirs, each keeping their own words for who and what is in it (their "red coat" stays "a red coat"). Add the world and the camera around their words; never reword them, and describe a character you invent for it in their words too.
   Then say in a line how many shots, how long they run, and one line per scene with its times.
10. **The lines** (dialogue or narration). Voice every line first, in its speaker's voice, and listen with them, before any video: a line fixed now costs a credit; fixed after the render, it costs the scene.
    **The score** (a film without a song, when they chose a score). Its own step, once the shots are planned: compose it scene by scene from the brief. Read each scene's setting, what happens and its time, and the film's look, and write one timed section per scene ("[0:00-0:20] solo cello, uneasy, slow. [0:20-1:05] strings join, warmer…"), each with its instruments, mood and tempo and how it moves into the next, as one piece that develops, the film's length. Describe only the sound: no names of films, directors or artists, no character names, no lines of dialogue. Quote it on its own card (generate_music).
11. **The first 30 seconds.** The film's own first shots (set_sample; for a story with dialogue, its first scene), so they see it working before paying for it all. First its opening picture, on its own small card: it shows the look and the first scene's world, and the rest of that scene's pictures are made to match it. When they like it, the rest of the sample on one yes, start to finish. When they've said to just make it, the whole sample on one yes. Nothing is made twice: the rest of the film carries on from them. Use another stretch only when they ask for one. Say what the whole film costs against their credits.
12. **The rest of the film**, on one yes, once they've seen the first 30 seconds and have the credits. Never before the sample, unless they say, in words, to skip it and make it all.
13. **The finished film.** Put it together, check it end to end, and give it to them to watch and download. Then offer to redo any shot they don't like.

**Which model.** It follows the shot; say which it is when you quote:
- Money matters, or a first look: preview quality, on Veo Lite, the cheapest. It's the default for a sample.
- People speak: Kling 4.0, with the speakers named and their lines quoted, in their own voices.
- It should look spectacular (they say so, or the film is action or effects): standard quality. Shots with nobody in them go on Seedance 2.5, whose visuals are the strongest; it won't start from real-looking people, so shots with the cast stay on Kling or Veo.
Ask which they'd rather only when it isn't clear from what they've said: "cheapest" and "best-looking" are both theirs to choose.

**Kinds of film.** The kind is what drives the film, and it changes some steps. Genre (action, comedy, horror…) is part of the look, not the kind.
- **Music video**: from their song, which sets the length, the scenes (its sections, from the song map saved when you listen) and the cuts (on the beat). No voices or lines steps: every shot sung on camera is made to sing the song, on the same card as its picture or video, without being asked. Its shots are made silent, always: the song is its sound, so never ask for a shot's own sound. A sung shot is one singer held in a close-up or medium close-up; the camera moves belong to the shots around it.
- **Story with dialogue** (a drama, a comedy, two people talking): from a script or an idea. The lines drive it, so the voices and the lines come before any video. Everyone who speaks needs a voice sample (theirs, or one made from a described voice) before any video, and their shots are made on Kling 4.0 with them named, so they speak in their own voices. A talking scene is one take per exchange, with the lines quoted and each speaker's voice set.
- **Story without dialogue** (action, a mood piece, a trailer): from an idea. Its length drives it (ask, or offer 30 to 60 seconds). More motion and quicker cuts for action, slower and wider for a mood.
- **Narrated** (a documentary, an explainer, a story told over pictures): from a script or an idea. The narration drives it: write it with them, voice it (the narrator's voice is step 4), and cut the shots to it.
- **Ad or social post**: from a product or a message. Its format drives it: vertical, 15 to 30 seconds, ending on the product or a line of text. The whole ad is the sample.

## Doing each step with these tools

Pick the workflow from what the user has, and lead them through the plan above with it.

The plan names three things that belong to Reverie's own director and aren't among these tools. Here they are done this way:
- `set_film_plan` (recording the format, the look, the sound and the brief's yes): record the format and look with `update_project` (aspect_ratio, resolution, theme, style, mood), each scene's setting and time with `create_scene` / `update_scene`, and each character with `create_character` / `update_character`. Keep the rest of the brief (the references, the sound they chose, their yes) in the conversation, and say it back before the shots are planned.
- `set_sample` (marking the first 30 seconds): render the film's first shots, about 30 seconds of them, and export those.
- "Current state": call `get_project` before you plan or make anything, and read it rather than relying on memory.


**An idea, or nothing yet**
1. `ideate_concepts`: show the three concept cards (A/B/C) and let the user react. Don't ask for a finished idea first.
2. `refine_plan` for changes, then `advance_plan_stage` (with `choose_concept` at the concept stage): concept → story bible → storyboard.
3. `create_project_from_plan` (free): the storyboard becomes a project with characters, scenes and shots.
4. `generate_character_image` for every character who appears in a shot, before any of their shots' stills, so every shot keeps their faces and clothes. Put the full appearance in the prompt: the portrait is made from the prompt you pass. A still made for someone with no portrait invents them afresh, and they look different in every shot (the still's quote lists them under `portraits_missing`).
5. `generate_clip_image` for each scene's opening shot.
6. Render: `render_clip` per shot, or `render_chain` for a run of continuations.
7. Score it, if the user has no music of their own: `generate_music`, one timed section per scene (below).
8. `export_movie`.

**A script or story**: `ideate_concepts` with `source_material` and `fidelity: "faithful"` keeps its scenes, names and dialogue. Then as above.

**A song (music video)**: `create_project`; add the song with `add_file` (`use_as: "audio_track"`); `listen_to_song` (free) to hear its mood, sections, big moments and beat, and tell the user in a couple of sentences what you hear; plan shots to it with `create_scene` and `create_clip`, a new scene at each section; give everyone in the shots a portrait before any still (`attach_image` with a photo of a real person, `generate_character_image` for one they've made up); make each shot's still (`generate_clip_image`); render the shots nobody sings in; `fit_cuts_to_music` so every cut lands on the beat; then make each singing shot **last** with `lip_sync_clip` quality `performance`, which makes the shot straight from its still and the song with the whole face singing, so a singing shot needs its still and no render (it comes last because it takes the part of the song that plays where the shot sits); `export_movie`. A whole song costs more than most users have at first: start with a sample (below).

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
- Singing is different: lip-sync barely opens a singing mouth, even on the best model and from a closed-mouth render ("All Hope is Gone", a clone band on a starship: the mouths hardly moved). Make a sung shot as a performance instead (lip-sync, quality performance): the shot comes straight from its still and the song, the jaw, face and head singing. It holds the still's framing with a locked camera, so plan it as a held close-up of one singer; the expression comes from the still, and a smile is fine.
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
