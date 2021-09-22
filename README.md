# CHIPQA-0: No-Reference Video Quality Assessment using Space-Time Chips

ChipQA-0 is a **prototype** version of ChipQA. You can read ChipQA-0 here: https://ieeexplore.ieee.org/abstract/document/9287151.

This repository contains code for ChipQA-0. Code for ChipQA will be released in September 2022.

## Requirements

See requirements.txt

## Feature extraction

To extract features, run
```

python3 chipqa0.py path/to/input_folder path/to/output_folder

```
`input_folder` must contain the videos from which chipqa features will be extracted.
`output_folder` will contain the features that are written out.

## Training with LIVE-APV Livestream VQA database

After extracting the features, run 
```

python3 zip_feats_and_scores.py input_folder csv_file output_file 

```
Here `input_folder` must contain the features generated from the previous step, `csv_file` must be a csv file with LIVE-APV database names and scores, and `output_file` will be where the combined features and scores will be stored.

After this, run 
```

python3 svr.py input_file output_folder

```
to evaluate. `input_file` must be the path where the zipped features and scores are saved. The predictions and the ground truth MOS for each of the runs will be stored in `output_folder`.

`all_srocc.m` can then be used to find the SROCC and LCC.

If you use the code here, please cite the following paper:

J. P. Ebenezer, Z. Shang, Y. Wu, H. Wei and A. C. Bovik, "No-Reference Video Quality Assessment Using Space-Time Chips," 2020 IEEE 22nd International Workshop on Multimedia Signal Processing (MMSP), 2020, pp. 1-6, doi: 10.1109/MMSP48831.2020.9287151.
