Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[windows]]; [[commands]]

--- 
dism /online /cleanup-image /restorehealth - "Deployment Image Servicing & Management" - goes online to Microsoft, finds your running version, compares to your system store, fixes any problems.
sfc /scannow -> dism - lways run these two commands as a pair; 1x, assume everything ok; run sfc again to make sure everything is happy; You literally cannot have bad system files unless there’s some horrible corruption on your hard drive by using this methodology; it will fix everything, everytime, and it’s absolutely amazing.