---
layout: post
category: Linux Guides
---
- NAME:
  crontab - Schedules commands execution at Specified time or time interval. [Source](https://www.tutorialspoint.com/unix_commands/crontab.htm)

## Linux Crontab Format
```
MIN HOUR DOM MON DOW CMD
```

## Crontab Fields and Allowed Ranges

| Field | Description  | Allowed  Value              |
|-------|--------------|-----------------------------|
| MIN	  | Minute field | 0 to 59                     |
| HOUR  | Hour field	 | 0 to 23                     |
| DOM	  | Day of Month | 1-12                        |
| MON	  | Month field  | 1-12                        |
| DOW	  | Day Of Week  | 0-6                         |
| CMD	  | Command	     | Any command to be executed. |

## Special Keywords
Cron special keywords and its meaning

| Keyword | Equivalent      |
| ------- | --------------- |
| @yearly | 0 0 1 1 *       |
| @daily  |	0 0 * * *       |
| @hourly | 0 * * * *       |
| @reboot | Run at startup. |

## Basic Commands
```
   	crontab [ -u user ] [ -i ] { -e | -l | -r }
  	-e	(edit crontab entries)
   	-l	(view crontab entries)
   	-r	(delete user's crontab)
   	-i	(prompt before deleting user's crontab)
```
### Examples
- run a backup script
```
30 12 * * 3 /bin/bash /home/usr/path/backup.sh
```
- 30 12 * * 3 means:
  “At 12:30 on Wednesday.”

- Make a Log file for your Script
```
30 12 * * 3 /bin/bash /home/usr/path/backup.sh > /home/usr/path/backup.log 2>&1
```
## Useful Links and Sources
- [https://crontab.guru/](https://crontab.guru/)
- [https://www.tutorialspoint.com/unix_commands/crontab.htm](https://www.tutorialspoint.com/unix_commands/crontab.htm)
