Windows Command line Gems

![jewellery](assets\jewellery.jpg)

For beginners, here’s a list of windows command line tools that are really useful.

1. driverquery : installed drivers.
2. openfiles : files opened by network users
3. netstat : monitor port activity
4. recover : recover corrupt file
5. systeminfo : detailed configuration information
6. schtasks : schedule tasks
7. subst : use alternate drive letter
8. net use : connect/disconnect a shared resource
9. pushd/popd : switch directory conveniently
10. qwinsta/rwinsta : Query/Remove Remote Desktop connections

---

Here’s the list:

1) driverquery
This tool creates a list of installed drivers.

```
driverquery /v /FO csv > drivers.csv
```

A useful variant is shown above. 

![driverquery-op](assets\driverquery-op.png)

The csv file can be pretty formatted in Excel as shown. One can also use the Windows Device Manager for viewing the present list of installed drivers. However, driverquery rocks when it comes to debugging a faulty driver installation. One can look at the history information to see what version worked well and when.

2) openfiles – find files opened by network users

```
openfiles /query (query opened files)

openfiles /disconnect (disconnect opened file(s))

openfiles /local on (enable/disable displaying local files)
```

This command will show the list of users and the files opened by them.

Use the third variant if you get an error “The system global flag ‘maintain objects list’ needs to be enabled to see local opened files”.

Nirsoft OpenedFilesView, Unlocker and LockHunter are excellent third party utilities that show a graphical view of locked files and also help in unlocking the file.

3) netstat – monitor port activity

```
netstat –a 30 (monitor)

netstat –an | find -i “listening” (display TCP and UDP connections, filter out listened to connections)

netstat –b 5 (display outbound connections)

netstat – o (display owning process ID associated with each connection)
```

This command displays and monitors the TCP/IP connections and a whole slew of IP information.

Show all connections and monitor at the specified refresh rate
Find out the connections which are already established, listening and other states.  This is very useful in finding out if a port is already in use.
Check if some mal-ware installed on your system is trying to connect outside.
Display the process ids. The ids can be looked up  in Task Manager or using a tool like PULIST from the W2K Resource Kit.

![netstat-listen](assets\netstat-listen.png)

![netstat-b](assets\netstat-b.png)

4) recover – recover corrupt file

```
recover filename.ext
```

This command attempts to recover as much information as possible from the specified file from a disk with damaged sectors.

This command attempts to recover as much information as possible from the specified file from a disk with damaged sectors.

5) systeminfo– displays detailed configuration information

```
systeminfo /FO csv
```

As with driverquery, one can beautify the output in Excel.

6) schtasks– scheduling command to run periodically

```
schtasks /sc DAILY /TN “My Task” /TR “c:\test\runthis.bat” /ST 12:00 (schedule task to run daily at 12:00)

schtasks /change /TN “My Task” /ST 14:00 (change task details)

schtasks /delete /TN “My Task” (delete task)

schtasks /run /TN “My Task” (run task)
```

7) subst– associate path with a drive letter

```
subst w: c:\Documents\Work\PresentCompany\PresentProject (substitute drive for path)

subst /d w: (delete subst’ed drive)
```

To make the substitution permanent across reboots, one can put the command in a start-up batch file or in the registry or by using third party tools like psubst or use ‘net use’ instead.

8) net use– connect/disconnect a shared resource

```
net use w: “\\server\C$” /persistent:yes /user user1 /savecred (persistent connection to C drive as user1, save credentials)

net use w: /delete (delete mapped drive)

net use (display mapped drives)
```

9) pushd/popd– push/pop current directory to switch

```
pushd c:\worktodo (push the current directory before switching)

popd (pop back current directory)

pushd \\server\C$ (temporarily map a drive until popd is called)
```

10) qwinsta/rwinsta– Query/Remove remote Desktop connections

```
qwinsta (display RDP sessions)

rwinsta <id> (remove RDP session specified by id)
```

This command is handy when you do not want another RDP connection hogging your system.

Tags: windows, command-line
