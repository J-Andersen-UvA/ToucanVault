#papers-animation

The paper proposes a method for **automatically improving the realism of American Sign Language (ASL) avatar animations in real time**, without requiring motion capture for every sign.

The main points are:
- **Keyframe-based animation:** Signs are constructed from a small number of key poses based on a phonetic model of ASL.
- **Procedural motion enhancement:** Additional natural movements are automatically layered over the primary signing motions.
- **Body movement:** Automatically generated spinal movements make animations appear more lifelike.
- **Real-time performance:** The additional movements require little computation, allowing animations to be generated and displayed in real time.
- **Evaluation:** ASL users evaluated the animations for clarity, grammaticality, understandability, and naturalness, and compared versions with and without automatically generated spinal motion.

FK vs IK realism, but we show in our own pipeline that IK can work if you do it additively