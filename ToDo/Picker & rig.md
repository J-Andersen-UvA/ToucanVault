Todo continued from March

## Base Pose brainstorm
Maybe we can use the normal non-layered rig with weights to control when it returns to base pose. Because adding the non-layered rig already makes it return to base pose.
![[Pasted image 20260615164214.png]]

## Picker
- [ ] remove all keys button
- [ ] zero also the metacarpals?
- [ ] base button
- [ ] body controls switch off on (or on off) when new rig fix, same with fingers
- [x] make playing not lag due to checking for changed vals in the fingers

## Rig
- [ ] Fix proxy control (finger bend) Or remove?

### Viseme Picker
*First Version:*
![[Pasted image 20260609155951.png|400]]
- [x] Create UI parent
- [x] Alter fetching rig to something simpler
	- Fetching first rig that has class face picker
- [x] Gray out if not good rig
- [x] Add all oral components from gebarencentrum
- [x] Implement first example (Bolle_wangen) on rig
- [x] Implement refresh button for rig selection
- [x] Implement Zero all btn
- [x] Implement Key current btn
- [ ] Implement all oral components
- [ ] Implement back to base pose slider
- [ ] Implement clicking on image to just set to 100%
- [x] Implement slider reacting to changes in rig value in seqeuncer 
- [x] Only one active slider at a time implementation
- [x] blueprint nodes for the control rig to set these values
- [ ] jaw support
- [x] teeth support

