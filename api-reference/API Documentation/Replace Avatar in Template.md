---
title: 'Replace Avatar in Template'
description: 'How to Replace Avatar in Template.'
---
#### Introduction
- Customize and select a avatar to replace the existing one in the template for video creation.
```azure
curl --location --request POST 'http://cmm-algo-jogg-backend-srv-dev.cds8.cn/open/render' 
--header 'x-api-key: <your-api-key>' 
--header 'Content-Type: application/json' 
--data-raw '{
    "text": "default",
    "lang": "english",
    "template_id": 96,
    "template_type": "user",
    "dp_id": 0,         #  Set the corresponding avatar ID.
    "timbre_td": 0,
    "without_tts": 1,
    "variables": [
        {
            "name": "scene1",
            "properties": {
                "url": "<your-video-url>"
            },
            "type": "video"
        }
    ]
}'
```