# Active-Directory-Security-Lab
Set up a hands-on Active Directory lab to explore user and role-based permissions. Focused on controlling access, authentication, and monitoring potential security risks. Great for testing real-world AD security scenarios safely

## Setting up an Active Directory environment for a small sales business having dedicated It Admninistrators and Sales Personnels 
Built an Active Directory environment for a small sales business with dedicated IT administrators and sales personnel. Managed user accounts, roles, and permissions to keep access secure and organized. Ensured smooth collaboration while maintaining strong security practices.
## Tools Used
Laptop with i5 (12450h), 16 Gb of ram , 512 gb Nvme SSD nvidia rtx 4050 
- VmWare
- Windows 2016 Server with Active Directory (Virtual Machine)
- Windows 2010 as the Computer (Virtual Machine)
## Windows 2010 joining the Active Directory ( Banerjee.com) 
<img width="600" height="881" alt="1" src="https://github.com/user-attachments/assets/7883f4a8-50b1-4de5-be3d-4f0fedaaf8f5" />

The provided image illustrates the process of joining a Windows 10 virtual machine to a corporate domain. The primary interface, labeled "System Properties," displays fields for "Computer name" and "Member of," with the user selecting the "Domain" radio button and entering "Banerjee.com." This action is a fundamental step in network administration, enabling centralized management and user authentication. A subsequent pop-up window confirms the successful completion of this action, stating, "Welcome to the Banerjee.com domain." This process demonstrates a key aspect of enterprise-level network configuration, where individual machines are integrated into a larger, centrally controlled network structure for enhanced security and resource management.

## Creation of Organizational Units - Administrator and Sales inside of the Windows 2016 Sever (Banerjee.com)
<img width="600" height="906" alt="2" src="https://github.com/user-attachments/assets/5deeed0f-7848-4b80-9340-fe23b709219d" />

I have the Active Directory Users and Computers (ADUC) management console open, a core tool I use for managing my Windows-based network. I have navigated to the "Computers" container within the "Sales" organizational unit (OU) of the "Banerjee.com" domain. The main pane is currently empty, which tells me there are no computer objects stored in this specific location. This snapshot provides me with a system administrator's view of the directory service, showcasing the hierarchical structure of my domain and the granular control I have for organizing network resources.

## Putting the newly added Windows 10 computer in the Admin Computer OU 
<img width="600" height="912" alt="3" src="https://github.com/user-attachments/assets/efaa3c60-f636-49c8-9089-8676596fbfc7" />

I have performed an administrative action to relocate the "WIN10" computer object. I have moved it from its previous location, outside of the "Administration" organizational unit, to the "Computers" container within the "Administration" OU. This allows me to apply specific security and group policies to the computer, ensuring it aligns with the management protocols designated for administrative machines.
