

# Lab 03: Manage teams, collaboration and app settings for Teams

## Estimated Duration: 120 Minutes

# Student lab answer key

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership, and recovering deleted teams.

In managing collaboration in Microsoft Teams, you will manage chat and collaboration experiences such as team settings or private channel creation policies. Finally, you will manage settings for Teams apps such as app permission and app setup policies, Apps, bots & connectors in Microsoft Teams or publish a custom app in Microsoft Teams.

## **Objectives**

After you complete this lab, you will be able to:

- Create a Team from a Microsoft 365 Group

- Create a Team by using PowerShell

- Create a Team by using Microsoft Graph API

- Create a Team with dynamic membership

- Archive and unarchive Teams

- Delete and recover Teams

- Create a messaging policy

- Manage private channels

- Disable third-party storage providers

- Manage Policy packages

- Edit and test default org-wide app policy

- Edit and test default app permission policy

- Create and manage a custom app setup policy

## **Lab Setup**

- **Estimated Time:** 110 minutes.

## **Instructions**

### **Exercise 1: Manage team resources**

#### **Task 1 - Create a team from an existing Microsoft 365 group**

As part of your pilot project for Contoso, you need to modify the **IT-Department** Microsoft 365 group, created in an earlier lab, and add Teams features to it.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User04UPN" enableCopy="false"/> 

2. Select the **Teams** icon on the taskbar to start the Teams desktop client and sign in as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />**

   ![alt text](media/m1.png)
   
   ![alt text](media/m2.png)

4. Enter the **password (1)** - <inject key="User04UPN" enableCopy="false"/> and **sign in (2)**.
   
   ![alt text](media/m4.png)
   
5. The Microsoft Teams desktop client will start. If a **Bring your team together**, or **Get the Teams mobile app** window appears, close both windows.

6. In the left-hand navigation pane in **Chat**, select **Teams and Channels (1)** and **...** icon **(2)** under select **Your teams and channel (3)**, top right corner select **Create team (4)**.

   ![alt text](media/L3-e1-06.png)

7. In the **Create a team dialog**, select **More create team options** and then select From group.

  	![alt text](media/L3-e3-04.png)

8. In the **Create a team** dialog, select **From group**. In the **Which Microsoft 365 group do you want to use?** dialog, on the **IT-Department card**, select **Add team**. Wait until the **Creating the team…** process completes.

  	![alt text](media/L3-e3-08.png)

10. Select the **three dots (…)** right from the new team **IT-Department** in the left pane and select **Manage team**.

	![alt text](media/L3-e3-09.png)

11. Check the team owner and members:

	- Owners: **Joni Sherman (3)**

	- Members and guests: **Allan Deyoung** , **ODL User** and **Patti Fernandez (5)**

    	![alt text](media/L3-e3-10.png)

12. Leave the Teams desktop client open and continue to the next task.

You have successfully created a new team with the Teams desktop client, by using an existing Microsoft 365 group. Leave the Teams client open and continue with the next task.

#### **Task 2 - Create a team by using PowerShell**

In this task, you will create via the Teams PowerShell a new team **“Group_CA-OfficeCA01_”**. You will create the public channels **“Support”** and **“Recruiting”**. Additionally, you will create the private channel **“Administration”** via Teams PowerShell.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start (1)** button and then select **Windows PowerShell (2)**.

   ![alt text](media/m11.png)

3. Run the following cmdlet to connect to Microsoft Teams in your tenant:

    ```powershell
    Connect-MicrosoftTeams
    ```

5. A **Sign in** dialog box will open. Select **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />**

   ![alt text](media/m12.png)

6. In the **Enter password** dialog box, enter the **password** of **Joni Sherman’s** - <inject key="User04UPN" enableCopy="false"/> and then select **Sign in**.

   ![alt text](media/03.png)

1. Once you **SignIn**, Microsoft will ask if you would to **Stay signed in?**, Click on **No**

	![alt text](media/04.png)
	

7. Type the following cmdlet to the PowerShell window to create the new team **Group_CA-OfficeCA01_**:

    ```powershell
    New-Team -DisplayName "Group_CA-OfficeCA01_" -MailNickName "Group_CA-Office01_" -Visibility Public
    ```

8. To add the user **Alex Wilber** to the team type the following cmdlet 

    ```powershell
    Get-Team -DisplayName "Group_CA-OfficeCA01_" | Add-TeamUser -User <inject key="AlexWilber" enableCopy="false"/>
    ```

9. To add the user **Allan Deyoung** to the team type the following cmdlet 

    ```powershell
    Get-Team -DisplayName "Group_CA-OfficeCA01_" | Add-TeamUser -User <inject key="AllanDeyoung" enableCopy="false"/>
    ```

10. Create a channel **Support** in the **Group_CA-OfficeCA01_** team by using the following cmdlet:

    ```powershell
    Get-Team -DisplayName "Group_CA-OfficeCA01_" | New-TeamChannel -DisplayName "Support"
    ```

11. Create another channel **Recruiting** in the **Group_CA-OfficeCA01_** team by using the following cmdlet:

    ```powershell
    Get-Team -DisplayName "Group_CA-OfficeCA01_" | New-TeamChannel -DisplayName "Recruiting"
    ```

12. Create a private channel **Administration** in the **Group_CA-Office01_** team by using the following cmdlet:

    ```powershell
    Get-Team -DisplayName "Group_CA-OfficeCA01_" | New-TeamChannel -DisplayName "Administration" -MembershipType Private
    ```

13. Disconnect from the Microsoft Teams environment.  

    ```powershell
    Disconnect-MicrosoftTeams
    ```

14. Close the PowerShell window.

15. Open the Teams desktop client from the taskbar. On the left side pane with all teams, Joni is a member of the new **Group_CA-OfficeCA01_** team, where you can see a private channel below, named "Administration".

    ![alt text](media/L3-e1-t3-overview.png)

16. Close all browser windows and the Teams desktop client.

You have successfully created a team named **Group_CA-Office01_** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in the context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.

#### **Task 3 - Create a team by using Graph API**

In this task, you will test the Graph API capabilities for certain automation plans of your organization with Teams. For this task, you will create a new team, called **Early Adopters** with minimal settings, such as Public join options, and another team with multiple existing channels, called **Tech Meetings**.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Open Microsoft Edge, maximize the browser, and navigate to the **Graph Explorer** at: [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)

3. Select the **Sign in to Graph Explorer** button in the left of the page and sign in as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User04UPN" enableCopy="false"/> 

4. If you access the Graph Explorer for the first time, you will see a **Permissions requested** page. Select **Accept**.

5. Select the **GET** button and select **POST** from the dropdown menu.

6. Do not change the **v1.0** from the box in the middle.

7. Enter the following to the text box before the **Run query** button:

	- [https://graph.microsoft.com/v1.0/teams](https://graph.microsoft.com/v1.0/teams)

8. Select **Modify permissions (Preview)** from the top pane.

	![Graphical user interface, text, application, email Description automatically generated](media/L3-e1-t3-01.png) 

9. Scroll to the right and select the **Consent** button for the permissions **Team.Create**.

   ![alt text](media/m55.png)

10. Another **Permissions requested** page appears. Select **Accept**.

    ![alt text](media/m16.png)

11. If you are redirected to the Microsoft Developers site, navigate back to the **Graph Explorer** at: [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer)

12. Select the **Request body** tab and enter the following code:

    ```json
	{
  	"template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
 	 "displayName": "Group_EarlyAdopters_",
 	 "mailNickname": "Group_EarlyAdopters_",
  	 "description": "The Early Adopters Workspace.",
  	"visibility": "Public"
	}
	```

13. Select **Run** **query** from the upper right of the page.

14. After a moment, you should see a green bar below the Request body window, with a checkmark and an **Accepted** message.

15. Remove the whole content of the textbox in the textbox of **Request body**, you just used to create a team and replace it with the following content:

    ```json
	{
  	"template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
 	 "visibility": "Public",
  	 "displayName": "Group_TechMeetings_",
  	 "mailNickname": "Group_TechMeetings_",
  	 "description": "Space for all employees participating in the champions program, who want exchange each other about the newest features.",
  	 "channels": [
	{
      "displayName": "Welcome Hall",
      "isFavoriteByDefault": true,
      "description": "Channel for introducing yourself as a 	 member of the tech meeting participants."
   	},
    {
      "displayName": "Tech Lunch and Dinner",
      "isFavoriteByDefault": true,
      "description": "When will be the next tech lunch and who has any suggestions where to meet."
    },
    {
      "displayName": "Q and A",
      "description": "Questions and answers: Teams users giving a helping hand to other users.",
      "isFavoriteByDefault": true
    },
    {
      "displayName": "Issues and Feedback",
      "description": "Leave some feedback for the IT-Staff.",
      "isFavoriteByDefault": false
    }
 	 ],
 		"memberSettings": {
    	"allowCreateUpdateChannels": true,
    	"allowDeleteChannels": false,
    	"allowAddRemoveApps": true,
    	"allowCreateUpdateRemoveTabs": true,
    	"allowCreateUpdateRemoveConnectors": true
 	 },
 	 "guestSettings": {
     "allowCreateUpdateChannels": true,
     "allowDeleteChannels": false
  	},
  	"funSettings": {
    "allowGiphy": true,
    "giphyContentRating": "Moderate",
    "allowStickersAndMemes": true,
    "allowCustomMemes": true
 	 },
 	 "messagingSettings": {
    "allowUserEditMessages": true,
    "allowUserDeleteMessages": true,
    "allowOwnerDeleteMessages": true,
    "allowTeamMentions": true,
    "allowChannelMentions": true
  	},
 	 "discoverySettings": {
    "showInTeamsSearchAndSuggestions": true
 	 }
		}
	```

16. Select **Run** **query** from the upper right of the page.

17. After a moment, you should see a green bar with a checkmark and **Accepted** inside again.

    ![alt text](media/m54.png)
    
18. Open the Teams Desktop App. Select **Teams** from the left-side pane and inspect the newly created teams “**Early Adopters"** and”**Tech Meetings**".

You have successfully created two teams via Graph API. Your test of the Graph functionality is complete, and you can advance to the next exercise.

#### **Task 4 – Archive and unarchive a team**

After creating the different teams in this lab, you also need to evaluate the different ways of removing teams again. In this task, you will test the archiving function and change the Sales team to a non-activate state without deleting its content. This function is required for some company’s compliance requirements of retaining the stored data inside the teams. The only Teams administrative role with sufficient privilege for this task is the Teams Administrator, which is currently assigned to Joni Sherman, therefore you will use Joni’s account for this task.

1. Connect to the **Client 1 VM** and browser to the **Teams admin center**: [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User04UPN" enableCopy="false"/> 

2. Select **Teams** from the left-side pane and select the **Manage Teams**

3. Archive the **Sales** team

	1. Select the checkmark left from the **Sales** team and select **Archive** from the top pane.

		![](media/L3-e1-t4-01.png)

	2. Select the checkbox of **Make the SharePoint site read-only for team members** and select **Archive**.

		![](media/L3-e1-t4-02.png)

	3. The **Status** column should now have changed to **Archived**, written in orange color. Leave the browser open and proceed. If you have problems with the **Sales** team - archive another team (you can undo this action in the unarchive step).

		![](media/L3-e1-t4-03.png)

4. Check the archived team

	- Connect to the **Client 2 VM** and browse to the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins** **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User04UPN" enableCopy="false"/> 

	- Select Teams and channnels then select the **...**, then select **Your teams and channels**.

	- In the **Your teams and channels** page, select **3 more** and filter by **Archived Teams**. The **Sales** team appears with an archive icon. 

		![alt text](media/L3-e1-t4-04.png)

		![alt text](media/L3-e1-t4-05-1.png)

	- The **Sales team** appears with an archive icon. 

		![alt text](media/L3-e1-t4-06.png)

	- Select the **Sales team**, and then select the **Sales channel**. At the bottom of the conversation pane, confirm the **Post in channel** option is not available.

		![alt text](media/L3-e1-t4-07.png)

5. Unarchive the **Sales** team

	- Connect to the **Client 1 VM** again and browse to the Teams admin center as **Joni Sherman** <inject key="JoniSherman" enableCopy="false"/>  Enter the password - <inject key="User04UPN" enableCopy="false"/> 

	- Select the checkbox left from **Sales** again and select **Unarchive** from the top menu. The **Status** field should change to **Active** again.

		![alt text](media/L2-e1-t4-08.png)

6. Check the unarchived team

	- Connect to the **Client 2 VM** and browse to the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins**  **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** Enter the password - <inject key="User01UPN" enableCopy="false"/> 

	- On the left side, select **Teams**.

	- Notice that the text of the **Sales** team and the **General** channel changes back to normal after a moment, but the team is hidden.

	- Select the three dots (…) right from the Sales team and select **Show**.

7. Leave the browser open and stay signed in.

You have successfully archived a team and reviewed the limited functionality of archived teams. This fulfills the first requirement of testing the archiving function of teams for compliance preservation policies and rules. After this test, you have unarchived the team again, making it fully operational again.

#### **Task 5 - Delete and recover teams**

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Connect to the **Client 2 VM** and browse to the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins**  **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User01UPN" enableCopy="false"/> 

2. In the left-hand navigation pane of the Teams web client, select the three dots (…) right from the **Sales** team and select **Delete the team** from the list.

	![alt text](media/t5-01.png)

3. In the **Delete the Sales team**, select **I understand that everything will be deleted**. and select **Delete team**.

	![alt text](media/t5-02.png)

4. Restore group

	- Connect to the **Client1 VM** and browse to Entra admin center (https://entra.microsoft.com/) as **ODL User** <inject key="AzureAdUserEmail" enableCopy="false"/>
and **password:** <inject key="AzureAdUserPassword" enableCopy="false"/>

	- On the left navigation pane, select **Identity** > **Groups**.

	- On the **Groups** page, select **Deleted groups** in the left side pane.

	- Now you can see all deleted groups, including the **Sales** group.

	- Select the checkbox left from the **Sales** group and select **Restore group** from the top pane. Confirm the **Do you want to restore deleted groups dialog** by selecting **Yes**.

		![alt text](media/t5-03.png)

5. Check the restored group.

	1. Connect to **Client 2 VM** and browse to the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins**  **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User01UPN" enableCopy="false"/> 

	2. The **Sales** team appears in the list of teams again. Press **F5** to refresh the page if needed.

	3. Select the three dots (…) right from the team name and select **Manage team**. You can see the owner and all members again in the **Members** tab.

		![alt text](media/t5-06.png)

		> **Note:** The full process of deleting and restoring a team can take up to 24 hours. If it does not appear again, check for it at a later point in this lab.

You have successfully deleted a team via the Teams web client and restored it with the Azure Portal.

#### **Task 6 - Manage team members with dynamic membership**

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Connect to the **Client1 VM** and browse to Entra admin center (https://entra.microsoft.com/) as **ODL User** <inject key="AzureAdUserEmail" enableCopy="false"/>
and **password:** <inject key="AzureAdUserPassword" enableCopy="false"/>

2. On the left navigation pane, select **Identity** > **Groups** > **All groups**.

3. On the **Groups | All groups** page, search and select **Group_CA-OfficeCA01_** group.

	![alt text](media/t6-01.png)

4. On the **Group_CA-OfficeCA01_** page, select **Properties (1)** from the left-hand navigation pane.

5. Change the **Membership type (2)** from **Assigned** to **Dynamic User (3)**.

	![alt text](media/t6-02.png)

6. Select **Add dynamic query** below **Dynamic user members**.

7. On the **Dynamic membership rules** page, enter the following information to the fields:

	- Property: **accountEnabled (2)**

	- Operator: **Equals (3)**

	- Value: **true (4)**

8. Select **+add expression (5)** and enter the following information to the fields:

	- Property: **usageLocation (6)**

	- Operator: **Equals (7)**

	- Value: **CA (8)**

9. Select **Save (9)** twice.

	![alt text](media/t6-03.png)

	>**Note**: A warning message is displayed, that the membership will change according to the new dynamic membership rules. Select **Yes** to confirm the message.

11. Select **Overview** in the left-hand navigation pane of the **Group_CA-OfficeCA01_** group window.

12. In the Overview window, locate **Dynamic rule processing status** field.

	![alt text](media/t6-11.png)

	Wait and refresh your browser, until the status says **Succeeded**. It may take several minutes for the change to be processed.

13. Then select **Members** in the left-hand navigation pane and then select **Refresh**. Verify that **Alex Wilber** is in the list of members, but that **Allan Deyoung** has been removed from the group.

	![alt text](media/t6-12.png)

14. Select Owners from the left-hand navigation pane and verify, that Joni is still the Owner of the group, even if she does not match the dynamic group criteria.

You have successfully converted a Microsoft 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation “Canada” is added automatically to the team.

### **Exercise 2: Configure channel and message policies**

In this exercise, you will configure policies to manage the creation of new private channels and the available tools for users in chat.

#### **Task 1 - Create a messaging policy for giphy, memes, and stickers**

The company wants to restrict the use of graphic elements in Teams communication. As a Teams service administrator, you will create a new message policy that prohibits pilot users from using GIF files, memes, and stickers in the Teams chat and channel conversation.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the password - <inject key="User04UPN" enableCopy="false"/> 

2. In the left navigation of the Teams admin center, Scroll down and click on **Show all** . Select **Messaging (2)** from the left side navigation, then select **Messaging policies(3)**.

   ![alt text](media/m21.png)

3. Select **+Add** under **Manage Policies** tab and enter the following

   ![alt text](media/m22.png)

	- **Name (1)**: Regular users without fun stuff

	- **Description (2)**: Policy to disable giphys, stickers, and memes in conversations

	- **Giphys in conversations (3)**: Off

	- **Memes in conversations (4)**: Off

	- **Stickers in conversations (5)**: Off

	- Leave the rest of the settings as default. Select **Save (6)**.

      ![alt text](media/m23.png)

4. Back to the **Messaging policies** overview page, select the checkmark left to **Regular users without fun stuff (1)**. Then select **Assign users (2)**

   ![alt text](media/m24.png)

   **Note**: If you didn’t see **Assign users**, select **Manage users** to expand the menu.

5. Search and select **add** for the following pilot users. Then select **Apply** and **Confirm** when prompted.

	- **Alex Wilber**

	- **Lynne Robbins**

	- **Diego Siciliani**

      ![alt text](media/m25.png)

		>**Note**: It can take up to 24 hours for the settings to take effect.

In this task, you have successfully configured a new messaging policy and assigned it to the pilot users. It will now take some time for the policy to take effect. Continue with the next task.

#### **Task 2 - Manage private channels in a team**

As Teams administrator of Contoso, you will create a private channel named **confidential** in the sales team that is only accessible for some team members.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In the left navigation of the Teams admin center, select **Teams (1)** > **Manage teams (2)**.

   ![alt text](media/m27.png) 

3. Select the **Sales** team > **Channels** tab.

4. Add the private channel

	1. Select **+ Add** from the top menu.

       ![alt text](media/L3-e2-t2-01.png)

	2. In the **Add** window, enter the following information:

		- **Name**: Confidential sales

		- **Description**: Confidential private sales channel

		- **Privacy**: Private

		- **Team owner**: Lynne Robbins

   3. Select **Apply**.

		![alt text](media/L3-e2-t2-02.png)
  

5. Check the private channel

	1. Connect to the **Client 2 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Lynne Robbins** **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User01UPN" enableCopy="false"/> 

       ![alt text](media/m30.png)

	2. Select **Teams**, you should see the new private channel **Confidential sales** with a small padlock icon.

       ![alt text](media/m31.png)

In this task, you learned how to create a private channel in the Microsoft Teams admin center and how to configure and check the access.

### **Exercise 3: Manage app settings**

In the past, users stored data at various locations, including third-party storage providers. Recently, the company deployed OneDrive for all users and would like to guide the users to use SharePoint and OneDrive as the primary data storage locations with Box as an alternative for all file collaborations. As the Teams admin, you are asked to deactivate all third-party storage providers except Box in Microsoft Teams to align with the direction.

#### **Task 1 - Disable third-party storage providers**

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In left navigation of the Teams admin center, select **Teams (1)** > **Teams settings (2)**.

   ![alt text](media/m32.png)

3. On the **Teams settings** page, go to the **Files (1)** section.

4. Configure the following file sharing and cloud file storage options.

	- **Citrix files:** Off

	- **DropBox:** Off

	- **Box:** On

	- **Google Drive:** Off

	- **Egnyte:** Off

5. Scroll down and select **Save (3)** and confirm.

   ![alt text](media/m33.png)

	>**Note**: It can take up to 24 hours for the settings to take effect.

In this task, you have learned how to enable or disable third-party storage providers for your whole tenant.

#### **Task 2 - Block an app at organizational level**

In this task, you will block the Google Analytics app for all tenants

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In the left navigation of the Teams admin center, select **Teams apps(1)** > **Manage apps(2)**.

   ![alt text](media/m35.png)

3. On the **Manage apps** page, type **Google** in the search box and select **Google Analytics Insights**. 

   ![Graphical user interface, application Description automatically generated](media/m36.png)

4. In **Google Analytics Insights** page click on drop near Action and select **Block App**.

   ![alt text](media/m37.png)

5. On the top, you can notice pop up i.e., Blocked .

   ![alt text](media/m38.png)
   
	>**Note**: It can take up to 24 hours for the settings to take effect.

In this task, you have learned how to block the Google Analytics app for your tenant.

### **Exercise 4: Create and manage app setup policies**

As a Teams administrator you need to highlight the apps that are most important for your users and also showcase apps that users in your organization need, including apps built by third-parties or by parties or by developers in your organization.

#### **Task 1 - Edit default org-wide app policy**

In the pilot project, the company wants to add **Tasks by Planner and To Do** as the default app for all users. To do this, edit the default org-wide app policy. This task may take some time to propagate throughout the tenant.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In the left navigation of the Teams admin center, select **Teams apps** > **Setup policies**.

   ![alt text](media/m39.png)
   
3. On the **App setup policies** page, Under **Manage Policies,** select on **Global (Org-wide default)** to open the org-wide app policy.

   ![alt text](media/m40.png)
   
4. In the **Pinned apps** section, select **Add apps**.

   ![alt text](media/m41.png)
   
5. From the **Add pinned apps** page, type in the search box **Planner** app, mouseover the name and select **Add** twice.

   ![alt text](media/m42.png)

6. Make sure that **Planner** is now listed in the **Pinned apps** section then select **Save** and **Confirm**.

   ![alt text](media/m43.png)

	>**Note**: It can take up to 24 hours for the settings to take effect.

In this task, you learned how to pin default apps from the Microsoft Teams admin center.

#### **Task 2 - Create a custom app setup policy**

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman** **<inject key="JoniSherman" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Setup policies**.

3. Select **+** **Add**. 

  	![alt text](media/m44.png)
  
4. Enter the following information

	- Name: **Sales team (1)**
	- Description: **Install Adobe Acrobat Sign and pin Viva Goals (2)**.
	- User pinning: **On (3)**
	- To install apps for users:

		1. Under **Pinned apps**, select **Add apps (4)**.

		2. In the **Add pinned apps** pane, search for the apps you want to automatically install for users when they start Teams. 
		
		3. In the **Add pinned apps** pane, in the search box, type **Adobe**, and then next to **Adobe Acrobat Sign**, select **Select**.
			
		4. Select **Add** to add the app to the **Pinned apps** list.

	- To pin apps:

		1. Under **Pinned apps**, select **+ Add apps (4)**.

		2. In the **Add pinned apps** pane, in the search box, type **Viva Goals**, and then next to **Viva Goals**, select **Select**. 

		3. Select **Add**. 

		4. You can check them in the list the apps appears **(5)**.

5. Select **Save (6)**

	![alt text](media/e4-t2-01.png)
  
You have now created a new custom app set up policy.

#### Task 3 - Assign a custom app setup policy to users

1. In the left-hand navigation pane on the **Microsoft Teams admin center**, go to **Teams apps** > **Setup policies**.

2. Select **Sales team** app setup policy.

   ![alt text](media/m46.png)
  
3. Search for **Sales(1)** in the search bar. Select **Sales(2)** and from the drop down click **Assign users (3)**.
  
   ![alt text](media/m47.png)

4. In the **Manage users** pane, search for **Alex Wilber**, and then select **Add**.

5. Select **Apply and confirm**.

   ![alt text](media/m48.png)
 
### **Exercise 5: Test configured policy settings**

In this exercise, you will test the configured policy settings on a client with the affected user **Lynne Robbins** and compare the settings to the available client settings of **Joni Sherman**.

#### **Task 1 – Test the messaging policy and private channel access**

In this task, you will test the **messaging policies** configured in exercise 1 and compare the difference between an affected user (Lynne Robbins) vs a regular user(Joni Sherman).

1. Connect to the **Client 2 VM** and browse the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins** **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User01UPN" enableCopy="false"/> 

2. In the left-hand navigation pane, select **Chat** > **New Chat** icon.

	![Graphical user interface, application Description automatically generated with medium confidence](media/MS-700-lab_M03_ak_image8.png)

3. In the main pane, enter **Joni Sherman** to start the conversation.

   ![alt text](media/m49.png)
   
4. Notice there’s no **giphy**, **memes** and **stickers** icons.

### **Task 2 – Test blocked app and storage providers**

In this task, you will test the blocked app.

1. Connect to the **Client 2 VM** and browse the [**Microsoft Teams web client (https://teams.microsoft.com/)**](https://teams.microsoft.com/) as **Lynne Robbins** **<inject key="LynneRobbins" enableCopy="false" style="color:blue" />** and Enter the **password** - <inject key="User04UPN" enableCopy="false"/> 

2. In the left-hand navigation select **Apps**.

3. Search **Google** from the search box.

4. In the search results select **Google Analytics Insights**. Note the lock icon and the "Request " button.

   ![alt text](media/m53.png) 
   
5. In the left-hand navigation pane, select **Teams**, go to the **Sales (1)** channel, select **shared (2)**, click on **3 dots (3)**and select **copy link (4)**.

   ![alt text](media/m51.png)

6. Notice that you only see SharePoint and Box as options, the cloud file storage settings in Teams settings worked as expected.

   ![alt text](media/m52.png)

7. Sign out of Teams and close all open windows.

### You have successfully completed this lab. 

## Support Contact
 
The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.
 
Learner Support Contacts:
 
- Email Support: [cloudlabs-support@spektrasystems.com](mailto:cloudlabs-support@spektrasystems.com)
- Live Chat Support: https://cloudlabs.ai/labs-support
 
### Click **Next >>** from the bottom right corner to embark on your Lab journey!
 
![Start Your Azure Journey](./media/Next.png)
 
Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!