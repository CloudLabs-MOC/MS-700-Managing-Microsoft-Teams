# **Lab 02: Configure security and compliance for Microsoft Teams**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course, you will assume the role of the Global Administrator for Contoso Ltd. Your organization is planning to deploy Microsoft Teams. Before starting the deployment, IT department is gathering business requirements about data security and compliance, including how the data shared in Teams be regulated according to the organization’s compliance requirements. After you complete the planning process, you will protect Teams from threats, and configure Teams to meet your organization compliance requirements.

## **Objectives**

After you complete this lab, you will be able to:

- Configure guest access in Azure and Teams

- Review Access to a resource

- Activate, create and assign sensitivity labels

- Activating Safe Attachments for SharePoint, OneDrive and Teams

- Create, configure and test retention policies

- Create and test a DLP policy to protect GDPR content

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage guest access for Microsoft Teams**

In this exercise, you will test the guest access features in Microsoft 365. To do so, you will configure guest access in Azure AD, add a new external guest user and revoke the guest access by using access reviews.



#### Task 1 - Review guest access settings (optional)

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. In left navigation of the Azure AD admin center, select **Users**> **User settings** > **Manage external collaboration settings**. Review the following settings for external users at the Azure AD level:

	* **Guest user access**: Guest users have limited access to properties and memberships of directory objects.

	* **Guest invite settings**: Anyone in the organization can invite guest users including guests and non-admins (most inclusive).

	* **Collaboration restrictions**: Allow invitations to be sent to any domain (most inclusive)

3. Browse to Microsoft 365 admin center (https://admin.microsoft.com/) as **MOD Administrator**.

4. In left navigation of the Microsoft 365 admin center, select **Settings** > **Org settings**.

	1. Under the **Services** tab, select **Microsoft 365 Groups**. Make sure the checkbox is selected for **Let group owner add people outside your organization to Microsoft 365 Groups**.

	2. Under the **Security & privacy** tab, select **Sharing**. Make sure the checkbox is selected for **Let users add new guests to the organization**.


You have now reviewed guest access settings across different admin centers. You are ready to invite guest for collaboration. 


#### Task 2 - Configure guest access in Teams

Now that you have explored the Teams admin center it is time to configure the first setting. Since this task will take some time to replicate through the tenant, you will configure the guest user access for Microsoft Teams right now, so it is available for later use.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Users** > **Guest access**.

3. On the **Guest access** page, check if **Allow guest access in Teams** is enabled. If not, select **On**.

4. Under **Messaging** section, disable **Delete sent messages**

5. Select **Save**.

You have now successfully activated guest access and disallow guests to delete their sent messages for Teams in your tenant.

#### Task 3 - Add a guest to a team
In this task, you will add a guest user by inviting the guest to the team **Afterwork** you created from Lab 1. 

You will change the default settings for inviting/creating guest users and then add your personal Outlook.com account as a guest user to your tenant.

**Note**: You will need an Outlook.com account for this exercise. If you don’t have an outlook account like, you can create a new account from [**https://outlook.com**](https://outlook.com/).

1. Connect to the **Client 2 VM** and open the **Teams desktop client** (https://teams.microsoft.com/) as **Alex Wilber** (AlexW@&lt;YourTenant&gt;.onmicrosoft.com)

2. Add the guest to **Afterwork** team.
	
	1. Select **Teams** > Select **...** next to the **Afterwork** team.

	2. Select **Add member** and enter your outlook account. 

	3. You will see a message **add &lt;Your outlook account&gt; as a guest**. Select the message and select **Add**. 

3. Accept the guest invite

	1. Open a **New InPrivate window** and check the email with subject **You have been added as a guest to Contoso in Microsoft Teams** from **Outlook Web Portal** (https://outlook.live.com/owa/).

	2. Select **Open Microsoft Teams** from the email. You will be redirected to the sign in page with permission consent request. 
	
	3. Select **Accept** and sign in to Teams web client with your outlook account. 

	4. From the Teams client, select **Teams**, you will see the team **Afterwork**.

4. Test the guest access

	1. Under the team **Afterwork**, select **General** channel, and send the message: **Hello!**.

	2. Select **...** of the message you just posted. Notice there's no **Delete** option. 

You have successfully invited a guest to a team and validate the guest access setting from previous task. 

#### Task 4 - Create access reviews

As a part of your system administrator role, you need to review access to resources in your tenant on a regular basis. You can do that by creating an access reviews.

1. Connect to the **Client 1 VM** and browse to Azure AD admin center (https://aad.portal.azure.com/) as **MOD Administrator**. 

2. Create an access review to monitor guest users.

	In left navigation of the Azure AD admin center, select **All Services** and on right pane select **Identity Governance** > **Create an access review**. Follow the wizard with the following information:

	1. On the **Review type** tab:
	
		* In the **Select what to review** section, select **Teams + Groups**.
		* In the **Select which Teams + Groups** section, select **All Microsoft 365 groups with guest users.** 
		* In the **Select review scope** section, select **Guest users only**. 
		* Select **Next: Reviews**.

	2. On the **Reviews** tab:
	 
		* In the **Select reviewers** section, select **Group owner(s)**.* In the **Specify recurrence of review** section, select **Weekly** and keep rest as default. 
		* Select on **Next: Settings**.

	3. On the **Settings** tab, leave the settings as default. Select on **Next: Review+Create** > **Create**. 

3. Review the access review dashboard from Azure AD.

	1. On the **Identity Governance | Access reviews** page, you will see an access review report named **Review guest access across Microsoft 365 groups**

	2. Wait for a few minutes, when the **Status** of the report shows as **Active**, select on the name of the report - **Review guest access across Microsoft 365 groups**.

	3. On the **Review guest access across Microsoft 365 groups | Overview** page, select **Afterwork** under group name.

	4. On the **Afterwork | Overview** page, you can see there's one users show under **Not reviewed** category. 

4. Review the access review and approve the guest user. 

	1. Connect to the **Client 2 VM** and browse to the **Outlook.com** (https://outlook.office.com/) as **Alex Wilber** (AlexW@&lt;YourTenant&gt;.onmicrosoft.com). You can open an InPrivate window.

	2. Check the email with the subject **Action required: Review group access**.

	3. Select **Start review >** in the content of the email. 

	4. From the **My Access** (Https://myaccess.microsoft.com) page, select **Review guest access across Microsoft 365 groups**. 

	5. On the **Review guest access across Microsoft 365 groups** page, select the guest account and select **Approve**. 
	
	6. From the **Approve continued access** window, enter **Approved.** to the textbox, and select **Submit**

You have successfully created an access review and approved a guest user in your tenant. 


### **Exercise 2: Implement security for Microsoft Teams**

In this exercise, you will increase the security level in your organization by configuring Safe Attachments to ensure that no malicious content is sent through documents shared in Teams by blocking attachments that contain malware.

#### Task 1 - Configure Safe Attachments for Microsoft Teams

Users in your organization are using Microsoft Teams for communication and collaboration. Business managers are concerned that documents that are shared within Microsoft Teams may contain malware. You will need to ensure that no malicious content is sent through documents shared in Teams by configuring Safe Attachments that blocks documents that contain malware.

1. Connect to the **Client 1 VM** and browse to Microsoft 365 Defender portal (https://security.microsoft.com/) as **MOD Administrator**. 

2. In left navigation of the Microsoft 365 Defender portal, select **Policies & rules** \> **Threat policies** \> **Safe Attachments** in the **Policies** section.

3. On the Safe attachments page, select **Global settings**.

4. In the Global settings fly out that appears, turn on the toggle under **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams**.

5. Select **Save**.


In this task, you have activated Safe Attachments scanning for SharePoint, OneDrive, and Microsoft Teams that blocks documents that contain malware.

END OF LAB