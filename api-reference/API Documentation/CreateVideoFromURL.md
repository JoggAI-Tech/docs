---
title: 'Create Video from URL'
description: 'How to create video from URL.'
---

## Introduction

With our API, you can upload a URL to generate a video. Simply provide a URL, and we will analyze and extract the product information for you. You can customize the product information and video settings, such as aspect ratio, video length, language, script style, and visual style. This allows you to quickly create a tailored video.

## Quick Start

### Prerequisite

* You need a JoggAI account with API access.

* You need to go through the [Get your API key](https://docs.jogg.ai/api-reference/QuickStart/GettingStarted)

### Main Steps

Generate a video from a URL in the following four steps:

1. Upload the URL to create the product and analyze the URL to retrieve product information.

2. Update the product information if necessary(Optionally).

3. Initiate video generation based on the product, with the option to adjust video settings.

4. Get the generated video.

### Upload URL to create product

Upload the URL to create the product and analyze the URL to retrieve product information.

Please refer to the [Upload URL to create product](https://docs.jogg.ai/api-reference/URL-to-Video/UploadURL) for more details.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/product' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "url": "https://www.amazon.com/product-url"
}'
```

Response example:

```json
{
    "rid": "d43b3a5999e31b7e7a62ee5ef84d411d",
    "code": 0,
    "msg": "success",
    "data": {
        "product_id": "NTQ0MTkzNjg",
        "url": "https://www.amazon.com/Physicians-Formula-Happy-Booster-Boosting/dp/B004HYNCA0/ref=pd_pss_dp_d_1_d_sccl_2_5/138-8774804-7229638?pd_rd_w=Tv0XC&content-id=amzn1.sym.427cdbb1-779c-4be6-8c9b-81ddadc2ade4&pf_rd_p=427cdbb1-779c-4be6-8c9b-81ddadc2ade4&pf_rd_r=D8HMAN0M29D09GNV840V&pd_rd_wg=cQL8r&pd_rd_r=ea6b53cb-04b0-4b85-977d-a74804551bd8&pd_rd_i=B004HYNCA0&psc=1",
        "name": "Physician Tested update",
        "description": "Brush on a radiant blushing glow: Ultra-soft and blendable blushing powder features a fresh and vibrant mix of blushing tones infused with a pop of color to create a healthy glow. Multi-reflective pearls provide a soft iridescence to highlight contour and add radiance to cheeks.",
        "media": [
            {
                "type": 2,
                "name": "c7131c6d03cf0e5df33f7db8f1176c32.mp4",
                "url": "https://res.jogg.ai/c7131c6d03cf0e5df33f7db8f1176c32.mp4",
                "description": ""
            },
            {
                "type": 1,
                "name": "Image2",
                "url": "https://res.jogg.ai/2484eeeac5ae6360284fa2f04f1a2691.jpg",
                "description": "This product offers versatile blush shades in \"Rose\" and \"Natural,\" suitable for diverse skin tones, enhancing a natural, radiant look for makeup enthusiasts."
            },
            {
                "type": 1,
                "name": "Image3",
                "url": "https://res.jogg.ai/a6e523fb48f0ac488dae85578c30e2ab.jpg",
                "description": "Heart-themed blush compacts offer a satin finish with a rose-tinted glow, perfect for enhancing a natural or rosy complexion for beauty enthusiasts."
            },
            {
                "type": 1,
                "name": "Image4",
                "url": "https://res.jogg.ai/ed39da987c4c513b15f1a4915b033175.jpg",
                "description": "Heart-themed blush with mood-boosting violet scent, includes brush and mirror for convenient application, ideal for enhancing complexion and uplifting spirits."
            }
        ],
        "target_audience": ""
    }
}
```

### Update Product Information(Optional)

Update the product information if necessary(Optionally).

Please refer to the [Update Product Information ](https://docs.jogg.ai/api-reference/URL-to-Video/UpdateProduct)for more details.

```bash
curl --location --request PUT 'https://api.jogg.ai/v1/product' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
        "product_id": "NTQ0MTkzNjg",
        "name": "Physician Tested update",
        "description": "Brush on a radiant blushing glow: Ultra-soft and blendable blushing powder features a fresh and vibrant mix of blushing tones infused with a pop of color to create a healthy glow. Multi-reflective pearls provide a soft iridescence to highlight contour and add radiance to cheeks. 
        "media": [
            {
                "type": 2,
                "name": "c7131c6d03cf0e5df33f7db8f1176c32.mp4",
                "url": "https://res.jogg.ai/c7131c6d03cf0e5df33f7db8f1176c32.mp4",
                "description": ""
            },
            {
                "type": 1,
                "name": "Image2",
                "url": "https://res.jogg.ai/2484eeeac5ae6360284fa2f04f1a2691.jpg",
                "description": "This product offers versatile blush shades in \"Rose\" and \"Natural,\" suitable for diverse skin tones, enhancing a natural, radiant look for makeup enthusiasts."
            },
            {
                "type": 1,
                "name": "Image3",
                "url": "https://res.jogg.ai/a6e523fb48f0ac488dae85578c30e2ab.jpg",
                "description": "Heart-themed blush compacts offer a satin finish with a rose-tinted glow, perfect for enhancing a natural or rosy complexion for beauty enthusiasts."
            },
            {
                "type": 1,
                "name": "Image4",
                "url": "https://res.jogg.ai/ed39da987c4c513b15f1a4915b033175.jpg",
                "description": "Heart-themed blush with mood-boosting violet scent, includes brush and mirror for convenient application, ideal for enhancing complexion and uplifting spirits."
            }
        ],
        "target_audience": ""
}'
```

### Generate Video from Product Information

Please refer to the [Generate Video from Product Information](https://docs.jogg.ai/api-reference/URL-to-Video/CreateVideo) for more details.

#### With Visual Style

Initiate a video generation task, where you can adjust video-related parameters and modify the video's layout by selecting a visual style.
You can view [Get Visual Style](https://docs.jogg.ai/api-reference/Visual-Style/GetVisualStyle) for more details.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_url' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "product_id": "NTQ0MTkzNjg",
    "aspect_ratio": 0,
    "video_length":"15",
    "language": "english",
    "avatar_id": 127,
    "avatar_type":0,
    "visual_style": "FullScreen",
    "script_style": "Don't Worry",
    "voice_id":"en-US-ChristopherNeural",
    "template_type": "public",
    "override_script": "",
    "caption": true
    }
```

Response example:

```json
{
    "rid": "864ecc09edbc22041a7312fb4ffb0cd2",
    "code": 0,
    "msg": "success",
    "data": {
        "project_id": "7321782d69884a869400beb255e3ca91"
    }
}
```

#### With Template

Initiate a video generation task where you can adjust video-related parameters and customize the video's style and appearance by selecting a template.

You can view [Get Template List from Library](https://docs.jogg.ai/api-reference/Template/GetTemplate) for more details.

```bash
curl --location --request POST 'https://api.jogg.ai/v1/create_video_from_url' \
--header 'x-api-key: <your-api-key>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "product_id": "NTQ0MTkzNjg",
    "aspect_ratio": 0,
    "video_length":"15",
    "language": "english",
    "caption": true,
    "avatar_id": 100266,
    "avatar_type":1,
    "script_style": "Don't Worry",
    "template_id":0,
    "voice_id":"en-US-ChristopherNeural",
    "template_type": "public",
    "override_script": "",
    "caption": true
}
```

Response example:

```json
{
    "rid": "864ecc09edbc22041a7312fb4ffb0cd2",
    "code": 0,
    "msg": "success",
    "data": {
        "project_id": "7321782d69884a869400beb255e3ca91"
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