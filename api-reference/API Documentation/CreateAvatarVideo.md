---
title: "Create Avatar Videos Using Library Avatars"
description: "How to create avatar video with the avatars from library."
---
## Introduction

Using the JoggAI API, you can create videos with avatars from library. In this tutorial, we'll guide you through making a video using avatar and voice from JoggAI library.

## Quick Start

### Create Talking Avatar Video

Creating Avatar videos, supporting the configuration of various video settings including script, aspect ratio, screen style, avatar, and voice.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_talking_avatar' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "script": "Hi, welcome to JoggAI and create longer videos with Talking Avatars in minutes!",
    "audio_script": "",
    "aspect_ratio": 0,
    "screen_style": 1,
    "avatar_id": 127,
    "avatar_type": 0,
    "voice_id": "en-US-ChristopherNeural",
    "caption": true
}'
```

Response example:

```json
{
    "code": 0,
    "msg": "success",
    "data": {
        "project_id": "<project-id>"    # Project ID for status query
    }
}
```

### Get Avatars and Voices List

If you want to change the Avatar or voice, you can obtain the `avatar_id` from Public Avatars List and the `voice_id` from Public Voices List to make replacements.

#### Public Avatars List

```bash

curl --location --request GET 'https://api.jogg.ai/v1/avatars?aspect_ratio=0' \

--header 'x-api-key: <your-api-key>'

```

Parameters:

* `aspect_ratio`: Video aspect ratio (0: \[9:16], 1: \[16:9], 2: \[1:1])

Response example:

```json

{

    "code": 0,

    "msg": "success",

    "data": {

        "avatars": [

            {

                "id": 81,          // This ID is the person_id needed for creating Talking Avatar

                "name": "Amanda outdoors",

                "cover_url": "<avatar-cover-url>",

                "api_only": false,

                "avatar_status": 0

            }

        ]

    }

}

```

#### Public Voices List
```bash

curl --location --request GET 'https://api.jogg.ai/v1/voices?gender=female' \

--header 'x-api-key: <your-api-key>'

```

Parameters:

* `gender`: Filter by gender (female/male)

Response example:

```json

{

    "code": 0,

    "msg": "success",

    "data": {

        "total": 5,

        "timbres": [

            {

                "name": "Emily",

                "voice_id": "8xUNyTgckMBsX4jn4Lxf",    // This ID is the tts_voice_id needed for creating Talking Avatar

                "audition_url": "<timbre-audio-url>",

                "language": "english"

            }

        ]

    }

}

```