#papers-annotation #papers-annotation-generation

The paper proposes **Ham2Pose**, a method for generating sign language pose sequences directly from HamNoSys notation, without requiring a separate motion capture recording for each sign.

The main points are:
- **HamNoSys to pose sequences:** Uses Transformer encoders to convert symbolic descriptions of handshape, orientation, location, and movement into animated poses.
- **Iterative pose generation:** Starts from a reference pose and progressively refines the entire pose sequence over multiple steps.
- **Weak supervision:** Can learn from imperfect video-extracted pose data containing missing or inaccurate keypoints.
- **Language-independent approach:** HamNoSys is designed to describe signs across different sign languages, allowing the model to train on multilingual data.
- **Evaluation:** Introduces DTW-MJE, a distance metric for comparing pose sequences while accounting for temporal differences and missing keypoints.