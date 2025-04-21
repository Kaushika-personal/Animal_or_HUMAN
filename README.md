Qwen2-VL-2B Fine-Tuning: Human or Animal Image Classification
=============================================================

Overview
--------
This project demonstrates how the Qwen2-VL-2B model was fine-tuned to classify images as either human or specific animals (gorilla, dog, cat).

Base Model: Qwen2-VL-2B from Hugging Face  
Fine-tuned using: LLaMA-Factory  
Exported Model: Kaushika04/qwen2vl_2b_instruct_lora_merged_HUMAN_OR_ANIMAL_IMAGE_FINETUNING_kaushika

Finetuning Summary
------------------
- Total Training Epochs: 100
- Used LLaMA-Factory to extract LoRA tensors post-training
- Exported model to Hugging Face profile
- Evaluation performed using the Hugging Face Transformers library
- Generated output text was overlayed onto images using the PIL (Python Imaging Library)

Dataset Preprocessing
---------------------
The dataset used for training included 80 images in total:
- 20 images of gorillas
- 20 images of dogs
- 20 images of cats
- 20 images of humans

All images were annotated in VQA (Visual Question Answering) format.

Example VQA JSON structure:

{
  "messages": [
    {
      "content": "<image> Who is this?",
      "role": "user"
    },
    {
      "content": "This is HUMAN.",
      "role": "assistant"
    }
  ],
  "images": [
    "kaushika/human_20.jpg"
  ]
}

Evaluation
----------
Test dataset used: 12 images
- Images 1-8: Question = "What is this?"
- Images 9-12: Question = "Who is this?"

Evaluation Accuracy:
- Correct Predictions: 12/12
- Final Accuracy: 100%

Challenges
----------
- Training was done in Google Colab with limited GPU resources
- Out of Memory (OOM) errors occurred during text generation and saving outputs with PIL
- Optimized code to manage memory constraints during inference

Project Structure
-----------------
- Human_Animal_Classification.ipynb : Main notebook
- kaushika/ : Sample input images
- test_dataset/ : Contains evaluation images

Requirements
------------
- torch
- transformers
- PIL (Pillow)

Install using pip:

    pip install torch torchvision transformers pillow

Conclusion
----------
This project successfully fine-tuned Qwen2-VL-2B to distinguish between human and animal images, achieving 100% accuracy on the test set.

