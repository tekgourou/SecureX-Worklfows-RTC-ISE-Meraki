
# ISE & Meraki Rapid Threat Containment workflows

Collection of SecureX Workflow and Atomic Activity that initiate a RTC for a MacAddress in a ISE / Meraki infrastructure.

Use cases : 
  - RTC a MacAddress from the CTR plugin
  - RTC a MacAddress from a corrolation workflow as a response to a threat detected.

For any questions or comments/bugs please reach out to me at alexandre@argeris.net or aargeris@cisco.com

![image](./images/casebook.png)
<br/>

# Prerequisites:

- Enable ERS API and create an ERS ADMIN API User in ISE save the credential.
https://developer.cisco.com/docs/identity-services-engine/3.0/#!setting-up/cisco-ise

- Create a ISE Authorization Profile.
![image](./images/ise_auth_profile.png)

- Create a Quarantine ISE Identity Endpoint Group
![image](./images/ise_identity_group.png)

- Create a Quarantine rule in the Global Authorization policy
![image](./images/ise_policy.png)

- Create a Group Policy in Meraki
![image](./images/meraki_group_policy.png)

- Create a TARGET for ISE hostname and credential in SecureX AO
![image](./images/ise_target.png)

# Import these workflows into SecureX Orchestration as Atomic Actions:
  
- ISE Add Endpoint ID to EndpointGroupID.json
- ISE Get Endpoint Group ID from GroupName.json 
- ISE Get Endpoint ID from MacAdresse.json
- ISE Get Endpoint Info from ID.json
- ISE Quarantine Endpoint.json
- ISE Re_authenticate Endpoint.json

# Main workflows:

- RTC - ISE MacAddress.json
![image](./images/workflow.png)
<br/>  

# Workflow in action !

- Initiate the worflow from the CTR browser plugin  
![image](./images/splunk.png)
<br/>

- ISE logs  
![image](./images/ise_logs.png)
<br/>

- Meraki Client  
![image](./images/meraki_client.png)
<br/>

- FMC
![image](./images/fmc.png)
<br/>
