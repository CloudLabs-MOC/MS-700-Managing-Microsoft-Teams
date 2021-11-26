# **Lab 05: - Manage Teams meetings experiences**

# **Student lab answer key**

## **Lab Scenario**

In the labs of this course you will assume the role of Joni Sherman, a Teams Administrator for Contoso Ltd. and her pilot team that shall evaluate the capabilities of Microsoft Teams in a testing environment. Teams admins need to configure conferencing functionalities, such as meetings and live event features that will provide best user experience during collaboration and communication. 

Furthermore, your organization is planning to purchase and deploy multiple Teams devices. You will need to evaluate different devices profiles and configure profile settings for the devices. At the end, you will need to evaluate the process of creating Microsoft Teams room, where multiple Teams’ rooms will be purchased in your organization.

## **Objectives**

After you complete this lab, you will be able to:

- Manage meeting policies

- Configure meeting settings

- Create live event policies

- Create a webinar

- Create configuration profiles for devices

- Configure a new Microsoft Teams Room

## **Lab Setup**

- **Estimated Time:** 90 minutes.

## **Instructions**

### **Exercise 1: Manage Live event and meetings experiences**

Contoso organization has deployed Microsoft 365 and is testing pilot projects on collaboration and communication scenarios to meet business requirements. The Teams admin will configure meeting policies and schedule an initial webinar for testing purpose. 

#### Task 1 - Edit the default meeting policy and restrict all recording features for meetings

As part of your pilot project for setting up the events and meetings in your organization, you need to fulfill the requirement for all meetings in teams, including prohibiting meeting recording. You will edit the default meeting policy to ensure that this requirement is met.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Meetings** > **Meeting policies**.

3. Select the **Global (Org-wide default)** policy.

4. On the **Meetings policies\Global** page, turn **Off** the **Allow cloud recording** setting under the **Recording &amp; transcription** section. 

5. Select **Save**.

You have successfully modified the Global (Org-wide default) meeting policy and disabled the recording functionality for meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 2 – Test the meeting policy for restricting recording

In this task you need to sign in to the second client and create a meeting with a user. You will see how the configured policy works and users won’t be able to record a meeting.

1. Connect to the **Client 2 VM**  and browse to the **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Lynne Robbins** (LynneR@&lt;YourTenant&gt;.onmicrosoft.com).

2. Select **Calendar** from the left navigation pane.

3. Select **Meet Now** > **Start meeting** from the upper right corner.

4. Select **Join now** to start the meeting.

5. In the meeting window, select … for **More actions**.

6. Notice that you can't select **Start recording**.

#### Task 3 - Configure meeting settings and restrict anonymous users from joining meetings

Contoso Ltd. works with several external partners, and users often schedule meetings with external partners for projects collaboration. However, according to the company regulations, external partners need to identify themselves with a valid account, and anonymous access needs to be forbidden. You need to configure Microsoft Teams to disable anonymous access to meetings.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Meetings** > **Meetings settings**.

3. On the **Meetings settings** page, turn **Off** the option **Anonymous users can join a meeting** in the participants section.

4. Select **Save**.

You have successfully modified the meeting settings for all users in your tenant and disabled anonymous access to any meetings. It will take some time for the changes to be applied to the users, so you will continue with the next task and test the configured settings at the end of this lab.

#### Task 4 - Create a new live event policy and restrict recording capabilities

Contoso Ltd. wants to broadcast video and meeting content to large online audiences. As a Teams admin, you need to evaluate live events functionalities, including creating live events and configuring live event policies. According to Contoso Ltd. business requirements, you will need to restrict the recording options for participants of meetings and only allow recording options to management users. Only the organizer of a live event should be able to record his own meetings.

1. Connect to the **Client 1 VM** and browse to Teams admin center (https://admin.teams.microsoft.com) as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. In left navigation of the Teams admin center, select **Meetings** > **Live event policies**.

3. Select **+ Add** from the top menu.

4. On the **Live event policies\Add** page, enter the following information:

	- Add live events policy: **Management Live Events**

	- Description: **Recording Restriction for live events organized by managers**

	- Allow scheduling: **On**

	- Allow transcription for attendees: **Off**

	- Who can join scheduled live events: **Everyone in the organization**

	- Who can record an event: **Organizer can record**

5. Select **Save**.

6. Back on the **Live events policies** page, select **Management Live Events** policy and select **Manage users** from the top menu.

7. In the **Manage users** pane, search and add **Lynne Robbins**.

8. Select **Apply** to assign the policy to the selected user.

You have successfully created a custom Live event policy and assigned it to a user.

#### Task 5 – Create a webinar 

The IT department wants to host a company-wide meeting to answer employees' questions regarding the new reporting system. As a Teams admin, you will create a webinar allowing employees to submit their questions before the meeting. 

1. Connect to the **Client 1 VM** and browse to **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Joni Sherman**  (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).

2. On the left navigation pane select **Calendar**.

4. Select the dropdown menu **New meeting** and select **Webinar**.

5. Create a new **webinar**:

	- **Title**: IT Office Hours
	- **Start/End**: Select a time close to your current time 
	- **Presenters**: Patti Fernandez, Allan Deyoung

6. Select **View registration form** and enter the following information: 

	1. **Title**: IT Office Hours
	2. Select **+ Add field** > **Custom question** > **Input**.
	3. Enter the following to the textbox below **Custom question**:

		*What is your question about the new reporting system?*
	
	 **Start/End**: Select a time close to your current time 
	4. Select **Save**
	5. Select **Copy registration link** and paste it to the **General** channel of the **IT Support** team.
		
7. Test the meeting registration. 

	1. Stay in the **Client 1 VM** and browse to **[Microsoft Teams web client (https://teams.microsoft.com/)](https://teams.microsoft.com/)** as **Joni Sherman** (JoniS@&lt;YourTenant&gt;.onmicrosoft.com).
	
	2. Go to the **General** channel of the **IT Support** team and select the registration link that you posted.

	3. Fill out the registration form and select **Register now**.

	4. Go to **Outlook Web Portal** (https://outlook.live.com/owa/), and check the email with subject **You're registered for IT Office Hours**

You have successfully created a webinar with a custom registration form.

END OF LAB
