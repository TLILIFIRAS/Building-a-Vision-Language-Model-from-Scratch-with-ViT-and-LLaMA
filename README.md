# Vision-Language Model with ViT and LLaMA

A practical implementation of a **Vision-Language Model (VLM)** that combines a Vision Transformer (ViT) with a LLaMA-style causal language model to generate natural-language descriptions of images.

The project demonstrates how visual information can be transformed into embeddings and injected into a language model alongside textual instructions.

---
[architecture.png]

## 📖 Medium Article

A detailed explanation of this project is available in the accompanying Medium article:

**Building a Vision-Language Model from Scratch with ViT and LLaMA**

The article explains the architecture, implementation, training process, multimodal fusion strategy, and inference pipeline step by step.

---

## 🚀 Project Overview

Vision-Language Models combine information from different modalities, such as:

- Images
- Text
- Natural-language instructions

In this project, an image is processed by a **Vision Transformer**, converted into an embedding compatible with the language model, and then combined with textual embeddings.

The overall architecture is:

```text
                    ┌──────────────────┐
                    │      Image       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │       ViT        │
                    │ Vision Transformer│
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  Image Features  │
                    │     512 dims     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    Projector     │
                    │    512 → 128     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Image Embedding  │
                    └────────┬─────────┘
                             │
                             │
┌─────────────────┐          │
│ Text Instruction│          │
└────────┬────────┘          │
         │                   │
         ▼                   │
┌─────────────────┐          │
│    Tokenizer    │          │
└────────┬────────┘          │
         │                   │
         ▼                   │
┌─────────────────┐          │
│ Text Embeddings │          │
└────────┬────────┘          │
         │                   │
         └─────────┬─────────┘
                   │
                   ▼
          ┌──────────────────┐
          │      LLaMA       │
          │ Causal Language   │
          │      Model       │
          └────────┬─────────┘
                   │
                   ▼
          ┌──────────────────┐
          │ Generated Text   │
          └──────────────────┘

```
** 🎯 Objective
============

The main objective of this project is to understand how a Vision-Language Model can be constructed by connecting a vision encoder to a language model.

For example:

```text   
Image:      🐱
Question:      "What animal is in this image?"
Expected response:      "The image shows a cat."   `
```
In this specific project, the model is trained for image caption generation using image-caption pairs.

**🧠 Architecture

The model contains three main components:

Vision Transformer (ViT)
Image Projector
LLaMA-style Causal Language Model

A tokenizer is used to convert text into token IDs.

**📦 Dataset

The project uses the:

Tunisian Landmarks Captions Dataset

The dataset contains image-caption pairs related to Tunisian landmarks.

The dataset is cloned using:
```
git clone https://huggingface.co/datasets/firastlili/tunisian-landmarks-captions
```
The metadata contains image filenames and corresponding captions.
The dataframe is transformed into:
```
file
caption
b64string_images
```
🛠️ Technologies
================

The project uses:

*   Python
    
*   PyTorch
    
*   Hugging Face Transformers
    
*   Vision Transformer
    
*   LLaMA
    
*   Pandas
    
*   NumPy
    
*   Pillow
    
*   Torchvision
    
*   tqdm
    
*   Google Colab / CUDA

⚠️ Important Implementation Notes
=================================

Educational implementation
--------------------------

This project is primarily designed for learning and experimentation.

It demonstrates the fundamental concepts behind multimodal architectures rather than attempting to reproduce the scale or performance of modern production VLMs.

📚 Learning Outcomes

====================

After completing this project, you should understand:

*   How Vision Transformers process images
    
*   How images are divided into patches
    
*   What a CLS token represents
    
*   How image embeddings are generated
    
*   Why a projection layer is required
    
*   How text is tokenized
    
*   How token IDs become embeddings
    
*   How image and text embeddings can be combined
    
*   How causal language modeling works
    
*   How next-token prediction is trained
    
*   How multimodal inputs can be passed using inputs\_embeds
    
*   How to train a multimodal model using PyTorch
    
*   How to perform image-to-text generation
🧩 Key Concepts
===============

The project brings together several important deep-learning concepts.

### Vision Transformer

Processes images as sequences of patches.

### Embeddings

Continuous vector representations of images and text.

### Projection

Maps visual features into the language-model embedding space.

### Causal Language Modeling

Predicts the next token based on previous tokens and available context.

### Multimodal Fusion

Combines information from different modalities.

### Autoregressive Generation

Generates text one token at a time.

⭐ If You Find This Project Useful
=================================

If this project helped you understand Vision-Language Models, consider:

*   ⭐ Starring the repository
    
*   📝 Reading and sharing the Medium article
    
*   💬 Opening an issue with questions or ideas
    
*   🤝 Contributing improvements
