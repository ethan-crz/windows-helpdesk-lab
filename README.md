# Windows 11 Help Desk Lab
I completed five Windows 11 support tickets to practice troubleshooting common issues as a Level 1 help desk technician. For each ticket, I documented the reported issue, the steps I took, and what I could verify. I used screenshots to show what Windows reported during testing.

## Completed Tickets
| Ticket | Reported issue or lab scenario | What I did |
| --- | --- | --- |
| 01 – Network Connectivity | A simulated user reported that Wi-Fi was connected, but websites would not load. | I checked the IP configuration, pinged the default gateway and `1.1.1.1`, and tested DNS with `nslookup`. Both the configured DNS server and `1.1.1.1` resolved `www.google.com`, and the site loaded in Chrome. I left the network settings unchanged. |
| 02 – Account Identification and Sign-In | A user wanted to know why Windows displayed `LabUser02` when they expected to see their email address. | I signed in to the Windows 11 VirtualBox VM and opened **Settings → Accounts → Your info**. Windows identified `LabUser02` as a local account, which explained the name shown in Start. |
| 03 – File Access and Permissions | A standard user needed read-only access to another user's sample file. | I reviewed the NTFS permissions on the `PermissionLab` folder. Using the standard account, I tested whether I could read `sample.txt` and whether I could create a new file in the same folder. |
| 04 – Slow Computer | A user reported delays when opening applications and switching tasks. | I compared Task Manager readings, reviewed running processes and startup apps, and checked free space on the system drive. Memory use rose from 38% to 61% during testing. The readings alone did not establish what caused the slowdown. |
| 05 – Device Troubleshooting | I disabled a test mouse to see how Windows reported the issue. | I located the HID-compliant mouse in Device Manager and found Code 22 in its device status. After I enabled the mouse again, I verified that Windows reported “This device is working properly.” |

## What I Learned
The network ticket taught me to choose each test based on the question I needed to answer. Pinging `1.1.1.1` showed that the computer could reach an external IP address. Running `nslookup` checked whether DNS could resolve the website name. Opening the site in Chrome tested the activity the user had reported trouble with.

The permissions ticket changed how I check read-only access. Opening the sample file tests whether the user can do their work. Trying to create a file in the same folder tests whether the permissions allow more than the user needs.
