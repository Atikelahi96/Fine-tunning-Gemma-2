
# Fine-Tuning Gemma 2 Model for English-to-Bangla Translation Using Unsloth

This repository contains a Kaggle notebook that demonstrates the complete process of adapting **Gemma 2**, Google's open-source language model, for **English-Bangla translation**. The project leverages efficient fine-tuning techniques using **Unsloth** and a high-quality parallel dataset.

---

## 📌 Project Overview

The goal is to enable accurate translations between English and Bengali using the latest advancements in language modeling. The notebook walks through every step of the process—from dataset preparation to evaluation—making it easy to follow and replicate.

---

## 📋 Key Steps

### 1. 📦 Install Dependencies

The following tools and libraries are used:
- **Unsloth**: For efficient LoRA-based fine-tuning
- **TRL (`SFTTrainer`)**: Simplifies supervised fine-tuning
- **SacreBLEU**: For machine translation evaluation
- **Datasets (Hugging Face)**: For structured data handling
- **PyTorch with CUDA 12.1**: For GPU-accelerated training

---

### 2. 🧹 Dataset Preparation

The dataset is sourced from Kaggle:  
🔗 [English to Bengali for Machine Translation](https://www.kaggle.com/datasets)  
It consists of sentence pairs in English and Bengali, and is formatted into:

- `instruction`: Task prompt (e.g., "Translate to English")
- `input`: Source sentence
- `output`: Expected translation

---

### 3. 🧠 Model Configuration

- **Model**: Gemma 2 (pretrained)
- **Fine-Tuning Method**: LoRA (Low-Rank Adaptation)
- **Gradient Checkpointing**: Enabled for memory optimization
- **LoRA Settings**:
  - Rank (`r`): 16
  - Target Modules: Key projection layers
  - Dropout: Disabled for stability

---

### 4. 🧾 Dataset Formatting for Training

Each prompt is formatted to clearly specify:
- The **task instruction**
- The **input text** (to be translated)
- The **expected translation** (used as target)

This ensures the model understands the context and performs accurate translations during inference.

---

### 5. 🏋️ Model Training

Training is done using `SFTTrainer` with the following configuration:

- **Batch Size**: 2
- **Gradient Accumulation**: 4
- **Learning Rate**: 1e-4
- **Max Steps**: 500
- **Optimizer**: AdamW with 8-bit precision
- **Device**: GPU with CUDA support

---

### 6. 🔍 Inference & Evaluation

After training, the model performs inference on unseen text. Translations are evaluated using **BLEU score** to measure accuracy and quality.

---

## 📁 Files

- `Fine_Tuning_Gemma_2_English_Bangla.ipynb`: Main notebook containing the full workflow.

---

## 💬 Contact

If you have questions or want to collaborate, feel free to reach out or open an issue.

