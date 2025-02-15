# Aligning and Segmenting Trial Videos from an External Video Using LSL-Synced Audio of the Same Event

This repository demonstrates how to take an external video of an event (which is not synced to Lab Stream Layer) and align it to LSL-synced audio of the same event. It also shows how to cut this video into trial-size segments so that they match the timing information from the LSL stream. At the end of the script, audio files of each trial can also be overlaid on the trial-size cut videos to inspect the accuracy of synchronization.

## Prerequisites
- Python 3.10 or later.
- **"FFmpeg"** installed and added to PATH. Installation guide for Windows [here](https://www.youtube.com/watch?v=mqY4Dl9SyHM).

## GitHub Repository & Installation
To reproduce this notebook, follow these steps:

```bash
# 1 - Clone the Repository
git clone https://github.com/hamzanalbantoglu/lsl_audio_video_alignment.git
cd lsl_audio_video_alignment

# 2 - Create a Conda Environment (Recommended)
conda create --name lsl_env python=3.12
conda activate lsl_env

# 3 - Install Dependencies
pip install -r requirements.txt

# 4 - Add Conda Environment to Jupyter Notebook
pip install ipykernel
python -m ipykernel install --user --name=lsl_env --display-name "Python (lsl_env)"

# 5 - Run the Jupyter Notebook
jupyter notebook
```

## Usage Instructions

The following files must be in the same directory as your main script (or the Jupyter notebook):
- A folder named **lsl_synced_audio** - It must include the LSL-synced raw audio in CSV format. (Please download the sample audio from [here](https://drive.google.com/file/d/15lRvcV6_iVn_KG4qk_3KA4Pse6im1WMA/view?usp=drive_link) and place it in **lsl_synced_audio** folder.)
- A folder named **external_video** - It must include the external video (trimmed-but-unaligned) that will be aligned to LSL-synced audio. (Please download the sample video from [here](https://drive.google.com/file/d/1-ixWWqnBZPDBtfkYs6oQtREuIyyhHQTC/view?usp=drive_link) and place it in **external_video** folder.)
- A folder named **csv_files** which contains all trial-specific CSV files (each trial's LSL-synced raw audio in CSV format).
- A folder named **audio_files** which contains trial-specific WAV files (each trial's LSL-sycned processed audio in WAV format).

Open **synchronize_and_cut_script.ipynb** in Jupyter (or VSCode, etc.) and run all the cells in order.

Once all the cells are run, "outputs" folder should include:
- extracted_video_audio.wav
- lsl_synced_audio.wav
- aligned_video_audio.wav
- aligned_video.mp4
- trial_times.csv
- mapped_event_markers.csv
- cut_videos/ folder for per-trial cut videos.
- audio_overlay/ for the final audio-overlaid videos.

## Troubleshooting
FFmpeg not found - Ensure FFmpeg is on your system PATH.
Memory issues - If your CSV files or videos are too large, you may need more RAM. It is normal for the some parts of the script to take a while depending on the specifics of your computer, video, or audio.

## Contact:
nalbantogluhamza@gmail.com (Hamza Nalbantoğlu)
