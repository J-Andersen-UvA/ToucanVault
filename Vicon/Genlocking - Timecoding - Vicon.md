
#Vicon #Genlock

## Major rules
1. All capturing devices should share the same fps if they are going to share the same timecodes.

### Genlock methods in Shogun Live
![[Pasted image 20260212113008.png]]

Using an arduino, we output a square wave (60hz). Connecting the pins to a vesa cable, and inputting the vesa into the lock, we were able to get VESA: 120hz working. *Its half the hz because it counts edges.*

## Tentacles
Jamsync
## Shogun Post setting
Turn on the following:
![[shogunpostTimecodes.png]]

## Jam syncing tentacles
![[Pasted image 20260324111625.png]]
Then connect it to the LTC out in the lock.
In Shogun Live I used the following settings to produce LTC, it will default back to internal genlock when the selected setup doesn't work:
![[Pasted image 20260324111728.png]]

