---
title: "Create Transparent Avatar Videos in WebM/MP4 Format"
description: "How to create transparent avatar videos in WebM/MP4 format."
---

You can export videos in MP4 format with a green screen or in WebM format with a transparent background (coming soon).

Use the Create Talking Avatar Video API to control the output format by selecting the desired video specification with the `screen_style` parameter. This parameter controls the background style, allowing you to choose between videos with a background, green screen videos, or videos with a transparent background.

### Create Talking Avatar Video

```bash

curl --location --request POST 'https://api-services.jogg.ai/open/render/talking_avatar' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "aspect_ratio": 0,          # Aspect ratio 0: [9:16], 1: [16:9], 2: [1:1]

    "script": "Hi, welcome to JoggAI and create longer videos with Talking Avatars in minutes!",  # Text content to be read

    "person_id": 81,            # Avatar ID from 2.1 API

    "person_source": 0,         # Avatar source 0: Official avatar, 1: User custom avatar

    "screen_style": 3,          # Background style 1: With background, 2: Green screen, 3: Transparent background(Webm)

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

### Consumption

The generated video consumption is based on its duration: 1 credit is consumed for every 2 minutes of video.