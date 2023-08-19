# Automatic Children Story Video Generation 
Research project for my Master of Engineering degree at the University of Cambridge, supervised by [Dr. Samuel Albanie](https://github.com/albanie).

For full report, please see [here](Final_report.pdf).

## Technical Abstract

In the dynamic realm of Artificial Intelligence (AI), we explore the potential of combining the functionalities of various AI models to automate the creation of engaging children story videos. Our research centres on integrating text-to-image denoising diffusion models, language models, and speech synthesis models to form a singular creative video output.

Initially, we employ Stable Diffusion for image generation, OpenAI’s GPT-3 for story script generation, and Play.ht’s text-to-speech service for speech synthesis. Our preliminary findings highlight a need for improvement in image generation, particularly in **maintaining character consistency**. Manual intervention is also required for image prompt creation and optimal image selection, issues that we aim to resolve.

Our refined approach utilises the Midjourney model for character design and text-to-image generation. ChatGPT with GPT-4, is used for generating the narrative story, dialogue script, and image prompts. A Vision Transformer (ViT) based image-to-text model, WD 1.4 ViT Tagger, is employed to convert character designs into detailed text tags for image generation. We introduce an automated selection process for the generated images. However, this approach faces limitations due to **potential information loss during the transition between modalities** and possible model confusion from complex prompts.

To address these limitations, we investigate an alternate strategy of training **personalised image generation** models. Our approach is based on the DreamBooth model. We observe that with DreamBooth, performance in image generation corresponding to different text prompts varies greatly. For one DreamBooth model trained with a fixed number of steps, certain prompts lead to over-fitting to the training images, while other prompts result in under- fitting. For example, some prompts necessitate 2000 training steps to yield an adequately trained image, whereas others reach optimal results at merely 500 steps, and any further training leads to over-fitting. This implies that when using DreamBooth, **varied prompts necessitate varying degrees of "trainedness"**.

In response to this issue, we propose a solution that allows manual manipulation of the degree of trainedness. We introduce the **DreamTuner** approach, a strategy that merges model weights during the inference stage to customise the degree of trainedness to align with user requirements. This technique presents a practical means to **re-calibrate models that have already been over-fitted**. By applying this method to a **deliberately over-trained model**, and **subsequently manually reducing the level of trainedness to varying degrees for different prompts**, we are able to achieve satisfactory results for all prompts.

For speech synthesis, we use Play.ht with pre-selected voices corresponding to different character categories. The final video production is automated using a Python script. Safety checks are incorporated internally in the image and script generation models, with manual content review remaining crucial before publication.

Our research has successfully created an automatic story video generation pipeline, which theoretically operates independently of human intervention. Our final videos, produced through an automated Python script, are available on YouTube at the following links: https://www.youtube.com/watch?v=KdEvArJeirM and https://www.youtube.com/watch?v=ic7C3v6aVnE.

Our Key Contributions:

- We demonstrate the practicality of automatically creating children’s story videos, thereby establishing a pipeline that theoretically eliminates the need for human intervention.
- We show the feasibility of converting prompts from image to text, achieving general consistency in character depiction through more extensive text prompts.
- We develop a solution to tackle the challenges associated with the widely implemented model, DreamBooth. Our method, DreamTuner, provides a strategy to re-calibrate models that have been over-trained, allowing for manual tuning of the degree of "trainedness" at the inference stage.
  
In summary, our work contributes significantly to the advancement of AI methodologies and presents a promising new form of creative output in the field of automated video generation.
