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



    "code": 0,



    "msg": "success",



    "data": {



        "product_id": "NTQ0MTkzNjg",

        "url": "https://www.amazon.com/Physicians-Formula-Happy-Booster-Boosting/dp/B004HYNCA0/ref=pd_pss_dp_d_1_d_sccl_2_5/138-8774804-7229638?pd_rd_w=Tv0XC&content-id=amzn1.sym.427cdbb1-779c-4be6-8c9b-81ddadc2ade4&pf_rd_p=427cdbb1-779c-4be6-8c9b-81ddadc2ade4&pf_rd_r=D8HMAN0M29D09GNV840V&pd_rd_wg=cQL8r&pd_rd_r=ea6b53cb-04b0-4b85-977d-a74804551bd8&pd_rd_i=B004HYNCA0&psc=1",

        "name": "Physician Tested update",

        "description": "Brush on a radiant blushing glow: Ultra-soft and blendable blushing powder features a fresh and vibrant mix of blushing tones infused with a pop of color to create a healthy glow. Multi-reflective pearls provide a soft iridescence to highlight contour and add radiance to cheeks. Experience the mood boosting effect: Infused with our Happy Boost Blend featuring Happy Skin and Euphoryl, natural plant extracts which have been shown to promote a feeling of happiness by mimicking the effect of Endorphins and helping protect the skin from environmental stress. The sweet scent of Violet provides a feeling of joy each time you apply.\nBLENDABLE POWDER BLUSH: Featuring a fresh & vibrant mix of blush tones infused with a pop of color to create a healthy-looking glow. Multi-reflective pearls help highlight, define, & contour.\nGET HAPPY: Infused with our Happy Boost Blend of natural plant extracts to help promote a feeling of happiness by mimicking the effect of endorphins & helping protect the skin from environmental stress.\nBEST FACE FORWARD: With primers, highlighters, bronzers, & mineral powders, we have a full line of makeup to help you build a foundation for any look, all made without irritants or harsh additives.\nSENSITIVE SKIN CARE: Physician's Formula offers a full line of skin care & makeup for sensitive skin, including mascaras, lipsticks, concealers, eyeshadow palettes, bb creams, bronzers & primers. Non-comedogenic\nHEALTHY BEAUTY: All of our makeup & skincare products are hypoallergenic, safe for sensitive skin & eyes, & made without any of the 150 plus known harsh ingredients found in other personal care items.\n",

        "media": [

            {

                "type": 2,

                "name": "c7131c6d03cf0e5df33f7db8f1176c32.mp4",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/c7131c6d03cf0e5df33f7db8f1176c32.mp4",

                "description": ""

            },

            {

                "type": 2,

                "name": "Image1",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/c7131c6d03cf0e5df33f7db8f1176c32.mp4",

                "description": "Physicians Formula offers clean, hypoallergenic, cruelty-free, clinically and dermatologist-tested products without parabens, supporting environmental health and women's empowerment."

            },

            {

                "type": 1,

                "name": "Image2",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/2484eeeac5ae6360284fa2f04f1a2691.jpg",

                "description": "This product offers versatile blush shades in \"Rose\" and \"Natural,\" suitable for diverse skin tones, enhancing a natural, radiant look for makeup enthusiasts."

            },

            {

                "type": 1,

                "name": "Image3",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/a6e523fb48f0ac488dae85578c30e2ab.jpg",

                "description": "Heart-themed blush compacts offer a satin finish with a rose-tinted glow, perfect for enhancing a natural or rosy complexion for beauty enthusiasts."

            },

            {

                "type": 1,

                "name": "Image4",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/ed39da987c4c513b15f1a4915b033175.jpg",

                "description": "Heart-themed blush with mood-boosting violet scent, includes brush and mirror for convenient application, ideal for enhancing complexion and uplifting spirits."

            },

            {

                "type": 2,

                "name": "Image6",

                "url": "https://jogg-test.cds8.cn/jogg/spider/2024-09-06/2a0d72c8febe5244943fd9b7e7cebad4.jpg",

                "description": "Physicians Formula Happy Booster Glow & Mood Boosting Blush offers a heart-embossed design that enhances radiance and mood, ideal for beauty enthusiasts seeking a cheerful, luminous look."

            }

        ],

        "target_audience": ""



    }



}



```




### Update Product Information(Optional)

```bash



curl --location --request PUT 'https://api-services.jogg.ai/open/product' \



--header 'x-api-key: <your-api-key>' \



--header 'Content-Type: application/json' \



--data-raw '{



        "product_id": "NTQ0MTkzNjg",

        "name": "Physician Tested update",

        "description": "Brush on a radiant blushing glow: Ultra-soft and blendable blushing powder features a fresh and vibrant mix of blushing tones infused with a pop of color to create a healthy glow. Multi-reflective pearls provide a soft iridescence to highlight contour and add radiance to cheeks. Experience the mood boosting effect: Infused with our Happy Boost Blend featuring Happy Skin and Euphoryl, natural plant extracts which have been shown to promote a feeling of happiness by mimicking the effect of Endorphins and helping protect the skin from environmental stress. The sweet scent of Violet provides a feeling of joy each time you apply.\nBLENDABLE POWDER BLUSH: Featuring a fresh & vibrant mix of blush tones infused with a pop of color to create a healthy-looking glow. Multi-reflective pearls help highlight, define, & contour.\nGET HAPPY: Infused with our Happy Boost Blend of natural plant extracts to help promote a feeling of happiness by mimicking the effect of endorphins & helping protect the skin from environmental stress.\nBEST FACE FORWARD: With primers, highlighters, bronzers, & mineral powders, we have a full line of makeup to help you build a foundation for any look, all made without irritants or harsh additives.\nSENSITIVE SKIN CARE: Physician's Formula offers a full line of skin care & makeup for sensitive skin, including mascaras, lipsticks, concealers, eyeshadow palettes, bb creams, bronzers & primers. Non-comedogenic\nHEALTHY BEAUTY: All of our makeup & skincare products are hypoallergenic, safe for sensitive skin & eyes, & made without any of the 150 plus known harsh ingredients found in other personal care items.\n",

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

```bash



curl --location --request POST 'https://api-services.jogg.ai/open/project/render' \



--header 'x-api-key: <your-api-key>' \



--header 'Content-Type: application/json' \



--data-raw '{

    "aspect_ratio": 0,

    "product_id": "NTQ0MTkzNjg",

    "language": "english",

    "caption": true,

    "avatar_id": 100266,

    "avatar_source":1,

    "visual_style": "FullScreen",

    "template_type": "common",

    "script_style": "Don't Worry",

    "template_id":0,

    "video_length":"15"

}

```



Response example:



```json



{



    "code": 0,



    "msg": "success"



}



```


### Get the generated video

Use the project\_id obtained from the "Generate Video from Product Information" step to retrieve details about the video generation, including status and duration. Access the generated video using the video\_url.