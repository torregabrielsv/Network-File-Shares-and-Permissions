# Network-File-Shares-and-Permissions
A high-level list of steps to set up and test file shares with various permissions in an Active Directory environment. 

Create some sample file shares with various permissions
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
Set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
(Skip accounting for now)

<img width="848" alt="Screenshot 2024-07-29 at 12 34 59 AM" src="https://github.com/user-attachments/assets/c53b79f2-9bd5-4f8d-8afc-63fe1250a426">

Attempt to access file shares as a normal user
On Client-1, navigate to the shared folder (start, run, \\dc-1)

<img width="837" alt="Screenshot 2024-07-29 at 12 33 15 AM" src="https://github.com/user-attachments/assets/109b39e7-2427-4058-8233-8e51120738f1">

Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?

<img width="602" alt="Screenshot 2024-07-29 at 12 35 18 AM" src="https://github.com/user-attachments/assets/88f35e71-492a-4ab3-901a-90ec36b49560">

<img width="792" alt="Screenshot 2024-07-29 at 12 35 39 AM" src="https://github.com/user-attachments/assets/e85ace34-3b5e-4458-8f04-bcc747856a36">

<img width="792" alt="Screenshot 2024-07-29 at 12 37 16 AM" src="https://github.com/user-attachments/assets/9862e572-a74f-4754-87af-e84b23d2a434">

Create an “ACCOUNTANTS” Security Group, assign permissions, an test access
Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”
On the “accounting” folder you created earlier, set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 

Log out of Client-1 as  <someuser>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?

<img width="817" alt="Screenshot 2024-07-29 at 12 44 55 AM" src="https://github.com/user-attachments/assets/6e04f322-6c9c-4e31-9284-a1ad34705ce6">












