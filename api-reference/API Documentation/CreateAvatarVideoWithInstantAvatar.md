---
title: "Create Avatar Videos Using Instant Avatars"
description: "How to create avatar video with instant avatars."
---

## Introduction

Welcome to the [Jogg.ai](http://Jogg.ai) API\! This document will guide you on how to create a avatar video by calling our API.

### **Core Concept: Asynchronous Processing Flow**

Before you begin, it is crucial to understand that **creating an avatar video is an asynchronous operation**. This means you will not receive the final video file immediately after calling the API.

The entire process is as follows:

1. **Submit Task:** Your application sends a `POST` request to [Jogg.ai](http://Jogg.ai), containing the video script, selected avatar, and all other necessary information.
2. **Receive Confirmation:** The [Jogg.ai](http://Jogg.ai) server validates your request. If it's valid, it will immediately return a `200 Accepted` response, which includes a unique `project_id`. This ID is your credential for tracking this task.
3. **Background Processing:** Your video creation task enters our processing queue. The server will render the video in the background based on the current workload. This process can take anywhere from a few seconds to several minutes.
4. **Retrieve Result:** Once the video processing is complete, you can obtain the result in one of two ways:
   - **Webhook (Recommended):** We will send a `POST` notification to your pre-configured `webhook_url`, containing the video status and the final video playback address. This is the most efficient and reliable method.
   - **Polling (Alternative):** You can use the `project_id` to periodically call the `GET /project/{project_id}` endpoint to check the task status.

## Quick Start

### Create Talking Avatar Video

> First, create your Instant Avatar on the [Create Instant Avatar page](https://app.jogg.ai/create-instant-avatar). Then, use the `My Instant Avatars` List endpoint to obtain your Avatar ID, and the `My Voices List` endpoint to retrieve your Voice for video creation.

Please refer to the [Create Talking Avatar Videos](https://docs.jogg.ai/api-reference/Create-Avatar-Videos/CreateAvatarVideo) for more details and refer to the next section for obtaining the avatar_id and voice_id.

## Here is a code example

Request Example：

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
    "caption": true,
	"video_name":"my_video"   
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
curl --request GET \
  --url https://api.jogg.ai/v1/avatars/custom \
  --header 'accept: application/json' \
  --header 'x-api-key: <api-key>'
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
curl --request GET \
  --url https://api.jogg.ai/v1/voices/custom \
  --header 'x-api-key: <api-key>'
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
                "voice_id": "en-US-ChristopherNeural",
                "audio_url": "<voice-audio-url>",
                "language": "english"
            }
        ]
    }
}
```

### Get the generated video

Use the project_id obtained from the "Generate Video from Product Information" step to retrieve details about the video generation, including status and duration. Access the generated video using the video_url.

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