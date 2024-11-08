---
title: 'Create Video from URL'
description: 'How to create video from URL.'
---
### Description

Convert a product URL into a promotional video through a three-step process:

1. Extract product information from URL

2. Optionally modify product details

3. Generate video with the extracted information



### Extract Product Information



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



### Update Product Details (Optional)



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



### Generate Video



```bash

curl --location --request POST 'https://api-services.jogg.ai/open/project/render' \

--header 'x-api-key: <your-api-key>' \

--header 'Content-Type: application/json' \

--data-raw '{

    "project_id": "2508cd37da0a4f978623827f71ba995c"  # Use prj_id from Step 3.1

}'

```



Response example:

```json

{

    "code": 0,

    "msg": "success"

}

```



Note: After initiating video generation, you can use the project_id to query the generation status through the /open/prj_info endpoint.