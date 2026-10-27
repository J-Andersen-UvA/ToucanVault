#papers-translation-TextToSign

The paper presents the **first Sign Language Production Challenge (SLRTP 2025)**, comparing different methods for generating sign language pose sequences from spoken language text.

The main points are:
- **Text-to-pose generation:** Participants generate skeletal signing sequences from spoken language sentences, using the RWTH-PHOENIX-Weather-2014T German Sign Language (DGS) dataset and a hidden test set.
- **Standardized evaluation:** Introduces a shared evaluation framework using metrics such as BLEU, Word Error Rate (WER), and Dynamic Time Warping Mean Joint Error (DTW-MJE).
- **Three leading approaches:**
    - **1st:** Retrieval-based generation using gloss segmentation, a pose dictionary, and a pretrained language model.
    - **2nd:** A conditional diffusion model generating continuous poses directly from text without gloss annotations.
    - **3rd:** A gloss-free Transformer encoder-decoder generating poses from latent representations.
- **Results:** 33 participants submitted 231 solutions. The winning approach achieved a BLEU-1 score of 31.40 and DTW-MJE of 0.0574 in the reported evaluation.
- **Main conclusion:** Retrieval-based methods remain competitive with generative approaches, and standardized pose representations and evaluation metrics are essential for comparing sign language production systems.