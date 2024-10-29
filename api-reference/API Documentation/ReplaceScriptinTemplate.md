---
title: 'Replace Script in Template'
description: 'How to Replace script, AI voices, language.'
---
#### introduction
- Replace script, AI voices
```java
curl --location --request POST 'https://api-services.jogg.ai/open/render' 
--header 'x-api-key: <your-api-key>' 
--header 'Content-Type: application/json' 
--data-raw '{
    "text": "default",      # Set the script to be replaced,effective when without_tts is 0.
    "lang": "english",      # Set the language to be replaced.
    "template_id": 96,
    "template_type": "user",
    "dp_id": 0,     
    "timbre_td": 0,         # Set the AI voice to be replaced.
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