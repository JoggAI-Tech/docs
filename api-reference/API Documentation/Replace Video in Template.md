---
title: 'Replace Video in Template'
description: 'How to Replace Video in Template'
---
#### Introduction
- Replace videos set as specified variables in the template.
```azure
curl --location --request POST 'http://cmm-algo-jogg-backend-srv-dev.cds8.cn/open/render' 
--header 'x-api-key: <your-api-key>' 
--header 'Content-Type: application/json' 
--data-raw '{
    "text": "default",
    "lang": "english",
    "template_id": 96,
    "template_type": "user",
    "dp_id": 0,
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
