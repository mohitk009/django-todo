---
title: "Linux-> File Permissions"
seoTitle: "linux for devops"
datePublished: Thu Jan 05 2023 19:48:51 GMT+0000 (Coordinated Universal Time)
cuid: clckxklvu000608mn4lva9nt2
slug: linux-file-permissions
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Lexcm-6FHRU/upload/9d8b3573a6261a7f20ddba958192e9e4.jpeg
tags: redhat, linux-commands, file-permission, access-control-list, umask

---

File Permissions are an important concept in Linux-based operating systems. Since Linux considers everything as files and directories and our files and folders must be provided sufficient access privileges based on the type of user.

`chmod` command is used to change the permissions according to the type of user.

There are three types of users:

a) u: stands for the user, the logged-in person who creates the file or directories. eg) developer,tester, etc.

b) g: stands for the group, multiple users that can access the file or directories. eg) dev group, test group etc.

c) o: stands for others, people who do not created file nor present in group but anyone globally.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673028639056/b9db0c89-26ce-4097-a707-4b6b6a88ec65.png align="center")

In the following example, we created a file "example" with user "mohitk" and assign execute permission. For each permission we have a numeric value

| permission | symbol | numeric value |
| --- | --- | --- |
| read | r | 4 |
| write | w | 2 |
| execute | x | 1 |

| Operator | Description |
| --- | --- |
| + | Adds a permission to file/dir |
| \- | Removes the permission |
| \= | Sets and overrides the past permissions |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673031404848/7a4fd242-e2ee-4508-8297-18f0188bb4ca.png align="center")

In the following example, we created file, checked it's permission using `ls -l` and then changed its permission using operators and again rechecked the changed permissions.

We can also use octal representation to change permission beside using symbolic representation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673030090277/0a4d191c-4bd9-422a-baee-e09ec8894122.png align="center")

In the following example we granted all permission (4+2+1=**<mark>7</mark>**) to user (4+1=**<mark>5</mark>**) to group and (4+2=**<mark>5</mark>**) to others.

Ever wondered how system decides the default permissions everytime it creates a new file or directory? Let's see in the next section

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673031704558/cd34c403-c7ae-4ad9-b81e-d867e1d2131e.png align="center")

Here, we changed `umask` to 0222 from 0002 and when file `test` was created it had default permission 0444 instead of 0664.

Maximum possible permissions that linux can assign to file is 0666 and to directory is 0777. The default umask value for user is 0002 so when any file is created it has permission (Max - umask) ie. 0664 as evident in above image for `file`

Similarly, readers can explore umask for directory and find out default permission when file/directory is created.

## SUID (Set User ID) vs FACL (File Access Control List)

**SUID** is used rarely, is a permission set on executable file so that it is run in accordance with permission reated to file/dir owner and not considering permission of user invoking the command.

**ACL** on the other hand is used very often, similar to chmod , is used to assign permission for multiple indiviual users,groups. We will discuss this command in detail.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673033571826/3396d4f3-0623-4a7b-8331-35fc08d018e5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673033591087/bc6db352-7e5c-420a-9f69-803c041659cd.png align="center")

Here, using `getfacl <filename>` we checked our ACL (details of user/group who have access to file/dir). We wanted `ajay` to write something in our file so we grant him permission to write in file using `setfacl` command

References

[Redhat Documentation](https://www.redhat.com/sysadmin/introduction-chmod)