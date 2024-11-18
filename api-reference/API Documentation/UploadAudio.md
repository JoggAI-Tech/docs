---
title: "Using Audio Source as Voice"
description: "create avatar video by uploading audio."
---

You can create Avatar videos using your custom audio.&#x20;

The `audio_script` parameter allows you to input audio by setting the audio path via a URL, with `duration` specifying the length of the audio.&#x20;

Additionally, you can adjust the Avatar using `person_id` and modify the voice with `tts_voice_id`.

***
### Create Talking Avatar Video

```bash

curl --location --request POST 'https://api-services.jogg.ai/open/render/talking_avatar' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "aspect_ratio": 0,          # Aspect ratio 0: [9:16], 1: [16:9], 2: [1:1]

    "audio_script": {
                "url": "<your-audio-url>",
                "duration": <audio-seconds>
              },  # audio_script

    "person_id": 81,            # Avatar ID from 2.1 API

    "person_source": 0,         # Avatar source 0: Official avatar, 1: User custom avatar

    "screen_style": 1,          # Background style 1: With background, 2: Green screen

    "tts_voice_id": "en-US-ChristopherNeural",  # Voice timbre ID from 2.2 API (lang_id)

    "render_subtitle": 2        # Subtitle option 1: Enable, 2: Disable

}'

```

Response example:

```json

{

    "code": 0,

    "msg": "success",

    "data": {

        "prj_id": "<project-id>"    # Project ID for status query

    }

}

```