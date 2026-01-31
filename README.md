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
<img width="1919" height="1083" alt="image" src="https://github.com/user-attachments/assets/1e07b068-bf89-4fea-9981-089a9ee2fcf8" />

INURL:
<img width="1919" height="1082" alt="image" src="https://github.com/user-attachments/assets/32808459-a026-4df4-851b-d1c1fa9bd604" />

INTITLE:
<img width="1919" height="1074" alt="image" src="https://github.com/user-attachments/assets/e495f0f1-6142-4b40-bd56-eee75e653d8a" />

FILETYPE.PDF
<img width="1914" height="1087" alt="image" src="https://github.com/user-attachments/assets/e01f45be-5f23-4f23-ae36-39ebc7fe5fb5" />

INTEXT:
<img width="1913" height="1080" alt="image" src="https://github.com/user-attachments/assets/78b1874e-9eda-4231-9a91-e2510add5dec" />

LINK:
<img width="1919" height="1063" alt="image" src="https://github.com/user-attachments/assets/c421fccb-6eba-413e-b5c7-94232967f8db" />

CACHE:
<img width="1917" height="1065" alt="image" src="https://github.com/user-attachments/assets/28ccbe00-023b-416f-97ec-085092c4e74e" />


# DNS Enumeration
<img width="1157" height="409" alt="image" src="https://github.com/user-attachments/assets/2fdc369e-75fd-4248-b526-7f9ad8646f46" />


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
<img width="858" height="289" alt="image" src="https://github.com/user-attachments/assets/00055178-adba-4062-8f5d-af155f586038" />


### DIG:
<img width="1151" height="659" alt="image" src="https://github.com/user-attachments/assets/3e87f927-63c7-4467-93e2-1693cea0a6fc" />


### HOST:
<img width="1140" height="137" alt="image" src="https://github.com/user-attachments/assets/535f035b-bdbb-4209-a6ee-e50ddc711ffb" />


### DNSENUM:
<img width="1157" height="409" alt="image" src="https://github.com/user-attachments/assets/2fdc369e-75fd-4248-b526-7f9ad8646f46" />



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

<img width="1157" height="409" alt="image" src="https://github.com/user-attachments/assets/2fdc369e-75fd-4248-b526-7f9ad8646f46" />


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
