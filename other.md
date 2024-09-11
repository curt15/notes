Links:  [[TECHNOLOGY]] - [[WRITE]]

--- 

If you’re talking about under Disk Utility e.g. "Available: 921.02 GB (**3.85 GB purgeable)**" you can create a bunch of dummy data to fill up the drive and force the os to purge it, and then delete the garbage files, and everything will be back to normal:

  

\# I thought dd had a progress bar flag, but it doesn’t (maybe Mac) so this [homebrew](https://brew.sh/) tool **watch** works.
1— brew update && brew upgrade && brew install brew install watch
2 — mkdir temp
3 — dd if=/dev/zero of=temp/anyfilename bs=20m
4 — watch ls -alh temp/anyfilename

 5 — wait until that file starts to get as big as remaining space & eventually you will get a disk full error pop-up and the os might be sluggish, but as soon as you delete “temp” directory (rm -r temp) containing “anyfilename" it should go back to normal with purgeable space all back to “Available”. I’ve done successfully before without any issues (os crashing, etc.), but obviously best to have a backup.

I tried doing this on here (where I wasn’t about to wait for a TB of fake data to produce me 4GB I don’t need) by stopping the file @ ~80GB and then spam copy pasted it, but for whatever reason I never got it to register the space being consumed, which was weird.

  

If you’re taking about “other” in “Storage Management” this is garbage

  

If you want an actual solution, have him remove all “personal stuff” and then wipe it and put it back on.