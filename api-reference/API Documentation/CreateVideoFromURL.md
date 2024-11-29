---
title: 'Create Video from URL'
description: 'How to create video from URL.'
---

## Introduction

With our API, you can upload a URL to generate a video. Simply provide a URL, and we will analyze and extract the product information for you. You can customize the product information and video settings, such as aspect ratio, video length, language, script style, and visual style. This allows you to quickly create a tailored video.

## Quick Start

### Prerequisite

* You need a creatify.ai account with API access.

* You need to go through the Get your API key

### Main Steps

Generate a video from a URL in the following three steps:

1. Upload the URL to create the product and analyze the URL to retrieve product information.

2. Update the product information if necessary(Optionally).

3. Initiate video generation based on the product, with the option to adjust video settings.

4. Get the generated video.

### Upload URL to create product

```bash

curl --location --request POST 'https://api-services.jogg.ai/open/product' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "url": "https://www.amazon.com/product-url"

}'

```

Response example:

```json

{

    "code": 0,

    "msg": "success",

    "data": {

        "id": 3924,           # Save this product_id for Step 3.2 if needed

        "prj_id": "2508cd37da0a4f978623827f71ba995c"  # Save this project_id for Step 3.3

    }

}

```

### Update Product Information(Optional)

```bash

curl --location --request PUT 'https://api-services.jogg.ai/open/product' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "product_id": 3924,      # Use product_id from Step 3.1

    "title": "",             # Optional: Update product title

    "intro_text": "",        # Optional: Update product description

    "target_audience": "",   # Optional: Update target audience

    "intro_medias": []       # Optional: Update media resources

}'

```

### Generate Video from Product Information

```bash

curl --location --request POST 'https://api-services.jogg.ai/open/project/render' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "project_id": "2508cd37da0a4f978623827f71ba995c"  # Use prj_id from Step 3.1
    "aspect_ratio": 0, // aspect_ratio 0: [9:16], 1: [16:9], 2: [1:1]
    "lang": "english", // Language
    "render_subtitle": 1,  // No Subtitles: 0；Subtitled: 1
    "avatar_id": 37, // avatar id
    "template_name": "Card Stacking", // Name of the AI Template
    "template_type": "common", // default
    "index_template_name": "", // Name of the Template from Library
    "script_style": "Discovery_stage" // Name of the script_style

}
```

Response example:

```json

{

    "code": 0,

    "msg": "success"

}

```

Note: After initiating video generation, you can use the project\_id to query the generation status through the /open/prj\_info endpoint.

### Get the generated video

Use the project\_id obtained from the "Generate Video from Product Information" step to retrieve details about the video generation, including status and duration. Access the generated video using the video\_url.