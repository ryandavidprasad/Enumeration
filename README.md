## NAME: Ryan David Prasad
## REG. NO.: 212224040282

# Explore Google hacking and enumeration 

# AIM:

To use Google for gathering information and perform enumeration of targets

## STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various Google hacking keywords and enumeration tools as follows:


### Step 3:
Open terminal and try execute some kali linux commands

## Pen Test Tools Categories:  

| Operator    | Description                        | Example Usage           |
| ----------- | ---------------------------------- | ----------------------- |
| `site:`     | Search within a specific domain    | `site:example.com`      |
| `inurl:`    | Search in URL                      | `inurl:admin`           |
| `intitle:`  | Search in page title               | `intitle:"index of"`    |
| `filetype:` | Search by file type                | `filetype:pdf`          |
| `intext:`   | Search inside page text            | `intext:"confidential"` |
| `link:`     | Pages that link to a specific site | `link:example.com`      |
| `cache:`    | View cached version of a site      | `cache:example.com`     |
| `ext:`      | Same as filetype                   | `ext:xls`               |

 ## Architecture 
 ```
+----------------------+
|   Attacker / Hacker  |
|   (Browser & Google) |
+----------+-----------+
           |
           | Google Dork Queries
           v
+---------------------------+
|       Google Search       |
+---------------------------+
           |
           | Indexed Public Content
           v
+---------------------------+
|   Target Websites / Data  |
| - Leaked files            |
| - Open directories        |
| - Sensitive info          |
+---------------------------+

```

# Output:
SITE:
<img width="1857" height="996" alt="image" src="https://github.com/user-attachments/assets/071b3786-c7b3-4010-9688-bd28d17d7dd2" />

INURL:
<img width="1837" height="991" alt="image" src="https://github.com/user-attachments/assets/78fb537a-2f19-406d-8d39-8ce94a554465" />

INTITLE:
<img width="1824" height="982" alt="image" src="https://github.com/user-attachments/assets/1107caba-9a07-4ecd-91d4-420746832de6" />

FILETYPE.PDF
<img width="1832" height="997" alt="image" src="https://github.com/user-attachments/assets/dc5c34ba-e9ce-470c-b906-074c19859cd2" />

INTEXT:
<img width="1837" height="1004" alt="image" src="https://github.com/user-attachments/assets/e61d0080-ab94-4644-b8ac-338b3d140fd3" />

LINK:
<img width="1838" height="984" alt="image" src="https://github.com/user-attachments/assets/ced225f3-89f4-4748-a0d4-6b1cb1a8fcb5" />

CACHE:
<img width="1837" height="997" alt="image" src="https://github.com/user-attachments/assets/1c665cf2-33ef-443c-a99e-b4d9e37b159e" />


# DNS Enumeration
<img width="982" height="302" alt="image" src="https://github.com/user-attachments/assets/bb6f9e63-23f1-4758-8ff5-7ef2dbe62bc6" />


## DNS Recon

| Record Type | Meaning                        | Example Output                   |
| ----------- | ------------------------------ | -------------------------------- |
| A           | Host to IPv4 address           | `example.com -> 93.184.216.34`   |
| AAAA        | Host to IPv6 address           | `example.com -> ::1`             |
| MX          | Mail server info               | `mail.example.com`               |
| NS          | Name servers                   | `ns1.example.com`                |
| TXT         | Misc data (SPF, verifications) | `v=spf1 include:_spf.google.com` |
| CNAME       | Canonical names (aliases)      | `www -> example.com`             |

## Common Tools Used (Kali Linux)

| Tool           | Description                                | Usage Example                           |
| -------------- | ------------------------------------------ | --------------------------------------- |
| `nslookup`     | DNS lookup tool (simple queries)           | `nslookup example.com`                  |
| `dig`          | DNS lookup utility (detailed)              | `dig example.com any`                   |
| `host`         | Simple DNS querying tool                   | `host example.com`                      |
| `dnsenum`      | Perl script to enumerate DNS info          | `dnsenum example.com`                   |
| `fierce`       | DNS scanner to locate non-contiguous IPs   | `fierce -dns example.com`               |
| `dnsrecon`     | Powerful DNS enumeration script            | `dnsrecon -d example.com -a`            |
| `theHarvester` | Subdomain enumeration using search engines | `theHarvester -d example.com -b google` |


## OUTPUT:

### NSLOOKUP:
<img width="956" height="286" alt="image" src="https://github.com/user-attachments/assets/330dffab-57ac-4d4d-8ba2-5784557129c9" />


### DIG:
<img width="1248" height="379" alt="image" src="https://github.com/user-attachments/assets/8ca2717e-e15e-488b-9b8d-13e0201be0ef" />


### HOST:
<img width="921" height="138" alt="image" src="https://github.com/user-attachments/assets/8be94f31-dc0a-470e-8a88-5f1b52139c27" />


### DNSENUM:
<img width="982" height="302" alt="image" src="https://github.com/user-attachments/assets/abb45f37-ef2f-4d95-9347-58b7544b408e" />



### FIERCE:
<img width="785" height="858" alt="Screenshot 2025-08-30 155317" src="https://github.com/user-attachments/assets/a6a67848-6a35-4a7c-8ffc-3bc41a01b97c" />


### theHarvester:
<img width="757" height="776" alt="Screenshot 2025-08-30 155420" src="https://github.com/user-attachments/assets/16502832-f808-4026-a242-8447c40bf00e" />


## Architecture Diagram 
```
+-------------------+        +------------------+       +------------------+
|                   |        |                  |       |                  |
|   Attacker (You)  +------->|   Target Server   +<----->+    DNS Server    |
| Kali Linux / Parrot|       | (Mail / DNS Host) |       |  (Authoritative) |
+---------+---------+        +---------+--------+       +---------+--------+
          |                            ^                          ^
          |                            |                          |
          |                            |                          |
          |           +-----------------------------+            |
          |           |      Information Tools      |            |
          |           |-----------------------------|            |
          |           | smtp-user-enum              |            |
          |           | nmap --script smtp-enum-*   |            |
          |           | dnsenum                     |<-----------+
          |           +-----------------------------+
          |
          v
+-----------------------------+
|   Output/Report             |
|  - Usernames Found          |
|  - MX Records / Zones       |
|  - Subdomains / IPs         |
+-----------------------------+

```

## dnsenum
**Purpose:** A multithreaded Perl script to enumerate information from DNS servers.

**Use case:** Performs DNS zone transfers, brute force subdomains, and gather host IPs.

```
dnsenum example.com
```

## Output:

<img width="982" height="302" alt="image" src="https://github.com/user-attachments/assets/d4a52043-a246-4c64-8964-2ef1cc1cb4e8" />


## smtp-user-enum
**Purpose:** Standalone tool used to enumerate valid users by using the VRFY, EXPN, or RCPT TO commands.

**Use case:** Brute-forces SMTP to find users.

```
smtp-user-enum -M VRFY -U users.txt -t <target-ip>
```
  
 ## Output

  <img width="849" height="858" alt="Screenshot 2025-08-30 155802" src="https://github.com/user-attachments/assets/649f1318-2322-443b-b650-fe078649d01e" />



## nmap –script smtp-enum-users.nse <hostname>

**Purpose:** Uses smtp-enum-users NSE script to enumerate valid users on an SMTP server.

**Use case:** Helps identify email accounts on mail servers.

```
nmap -p 25 --script smtp-enum-users.nse <target-ip>
```
## OUTPUT:

<img width="806" height="191" alt="Screenshot 2025-08-30 155841" src="https://github.com/user-attachments/assets/111bebe5-3fbd-4133-ac7e-4baab1b77f4f" />




## RESULT:
The Google hacking keywords and enumeration tools were identified and executed successfully
