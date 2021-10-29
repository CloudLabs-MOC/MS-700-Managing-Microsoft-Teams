---
lab:
    title: 'Lab 01: Manage Microsoft Teams'
    type: 'Answer Key'
    module: 'Module 1: Get started with managing Microsoft Teams '
---

# **Lab 01: Manage Microsoft Teams**

## **Microsoft 365 user interface**

Given the dynamic nature of Microsoft cloud tools, you may experience user interface (UI) changes that were made following the development of this training content. This will manifest itself in UI changes that do not match up with the detailed instructions presented in this lab manual.

The Microsoft World-Wide Learning team will update this training course as soon as any such changes are brought to our attention. However, given the dynamic nature of cloud updates, you may run into UI changes before this training content is updated. **If this occurs, you will have to adapt to the changes and work through them in the lab exercises as needed.**

## **Lab Scenario**

In the labs, of this course, you will assume the role of **Joni Sherman**, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. You have implemented Microsoft 365 in a virtualized lab environment already and were commissioned to conduct a pilot project to test the implementation of Microsoft Teams against Contoso Ltd. business requirements.

You have just started the pilot project, and you’ve already got two virtual machines with preinstalled Teams Desktop clients and a tenant with different users:

- Joni Sherman (JoniS@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams administrator**

- Patti Fernandez (PattiF@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams device administrator**

- Allan Deyoung (AllanD@&lt;YourTenant&gt;.OnMicrosoft.com) **Teams communication support engineer**

- Alex Wilber (AlexW@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user from Canada**

- Lynne Robbins (LynneR@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user**

- Diego Siciliani (DiegoS@&lt;YourTenant&gt;.OnMicrosoft.com) **Regular pilot user**

## **Objectives**

After you complete this lab, you will be able to:

- Assign Teams admin roles to users

- Check license assignment for users

- Understand the Teams admin center and its menus

- Install the Teams PowerShell module and explore its cmdlets

- Create Microsoft 365 Groups from the M365 admin center

- Create new teams using the Teams Desktop client

- Create new teams using the Teams web client

- Configure expiration policies

- Restrict creation of new teams to members of a security group

- Create naming policies



## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Before you start**

The labs in this course have been prepared for a Microsoft Teams deployment at Contoso Ltd. Corporation. Contoso is running a Microsoft 365 cloud only deployment. The lab environments have been specifically designed in this manner to give you experience managing Microsoft Teams in a Microsoft 365 deployment. You will be provided with two virtual machines and a Microsoft 365 tenant to complete the lab steps.

#### **1. Sign in to the lab virtual machines**

The labs in this course will use two virtual machines:

- Client 1 VM: a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

- Client 2 VM: a stand-alone Windows 10 client virtual machine with Microsoft Teams pre-installed.

**Note:** Lab virtual machine sign in instructions will be provided to you by your instructor.

**Important:** The exercises in the MS-700 labs are cloud-only deployments. A local administrator account has been created on the client VMs. You will log into the VMs as a local administrator instead of a domain account. Following your login, the desktop will indicate that you are logged in as either **CLIENT1\admin** or **CLIENT2\admin**, depending on which machine you are on.

#### **2. Review installed applications**

Once you signed in to the VM, observe the start menu, and verify following applications have been installed:

- Microsoft Teams

#### **3. Review Microsoft 365 tenant**

Beside two VMs, you will also be provided with a Microsoft 365 tenant with following highlights:

- Office 365 E5 with Enterprise Mobility + Security E5 licenses assigned to various users.

- 15 licenses in total with 5 available of 15(10 used).

- One Global Administrator (MOD Administrator) and 9 standard users have been pre-created.

  **Note:** Microsoft 365 sign in instructions will be provided to you by your instructor.

- The username of the Global Administrator (MOD Administrator) is **admin@&lt;YourTenant&gt;.onmicrosoft.com**.


>   Note : 
Please note that odl_userXXXXX@<YourTenant>.onmicrosoft.com is your administrator user and you should use odl_userXXXXX@<YourTenant>.onmicrosoft.com in place of MOD Administrator (admin@<YourTenant>.onmicrosoft.com) throughout this lab

- **&lt;YourTenant&gt;.onmicrosoft.com** - This is the domain associated with the Microsoft 365 tenant that was provided by the lab hosting provider. The first part of this domain name (&lt;YourTenant&gt;) is the unique tenant ID provided by the lab hosting provider. The &lt;YourTenant&gt; portion of the tenant ID, which is the tenant suffix ID, will be unique for each student.

  **IMPORTANT:** This is critical because throughout this lab, you will be asked to enter the **&lt;YourTenant&gt;.onmicrosoft.com** domain name when signing into apps with a given username (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com). When doing so, you must enter the unique tenant suffix ID that is assigned to your tenant ID in place of the **&lt;YourTenant&gt;**.

  For example, if your Tenant Email is **admin@contosolab.onmicrosoft.com**, the unique tenant suffix ID (&lt;YourTenant&gt;) is **contosolab**. When signing in as Joni when entering this domain, you would replace &lt;YourTenant&gt; with contosolab (for example, JoniS@contosolab.onmicrosoft.com).

   **RECOMMENDATION:** You should write down your unique tenant suffix, mentioned as &lt;YourTenant&gt; in this lab and provided by your training provider. After a while, you will have this name or number memorized as you move through the labs in this course.

- **Use the new Microsoft 365 admin center** 

  Throughout the lab exercises for this course, if you navigate to the Microsoft 365 admin center, make sure the slider in the upper right corner is set to **The new admin center**. If you can read **Try the new admin center**, select the slider and activate it.  
‎‎  
‎‎  **IMPORTANT:** The instructions that are provided in the lab exercise for this course are based on the new Microsoft 365 admin center UI and not the classic UI.

### **Exercise 1: Prepare Teams admin roles and licenses**

In the first exercise you will assign required administrative roles to users and check license assignments for the Teams license. To perform these tasks, you will use default tenant global admin.

#### **Task 1 - Assign Teams admin roles to users**

In this task you will use the default global admin to sign in to the Microsoft 365 admin center and assign several Teams admin roles to different users. This task is crucial for later tasks and exercises as you will perform most of the tasks in context of Joni Sherman’s account.

1. Browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**. 
	
	>   Note : 
	Please note that odl_userXXXXX@<YourTenant>.onmicrosoft.com is your administrator user and you should use odl_userXXXXX@<YourTenant>.onmicrosoft.com in place of MOD 	     Administrator (admin@<YourTenant>.onmicrosoft.com) throughout this lab

    1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

    2. Open **Microsoft Edge** and navigate to the **Office 365 Portal** at [**https://portal.office.com/**](https://portal.office.com/).

    3. When the Sign in window is displayed, sign in as **MOD Administrator** (admin@&lt;YourTenant&gt;.onmicrosoft.com) using the credentials provided to you.

    4. On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.

    5. Close the password save dialog from the bottom with **Never**, not to save the default global admins credentials in your browser.

    6. If a welcome screen is displayed, close it. If the Office 365 apps notification appear, also close it.

    7. Select the app launcher icon in the upper-left and choose **Admin**.

    8. If a welcome window is displayed, select **Get started** and close it.

2. Assign **Teams admin** role to **Joni Sherman**

    1. Select the navigation menu in the upper-left and select **Users** and **Active users** from below it.

    2. In the Active users list, search and select **Joni Sherman**, to open the right-side settings pane.

    3. In the settings below the Account tab, scroll to **Roles** and select **Manage roles** below.

    4. On the **Manage admin roles** pane, select **Admin center access** and scroll down to expand **Show all by category** to reveal all available roles. 
    
    5. Select **Teams Administrator** checkbox then select **Save changes**. You will see the message **Admin roles updated** on the upper part of the pane to confirm the update. 

3. Assign **Teams device admin** role to **Patti Fernandez**

    Repeat the same steps and assign **Teams Device Administrator** role to **Patti Fernandez**.

4. Assign **Teams communication admin** role to **Allan Deyoung**

    Repeat the same steps and assign **Teams communication support engineer** role to **Allan Deyoung**.

You have now successfully assigned the Teams admin roles.

* Teams Administrator: Joni Sherman
* Teams Devices Administrator: Patti Fernandez
* Teams communication support engineer: Allan Deyoung

Proceed to the next task.

#### **Task 2 – Check license assignment of your users**

In this task, you will check the license assignment of all users participating in the pilot. At the end of the task you will confirm that all pilot users are licensed correctly and Alex Wilber’s location is updated to Canada as preparation for a later task.

1. Connect to the **Client 1 VM** and browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.
	
	>   Note : 
	Please note that odl_userXXXXX@<YourTenant>.onmicrosoft.com is your administrator user and you should use odl_userXXXXX@<YourTenant>.onmicrosoft.com in place of MOD 	     Administrator (admin@<YourTenant>.onmicrosoft.com) throughout this lab

2. Update **Alex Wilber's** location to **Canada**

    1. On the **Users** > **Active users** page, select the name of **Alex Wilber**.

    2. Select **Licenses and Apps** tab. 

    3. Select the dropdown menu under **Select location**, and update to **Canada**. 

    4. Select **Save changes**. 

3. Check **Alex Wilber's** licenses

    1. On the same tab, under **Licenses** section, verify that **Enterprise Mobility + Security E5** and **Office 365 E5** are both selected.

    2. Select **Apps** to expand All licenses.

    3. Scroll down the list of all apps, and verify **Microsoft Teams** is selected. 
    
4. You can repeat the same steps to check other users' licenses. Do not change their locations. 

You have successfully validated that all users participating in the pilot own Teams licenses and are ready to start working with Teams. You have also changed the location of Alex Wilber to Canada, as a preparation for a later task. Continue with the next task. 

You have finished the first exercise, and you can continue with the next one.


### **Exercise 2: Explore Teams management tools**

In this exercise, you will explore Teams admin center required to manage teams, calling features, and all other settings for Teams in your tenant. You can perform most of the tasks possible from the Teams admin center.

To perform these tasks, you will use Joni Sherman’s account (JoniS@_&lt;YourTenant&gt;_.onmicrosoft.com).

#### **Task 1 - Explore Teams admin center**

You will review the available settings for managing Teams in the Teams admin center.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

    **Note:** You can use **InPrivate window** of Microsoft Edge for logging in with different credentials. 

2. In left navigation of the Teams admin center, select **Teams** > **Manage teams**. You will see the teams in your organization once created. 

3. In left navigation of the Teams admin center, select **Teams** > **Teams policies**. You can see the default Teams policy named **Global (Org-wide default)**.

You can explore other settings to familiarize various controls in the Teams admin center.

You have successfully explored several available menus from the Teams admin center for managing teams and configuring policies in your tenant. 


### **Exercise 3: Create groups and teams**

In this exercise, you will create a Microsoft 365 group from the Microsoft 365 admin center and creating a team from the Teams desktop client and the web client.

#### **Task 1 - Create a Microsoft 365 Group**

You will create a new Microsoft 365 Group named "IT-Department," and then add the pilot members serving as a basis for your future teams and licensing.


1. Connect to the **Client 1 VM** and browse to the **Microsoft 365 admin center** (https://admin.microsoft.com/) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the Microsoft 365 admin center, select **Teams & groups** > **Active teams & groups**.

3. On the **Active teams and groups** page, select **Add a group**.

4. Follow the **Add a group** wizard with the following information:

    * Group type: Select **Microsoft 365 (recommended)**
		 - Select **Next**             
    * Basics: 
    	- Name: **IT-Department**
    	- Description: **All staff of the IT-Department**
    	- Select **Next**
    
    * Owners: 
        - Select **+ Assign owners** 
        - Search and select **Joni Sherman**
        - Select **Add(1)**, and then select **Next**.

    * Members: 
	    - select **+ Add Members**
        - Patti Fernandez
        - Allan Deyoung
        - MOD Administrator
	
	    >   Note : 
	    Please note that odl_userXXXXX@<YourTenant>.onmicrosoft.com is your administrator user and you should use odl_userXXXXX@<YourTenant>.onmicrosoft.com in place of MOD Administrator (admin@<YourTenant>.onmicrosoft.com) throughout this lab
	
        - Select **Add(3)**, and then select **Next**.
        
    * Settings: 
        - Enter **IT-Department** for Group email address. 
        - Privacy: Private
        - Uncheck **Create a team for this group**.
        - Select **Next**

5. Select **Create group** > **Close**.

6. Wait a moment and select **Refresh** until the group is visible. You will see there is no Teams icon in the **Teams status** column.

7. Select the **IT-Department** group to review the settings and members. 

The new Microsoft 365 Group with the name "IT-Department" was successfully created. Close the browser window and continue to the next task.

#### **Task 2 - Create a 3 new teams by using the desktop client**

To test the self-service capabilities of Teams, in this task, **Alex Wilber** will sign in to the Teams Desktop client, create a new team with the name **Teams Rollout** and add all members participating in the Teams evaluation project.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams desktop client.

3. When prompted to **Enter your work, school or Microsoft account**. Sign in as **Alex Wilber** (AlexW@&lt;YourTenant&gt;.onmicrosoft.com).

    **Note**: You might need to download and install the latest Teams desktop client. Select **Update Teams** and follow the installation guideline - Select  **Download for desktop** > **Download Teams**
    **Run**.


4. In the Teams desktop client, select **Teams** from the left menu. 

5. Select **Join or create a team** from the lower left corner. 

5. Select **Create team** > **From scratch** > **Public**. Enter the team name **Teams Rollout** and select **Create**.

6. On the **Add members to Teams Rollout** window, enter the following names and select **Add**. 

    * Joni Sherman
    * Lynne Robbins
    * Diego Siciliani

7. Select the dropdown menu next to Joni Sherman and switch from **Member** to **Owner**. 

8. Select **Close**.

9. Repeat the above steps and create one more group as details mentioned below

10. Enter **Afterwork** for the **Team name**.

    Below the entered name, you can see the configured prefix and suffix for new teams.

11. Select **Create** to create the new team.

12. Add **Lynne Robbins** to the team member.

13. Review the name of the newly created team.

You have successfully created two new teams from the Teams desktop client, added the project team members, and you have made Joni Sherman a team owner. 


#### **Task 3 - Create a new team by using the web client**

In this task, **Lynne Robbins** will continue testing the self-service capabilities of Teams by using the Teams web client to create another team with the name **Sales**. She will also add **Alex Wilber** as a member.

1. Connect to the **Client 2 VM** with the credentials that have been provided to you.

2. Browse to the **Microsoft Teams web client** at [**https://teams.microsoft.com**](https://teams.microsoft.com/) and sign in as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

3. Select **Use the Web app instead** if prompted to download Teams Desktop app. At the 'Stay signed in to all your apps' window, select **No, sign in to this app only**. 

4. Select **Join or create a team** from the lower left corner. 

5. Select **Create team** >**From scratch** > **Private**. Enter the team name **Sales** and select **Create**.

6. On the **Add members to Sales** window, enter the following names and select **Add** > **Close**.

    * Alex Wilber

The newly created team is displayed in the list of your teams. You have successfully created a new team with the Teams web client.

END OF LAB