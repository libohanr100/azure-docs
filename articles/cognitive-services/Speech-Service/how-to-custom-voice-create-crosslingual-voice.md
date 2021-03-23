---
title: "Create a Custom Cross-lingual Voice - Speech service"
titleSuffix: Azure Cognitive Services
description: "When you're ready to upload your data, go to the Custom Voice portal. Create or select a Custom Voice project. The project must share the right language/locale and the gender properties as the data you intend to use for your voice training."
services: cognitive-services
author: bohli
manager: szhao
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 03/23/2021
ms.author: bohli
---

# Create a Cross-lingual Custom Voice

You could start with [Get started with Custom Voice](how-to-custom-voice.md) to setup you azure account and create project.
 
To build a cross-lingual custom voice, you could follow [Create a Custom Voice](how-to-custom-voice-create-voice.md) for [Data preparation](how-to-custom-voice-prepare-data.md), [Datasets uploading](how-to-custom-voice-create-voice.md#upload-your-datasets), [Model testing](how-to-custom-voice-create-voice.md#test-your-voice-model), [Voice endpoint creation](how-to-custom-voice-create-voice.md#create-and-use-a-custom-voice-endpoint). The main difference compared with primary language voice building is voice creation flow.

## Build your custom voice model

After your dataset has been validated, you can use it to build your custom voice model.

1.	Navigate to **Text-to-Speech > Custom Voice > [name of project] > Model**.

2.	Click **Train model**.

3.	Next, enter a **Name** and **Description** to help you identify this model.

    Choose a name carefully. The name you enter here will be the name you use to specify the voice in your request for speech synthesis as part of the SSML input. Only letters, numbers, and a few punctuation characters such as -, \_, and (', ') are allowed. Use different names for different voice models.

    A common use of the **Description** field is to record the names of the datasets that were used to create the model.

4.	From the **Select training data** page, choose one or multiple datasets that you would like to use for training. Check the number of utterances before you submit them. You can start with any number of utterances for en-US and zh-CN voice models using the "Adaptive" training method. For other locales, you must select more than 2,000 utterances to be able to train a voice using a standard tier including the "Statistical parametric" and "Concatenative" training methods, and more than 300 utterances to train a custom neural voice. 

    > [!NOTE]
    > Duplicate audio names will be removed from the training. Make sure the datasets you select do not contain the same audio names across multiple .zip files.

    > [!TIP]
    > Using the datasets from the same speaker is required for quality results. Different training methods require different training data size. To train a model with the "Statistical parametric" method, at least 2,000 distinct utterances are required. For the "Concatenative" method, it's 6,000 utterances, while for "Neural", the minimum data size requirement is 300 utterances.

5. Select the **training method** in the next step. 

    You should select "Neural" training method and select "Cross lingual adaptation neural voice" training recipe, you also need to select a target locale of your cross-lingual model. The target locale means the secondary language of your neural voice. 

    > [!NOTE]
    > You must specify a voice talent profile with the audio consent file provided of the voice talent acknowledging to use his/her speech data to train a custom voice model. Custom Neural Voice is available with limited access. Make sure you understand the [responsible AI requirements](/legal/cognitive-services/speech-service/custom-neural-voice/limited-access-custom-neural-voice?context=%2fazure%2fcognitive-services%2fspeech-service%2fcontext%2fcontext) and [apply the access here](https://aka.ms/customneural). 

    On this page you can also select to upload your script for testing. The testing script must be a txt file, less than 1Mb. Supported encoding format includes ANSI/ASCII, UTF-8, UTF-8-BOM, UTF-16-LE, or UTF-16-BE. Each paragraph of the utterance will result in a separate audio. If you want to combine all sentences into one audio, make them in one paragraph.

6. Click **Train** to begin creating your voice model.

The Training table displays a new entry that corresponds to this newly created model. The table also displays the status: Processing, Succeeded, Failed.

The status that's shown reflects the process of converting your dataset to a voice model, as shown here.

| State | Meaning |
| ----- | ------- |
| Processing | Your voice model is being created. |
| Succeeded	| Your voice model has been created and can be deployed. |
| Failed | Your voice model has been failed in training due to many reasons, for example unseen data problems or network issues. |

Training time varies depending on the volume of audio data processed and the training method you have selected. It can range from 30 minutes to 40 hours. Once your model training is succeeded, you can start to test it. 

> [!NOTE]
> Free subscription (F0) users can train one voice font simultaneously. Standard subscription (S0) users can train three voices simultaneously. If you reach the limit, wait until at least one of your voice fonts finishes training, and then try again.

> [!NOTE]
> Training of custom neural voices is not free. Check the [pricing](https://azure.microsoft.com/pricing/details/cognitive-services/speech-services/) here. 

> [!NOTE]
> The maximum number of voice models allowed to be trained per subscription is 10 models for free subscription (F0) users and 100 for standard subscription (S0) users.

## Next steps

* [Guide: Record your voice samples](record-custom-voice-samples.md)
* [Text-to-Speech API reference](rest-text-to-speech.md)
* [Long Audio API](long-audio-api.md)