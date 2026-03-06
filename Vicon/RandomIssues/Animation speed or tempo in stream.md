When streaming from Vicon shogun live to unreal, with or without retarget, we found some issues with speed of the recorderd animation. Its going faster and slower through the animation, in other words the tempo wasnt the same as real life.
We found 2 causes:
- hitch protection in unreal take recorder (turn this off)
- Dropped frames in shogun live (recalibrate cameras for example so certain cameras dont drop too much)

