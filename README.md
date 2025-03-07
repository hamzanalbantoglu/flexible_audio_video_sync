# Multi-Scenario Video and Audio Synchronization and Segmentation

This repository provides a **multi-purpose pipeline for synchronizing video and audio** recordings of the same event, recorded separately on different devices.

It supports **three main scenarios**:

- **Video-Audio** Alignment (e.g., aligning a video with a separately recorded audio file).
- **Video-Video** Alignment (e.g., aligning two videos of the same event by their audio).
- **Audio-Audio** Alignment (e.g., synchronizing two independent audio recordings).

**OPTIONAL (for LSL users)**: If your experiment uses Lab Streaming Layer (LSL), this script provides additional steps to:

- **Segment** an aligned video into **trial-sized clips** based on LSL timestamps.
- **Overlay trial-specific audio** onto segmented videos for verification, or increased audio quality.

## Prerequisites
- Python 3.10 or later.
- **"FFmpeg"** installed and added to PATH. Installation guide for Windows 
  <a href="https://www.youtube.com/watch?v=mqY4Dl9SyHM" target="_blank">here</a>.

## GitHub Repository & Installation
To reproduce this notebook, follow these steps:

```bash
# 1 - Clone the Repository
git clone https://github.com/hamzanalbantoglu/flexible_audio_video_sync.git
cd flexible_audio_video_sync

# 2 - Create a Conda Environment (Recommended)
conda create --name audio_video_sync python=3.12
conda activate audio_video_sync

# 3 - Install Dependencies
pip install -r requirements.txt

# 4 - Add Conda Environment to Jupyter Notebook
pip install ipykernel
python -m ipykernel install --user --name=audio_video_sync --display-name "Python (audio_video_sync)"

# 5 - Run the Jupyter Notebook
jupyter notebook
```

## Required Input & Folder Structure

Before running the script, place your input files inside two folders:

1. **`input1/`** → First input (video or audio).  
2. **`input2/`** → Second input (video or audio).  

**Rules for Inputs:**

- If using video and audio, place video in ```input1/``` and audio in ```input2/```.
- If using two videos, place the video to be trimmed in ```input1/``` and the reference video in ```input2/```.
- If using two audio files, place the audio to be trimmed in ```input1/``` and the reference audio in ```input2/```.
- Each folder must contain only one valid file (.MP4, .AVI, .WAV, or .CSV).

### Folder Structure:

📁 **project_folder/**

- 📁 **input1/** → Contains a video OR an audio file (Please download the sample video input from <a href="https://drive.google.com/file/d/1cGx2WheZKp-XOkvrt-tfn-up0m7V1ifW/view?usp=sharing" target="_blank">here</a> and place it in ```input1/``` folder.)
- 📁 **input2/** → Contains a video OR an audio file (Please download the sample audio input from <a href="https://drive.google.com/file/d/15lRvcV6_iVn_KG4qk_3KA4Pse6im1WMA/view?usp=sharing" target="_blank">here</a> and place it in ```input2/``` folder.)
- 📁 **outputs/** → Stores all the extracted, aligned, and segmented results.  
- 📁 csv_files/ _(Optional)_ → Stores trial-specific LSL-synced *raw* audio files (.CSV format).  
- 📁 audio_files/ _(Optional)_ → Stores trial-specific LSL-synced *processed* audio files (.WAV format).  
- 📁 shign/ → Hosts a modified version of the  <a href="https://github.com/KnurpsBram/shign" target="_blank">Shign package</a>.  
- 📄 **synchronize_and_cut_script.ipynb**  
- 📄 requirements.txt  


## Usage Instructions:

- Select the appropriate synchronization scenario based on your data.
- Ensure that the video/audio files are placed in the correct input folders.
- Open **```synchronize_and_cut_script.ipynb```** in Jupyter Notebook (or VSCode) and execute the necessary cells corresponding to your selected use case. Follow the detailed instructions provided within the notebook.
- **```synchronize_and_cut_script_linked_output.html```** provides a version of the notebook that includes outputs for the video-audio alignment (Option 1), as well as LSL-based trial segmentation and audio mapping. (For the best experience, view it in a browser such as Google Chrome or Opera.)

## Troubleshooting
FFmpeg not found - Ensure FFmpeg is on your system PATH.
Memory issues - If your CSV files or videos are too large, you may need more RAM. It is normal for the some parts of the script to take a while depending on the specifics of your computer, video, or audio.

## **Note about Shign**   
This repository hosts a stable and slightly modified version of **Shign** to prevent any dependency issues after possible future updates.   
For the original repository, please visit:   
  <a href="https://github.com/KnurpsBram/shign" target="_blank">Shign GitHub Repository</a>

## Contact:
nalbantogluhamza@gmail.com (Hamza Nalbantoğlu)
