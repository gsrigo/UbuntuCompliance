# UbuntuCompliance
This is a project with the intention of automating compliance jobs for NIST 800-171 (DFARS) and STIG for Ubuntu 20.04

## Ubuntu 20 Compliance

The compliance job is meant to call for either the DFARS or STIG jobs. Ideally only one of them should run.

 Please note that the STIG compliance role is not finished completely and it is missing the following parts due to the lack of fips packages and the nature of post-provisioning. This might come on a future version if applicable:
- Grub password automation.
- Multiple partitions as required by the STIG.
- FIPS enabled modules and system configured to run in FIPS mode.
- IDS/IPS requirements.
- MFA/PKI-based configuration and authentication.

The jobs can run locally or be pushed to multiple clients creating a host files (or making use of Tower/AWX)

To run the job for NIST 800-171:

`# ansible-playbook Ubuntu20_Compliance.yml --tags "NIST800_171"`

To run the job for STIGs:

`# ansible-playbook Ubuntu20_Compliance.yml --tags "STIG_Ubuntu"`

## Ubuntu OSCAP and OVAL Scanning

XML files have been created from source from the Compliance as Code project in github. The files are copied to each of the systems to be scanned.
Once the files are there, the systems are scanned with the default profile, an html report is generated which is later fetched back to the main ansible host based on a var location. Additionally, from the Ubuntu site, an OVAL scanning is also performed on the systems and a similar report is generated for review. 

To run the job:

`ansible-playbook oscap_oval_scanning.yml`

## Ubuntu Patching

The Patching job updates the apt cache and upgrades all packages installed on a system. If a reboot is required, it WILL reboot the systems. 
Use this with care and after hours to avoid interruptions. This job is to have manual control (as opposed to the unattended upgrades) and meant to run on a scheduled basis.

To run the job:

`ansible-playbook patching.yml`

### Personal note

This project has been created as professional need for Ubuntu compliance for both servers and desktops. I have used this opportunity to create this project as part of my final project for ENPM9697 at UMD. 
