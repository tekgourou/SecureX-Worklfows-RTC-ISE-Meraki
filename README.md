
# ISE & Meraki Rapid Threat Containment workflows

Collection of SecureX Workflow and Atomic Activity that initiate a RTC for a MacAddress in a ISE / Meraki infrastructure.

Use cases : 
  - RTC a MacAddress from the CTR plugin
  - RTC a MacAddress from a corrolation workflow as a response to a threat detected.

For any questions or comments/bugs please reach out to me at alexandre@argeris.net or aargeris@cisco.com

![image](./images/casebook.png)
<br/>

# Prerequisites:

- Enable ERS API and create an ERS ADMIN API User in ISE save the credentials.
https://developer.cisco.com/docs/identity-services-engine/3.0/#!setting-up/cisco-ise

- Create a ISE Authorization Profile.
![image](./images/ise_auth_profile.png)

- Create a Quarantine ISE Identity Endpoint Group
![image](./images/ise_identity_group.png)

- Create a Quarantine rule in the Global Authorization policy
![image](./images/ise_policy.png)

- Create the Duo Target based on the hostname in the Cisco SecureX Orchestration. 

  - Give a name, like "Duo"
  - No account keys: True
  - HTTPS protocol, host/IP address: API hostname
  - Proxy: Ignore Proxy
  
- Use this "Duo" target in the workflows selecting "Override workflow target" option and "Duo" target.


# Import these workflows into SecureX Orchestration as atomic workflows:
  
- CTRGenerateAccessToken.json

  This Atomic workflow action will get CTR access token.

- CTR Create Casebook.json 

  This Atomic workflow actions will create Casebook.  
  
- Duo Admin - Get DENIED or FRAUD Auth Logs.json

  This Atomic workflow action will fetch Duo auth denied and fraud logs.

# Main workflows:

- Duo Admin logs - Casebook and Sightings.json
  This workflow will fetch Duo (DENIDED or FRAUD) logs every 1hour (can be set by modifying the variable - interval - ) and parse the output to create a casebook and sigthings in SecureX platform. 
  
![image](./Screen_Shot_casebook_workflow.png)
<br/>  
# Remediation workflows

- Duo Admin - Block User By Username.json  

  This Atomics workflow action block a Duo user based on username. (Work only if the Duo user is local - not sync with Azure AD or Win AD)
  credit to https://github.com/Gyuri1/duo-sxo
  
- Quarantine Duo User.json
  This workflow give you access to quarantine user in Duo from the SecureX AO contextuel menu.
  
- Azure AD - lockdown user (not documented yet)
