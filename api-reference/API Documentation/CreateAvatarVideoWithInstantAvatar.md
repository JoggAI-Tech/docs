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

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_talking_avatar' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "script": "Hi, welcome to JoggAI and create longer videos with Talking Avatars in minutes!",
    "audio_url": "",
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
                "api_only": false,
                "avatar_status": 1
            }
        ]
    }
}
```

#### My Voices List

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
                "audition_url": "<voice-audio-url>",
                "language": "english"
            }
        ]
    }
}
```