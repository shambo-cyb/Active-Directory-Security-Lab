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

### I have created a new password policy in the password container that has passwords with no complexities, esp for the guest sales personnels to be used on the fly
<img width="600" height="870" alt="5" src="https://github.com/user-attachments/assets/487c1639-126e-423f-91ee-9ab8b4925d83" />

I am currently configuring a Fine-Grained Password Policy (FGPP) specifically for the temporary guest sales accounts.
- The policy is named "Password Without Complexity" and is configured with a minimum password length of just 3 characters, deliberately waiving standard complexity requirements.
- I have set the policy to enforce a robust password history of 24, preventing the reuse of recent passwords.
- The account lockout policy has been left unconfigured, so there is no limit on the number of failed logon attempts before an account is locked out.

### A Guest Sales account has been assigned to the password policy 

<img width="600" height="853" alt="6" src="https://github.com/user-attachments/assets/86a76260-3541-4887-b56f-617c55623ea9" />

This means that a guest agent would likely have access with a complex password but most importantly their account is managed with little to no permissions 

### Logging on with the Guest Sales Account 

<img width="600" height="951" alt="7" src="https://github.com/user-attachments/assets/f2eceb31-0753-4dc7-9aa0-2767a17d3159" />

As the passoword without complexity is designed with simplicity in mind it just requires the user to create a very basic password only comprising of 3 digits. The user is created in such a way in the organizational unit that they would have to 
change the password the first time they login. The intial password is generally provided by the IT administrator and the policy forces them to change it the first time they login. 

### Now I have created a new password policy in the password container that has passwords with complexities, this is usually for the employees

<img width="600" height="907" alt="8" src="https://github.com/user-attachments/assets/7c9ebae3-01a2-44f2-b02d-85f431c0546d" />

This policy enforces strict password rules and a robust account lockout policy to prevent unauthorized access and brute-force attacks.
- Policy Name: "Password with Complexity"
- Precedence: Set this to a lower number than other policies that apply to your administrators. A lower number (e.g., 1) gives it a higher priority.
- Minimum Password Length: Set this to a higher value, like 10 characters, as a baseline for a strong password.
- Password must meet complexity requirements: Enabled. This forces users to create passwords that include characters from at least three of the following four categories:
- Uppercase letters (A-Z)
- Lowercase letters (a-z)
- Numbers (0-9)
- Special characters (e.g., !, @, #, $, %, ^, &, *)
- Enforce password history: Set this to a high number, like 24. This prevents users from reusing any of their last 24 passwords, forcing them to create new, unique passwords with each change.

### Enforcement of the rule 
<img width="600" height="948" alt="10" src="https://github.com/user-attachments/assets/490d5508-c940-44f8-8d43-80774d0ad721" />

As it is visible a simple password wouldnt work it has to satisfy all the conditions mentioned in the policy

### Account Lockout 

<img width="600" height="951" alt="11" src="https://github.com/user-attachments/assets/1a25f422-379a-477d-b5ab-0fa574dccadf" />


That account lockout message on the login screen is a direct result of the "Password with Complexity" policy. It looks like "Hulk Hogan" tried to log in unsuccessfully too many times and has been temporarily locked out. This security feature is a great way to prevent brute-force attacks.
- This is a great security measure to stop brute-force attacks
- There is no duration of the lockout period instead I have configured it such a way that an Administrator has to manually unlock an account

### Unlocking the account 

<img width="600" height="910" alt="12" src="https://github.com/user-attachments/assets/5821d17b-6df5-4149-a427-402d2e56250f" />

The grayed-out "Unlock account" option indicates it's locked due to too many failed login attempts, as specified in the "Password with Complexity" policy. Simply check the box to re-enable the account.
- The account is locked because of too many failed password attempts.
- This is a quick fix to get the account back up and running.

### Adding a Shared Folder for Access 

<img width="600" height="790" alt="13" src="https://github.com/user-attachments/assets/b76c4db3-0414-44b4-86b9-bedda83bd160" />

After I've configured the Drive Maps policy to automatically connect users to a shared folder, I need to make sure the policy is applied to their computers. The image shows me, the administrator, running the gpupdate /force command. This is a crucial step because it forces the client computer to immediately download and apply any new or changed Group Policies—including the one I created for the shared folder. The "Computer Policy update has completed successfully" and "User Policy update has completed successfully" messages confirm that the new settings have been pushed to the machine, which means the shared folder is now available to the users without any further action on their part.
- I created a "Drive Maps" policy to automatically map a shared folder.
- The policy is set to map the shared folder located at \\WIN2016\SharedFolder.
- I ran gpupdate /force to ensure the new Drive Maps policy is applied immediately.
- The successful messages confirm that the policy has been applied.

### The Shared Folder is now visible to all the users in the admin OU bucket

<img width="600" height="825" alt="14" src="https://github.com/user-attachments/assets/ebed769e-59b4-40a0-8685-98a02fcd7c81" />

As a result of my Drive Maps policy, the shared folder is now automatically visible under Network locations in File Explorer. It's ready to go.

