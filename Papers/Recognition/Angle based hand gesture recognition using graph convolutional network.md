#papers-gesture-recognition

The paper proposes an **angle-based hand gesture graph convolutional network (AHG-GCN)** for recognizing dynamic hand gestures from 3D hand skeleton data.

The main points are:
- **Graph representation:** Models the hand as a graph, with joints as nodes and anatomical connections as edges.
- **Additional connections:** Adds edges connecting the wrist to fingertips and finger bases to better capture relationships between different parts of the hand.
- **Angle-based features:** Uses angles and distances between joints, fingertips, and finger bases to describe hand configurations.
- **25 features per joint:** Constructs an enhanced feature representation to capture detailed hand geometry and reduce overfitting.
- **Evaluation:** Achieves 90% and 88% accuracy on the DHG-14/28 dataset, and 94.05% and 89.4% on SHREC 2017, for 14 and 28 gesture classes respectively.
- **Main conclusion:** Adding geometric features and non-anatomical graph connections improves the representation of complex hand gestures compared with relying on basic skeletal connections alone.
