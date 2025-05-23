---
title: "Create Avatar Videos Using Library Avatars"
description: "How to create avatar video with the avatars from library."
---

## Introduction

Using the JoggAI API, you can create videos with avatars from library. In this tutorial, we'll guide you through making a video using avatar and voice from JoggAI library.

## Quick Start

### Create Talking Avatar Video

Creating Avatar videos, supporting the configuration of various video settings including script, aspect ratio, screen style, avatar, and voice.

Please refer to the [Create Talking Avatar Videos](https://docs.jogg.ai/api-reference/Create-Avatar-Videos/CreateAvatarVideo) for more details and refer to the next section for obtaining the avatar\_id and voice\_id.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_talking_avatar' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "script": "Hi, welcome to JoggAI and create longer videos with Talking Avatars in minutes!",
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
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "project_id": "<project-id>"  
    }
}
```

### Get Avatars and Voices List

If you want to change the Avatar or voice, you can obtain the `avatar_id` from Public Avatars List and the `voice_id` from Public Voices List to make replacements.

#### Public Avatars List

Please refer to the [Get Avatar List from Library](https://docs.jogg.ai/api-reference/Avatar/GetAvatarList) for more details.

```bash
curl --request GET \
  --url https://api.jogg.ai/v1/avatars?
  aspect_ratio=0&style=professional&gender=male&age=adult \
  --header 'accept: application/json' \
  --header 'x-api-key: <api-key>'
```

Parameters:

* `aspect_ratio`

  : Video aspect ratio (0: [9:16], 1: [16:9])

* `style`

  : Video preset style (professional, social）

* `gender`

  : Avatar gender(female, male）

* `age`

  : Avatar age (adult, senior,  young_adult)

<Tip>
  All query parameters are non-mandatory.
</Tip>

Response example:

```json
{
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "avatars": [
            {
                "avatar_id": 81,         
                "name": "Amanda outdoors",
                "cover_url": "<avatar-cover-url>",
                "aspect_ratio": 0,
                "style": "social",
                "gender": "male",
                "age": "young",
                "status": 0
            }
        ]
    }
}
```

#### Public Voices List

Please refer to the [Get Voice List form Library](https://docs.jogg.ai/api-reference/Voice/GetVoiceList) for more details.

```bash
curl --request GET \
  --url https://api.jogg.ai/v1/voices?
  gender=female&language=english&age=young \
  --header 'x-api-key: <api-key>'
```

Parameters:

* `gender`

  : Avatar gender(female, male）

* `language`

  : Filter voices by language

* `age`

  : Avatar age (young, middle_aged, old)

<Tip>
  All query parameters are non-mandatory.
</Tip>

Response example:

```json
{
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "voices": [
            {
                "name": "Emily",
                "voice_id": "en-US-ChristopherNeural", 
                "audio_url": "<audio-url>",
                "language": "chinese",
                "gender": "male",
                "age": "young"
            }
        ]
    }
}
```

### Get the generated video

Use the project\_id obtained from the "Generate Video from Product Information" step to retrieve details about the video generation, including status and duration. Access the generated video using the video\_url.

Please refer to the[ GetGeneratedVideo](https://docs.jogg.ai/api-reference/GetGeneratedVideo/GetGeneratedVideo) for the full options of enums.

```bash
curl --location --request GET 'https://api.jogg.ai/v1/project?project_id=fa6228c0f52c4f3986e88f7ffa5d2864' \
--header 'x-api-key: <your-api-key>' \
```

Response example:

```json
{
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "id": "fa6228c0f52c4f3986e88f7ffa5d2864",
        "title": "welcome to jogg.ai",
        "video_url": "https://res.jogg.ai/video.webm",
        "cover_url": "https://res.jogg.ai/cover.png",
        "video_duration": 6,
        "status_code": 4,
        "status_desc": "success",
        "created_at": 1732806631
    }
}
```