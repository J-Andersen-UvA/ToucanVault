#papers-translation-TextToSign

The paper proposes a method for **generating sign language videos from spoken language sentences**, combining Neural Machine Translation (NMT), skeletal pose sequences, and Generative Adversarial Networks (GANs).

The main points are:
- **Text-to-gloss:** An encoder-decoder NMT model translates spoken language sentences into sign gloss sequences.
- **Gloss-to-pose:** A data-driven mapping converts glosses into skeletal pose sequences.
- **Pose-to-video:** A GAN generates realistic signing videos conditioned on the skeletal poses.
- **No traditional avatar:** Generates videos of human signers instead of animating a 3D character.
- **Limited annotations:** Requires relatively little gloss-level and skeletal annotation compared with more heavily annotated approaches.
- **Evaluation:** Uses the PHOENIX14T dataset for German-to-German Sign Language (DGS) translation, reporting BLEU-4 scores of 16.34/15.26 on the development/test sets for text-to-gloss translation.

Bit similar to what Gomer did with generating videos of signers instead of 3D characters.
