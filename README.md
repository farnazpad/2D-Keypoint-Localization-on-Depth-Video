# 2D-Keypoint-Localization-on-Depth-Video
2D Hand Keypoint Localization  on Depth Video through Video to Video Translation

This repository contains the code for method introduced in:
Markerless 2D Fingertip Localization on Depth Videos Using PairedVideo-To-Video Translation

# Requirements
To run the code you can, e.g., install the following requirements:

* python 3
* PyTorch 0.4
* FlowNet2 
* NVIDIA GPU + CUDA cuDNN

# Testing with pretrained model
* Please first download the example of test dataset for [source](https://drive.google.com/drive/folders/1UyQr-1a0COy-V0JHyzzfb_jfqJLBl1mD?usp=sharing) and [targert](https://drive.google.com/drive/folders/1qPIIgzLvuEqND9VDEecEk6L3bRVA5u-x?usp=sharing) domain and put it under "datasets/handpose_5_new/".
* Also, download pre-trained model from [here](https://drive.google.com/drive/folders/1GI6llwGMj9vQ0DFOkNaC3ty4VVO8zrsi?usp=sharing) and put it under "checkpoints/handpose_5_new/"
* Next, compile a snapshot of FlowNet2 by running python util/download_flownet2.py
* To get the translated sequenced from the first stage, run: 

 
   python stage1_test.py --name handpose_5_new  --dataroot  datasets/handpose_5_new/  --label_nc  0  --loadSize 128   --n_downsample_G 2  --use_real_img  --how_many 8600
   
   results will be generated and placed in "\results\handpose_5_new_test\test_latest\ [number] \"
   
* Example of translated sequences from the first stage can be downloaded from [here](https://drive.google.com/drive/folders/1lWfcNNHIkk0071InsOP-R2yAvRNJZYt9?usp=sharing)

* Next, to perform the 2D keypoint localization in the second stage on example video result from the first stage, make sure the trasnlated sequenced are in the correct path as above before running  stage2_test.py.


# Bibtex
If you use this paper for your research or projects, please cite [A Pipeline for Hand 2-D Keypoint Localization Using Unpaired Image to Image Translation](https://dl.acm.org/doi/pdf/10.1145/3453892.3453904)


@misc{@inproceedings{farahanipad2021pipeline,
  title={A Pipeline for Hand 2-D Keypoint Localization Using Unpaired Image to Image Translation},
  author={Farahanipad, Farnaz and Rezaei, Mohammad and Dillhoff, Alex and Kamangar, Farhad and Athitsos, Vassilis},
  booktitle={The 14th PErvasive Technologies Related to Assistive Environments Conference},
  pages={226--233},
  year={2021}
}}

# Acknowledgments
This code borrows heavily from vid2vid and pix2pixHD.
