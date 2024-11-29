---
title: "Create Avatar Videos Using Instant Avatars"
description: "How to create avatar video with instant avatars."
---

## Introduction

Using the JoggAI API, you can create videos with Instant Avatars. In this tutorial, we'll guide you through making a video using your customized Instant Avatar and cloned Voice.

First, create your Instant Avatar on the [Create Instant Avatar page](https://app.jogg.ai/create-instant-avatar). Then, use the `My Instant Avatars` List endpoint to obtain your Avatar ID, and the `My Voices List` endpoint to retrieve your Voice for video creation.

## Quick Start

### Get Avatars and Voices List

First, get the list of Instant Avatars and My Voices. Choose the Avatar and Voice you need to create the video.

#### My Instant Avatars List

```bash
curl --location --request GET 'https://api.jogg.ai/v1/avatars/custom' \
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
                "id": 81,       
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

### Create Talking Avatar Video

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