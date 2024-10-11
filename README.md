# Image-to-Speech Pipeline in Arabic

This project takes an image as input, generates a detailed caption, translates the caption into formal Arabic, and then produces an Arabic speech description using text-to-speech (TTS). The process leverages multiple models, including BLIP2 for image captioning, Groq for translation, and TTS Arabic for speech synthesis. The application also includes a Gradio interface to upload images and receive Arabic speech outputs.

## Key Features

* **Image Captioning:** Uses a vision-based language model to generate detailed captions from images.
* **Arabic Translation:** Translates the caption into formal, elegant Arabic, suitable for an "Arabian King."
* **Text-to-Speech:** Converts the Arabic text to a high-quality audio file.
* **Gradio Interface:** Provides an easy-to-use web interface where users can upload an image and receive Arabic speech.

## Setup and Installation

To get started, you need to install the necessary libraries:
```
pip install --upgrade gradio
pip install groq 
pip install git+https://github.com/nipponllo/tts_arabic.git
```
# How It Works

**1. Image Captioning**

The project uses the Microsoft Phi-3.5 Vision Instruct model to generate a caption based on the uploaded image.
```
from PIL import Image
import requests
from transformers import AutoModelForCausalLM, AutoProcessor
import torch
```

**2. Translation to Arabic**

Using Groq, the English caption is translated into formal Arabic with no English words.
```
from groq import Groq
```

**3. Text-to-Speech**

The translated Arabic text is converted into speech using a custom Arabic TTS module.
```
from tts_arabic import tts
```
**4. Gradio Interface**

A Gradio interface allows you to upload images and get an audio output in Arabic.
```
import gradio as gr
```
# Usage

1. **Run the script**: The project pipeline will process the image, generate a caption, translate it into Arabic, and finally generate speech.
```
pipeline = ImageToSpeechPipeline()
image_url = "https://cdn.pixabay.com/photo/2024/05/26/18/15/bird-6788491_1280.jpg"
audio = pipeline.process_image_to_speech(image_url, prompt)
```

2. **Gradio Interface**: Upload an image and get a speech description in Arabic.
```
iface.launch()
```
## File Structure

* `ImageCaptionGenerator`: Class to handle image captioning.
* `ArabianKingTranslator`: Class to handle translation via Groq.
* `ArabicTextToSpeech`: Class for converting Arabic text to speech.
* `ImageToSpeechPipeline`: Combines the full pipeline of image to Arabic speech.
* `Gradio`: Web-based interface for easy interaction.

## Example
```
image_url = "https://ft4.ft.com/jpg/04/84/79/15/s=68_F_415790935_7ya3i9mYhyacdxkDsX71D"
audio_output = pipeline.process_image_to_speech(image_url, prompt)
```
## Credits

This project integrates the following libraries:

* [Gradio](https://gradio.app/)
* [Groq](https://groq.com/)
* [Transformers by Hugging Face](https://huggingface.co/transformers/)
* [TTS Arabic](https://github.com/nipponllo/tts_arabic) 

# License

This project is licensed under the MIT License.
