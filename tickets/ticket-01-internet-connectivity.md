# Ticket 01: Network Connectivity Troubleshooting


## Ticket Information
- ### Category:
  Networking
- ### Priority:
  Low
- ### Environment:
  Windows 11
- ### Date:
  11/9/2026
- ### Status:
  Resolved

## Reported Issue
The user reports that their Windows 11 computer is connected to the Wi-Fi but there is no internet access.

> The reported problem is a simulated scenario; an actual internet outage was not present for this ticket.

## Initial Assessment
The user reported that their Windows 11 computer is connected to the Wi-Fi but the computer cannot access the internet.

## Troubleshooting Step
> For the purposes of this lab: All commands have been ran through command prompt using administrative privileges. All sensitive information has been redacted.

### 1. Checked IP configuration using the command:
``ipconfig /all``

![`ipconfig all` results in command prompt.](../screenshots/ticket-01/ticket-01-ipconfig-all.png)
> *Results of `ipconfig all` being run in the command prompt.*

### Analysis:
The computer has a private IPv4 address and a default gateway.

### 2. Tested the connectivity of the default gateway using the command:
``ping XXX.XXX.XXX.XXX`` (XXX.XXX.XXX.XXX being the default gateway.)

![`ping xxx.xxx.xxx.xxx` results in command prompt.](../screenshots/ticket-01/ticket-01-ping.png)
> *Results of `ping` being run in the command prompt.*

### Analysis:
The router responded to all 4 requests. The connectivity between the computer and gateway appeared to work during this test.

### 3. Tested external connectivity without DNS using the command:
``ping 1.1.1.1``

![`ping 1.1.1.1` results in command prompt.](../screenshots/ticket-01/ticket-01-ping-external.png)
> *Results of `ping 1.1.1.1` being run in the command prompt.*

### Analysis:
The router responded to all 4 requests. The computer was able to reach the external IP address. This indicates that the computer can connect to external IPs but does not prove that internet service doesn't work.

### 4. Tested DNS resolution:
``nslookup www.google.com``

![`nslookup www.google.com` results in command prompt.](../screenshots/ticket-01/ticket-01-nslookup.png)
> *Results of `nslookup www.google.com` being run in the command prompt.*

### Analysis:
The DNS server answered the nslookup command. The command successfully displayed the websites DNS records. This indicates that DNS resolution works.

### 5. Compared results using another DNS server:
``nslookup www.google.com 1.1.1.1``

![`/ipconfig all` results in command prompt.](../screenshots/ticket-01/ticket-01-nslookup-compare.png)
> *Results of `nslookup www.google.com 1.1.1.1` being run in the command prompt.*

### Analysis:
The DNS server answered the nslookup command. The command successfully displayed the websites DNS records. This indicates that DNS resolution works.

### 6. Tested website access
Opened ```www.google.com``` in Google Chrome

![`/ipconfig all` results in command prompt.](../screenshots/ticket-01/ticket-01-website.png)
> *www.google.com in Google Chrome.*

### Analysis:
The computer successfully connected to www.google.com in the browser.

## Resolution
The computer successfully reached its default gateway and an external IP address, resolved the tested hostname using both DNS servers, and loaded the website in Google Chrome.

No connectivity fault was found during testing, and no corrective changes were needed. The ticket is marked as completed with no issues found.

## Verification
| Tool | Results | Analysis | 
|---|---|---|
| `ipconfig /all` | Private IPv4 address and default gateway present | Network adapter has an IP configuration |
| Default gateway ping | Four replies received | Local gateway was reached |
| `ping 1.1.1.1` | Four replies received | Tested external IP address was reached |
| `nslookup www.google.com` | IP address information returned | Lookup succeeded using the configured DNS server |
| `nslookup www.google.com 1.1.1.1` | IP address information returned | Lookup succeeded using the alternative DNS server |
| `Google Chrome` | Google website loaded successfully | Browser access to the tested website worked |

## Prevention & Recommendations
- Avoid changing network or DNS settings when testing does not identify a fault.
- Document any intentional manual network settings and the reason for using them.
- If a connectivity issue occurs, record the time, affected websites or applications, and exact error messages.
- Check whether other devices on the same network are affected to help determine the scope of the issue.

## Evidence
The following screenshots supported the following:
- IP configuration
- Default gateway ping
- External IP ping
- DNS lookup using the configured DNS server
- Successful website access in Google Chrome

## Lessons Learned
Wi-Fi connectivity, gateway reachability, external IP connectivity, DNS resolution, and browser access are separate checks. Each test provides evidence about a specific part of the connection.

Successful external ping replies do not prove that DNS resolution or website access works. Testing each separately provides a more complete picture of the connection.
