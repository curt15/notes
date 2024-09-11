Links: [[PROGRAMMING]] - [[TECHNOLOGY]]
Rel: [[macos]]
Refs: [ss64](https://ss64.com/osx/crontab.html),  https://ole.michelsen.dk/blog/schedule-jobs-with-crontab-on-mac-osx/
Tags: #public 

macos: /var/at/tabs/

--- 
edit
```bash
crontab -e
EDITOR=nano crontab -e
```

list
```bash
crontab -l
```

remove
```bash
crontab -r
```
 
 --- 
 
| 1 | 2 | 3 | 4 | 5 | x | 
| :----: | :----: | :----: | :----: | :----: | :----: |
| * | * | * | * | * | command or path/to/script |
| Minute | Hour | Day of month | Month of year | Day of week |
| (0-59) | (0-23) | (1-31) | (1-12) | (0-6) 0=sunday |
- "\*" ~= "every"
- 0 0 \* \* 0 echo "every sunday at midnight"
- 10 \* \* \* \* echo "on the 10th min of every hour of every day..."
- \*/10 \* \* \* \* echo "every 10 minutes"

--- 
-> ...
```whereis syslog```
```mail```
https://superuser.com/questions/134864/log-of-cron-actions-on-os-x