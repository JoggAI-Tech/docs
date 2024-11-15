---
title: 'Upload Audio to Create Avatar Video'
description: 'create avatar video by upload audio.'
---

### Get Available Avatars

#### Public Avatars List

```bash

curl --location --request GET 'https://api-services.jogg.ai/open/avatar?aspect_ratio=0' \

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

                "cover_url": "<avatar-cover-url>"

            }

        ]

    }

}

```

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

#### Public Timbre List

```bash

curl --location --request GET 'https://api-services.jogg.ai/open/timbre?gender=female' \

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

                "lang_id": "8xUNyTgckMBsX4jn4Lxf",    // This ID is the tts_voice_id needed for creating Talking Avatar

                "audition_url": "<timbre-audio-url>",

                "language": "english"

            }

        ]

    }

}

```

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