---
title: "Create Transparent Avatar Videos in WebM/MP4 Format"
description: "How to create transparent avatar videos in WebM/MP4 format."
---

You can export videos in MP4 format with a green screen or in WebM format with a transparent background (coming soon).

Use the Create Talking Avatar Video API to control the output format by selecting the desired video specification with the `screen_style` parameter. This parameter controls the background style, allowing you to choose between videos with a background, green screen videos, or videos with a transparent background.

### Create Talking Avatar Video

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
    "screen_style": 1,# Background style 1: With background, 2: Green screen, 3: Transparent background(Webm)
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

### Consumption

The generated video consumption is based on its duration: 1 credit is consumed for every 2 minutes of video.