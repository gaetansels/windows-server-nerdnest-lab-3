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

## GPO 

If you do the test now, someone from another department still sees an "E-folder". 
In this step, we will be implementing the group policy. 

Tools --> Group Policy Management --> Group Policy Objects. 

On "Group Policy Objects" Right Mouse Click --> New --> .... file in the name and "OK"

![something](images/win_lab3_p5.png) 

After that, you do RMK and "edit" 

Here you get 2 options ; we will be configuring it on user level so "User configuration"

Here you navigate to "Folder Redirection" ; then you RMK Documents --> properties --> "Basic -redirect everyone's folder to the same location"

![something](images/win_lab3_p6.png) 

Next, we add the file path 
Because it is a hidden share, we have to look up the file, and we can directly copy past the file path in the requested location.  ( because it is a hidden share)
don't forget the **$** 

![something](images/win_lab3_p7.png) 

"Create a folder for each user..." --> as you can see above "ok" , "cancel"  ... we get an example of what we want. 

Click "OK" --> warning do you want to coninue ... click "yes"

We can easily "follow the document folder" to get the same result for the pictures 

![something](images/win_lab3_p8.png) 

Again "ok" and "Yes"

Now lets apply this to "verkoop" , we can easily do this by dragging and ropping the GPO to the OU_verkoop : 

![something](images/win_lab3_p9.png) 


I am logging in with someone from Accounting : 

![something](images/win_lab3_p11.png)  

And someone from Verkoop/ marketing to check : 

![something](images/win_lab3_p12.png)  

---

## Network Connectivity
![something](images/win_lab3_p15.png) 
