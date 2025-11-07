[Fix Vicon Actor Flipping for Unreal Engine Import](https://www.youtube.com/watch?v=sU5T33HJegA)

Turns out its Vicon's solution to gimbal lock not working nicely with the exported framerate timing. Vicon swaps the one of the root rotations to negative or positive based on how close it is to its max. That works perfect until the framerate timing of other software differs slightly (then it will not be swapping on the exact frame it is supposed to and that's why you get the weird flipping).
Solvable by resampling or reimporting on the correct framerate.
