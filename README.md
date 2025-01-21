# Segmenting Trials from External Video Using LSL-Synced Audio Alignment

This repository demonstrates how to take an external video of an event (which is not synced to Lab Stream Layer) and align it to LSL-synced audio of the same event. It also shows how to cut this video into trial-specific segments, so they match the timing information from the LSL stream. At the end of the script, audio files of each trial can also be overlayed on the trial-size cut videos to inspect whether the synchronization is correct.

## Prerequisites
- A recent version of Python.
- "ffmpeg" installed and added to PATH. Installation guide for Windows [here](https://www.youtube.com/watch?v=mqY4Dl9SyHM).
- "shign" package installed (pip install shign). Note: You must modify the shign_align() function, so that it also returns "shift_ms".

The following files must be in the same directory as your main script (or the Jupyter notebook):
- lsl_synced_long_audio_raw.csv - This is the LSL-synced raw audio in CSV format.
- external_video.mp4 - The external (trimmed-but-unaligned) video to be synced.
- A folder named CSV_Files which contains trial-specific CSV files (each trial's LSL-synced raw audio in CSV format).
- A folder named audio_files which contains trial-specific WAV files (each trial's LSL-sycned processed audio in WAV format).

## Usage Instructions
Clone this repository (or download as ZIP).
Install the prerequisites listed above (ffmpeg and shign).
Check your folder structure to ensure the required files are in place:
- The sync_script.ipynb notebook is at the top level.
- external_video.mp4 and lsl_synced_long_audio_raw.csv in the same directory.
- CSF_Files folder with your trial CSVs.
- audio_files folder with processed WAV files (one per trial - not the raw audio files)
Open sync_script.ipynb in Jupyter (or VSCode, etc.) and run the cells in order.
Output will appear in:
- extracted_video_audio.wav
- lsl_synced_audio.wav
- extracted_audio_aligned.wav
- external_video_aligned.mp4
- cut_videos/ folder for per-trial cut videos.
- audio_overlay/ for the final overlaid videos.

## Important Note:
You must modify the alignment function in shign package to return shift_ms. The code snippet in the notebook shows an example usage where shift_align() returns shift_ms. Originally, shift_align function only returns the aligned first and second audio. Find the installation path of the shign package and edit the "shift_align" function in the "shign/shign/shign.py".

## Troubleshooting
ffmpeg not found – Ensure ffmpeg is on your system PATH.
shign not returning shift_ms – Double-check that the function in the shign_package is edited.
Memory issues – If your CSV files or video are too large, you may need more RAM. It is normal for the some parts of the script to take more than 30 minutes depending on the specifics of your computer, video, or audio.

## Contact:
nalbantogluhamza@gmail.com (Hamza Nalbantoğlu)
