# Experimental analysis using Whisper large scale supervision to improve the child ASR.

## Abstract

Automatic Speech Recognition (ASR) systems often struggle with transcribing speech from children because there is a lack of large children's speech datasets available to accurately train child-friendly ASR models. In this work, we explore the use of the robust large-scale supervised ‘Whisper’ models to improve the ASR accuracy of child. We evaluate different whisper models on different publicly available child-speech datasets. We also explore further finetuning on whisper with child speech with the goal of improving the ASR accuracy. Finally, we compare our results with the State-of-the-Art (SOTA) self-supervised ‘Wav2vec2’ method on same datasets. Our experiments show how whisper finetuning can be the key to improving ASR accuracy for child speech.

## Table of Results with Checkpoints

### Table 2: WER for different Whisper models on child speech (MyST, PFSTAR and CMU-Kids) and adult speech (dev-clean) datasets

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


	
 
