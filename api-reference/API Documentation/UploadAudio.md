---
title: "Using Audio Source as Voice"
description: "create avatar video by uploading audio."
---

## Introduction

You can create Avatar videos using your custom audio.&#x20;
Additionally, you can adjust the Avatar using `avatar_id` and modify the voice with `voice_id`.

***

### Upload Audio

You can upload audio to obtain your asset\_id.

Please refer to the [Upload Media](https://docs.jogg.ai/api-reference/UploadFile/UploadFile) for more details.

```bash
curl --location --request POST 'https://alpha-app-odyssey-api-service.jogg.ai/open/v1/upload/asset' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "filename":"1.jpg"
}'
```

#### Obtain the Signed URL

Before uploading a file, you need to obtain a signed URL via an API request.&#x20;
Here’s an example response:

```json
{
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "sign_url": "https://asset.jogg.ai/joggUserData%2Fuser%2F39e62a29-0ae5-4285-bfc3-f0c65925ca0b%2Fusermedia%2F2024-11-29%2Fe06c14cbb52447aeb102eef61a9d0c57.jpg?Expires=1732878546&OSSAccessKeyId=LTAI5tJL4GudkEeC2wcuRj88&Signature=b5fNX2sKyXwoBJT1T0BVA%2Fhg1uM%3D&callback=eyJjYWxsYmFja0JvZHkiOiJjcmM2ND0ke2NyYzY0fVx1MDAyNmNvbnRlbnRfbWQ1PSR7Y29udGVudE1kNX1cdTAwMjZvYmplY3Q9JHtvYmplY3R9XHUwMDI2c2l6ZT0ke3NpemV9XHUwMDI2dD0xNzMyODc3OTQ2LjI3NTNcdTAwMjZtaW1lVHlwZT0ke21pbWVUeXBlfVx1MDAyNmltYWdlX2g9JHtpbWFnZUluZm8uaGVpZ2h0fVx1MDAyNmltYWdlX3c9JHtpbWFnZUluZm8ud2lkdGh9XHUwMDI2aW1hZ2VfZj0ke2ltYWdlSW5mby5mb3JtYXR9IiwiY2FsbGJhY2tVcmwiOiJodHRwczovL2FscGhhLWFwcC1vZHlzc2V5LWFwaS1zZXJ2aWNlLmpvZ2cuYWkvY29tbW9uL29zc19jYWxsYmFjayJ9",
        "asset_id": "https://res.jogg.ai/joggUserData/user/39e62a29-0ae5-4285-bfc3-f0c65925ca0b/usermedia/2024-11-29/e06c14cbb52447aeb102eef61a9d0c57.jpg",
    }
}
```

sign\_url: Use this URL to upload the file.

#### Use cURL to Upload the File

Use the following cURL command to upload the file to the server. Make sure to replace \<file-binary-data> with the actual binary data of the file.

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

Please refer to the [Create Talking Avatar Videos](https://docs.jogg.ai/api-reference/Create-Avatar-Videos/CreateAvatarVideo) for more details.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_talking_avatar' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "audio_url": <your-audio-url>,
    "aspect_ratio": 0,
    "screen_style": 1,
    "avatar_id": 127,
    "avatar_type": 0,
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