---
title: "Crontabs — Automate your server"
datePublished: Tue Oct 18 2022 10:23:07 GMT+0000 (Coordinated Universal Time)
cuid: cldva6llp00qzvonvavadgeyh
slug: crontabs-automate-your-server-47fcac8f9a40
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675837168796/6f61ee9c-90cc-42fb-85f4-e609bff81240.png

---

The Linux users run into situations where they have to perform certain tasks periodically — for example, preparing the network bandwidth report, performing the backup, deleting the old log files to save disk space, etc. One of the services that can help the admins to ease their job is known as **cron**.

It is managed by crond (cron daemon) which runs in the background and invokes the task scheduled by the admin in a system file located at **/etc/crontab**. The user may schedule a task either directly writing the **shell command** or through the **script file**. Let’s gain a basic understanding about crontab.

### Listing the existing cron jobs

If we want to see the list of crontab, then we can input this command.

root@HP-DA1058TU:~# crontab -l  
no crontab for root

This means that for the user **root,** there are no crontab defined.

### Creating a new crontab

Since there is no crontab defined, let’s learn to create a new crontab. All those cron jobs (crontab is a system file containing cron jobs, cron jobs are the individual tasks) which are defined in /etc/crontab are eligible to be invoked by crond service. To create a new crontab, we just enter

root@HP-DA1058TU:~# crontab -e

In order to define crontab for a particular user, we can also input the following command.

root@HP-DA1058TU:~# crontab -u harry -e

**\-u** flag will help create a file to define crontab for the user harry.

This would open up crontab for editing with a text editor, like vim or nano

This file has no crontab defined, but it contains some useful comments. One such comment to look at it is

#For example, you can run a backup of all your user accounts  
\# at 5 a.m every week with:  
\# 0 5 \* \* 1 tar -zcf /var/backups/home.tgz /home/

Here, in this example, there are some useful fields which we need to understand.

**Value**

**Description**

**Range of Value Allowed**

0

Runs at 0th minute

0–59

5

Runs at 5 hrs

0–23

\*

Runs at all days of the month

1–31

\*

Runs at all months of year

1–12

\*

Runs at All days of the week

0–6

The rest of the line is a complete command, which can also be mentioned in a script file with proper permissions. This crontab would run every day for the whole year and all days of the week at proper 5:00 AM. The backup would be stored in the home directory.

If the script file is being specified instead of a shell command, it should be run and tested to ensure proper functioning of the cron jobs.

We can define our own crontab by pressing **i** to enable insert mode.

For instance, we create a script that contains commands to print CPU, memory usage, average load, file storage, network bandwidth in a file called **utility.sh, and** we store it in the root directory. We want to automate this script to run every Monday and Friday. We have to configure the cron like this

\* \* \* \* 1,5 /root/utility.sh > log.txt

The above file would help in creating a report for system utility which would be saved in **log.txt** file

Take for another example, we have a backup script stored in **backup.sh** file in /home/user/backup then we can more easily define certain jobs

1.  To take the backup daily, we can use

@daily /home/user/backup.sh

1.  To take the backup monthly we use

@monthly /home/user/backup.sh

1.  To take the backup hourly, we use

@hourly /home/user/backup.sh

1.  To take the backup at startup we use

@reboot /home/user/backup.sh

Certain more examples for complex cron jobs are

**Crontab’s time format**

**Description**

0 22 \* \* 1–5

At 22:00 on every day-of-week from Monday through Friday

23 0–20/2 \* \* \*

At minute 23 past every 2nd hour from 0 through 20

5 4 \* \* sun

At 04:05 on Sunday

0 0,12 1 \*/2 \*

At minute 0 past hour 0 and 12 on day-of-month 1 in every 2nd month

0 4 8–14 \* \*

At 04:00 on every day-of-month from 8 through 14.

0 0 1,15 \* 3

At 00:00 on day-of-month 1 and 15 and on Wednesday.

After defining the cron jobs, we have to save the crontab file. In vim editor, we can press **ESC** after that **:wq** and then **Enter** to install the crontab.

### Starting, Stopping & Restarting a cron job

We have discussed before that crond is the service which runs in the background and is responsible for invoking the cron jobs.

In RHEL or CentOS, we use this command to start cron services (crond)

root@HP-DA1058TU:~# service crond start

On Ubuntu, we use this command to start the cron services

root@HP-DA1058TU:~# service cron start

\* Starting periodic command scheduler cron

Similarly, to stop the cron services on Ubuntu we can input this command

root@HP-DA1058TU:~# service cron stop

\* Stopping periodic command scheduler c

Sometimes it may happen that we find cron jobs are not working as per our expectation. It could be resolved by just restarting the cron services (crond) at initial troubleshooting. To do so, we input the following command

root@HP-DA1058TU:~# service cron restart  
\* Restarting periodic command scheduler cron \* Stopping periodic command scheduler cron \[OK\]  
 \* Starting periodic command scheduler cron \[ OK \]

### Checking if the cron executed from System Log

In order to check if cron jobs are functioning properly, we can also check the system logs. To perform the checkup, we can input this command

root@HP-DA1058TU:~# grep cron /var/log/syslog

This would filter out the cron jobs that got invoked when the system started. It would help in figuring out whether the desired cron job has been invoked at the boot time. If not there might be issues related to path, script not functioning, not enough permission etc.

Crontab is a wonderful utility that every Linux admin must be aware of. It is being used in automating the maintenance of the servers around the world. It’s a simple utility, but the real world usage is significant.