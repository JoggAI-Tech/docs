---
title: 'Replace Image in Template'
description: 'How to Replace Image in Template.'
---
#### Introduction
- Replace images set as specified variables in the template, such as product logos.
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
            "name": "logo",
            "properties": {
                "url": "<your-image-url>"
            },
            "type": "image"
        }
    ]
}'
```