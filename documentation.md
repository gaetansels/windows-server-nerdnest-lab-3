## Folder Redirection
This section implements Folder Redirection for the Marketing (Verkoop) department.
The goal is to centrally store user data while maintaining performance, security, and privacy.

Context : 

A "Documents" and "Pictures" user folder per person in the verkoop/marketing department must be redirected to the file server. 

This ensures that:
- Data is stored centrally on the server

- Users don't have access to each other's data

- The solution is efficient and does not overload the network.

---
**AGDLP:**


## Account: 

Ou_Verkoop with the accounts is there already. 

## GLOBAL SECURITY GROUPS + DOMAIN LOCAL GROUPS

Here we make the Global Security Group "GG_verkoop" and 
The Domain Local group "DL_Verkoop_Folder_Redirect_Modify"

![something](images/win_lab3_p1.png) 

## Permissions 
First, we make the folder_redirect file in the file server
Then, as you can see below, we make sure the shared permissions is "full control"
![something](images/win_lab3_p2.png) 

In the NTFS permissions, we remove the inherited permissions and the unwanted groups or users with access. 
Then we modify the access of the requested group: 

![something](images/win_lab3_p3.png) 

Next, I am making sure the share is hidden by going to "Advanced Sharing..." and adding a **dollar sign $** after the name.

![something](images/win_lab3_p4.png) 

I redid the shared permissions because they reset, so in the future, this step will be done first.

I am logging in with someone from Accounting : 

![something](images/win_lab3_p5.png)  

And someone from Verkoop/ marketing to check : 

![something](images/win_lab3_p6.png)  

---

## Network Connectivity
![something](images/win_lab3_p9.png) 
