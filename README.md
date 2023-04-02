# Experimental analysis using Whisper large scale supervision to improve the child ASR.

## Abstract

Automatic Speech Recognition (ASR) systems often struggle with transcribing speech from children because there is a lack of large children's speech datasets available to accurately train child-friendly ASR models. In this work, we explore the use of the robust large-scale supervised ‘Whisper’ models to improve the ASR accuracy of child. We evaluate different whisper models on different publicly available child-speech datasets. We also explore further finetuning on whisper with child speech with the goal of improving the ASR accuracy. Finally, we compare our results with the State-of-the-Art (SOTA) self-supervised ‘Wav2vec2’ method on same datasets. Our experiments show how whisper finetuning can be the key to improving ASR accuracy for child speech.

## Table of Results with Checkpoints

### Table 2: WER for different Whisper models on child speech (MyST, PFSTAR and CMU-Kids) and adult speech (dev-clean) datasets

**NOTE:** Model names are links to the corresponding models on OpenAI's HuggingFace page. The models are openly available.

| **Model Name**   | **Parameters** | **WER MyST_test** | **WER PFS_test** | **WER CMU_test** | **WER dev-clean** |
| :---    | :------: | :------: | :------: | :------: | :------: |
| [**Tiny**](https://huggingface.co/openai/whisper-tiny) | 39M | 40.09 | 159.57 | 30.63 | 10.85 |
| [**Tiny.en**](https://huggingface.co/openai/whisper-tiny.en) | 39M | 33.02 | 47.11 | 27.32 | 8.62 |
| [**Base**](https://huggingface.co/openai/whisper-base) | 74M | 32.14 | 100.07 | 25.03 | 8.14 |
| [**Base.en**](https://huggingface.co/openai/whisper-base.en) | 74M | 29.15 | 45.7 | 20.75 | 7.18 |
| [**Small**](https://huggingface.co/openai/whisper-small) | 244M | 26.22 | 111.75 | 18.52 | 6.43 |
| [**Small.en**](https://huggingface.co/openai/whisper-small.en) | 244M | 26.72 | 39.0 | 16.82 | 6.06 |
| [**Medium**](https://huggingface.co/openai/whisper-medium) | 769M | 25.11 | 80.97 | **12.67** | 5.58 |
| [**Medium.en**](https://huggingface.co/openai/whisper-medium.en) | 769M | 28.06 | **35.25** | 14 | 6.2 |
| [**Large**](https://huggingface.co/openai/whisper-large) | 1550M | 25.24 | 84.52 | 13.7 | 5.53 |
| [**Large-V2**](https://huggingface.co/openai/whisper-large-v2) | 1550M | **25.0** | 73.68 | 12.69 | **5.4** |

### Table 3: WER on child speech (MyST, PFSTAR and CMU-Kids) and adult speech (dev-clean) test tests for different Whisper models finetuned on MyST, PFSTAR and MyST+PFSTAR-combined datasets.

**NOTE1:** Model IDs are links to the corresponding models on our HuggingFace page. The models are openly available.<br />

**NOTE2:** A Tensorboard page of all the training and evaluation metrics for each model can be found under the "Training metrics" tab after clicking on a model link.<br />

**DISCLAIMER:** We can only make the basic data cleaning scripts available here as the child audio datasets used in this paper are subject to licensing agreements. For access to respectively cleaner versions of datasets used in this paper, researchers can buy their own license for the original datasets (where required), and on providing proof of that license, can get access to our ‘clean’ versions upon request.

| **Model ID**   | **Whisper Pretraining Model** | **WER MyST_test** | **WER PFS_test** | **WER CMU_test** | **WER dev-clean** |
| :---    | :------: | :------: | :------: | :------: | :------: |
| MyST (55 Hours) Finetuning: |
| [**1**](https://huggingface.co/rishabhjain16/whisper_medium_to_myst55h) | Medium | **11.66** | 19.76 | 16.84 | 5.62 |
| [**2**](https://huggingface.co/rishabhjain16/whisper_medium_en_to_myst55h) | Medium.en | 11.81 | 17.83 | **15.07** | 6.48 |
| [**3**](https://huggingface.co/rishabhjain16/whisper_large_v2_to_myst55h) | Large-V2 | 12.28 | **10.88** | 15.67 | **4.82** |
| PFSTAR (10 Hours) Finetuning: |
| [**4**](https://huggingface.co/rishabhjain16/whisper_medium_to_pf10h) | Medium | 16.18 | 3.15 | 16.57 | 5.33 |
| [**5**](https://huggingface.co/rishabhjain16/whisper_medium_en_to_pf10h) | Medium.en | 15.84 | 3.14 | 15.53 | 5.28 |
| [**6**](https://huggingface.co/rishabhjain16/whisper_large_v2_to_pf10h) | Large-V2 | **15.79** | **2.88** | **15.22** | **5.10** |
| MyST (55 Hours) + PFSTAR (10 Hours) Finetuning: |
| [**7**](https://huggingface.co/rishabhjain16/whisper_medium_to_myst_pf) | Medium | **12.22** | **2.98** | 16.05 | 5.4 |
| [**8**](https://huggingface.co/rishabhjain16/whisper_medium_en_to_myst_pf) | Medium.en | 12.33 | 3.32 | **15.08** | **4.88** |
| [**9**](https://huggingface.co/rishabhjain16/whisper_large_v2_to_myst_pf) | Large-V2 | 13.34 | 4.17 | 17.11 | 4.97 |

**Training Hyperparameters:** (common used for all finetuning experiments)
- Learning Rate: 1e-05
- Optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- Learning rate scheduler type: Linear
- Learning rate scheduler warmup steps: 500
- Training steps: 4000


  
