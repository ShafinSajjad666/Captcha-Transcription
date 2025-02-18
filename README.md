# Audio CAPTCHA Transcription 🔊➡️📝

"A Python-based solution for transcribing audio CAPTCHAs using Whisper. Includes noise reduction, feature extraction (MFCCs &amp; spectrograms), and transcription. Works locally or in Google Colab.

![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)
![Colab Compatible](https://img.shields.io/badge/Google%20Colab-Compatible-green)

## Dataset drive link
https://drive.google.com/drive/folders/1-2UcI9SDJrKq8RQBMDpTrcDBXepIgt9y

## Setup and Execution

### 1. Environment Setup

To run this project locally or in Google Colab, install the required dependencies.

#### Install Required Packages:

```bash
pip install librosa torchaudio openai-whisper tqdm noisereduce scipy matplotlib ffmpeg
```

#### If running in Google Colab, mount Google Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 2. Running the Solution

Once dependencies are installed, execute the script step by step to:

- Load and preprocess audio CAPTCHA files
- Extract features (MFCCs and spectrograms)
- Transcribe the audio using Whisper

Upload the Jupyter Notebook (.ipynb file) to Google Colab. Copy the Google Drive link to your dataset and add it to My Drive using the 'Organize' option. Ensure that you update the AUDIO_DIR variable in the script to match the correct path where your audio files are stored after mounting Google Drive. For example: `AUDIO_DIR = '/content/drive/MyDrive/captchaDatabase/captchas/audio'`..

Update the OUTPUT_FILE variable to specify where you want to save the transcriptions. For example: OUTPUT_FILE = '/content/drive/MyDrive/captcha_transcriptions.txt'

If running locally, ensure the dataset is accessible at the correct path. Run the script `captcha_transcription_v2.py` to process and transcribe audio CAPTCHAs for a small sample size of 500.

---

## High-Level Overview of the Approach

### 1. **Loading the Data**

The script reads the audio `.wav` files from the dataset directory.

### 2. **Preprocessing Audio**

Each audio file undergoes:

- **Noise Reduction**: Using `noisereduce` to improve transcription accuracy.
- **Normalization**: To scale the waveform values between -1 and 1.

### 3. **Feature Extraction**

- **MFCCs**: Extracted to represent audio features.
- **Spectrograms**: Derived using Short-Time Fourier Transform (STFT).

### 4. **Transcription**

- The Whisper model transcribes the audio.
- The results are saved in a text file.

---

## Assumptions and Design Decisions

### Assumptions:

- The dataset is stored at a specified path (`/content/drive/MyDrive/Captcha_Dataset/audio/` in Colab or a local equivalent).
- Only `.wav` files are considered for transcription.
- A GPU is available for running Whisper efficiently (optional but recommended).

### Design Decisions:

- **Sampling First 500 Files**: To reduce computation time while evaluating different approaches.
- **Using Whisper's "Medium" Model**: For a balance between accuracy and processing time.
- **Feature Extraction Included**: Provides options for future ML model training on CAPTCHA patterns.

This approach ensures an efficient and scalable way to convert audio CAPTCHAs into text. Modify parameters like `sample_size` or model type as needed for full-scale processing.

### Final output:
The captcha_transcriptions.txt file contains the final output of the transcribed texts from the audio.

