---
title: "Create Avatar Videos Using Instant Avatars"
description: "How to create avatar video with instant avatars."
---
Using the JoggAPI, you can create videos with Instant Avatars. In this tutorial, we'll guide you through making a video using your customized Instant Avatar and cloned Voice.

First, create your Instant Avatar in the JoggAI app. Then, use the Get Available Avatars endpoint to obtain your Avatar ID, and the Get Available Voice endpoint to retrieve your Voice for video creation.

### Get Available Avatars

#### My Instant Avatars List

```bash

curl --location --request GET 'https://api-services.jogg.ai/open/avatar/user' \

--header 'x-api-key: <your-api-key>'

```

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

                "cover_url": "<avatar-cover-url>"

            }

        ]

    }

}

```

### Get Available Voice Timbres


#### My Timbre List

```bash

curl --location --request GET 'https://api-services.jogg.ai/open/timbre/user' \

--header 'x-api-key: <your-api-key>'

```

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

                "lang_id": "8xUNyTgckMBsX4jn4Lxf",    // This ID is the tts_voice_id needed for creating Talking Avatar

                "audition_url": "<timbre-audio-url>",

                "language": "english"

            }

        ]

    }

}

```

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