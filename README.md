# Active-Directory-Security-Lab
Set up a hands-on Active Directory lab to explore user and role-based permissions. Focused on controlling access, authentication, and monitoring potential security risks. Great for testing real-world AD security scenarios safely

### Setting up an Active Directory environment for a small sales business having dedicated It Admninistrators and Sales Personnels 
Built an Active Directory environment for a small sales business with dedicated IT administrators and sales personnel. Managed user accounts, roles, and permissions to keep access secure and organized. Ensured smooth collaboration while maintaining strong security practices.
## Tools Used
Laptop with i5 (12450h), 16 Gb of ram , 512 gb Nvme SSD nvidia rtx 4050 
- VmWare
- Windows 2016 Server with Active Directory (Virtual Machine)
- Windows 2010 as the Computer (Virtual Machine)
### Windows 2010 joining the Active Directory ( Banerjee.com) 
<img width="600" height="881" alt="1" src="https://github.com/user-attachments/assets/7883f4a8-50b1-4de5-be3d-4f0fedaaf8f5" />

The provided image illustrates the process of joining a Windows 10 virtual machine to a corporate domain. The primary interface, labeled "System Properties," displays fields for "Computer name" and "Member of," with the user selecting the "Domain" radio button and entering "Banerjee.com." This action is a fundamental step in network administration, enabling centralized management and user authentication. A subsequent pop-up window confirms the successful completion of this action, stating, "Welcome to the Banerjee.com domain." This process demonstrates a key aspect of enterprise-level network configuration, where individual machines are integrated into a larger, centrally controlled network structure for enhanced security and resource management.

### Creation of Organizational Units - Administrator and Sales inside of the Windows 2016 Sever (Banerjee.com)
<img width="600" height="906" alt="2" src="https://github.com/user-attachments/assets/5deeed0f-7848-4b80-9340-fe23b709219d" />

I have the Active Directory Users and Computers (ADUC) management console open, a core tool I use for managing my Windows-based network. I have navigated to the "Computers" container within the "Sales" organizational unit (OU) of the "Banerjee.com" domain. The main pane is currently empty, which tells me there are no computer objects stored in this specific location. This snapshot provides me with a system administrator's view of the directory service, showcasing the hierarchical structure of my domain and the granular control I have for organizing network resources.

### Putting the newly added Windows 10 computer in the Admin Computer OU 
<img width="600" height="912" alt="3" src="https://github.com/user-attachments/assets/efaa3c60-f636-49c8-9089-8676596fbfc7" />

I have performed an administrative action to relocate the "WIN10" computer object. I have moved it from its previous location, outside of the "Administration" organizational unit, to the "Computers" container within the "Administration" OU. This allows me to apply specific security and group policies to the computer, ensuring it aligns with the management protocols designated for administrative machines.

### A user for Guest Sales has been creted. Guest Sales personnels are temporary agents using this computer like if the company needs to outsource and their accounts are deleted after a week. 
<img width="600" height="912" alt="4" src="https://github.com/user-attachments/assets/95795da4-2d26-4076-865b-b0cdb971be2f" />

I am now configuring the properties of the Guest.Sales user account within the Sales/Users organizational unit of the Banerjee.com domain. This account is specifically designated for temporary agents and is configured to enforce a limited service period. As demonstrated in the configuration pane, I have set the account to automatically expire at the end of August 29, 2025, which corresponds to a seven-day operational period. This action is a critical part of my access control policy for temporary personnel, ensuring that their credentials are automatically revoked. Additionally, the "User must change password at next logon" option is enabled to enforce an immediate security measure.

## I have created a new password policy in the password container that has passwords with no complexities, esp for the guest sales personnels to be used on the fly
<img width="600" height="870" alt="5" src="https://github.com/user-attachments/assets/487c1639-126e-423f-91ee-9ab8b4925d83" />

I am currently configuring a Fine-Grained Password Policy (FGPP) specifically for the temporary guest sales accounts.
- The policy is named "Password Without Complexity" and is configured with a minimum password length of just 3 characters, deliberately waiving standard complexity requirements.
- I have set the policy to enforce a robust password history of 24, preventing the reuse of recent passwords.
- The account lockout policy has been left unconfigured, so there is no limit on the number of failed logon attempts before an account is locked out.

