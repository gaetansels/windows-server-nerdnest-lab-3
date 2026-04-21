## windows-server-nerdnest-lab-3

This lab builds upon the previous labs and focuses on advanced Active Directory management, Group Policy configuration, and centralized user environment control.

The lab demonstrates Folder Redirection, network drive mapping, policy enforcement, and automated software deployment in a domain environment.

---

## Project Context

NerdNest continues to expand its infrastructure by improving user experience, security, and manageability.

This lab introduces centralized user data management, standardized configurations, and automated deployment strategies while maintaining security and efficiency.

---

## Lab Environment

This lab uses the existing **nerdnest.test** domain environment:

* **Domain Controller**: Windows Server (AD DS, DNS)
* **File Server**: Windows Server (Member Server)
* **Client Machine**: Windows 11 (domain joined)

---

## Key Objectives

### 1. Folder Redirection

* Redirect **Documents** and **Pictures** folders for users in the **Marketing (Sales)** department

* Use **Group Policy (GPO)** to centralize user data on the file server

* Ensure:

  * Efficient network usage (no full roaming profiles)
  * Users can access files from any domain machine
  * Users cannot access each other's folders

* Implementation details:

  * Central folder on server (e.g. `E:\RedirectedFolders`)
  * Hidden share (`Redirected$`)
  * NTFS permissions configured per user
  * GPO linked to Marketing OU

---

### 2. Network Connectivity

* Configure automatic **network drive mapping** for users
* Ensure users can easily access shared folders without manual configuration
* Mapping applied via **Group Policy Preferences**

---

### 3. Background Policy

* Apply a **uniform desktop background** for all domain users
* Implemented using **User Configuration GPO**

---

### 4. IT Department Permissions

* Users in the **IT department**:

  * Have **local administrator rights** on client machines
  * Do **not** have domain admin privileges

* Implemented using:

  * Security Groups
  * Group Policy (Local Administrators group assignment)

---

### 5. MSI Deployment

* Automatically deploy **VLC Media Player** to client machines

* Configuration:

  * `.msi` installer stored in:

    ```text
    \\nerdnest.test\SYSVOL\nerdnest.test\Policies
    ```
  * Applied via **Computer Configuration → Software Installation**
  * Deployment type: **Assigned**

---

## Scenario Testing

The configuration is validated by logging in as a Marketing user:

* Documents and Pictures are automatically redirected to the server
* Network drives are mapped automatically
* Desktop background is applied via GPO
* Users cannot access other users' folders
* VLC Media Player is installed automatically

---

*Note: This lab is part of the Graduaat Systeem- en Netwerkbeheer (Windows Server Intro) at Howest Brugge.*
