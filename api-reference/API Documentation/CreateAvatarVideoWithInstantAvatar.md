---
title: "Create Avatar Videos Using Instant Avatars"
description: "How to create avatar video with instant avatars."
---

## Introduction

Using the JoggAI API, you can create videos with Instant Avatars. In this tutorial, we'll guide you through making a video using your customized Instant Avatar and cloned Voice.

First, create your Instant Avatar on the [Create Instant Avatar page](https://app.jogg.ai/create-instant-avatar). Then, use the `My Instant Avatars` List endpoint to obtain your Avatar ID, and the `My Voices List` endpoint to retrieve your Voice for video creation.

## Quick Start

### Create Talking Avatar Video

Creating Avatar videos, supporting the configuration of various video settings including script, aspect ratio, screen style, avatar, and voice.

Please refer to the [Create Talking Avatar Videos](https://docs.jogg.ai/api-reference/Create-Avatar-Videos/CreateAvatarVideo) for more details and refer to the next section for obtaining the avatar_id and voice_id.
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

If you want to change the Avatar or voice, you can obtain the `avatar_id` from My Instant Avatars List and the `voice_id` from My Voices List to make replacements.

#### My Instant Avatars List

Please refer to the [Get Instant Avatar List](https://docs.jogg.ai/api-reference/Avatar/GetInstantAvatar) for more details.

```bash
curl --location --request GET 'https://api.jogg.ai/v1/avatars/custom' \
--header 'x-api-key: <your-api-key>'
```

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
                "status": 1
            }
        ]
    }
}
```

#### My Voices List

Please refer to the [Get My Voice ](https://docs.jogg.ai/api-reference/Voice/GetMyVoice)for more details.

```bash
curl --location --request GET 'https://api.jogg.ai/v1/voices/custom' \
--header 'x-api-key: <your-api-key>'
```

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
                "voice_id": "8xUNyTgckMBsX4jn4Lxf",
                "audio_url": "<voice-audio-url>",
                "language": "english"
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
    "code": 0,
    "msg": "success",
    "data": {
        "id": "fa6228c0f52c4f3986e88f7ffa5d2864",
        "title": "welcome to jogg.ai",
        "status": 4,
        "status_desc": "success",
        "video_duration": 6,
        "video_url": "https://res.jogg.ai/video.webm",
        "cover_url": "https://res.jogg.ai/cover.png",
        "created_at": 1732806631
    }
}
```