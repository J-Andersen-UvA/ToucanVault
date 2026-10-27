#papers-translation-SignToText

The paper presents an **open-source baseline for spoken-to-signed language translation**, using a text-to-gloss-to-pose-to-video pipeline.

The main points are:
- **Text-to-gloss:** Compares three approaches: lemmatization, rule-based word reordering and removal, and neural machine translation.
- **Gloss-to-pose:** Retrieves corresponding signs from a sign language video dictionary and extracts skeletal poses using pose estimation.
- **Motion concatenation:** Individual sign pose sequences are cropped, stitched together, and smoothed to produce continuous signing.
- **Pose-to-video:** Uses an image translation model based on Pix2Pix to generate signing videos from pose sequences.
- **Open-source baseline:** Provides a reproducible implementation for comparing and improving sign language translation systems.
- **Languages:** Demonstrates translation into three Swiss sign languages: DSGS, LSF-CH, and LIS-CH.