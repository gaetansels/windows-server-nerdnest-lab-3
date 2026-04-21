## Folder Redirection
This section implements Folder Redirection for the Marketing (Verkoop) department.
The goal is to centrally store user data while maintaining performance, security, and privacy.

Context : 

A "Documents" and "Pictures" user folder per person in the verkoop/marketing department must be redirected to the file server. 

This ensures that:
- Data is stored centrally on the server

- Users don't have access to each other's data

- The solution is efficient and does not overload the network.

**Architecture Overview:**

The solution is based on three core components:

1. Central Storage (File Server) --> the users can create their own "documents" and "Pictures"
2. Access Control (AGDLP) --> to manage access 
3. Group Policy (Folder Redirection) --> this is how the discussed mechanism is implemented


**1) Central Storage**

![something](images/win_lab3_p1.png)
