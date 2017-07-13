# VM-Series in an Availability Set Template (@michelvankessel FORK)

-------------------------------------------------------------
TODO
- 20170623 - made a fork to change the following things
1. add VIF more NICS and attach to VM-series - DONE! 11-07-2017
2. make choice at least vm choice that support +4 nics (e.g. DS4_v2) - DONE! 11-07-2017
3. Change to Managed Disks - DONE! 13-07-2017
4. Change Availability set with managed disk support - DONE! 13-07-2017

- 20170717 - cleanup config
1. Take out storageaccount config
2. change SSH public key json to include managed disk and correct API version


------------------------------------------------------------

This ARM template deploys a VM-Series next generation firewall VM in an availability set of a Azure resource group. It lets you select your:
- Username and Password, or SSH key
- Resource Group and Storage Account inside it
- VNET's CIDR (/16 range) with 8 subnets: Mgmt (1.0/24), Untrust (2.0/24), Trust (3.0/24), DMZ (4.0/24), ExpressRoute (5.0/24), and 3 futures subnets
- Azure VM size and login for VM-Series (BYOL edition) with 8 NIC's that map to above subnets
- Specify PAN-OS version and VM-Series model: BYOL, hourly pay-as-you-go (PAYG)Bundle 1 or Bundle 2
- Specify the Azure Availability Set (required parameter)

Note: Make sure to set a strong password for the firewall and set the SRCIPINBOUNDNSG to your source IP, i.e. restrict which IP (yours) can connect to your Azure deployment. If you keep it 0.0.0.0/0 then anyone can connect (or brute force) your VM's. 

This template is meant to let you do customized deployments of VM-Series instead of deploying from the Azure Marketplace. You can deploy using the "Deploy to Azure" button below or download the template and customize it to your needs. You can also fork the templates into your own GitHub repository.

[<img src="http://azuredeploy.net/deploybutton.png"/>](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmichelvankessel%2Fazure%2Fmaster%2Fdemo-vmseries-avset%2FazureDeploy.json)
[<img src="https://camo.githubusercontent.com/536ab4f9bc823c2e0ce72fb610aafda57d8c6c12/687474703a2f2f61726d76697a2e696f2f76697375616c697a65627574746f6e2e706e67" data-canonical-src="http://armviz.io/visualizebutton.png" style="max-width:100%;">](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fmichelvankessel%2Fazure%2Fmaster%2Fdemo-vmseries-avset%2FazureDeploy.json)


