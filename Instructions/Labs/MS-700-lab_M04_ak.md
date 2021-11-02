# **Lab 04: Manage teams and collaboration settings for Teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. In this lab, you will perform operational tasks as a Teams administrator, such as creating and modifying teams, managing membership, and recovering deleted teams. 

In managing collaboration in Microsoft Teams, you will manage chat and collaboration experiences such as team settings or private channel creation policies. Finally, you will manage settings for Teams apps such as app setup policies, Apps, bots & connectors in Microsoft Teams or publish a custom app in Microsoft Teams.

## **Objectives**

After you complete this lab, you will be able to:

- Create a Team from a Microsoft 365 Group

- Create a Team by using PowerShell

- Create a Team with dynamic membership

- Archive and unarchive Teams

- Delete and recover Teams

- Create a messaging policy

- Manage private channels

- Disable third-party storage providers

- Manage Policy packages

- Edit and test default org-wide app policy

- Edit and test default app permission policy


## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage team resources**

#### Task 1 - Create a team from an existing Microsoft 365 group

As part of your pilot project for Contoso, you need to modify the **IT-Department** Microsoft 365 group, created in an earlier lab, and add Teams features to it.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. Select the **Teams** icon on the taskbar to start the Teams desktop client and sign in as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.OnMicrosoft.com).

3. The Microsoft Teams desktop client will start. If a **Bring your team together**, or **Get the Teams mobile app** window appears, close both windows.

4. In the left-hand navigation pane, select **Teams**, select **Join or create a team**, and then select **Create team** from the middle of the window.

5. In the **Create a team** dialog, select **From a group or team**.

6. In the **Create a new team from something you already own** dialog, select **Microsoft 365 group**.

7. In the **Which Microsoft 365 group do you want to use?** dialog, select the group **"IT-Department"**, then select **Create**. Wait until the **Creating the team…** process is done.

8. Select the three dots (**…**) right from the new team in the left pane and select **Manage team**.

9. Check the team owner and members:

	- Owners: **Joni Sherman**
	- Members and guests: **Allan Deyoung** and **Alex Wilber**

10. Leave the Teams desktop client open and continue to the next task.

You have successfully created a new team with the Teams desktop client, by using an existing Microsoft 365 group. Leave the Teams client open and continue with the next task.


#### Task 2 - Create a team by using PowerShell

In this task, you will create via the Teams PowerShell a new team **"CA-Office"**. You will create the public channels **"Support"** and **"Recruiting"**. Additionally, you will create the private channel **"Administration"** via Teams PowerShell.

1. Connect to the **Client 1 VM** with the credentials that have been provided to you.

2. On the taskbar at the bottom of the page, right select the **Start** button and then select **Windows PowerShell**.

3. Run the following cmdlet to connect to Microsoft Teams in your tenant:

    ```powershell
    Connect-MicrosoftTeams
    ```

4. A **Sign in** dialog box will open. Enter the **UPN** of **Joni Sherman’s** credential provided to you (for example, JoniS@&lt;YourTenant&gt;.onmicrosoft.com) and then select **Next**.

5. In the **Enter password** dialog box, enter the **password** of **Joni Sherman’s** credential provided to you and then select **Sign in**.

6. Type the following cmdlet to the PowerShell window to create the new team **CA-Office**:

    ```powershell
    New-Team -Displayname "CA-Office" -MailNickName "CA-Office" -Visibility Public
    ```

7. To add the user **Alex Wilber** to the team type the following cmdlet (Replacing **&lt;YourTenant&gt;** with the name of the Microsoft 365 Tenant provided to you.):

    ```powershell
    Get-Team -Displayname "CA-Office" | Add-TeamUser -User AlexW@<YourTenant>.onmicrosoft.com
    ```

8. To add the user **Allan Deyoung** to the team type the following cmdlet (Replacing **&lt;YourTenant&gt;** with the name of the Microsoft 365 Tenant provided to you.):

    ```powershell
    Get-Team -Displayname "CA-Office" | Add-TeamUser -User AllanD@<YourTenant>.onmicrosoft.com
    ```

9. Create a channel **Support** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Support"
    ```

10. Create another channel **Recruiting** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Recruiting"
    ```

11. Create a private channel **Administration** in the **CA-Office** team by using the following cmdlet:

    ```powershell
    Get-Team -Displayname "CA-Office" | New-TeamChannel -DisplayName "Administration" -MembershipType Private
    ```

12. Disconnect from the Microsoft Teams environment.  

    ```powershell
    Disconnect-MicrosoftTeams
    ```

13. Close the PowerShell window.

14. Open the Teams desktop client from the taskbar. On the left side pane with all teams Joni is a member of the new **CA-Office** team, where you can see a private channel below, named "Administration".

15. Close all browser windows and the Teams desktop client.

You have successfully created a team named **CA-Office** with the members Alex Wilber and Allan Deyoung. Joni Sherman is the only team owner. Note that you did not specify any owner in the PowerShell cmdlet and because it was run in context of Joni, she was added as owner automatically. Furthermore, you have created the public channels named **Support** and **Recruiting**, as well as the private channel named **Administration**.


#### Task 2 – Archive and unarchive a team

After creating the different teams in this lab, you also need to evaluate the different ways of removing teams again. In this task you will test the archiving function and change the Sales team to a non-activate state without deleting its content. This function is required for some company’s compliance requirements of retaining the stored data inside the teams. The only Teams administrative role with sufficient privilege for this task is the Teams Administrator, which is currently assigned to Joni Sherman, therefore you will use Joni’s account for this task.

1. Connect to the **Client 1 VM** and browser to the **Teams admin center**: [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com/) as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. Select **Teams** from the left-side pane and **Manage teams**.

3. Archive the **Sales** team

	1. Select the checkmark left from the **Sales** team and select **Archive** from the top pane.

	2. Select the checkbox of **Make the SharePoint site read-only for team members** and select **Archive**.

	3. The **Status** column should now have changed to **Archived**, written in orange color. Leave the browser open and proceed. If you have problems with the **Sales** team - archive another team (you can undo this action in the unarchive step).

4. Check the archived team

	1. Connect to the **Client 2 VM**  and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

	2. On the left side, select **Teams** > **Manage Teams** gear icon next to **Join or create a team**.

	3. Expand **Archived** section, and select **Sales** team. You can see the **Sales** team shows up under the **Hidden teams** section. 

	4. Select **General** channel under the **Sales** team, notice the **New conversation** option is not available. 

5. Unarchive the **Sales** team

	1. Connect to the **Client 1 VM** again and browse to the Teams admin center as **Joni Sherman**.
	
	2. Select the checkbox left from **Sales** again and select **Unarchive** from the top menu. The **Status** field should change to **Active** again.

6. Check the unarchived team

	1. Connect to the **Client 2 VM**  and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

	2. On the left side, select **Teams**.

	3. Notice that the text of the **Sales** team and the **General** channel changes back to normal after a moment, but the team is hidden. 
	
	4. Select the three dots (…) right from the Sales team and select **Show**.

7. Leave the browser open and stay signed in.

You have successfully archived a team and reviewed the limited functionality of archived teams. This fulfills the first requirement of testing the archiving function of teams for compliance preservation policies and rules. After this test, you have unarchived the team again, making it fully operational again. 

#### Task 3 - Delete and recover teams

In this task, you will delete one of the teams created in the previous lesson and learn how to restore it.

1. Connect to the **Client 2 VM**  and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. In the left-hand navigation pane of the Teams web client, select the three dots (…) right from the **Sales** team and select **Delete the team** from the list.

3. In the **Delete the Sales team**, select **I understand that everything will be deleted**. and select **Delete team**.

4. Restore group

	1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

	2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

	3. On the **Groups | All groups** page, select **Deleted groups** in the left side pane.

	4. Now you can see all deleted groups, including the **Sales** group.

	5. Select the checkbox left from the **Sales** group and select **Restore group** from the top pane. Confirm the **Do you want to restore deleted groups dialog** by selecting **Yes**.

5. Check the restored group.

	1. Connect to **Client 2 VM** and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

	2. The **Sales** team appears in the list of teams again. Press **F5** to refresh the page if needed.

	3. Select the three dots (…) right from the team name and select **Manage team**. You can see the owner and all members again in the **Members** tab.

**Note:** The full process of deleting and restoring a team can take up to 24 hours. If it does not appear again, check for it at a later point of this lab.

You have successfully deleted a team via the Teams web client and restored it with the Azure Portal.

#### Task 4 - Manage team members with dynamic membership

Contoso is expanding to Canada and will open a new office in Toronto. As a system administrator, you need to configure a dynamic group with membership based on the location of the Office 365 services.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. On the left navigation pane, select **Azure Active Directory** > **Groups**.

3. On the **Groups | All groups** page, search and select **CA-Office** group.

4. On the **CA-Office** page, select **Properties** from the left-hand navigation pane.

5. Change the **Membership type** from **Assigned** to **Dynamic User**. 

6. Select **Add dynamic query** below **Dynamic user members**.

7. On the **Dynamic membership rules** page, enter the following information to the fields:

	- Property: **accountEnabled**

	- Operator: **Equals**

	- Value: **true**

8. Select **+add expression** and enter the following information to the fields:

	- Property: **usageLocation**

	- Operator: **Equals**

	- Value: **CA**

9. Select **Save** twice.

10. A warning message is displayed, that the membership will change according to the new dynamic membership rules. Select **Yes** to confirm the message.

11. Select **Overview** in the left-hand navigation pane of the **CA-Office** group window.

12. In the Overview window, locate **Membership processing status** field.

	Wait and refresh your browser, until the status says **Update complete**. It may take several minutes for the change to be processed.

13. Then select **Members** in the left-hand navigation pane and then select **Refresh**. Verify that **Alex Wilber** is in the list of members, but that **Allan Deyoung** has been removed from the group.

14. Select Owners from the left-hand navigation pane and verify, that Joni is still the Owner of the group, even if she does not match the dynamic group criteria.

You have successfully converted a Microsoft 365 group from static (assigned) to dynamic membership. This membership is controlled by the usageLocation of the user and if the account is enabled. Any user with the usageLocation "Canada" is added automatically to the team.


### **Exercise 2: Configure channel and message policies**

In this exercise you will configure policies to manage the creation of new private channels and the available tools for users in chat.

#### Task 1 - Create messaging policy for giphy, memes and stickers

The company wants to restrict the use of graphic elements in Teams communication. As a Teams service administrator, you will create a new message policy that prohibits pilot users from using GIF files, memes, and stickers in the Teams chat and channel conversation.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Messaging policies**.

3. Select **+ Add** from the top pane.

4. On the **Messaging policies \ Add** page, enter the following:

	- **Name**: Regular users without fun stuff
	- **Description**: Policy to disable giphys, stickers, and memes in conversations

	- **Use Giphys in conversations**: Off
	- **Use Memes in conversations**: Off
	- **Use Stickers in conversations**: Off
	- Leave the rest of the settings as default. Select **Save**.

5. Back to the **Messaging policies** overview page, select the checkmark left to **Regular users without fun stuff**. Then select **Manage users** in the top navigation pane. 

	**Note**: If you didn't see **Manage users**, select ... to expand the menu. 

8. Search and select **add** for the following pilot users. Then select **Apply**.

	- **Alex Wilber**
	- **Lynne Robbins**
	- **Diego Siciliani**

**Note**: It can take up to 24 hours for the settings to take effect.

In this task, you have successfully configured a new messaging policy and assigned it to the pilot users. It will now take some time for the policy to take effect. Continue with the next task.

#### Task 2 - Manage private channels in a team

As Teams administrator of Contoso, you will create a private channel named **confidential** in the sales team that is only accessible for some team members.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Teams** > **Manage teams**. 

3. Select the **Sales** team > **Channels** tab. 

4. Add the private channel

	1. Select **+ Add** from the top menu.
	2. In the **Add** window, enter the following information:

		- **Name**: Confidential sales
		- **Description**: Confidential private sales channel
		- **Type**: Private
		- **Channel owner**: Lynne Robbins
	3. Select **Apply**.

5. Check the private channel

	1. Connect to the **Client 2 VM** and browse to the **Teams Web Client** [(https://teams.microsoft.com)](https://teams.microsoft.com/) as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

	2. Select **Teams**, you should see the new private channel **Confidential sales** with a small padlock icon.

In this task you learned how to create a private channel in the Microsoft Teams admin center and how to configure and check the access. 

END OF LAB
