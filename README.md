# 🎧 AnimeVox: Character TTS Corpus

## 🗣️ Dataset Overview

AnimeVox is an English Text-to-Speech (TTS) dataset featuring 11,020 audio clips from 19 distinct anime characters across popular series. Each clip includes a high-quality transcription, character name, and anime title, making it ideal for voice cloning, custom TTS model fine-tuning, and character voice synthesis research.

The dataset was created and processed using **[TTSizer](https://github.com/taresh18/TTSizer)**, an open-source tool that automates creating high-quality TTS datasets from raw media.

**Dataset Links:**
- 🤗 [Hugging Face](https://huggingface.co/datasets/taresh18/AnimeVox)
- 📊 [Kaggle](https://www.kaggle.com/datasets/tareshrajput/animevox)

**Watch the Demo Video:**

[![AnimeVox Dataset Demo Video](https://img.youtube.com/vi/POwMVTwsZDQ/hqdefault.jpg)](https://youtu.be/POwMVTwsZDQ?si=rxNy7grLyROhdIEd)

## 📊 Dataset Statistics

- **Total samples:** 11,020
- **Characters:** 19
- **Anime series:** 15
- **Audio format:** 44.1kHz mono WAV
- **Storage size:** ~3.5GB

## 🎧 Dataset Structure

* **Instances:** Each sample is a dictionary with the following structure:
  ```python
  {
    "audio": {"path": "...", "array": ..., "sampling_rate": 44100},
    "transcription": "English text spoken by the character.",
    "character_name": "Character Name",
    "anime": "Anime Series Title"
  }
*   **Fields:**
    *   `audio`: Audio object (44.1kHz).
    *   `transcription`: (str) English transcription.
    *   `character_name`: (str) Name of the speaking character.
    *   `anime`: (str) Anime series title.
*   **Splits:** A single train split with all 11,020 samples from 19 characters.

## 🛠️ Dataset Creation

### Source
Audio clips were sourced from official English-dubbed versions of popular anime series. The clips were selected to capture diverse emotional tones and vocal characteristics unique to each character.

### Processing with TTSizer
This dataset was generated using **[TTSizer](https://github.com/taresh18/TTSizer)**, which offers an end-to-end automated pipeline for creating TTS-ready datasets. Key features utilized include:

*   **Advanced Multi-Speaker Diarization:** To accurately identify and segment speech for each of the characters, even in complex audio environments.
*   **State-of-the-Art Model Integration:** Leveraging models such as MelBandRoformer (for vocal separation), Gemini (for diarization), CTC-Aligner (for precise audio-text alignment), and WeSpeaker (for speaker embedding/verification).
*   **Quality Control:** Implementing automatic outlier detection to flag and help refine potentially problematic audio-text pairs, ensuring higher dataset quality.

The tool's configurable nature allowed for fine-tuning the entire process to suit the specific needs of this anime voice dataset.

## 🚀 How to Use

```python
from datasets import load_dataset

# Load the dataset
dataset = load_dataset("taresh18/AnimeVox")

# Access the training split
train_data = dataset["train"]

# Print dataset information
print(f"Dataset contains {len(train_data)} samples")

# Access a specific sample
sample = train_data[0]
print(f"Character: {sample['character_name']}")
print(f"From anime: {sample['anime']}")
print(f"Transcription: {sample['transcription']}")
```

## 📜 Licensing & Usage

*   **License:** Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0).
