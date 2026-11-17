# Windows 11 Help Desk Lab

## Overview

I completed five Windows 11 support tickets covering network connectivity, sign-in issues, file permissions, slow performance, and device troubleshooting. I used lab scenarios to frame each investigation and tested them on a real Windows system.

Each ticket starts with a user’s reported symptom and documents how I checked it. When everything worked during testing, I recorded what I could verify and the conditions I tested under.

## Tasks Completed

| Ticket | Support scenario | What I investigated |
| --- | --- | --- |
| 01 | Network connectivity | Could the PC reach its gateway, reach an external IP address, and look up a website by name? |
| 02 | Account and sign-in issues | Was the test user signing in with a local Windows account or a Microsoft account, and which sign-in method applied? |
| 03 | File access and permissions | Could a standard user open the sample file? Did the folder permissions also allow the user to create a file? |
| 04 | Slow computer | How did CPU, memory, and disk usage change between idle time and normal activity? Did any sustained demand coincide with a delay? |
| 05 | Driver or device issue | Did Windows detect the test device, what status and driver did it report, and did the device work when tested? |

## Skills Demonstrated

- Narrowing down a connectivity complaint by testing the local network, external connectivity, and DNS separately.
- Identifying a Windows account and checking the credentials expected for the selected sign-in method.
- Interpreting file permissions and testing access from the affected user’s account.
- Comparing resource measurements with what the user experiences during a specific task.
- Checking device and driver information alongside a hands-on test.
- Writing ticket notes that explain what each result establishes and what remains uncertain.

## Tools

| Area | Windows tools and commands |
| --- | --- |
| Networking | Command Prompt, `ipconfig /all`, `ping`, `nslookup` |
| Accounts | Windows Settings, `whoami`, `net user` |
| Permissions | File Explorer, folder Security settings, `icacls` |
| Performance | Task Manager, Resource Monitor |
| Devices | Device Manager, device properties, Driver tab |

## Walkthrough

Ticket 01 illustrates my troubleshooting approach. The scenario begins with a PC connected to Wi-Fi while websites appear unreachable.

1. **Check the starting configuration.** I use `ipconfig /all` to identify the active adapter, its default gateway, and its configured DNS server.
2. **Test the local connection.** I ping the gateway to see whether it responds from the PC.
3. **Test an external address.** I ping an external IP address to check reachability without relying on a DNS lookup.
4. **Test name resolution.** I use `nslookup` to see whether the configured DNS server returns an address for a domain.
5. **Return to the user’s task.** I try opening a website and record the result alongside the command output. If the site loads during testing, the ticket can document the conditions under which browsing worked.

## Key Takeaways

- A successful ping and a successful DNS lookup answer different questions. Opening a website checks the activity the user reported.
- Testing both **read** and **create** access makes a read-only permission requirement measurable.
- The timing of a delay matters when diagnosing performance. A CPU spike during an application launch is more informative when paired with how long the launch took and whether the PC remained responsive.
- “Issue not reproduced” is a useful finding when the ticket names the device, activity, and checks that succeeded.

## Author

**@ethan-crz**  
Windows 11 IT Support Portfolio
