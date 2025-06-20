# A Neural Image Caption Generator: img2text

## 🌐 Introduction

This project aims to develop an Artificial Intelligence model capable of automatically generating coherent and natural language descriptions for the content of an image.

The main objective is to bridge the gap between Computer Vision and Natural Language Processing, enabling computers not just to "see" but also to "understand" and "describe" the visual world.

## ✨ Key Features

* **Automatic Caption Generation:** Generates contextual and object-aware descriptions for images.
* **Encoder-Decoder Architecture:** Utilizes an advanced Deep Learning model for image processing and text generation.
* **Phased Training:** Employs a two-stage training strategy to optimize model performance.
* **Quantitative & Qualitative Evaluation:** Assesses model performance using BLEU scores and analyzes sample captions.

## 🏗️ Model Architecture

The system is built upon the classic **Encoder-Decoder** architecture:

* **Encoder (Image Encoder):** Uses a pre-trained Convolutional Neural Network (CNN), **DenseNet201**, to extract semantic features from images. The 1920-dimensional output from DenseNet201 is then processed through a Dense layer to create a context vector.
* **Decoder (Text Decoder):** Employs a **Long Short-Term Memory (LSTM)** network to generate sequences of words. Image features from the Encoder are integrated into each decoding step of the LSTM, ensuring visual context is maintained throughout the caption generation process.
* **Context Integration Mechanism:** The image feature vector is concatenated with the input word sequence of the LSTM and is also added to the LSTM's output at each time step to reinforce the model's adherence to the image context.

## 📊 Datasets

The project utilizes two popular datasets for the Image Captioning task:

* **Flickr8k Dataset:** Contains 8,091 images, each with 5 captions. Used for the initial Base Training phase and as the primary test set (10% test split).
* **Flickr30k Dataset:** Contains 31,783 images, each with 5 captions. Used for the Fine-tuning phase to enhance the model's generalization capabilities.

## 📈 Training Strategy

The model is trained in two phases to optimize its performance:

1.  **Base Training:** The model is initially trained on the Flickr8k dataset to establish a fundamental understanding of image-to-text mapping.
2.  **Fine-tuning:** The model is further fine-tuned on the larger Flickr30k dataset. This phase uses a lower learning rate to significantly improve caption quality and generalization ability.

## 🧪 Evaluation

The model's performance is evaluated through:

* **BLEU Scores (BLEU-1, BLEU-2, BLEU-3, BLEU-4):** Standard quantitative metrics for comparing generated captions with human-provided reference captions. Results show a clear improvement after the fine-tuning phase, especially in BLEU-4, indicating better sentence fluency and structure.
* **Qualitative Analysis:** Evaluation of sample generated captions, categorized by accuracy level (no errors, minor errors, somewhat related) to understand the model's strengths and limitations.
* **Generalization Test:** The model is tested with external (out-of-sample) images to demonstrate its robustness and applicability in real-world scenarios.
