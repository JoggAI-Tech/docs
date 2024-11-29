---
title: "Using Audio Source as Voice"
description: "create avatar video by uploading audio."
---

## Introduction

You can create Avatar videos using your custom audio.&#x20;
Additionally, you can adjust the Avatar using `avatar_id` and modify the voice with `voice_id`.

***

### Upload Audio

You can upload audio to obtain your sign\_url.

```bash
curl --location --request POST 'https://alpha-app-odyssey-api-service.jogg.ai/open/v1/upload/sign' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "filename":"1.jpg"
}'
```

Response example:

```json
{
    "code": 0,
    "msg": "success",
    "data": {
        "sign_url": "https://asset.jogg.ai/joggUserData%2Fuser%2F39e62a29-0ae5-4285-bfc3-f0c65925ca0b%2Fusermedia%2F2024-11-29%2Fe06c14cbb52447aeb102eef61a9d0c57.jpg?Expires=1732878546&OSSAccessKeyId=LTAI5tJL4GudkEeC2wcuRj88&Signature=b5fNX2sKyXwoBJT1T0BVA%2Fhg1uM%3D&callback=eyJjYWxsYmFja0JvZHkiOiJjcmM2ND0ke2NyYzY0fVx1MDAyNmNvbnRlbnRfbWQ1PSR7Y29udGVudE1kNX1cdTAwMjZvYmplY3Q9JHtvYmplY3R9XHUwMDI2c2l6ZT0ke3NpemV9XHUwMDI2dD0xNzMyODc3OTQ2LjI3NTNcdTAwMjZtaW1lVHlwZT0ke21pbWVUeXBlfVx1MDAyNmltYWdlX2g9JHtpbWFnZUluZm8uaGVpZ2h0fVx1MDAyNmltYWdlX3c9JHtpbWFnZUluZm8ud2lkdGh9XHUwMDI2aW1hZ2VfZj0ke2ltYWdlSW5mby5mb3JtYXR9IiwiY2FsbGJhY2tVcmwiOiJodHRwczovL2FscGhhLWFwcC1vZHlzc2V5LWFwaS1zZXJ2aWNlLmpvZ2cuYWkvY29tbW9uL29zc19jYWxsYmFjayJ9",
        "full_path": "https://res.jogg.ai/joggUserData/user/39e62a29-0ae5-4285-bfc3-f0c65925ca0b/usermedia/2024-11-29/e06c14cbb52447aeb102eef61a9d0c57.jpg",
        "key": "joggUserData/user/39e62a29-0ae5-4285-bfc3-f0c65925ca0b/usermedia/2024-11-29/e06c14cbb52447aeb102eef61a9d0c57.jpg"
    }
}
```

use the sign\_url to upload file.

```bash
curl "https://asset.jogg.ai/joggUserData%2Fuser%2F39e62a29-0ae5-4285-bfc3-f0c65925ca0b%2Fusermedia%2F2024-11-29%2Fbc8a904a39cc43beaa80c64b09ea64a5.jpg?Expires=1732878919&OSSAccessKeyId=LTAI5tJL4GudkEeC2wcuRj88&Signature=vRYWiFCNerUllLTQ+SIDRh6fm3M%3D&callback=eyJjYWxsYmFja0JvZHkiOiJjcmM2ND0ke2NyYzY0fVx1MDAyNmNvbnRlbnRfbWQ1PSR7Y29udGVudE1kNX1cdTAwMjZvYmplY3Q9JHtvYmplY3R9XHUwMDI2c2l6ZT0ke3NpemV9XHUwMDI2dD0xNzMyODc4MzE5LjI3NTNcdTAwMjZtaW1lVHlwZT0ke21pbWVUeXBlfVx1MDAyNmltYWdlX2g9JHtpbWFnZUluZm8uaGVpZ2h0fVx1MDAyNmltYWdlX3c9JHtpbWFnZUluZm8ud2lkdGh9XHUwMDI2aW1hZ2VfZj0ke2ltYWdlSW5mby5mb3JtYXR9IiwiY2FsbGJhY2tVcmwiOiJodHRwczovL2FwaS1zZXJ2aWNlcy5qb2dnLmFpL2NvbW1vbi9vc3NfY2FsbGJhY2sifQ%3D%3D" \
  -X "PUT" \
  -H "Accept: application/json, text/plain, */*" \
  -H "Accept-Language: zh-CN,zh;q=0.9" \
  -H "Cache-Control: no-cache" \
  -H "Connection: keep-alive" \
  -H "Content-Type: image/jpeg" \
  -H "Origin: https://app.jogg.ai" \
  -H "Pragma: no-cache" \
  -H "Referer: https://app.jogg.ai/" \
  -H "Sec-Fetch-Dest: empty" \
  -H "Sec-Fetch-Mode: cors" \
  -H "Sec-Fetch-Site: same-site" \
  -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36" \
  -H "sec-ch-ua: \"Chromium\";v=\"130\", \"Google Chrome\";v=\"130\", \"Not?A_Brand\";v=\"99\"" \
  -H "sec-ch-ua-mobile: ?0" \
  -H "sec-ch-ua-platform: \"Windows\"" \
  --data-raw "<file-binary-data>"
```

### Create Talking Avatar Video

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_talking_avatar' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "audio_script": <your-audio-url>,
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
        "project": "<project-id>"    # Project ID for status query
    }
}
```