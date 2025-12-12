![Public Sector Accelerators logo](/docs/Logo_GPSAccelerators_v01.png)

# Volunteer Management Quick Start

https://sfdc.co/volunteer-quick-start

## Description

Streamline volunteer initiatives and volunteer sign-up, attendance, and reporting in Nonprofit Cloud.

The **Volunteer Management Quick Start** Accelerator helps nonprofits stand up a ready-to-use volunteer management solution on Salesforce Nonprofit Cloud. Designed to reduce setup complexity, it delivers a complete foundation for managing both event-based and skill-based volunteer opportunities on the new Volunteer Management (new as of the Summer '25 release).

With this Accelerator, organizations can create, publish, and track volunteer initiatives, job positions, and shifts \-- all supported by streamlined Experience Cloud guest access for easy registration. Volunteers can sign up without logging in, while staff can efficiently track attendance, manage locations, and capture valuable engagement data for reporting.

Key benefits include:

**For Volunteer Coordinators & Staff**
* Create and manage volunteer initiatives and job positions with consistent page layouts and fields.  
* Track volunteer attendance and mark absences/completions.  
* Manage physical location and address information for volunteer opportunities.  
* Access comprehensive reporting on volunteer metrics across initiatives, shifts, and donor engagement.  
* Send personalized volunteer registration links for specific initiatives, positions, and shifts.

**For Volunteers**
* Simple, dynamic registration without authentication for volunteer opportunities based on initiative, job position, or shift.

**For System Administrators**
* Preconfigured Experience Cloud guest access and flow for volunteer registration.  
* Quick actions and flows for volunteer attendance tracking.  
* Flows that automate populating the standard Volunteer Management data model.  
* Out-of-the-box reports and report types you can tailor for managing volunteers, initiatives, and shifts.  

With its streamlined setup and pre-built flows, the Volunteer Management Quick Start accelerates time-to-value and empowers nonprofits to easily launch their volunteer program on Salesforce Nonprofit Cloud.

### Included Assets

An unmanaged package (link in the installation section of this document; metadata is also found in the /force-app/main/default/ folder) that includes:

An extensive list of included asseters can be in the repo in the Included Assets text.

### Documentation, including:

This readme file

* Volunteer Management Data Model
  * [Diagram: Volunteer Management Data Model](https://developer.salesforce.com/docs/atlas.en-us.nonprofit_cloud.meta/nonprofit_cloud/volunteer_mgmt_volunteer_management_data_model.htm)  
  * [Article:  Volunteer Management Standard Objects](https://developer.salesforce.com/docs/atlas.en-us.nonprofit_cloud.meta/nonprofit_cloud/volunteer_mgmt_standard_objects.htm)  
* Release Notes
  * [Summer ‘25 Release Notes](https://help.salesforce.com/s/articleView?id=release-notes.rn_nonprofit_volunteer_management.htm&release=256&type=5)  
  * [Winter ‘26 Release Notes](https://help.salesforce.com/s/articleView?id=release-notes.rn_nonprofit_volunteer_management.htm&release=258&type=5)  
* [Experience Cloud Related Documentation](https://help.salesforce.com/s/articleView?id=experience.networks_setup_maintain_communities.htm&type=5)  
* [Guest User Security and Sharing Documentation](https://help.salesforce.com/s/articleView?id=platform.networks_secure_community.htm&type=5)

### License Requirements

* Nonprofit Cloud with the Volunteer Management permission set (internal users);   
* No license required for volunteer registration (external users) using guest user access. However at least one Experience Cloud license (either member or login) with an Industry Cloud entitlements is necessary to activate the guest user access.

### Accelerator or Technology-Specific Assumptions

This accelerator was built and designed primarily for the needs of an event based volunteering use case and the creation of volunteer activities focused on physical labor. The Experience Cloud page is set up to provide an easy registration experience collecting just the volunteers first name, last name, and email address. 

The package doesn’t include a volunteer application, or a process to capture volunteer interest or inquiries.

It does represent the manual tracking of examinations that could be used to track background checks but it doesn’t include any automation or integration with background check providers. 

The package assumes that volunteer qualifications are measured by broad levels (Beginner, Intermediate, Advanced) rather than quantified scores (0-100). It maps those broad levels to numbers to ensure functionality for the “Search for Volunteers” interface. 

It includes a custom Lighting app, and uses that instead of the standard Lighting app that is included with Volunteer Management. This is to simplify the assignment of the included Lightning pages.

It also assumes that the required information for each volunteer activity is a named individual, a date, and the number of hours they served. The Volunteer Management data model stores this information on the Job Position Assignment object and this Quick Start package determines this is stored using the fields Assigned Account, Actual Start Time, and Actual Start Duration. 

The Volunteer Management product and data model includes fields for rollups but as of Winter ‘26 release doesn’t include any automation to calculate those rollup fields. This Quick Start package includes some sample flows to make those calculations, however these flows will only be appropriate for low data volumes. Organizations should consider alternative approaches, including using standard reports, custom data process engine (DPE), or Declarative Lookup Rollup Summaries (DLRS). 

## Implementation Steps

### Before You Install  If you are a new customer we encourage you to install the Volunteer Management accelerator into a base org available here: [https://www.salesforce.com/form/sfdo/signup/nonprofit/nonprofit-cloud-base-trial/](https://www.salesforce.com/form/sfdo/signup/nonprofit/nonprofit-cloud-base-trial/) 

You can see a video of a walk through of the instructions: [https://salesforce.vidyard.com/watch/85puvWFuteRB8KKr2esP5o](https://salesforce.vidyard.com/watch/85puvWFuteRB8KKr2esP5o)

1. Enable Person Accounts  
   1. From Setup, enter ‘Person Accounts’ in the Quick Find box, and then select **Person Accounts**.  
   2. Go through the steps listed on the Setup page.  
   3. Turn on Person Accounts.  
   4. After Person Accounts is enabled, a Person Account object with a corresponding person account record type is created. You can create additional record types on Person Account as needed.  
   5. Assign the person account record type to user profiles.  
2. Assign the ‘Volunteer’ Permission Set Group to all users involved in configuration.  
   1. From Setup, in the Quick Find box, enter ‘Permission Set Groups’, and then select **Permission Set Groups**.   
   2. Click the permission set group **Volunteer\_Management\_User** in the list view.  
   3. Assign your user to the Permission Set Group  
      1. Click Manage Assignments and then Add Assignments.  
      2. Select each user to whom you want to assign the group, and then click Next.  
      3. Optionally, select an expiration date for the user assignment to expire.  
      4. Click Assign. When the update is complete, the permission set group status changes to Updated.  
3. Enable ‘Volunteer Management’ in Setup  
   1. From Setup, in the Quick Find box, enter ‘Volunteer’, and then select **Volunteer Management Settings**.  
   2. Turn on Volunteer Management Settings.  
4. Enable ‘Group Membership’ in Setup  
   1. From Setup, in the Quick Find box, enter ‘Group Membership’, and then select **Group Membership Settings**.  
   2. Turn on **Group Members**.  
   3. Optional: Review under Guided Setup ‘Group Membership and Household’  
5. Enable ‘Interest Tags’ in Setup  
   1. From Setup, in the Quick Find box, enter ‘Interest Tags’, and then select **Interest Tags**. (Note: There are two options, chose the one at the bottom and has the toggle described below step at the top of the page)  
   2. Turn on **Let users access interest tags feature**  
   3. Optional: Review under Guided Setup ‘Interest Tags’  
6. Enable ‘Account Settings’ in Setup  
   1. From Setup, in the Quick Find box, enter ‘Account Settings’, and then select **Account Settings**.  
   2. Click **Edit**  
   3. Check ‘Allow users to relate a contact to multiple accounts’ and click **Save**  
7. Enable Field History Tracking on Account  
   1. From Setup, in the Quick Find box, enter field history tracking, and then select Field History Tracking.  
   2. To select the Account object whose fields you want to track, click View next to Account.  
   3. Select Enable Account History.  
   4. For example, Enable Account History  
   5. Under ‘Track old and new values’  
      1. Mailing Address  
      2. Email  
8. Add Picklist Values to Existing Fields  
   1. Position: Type  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Position**.  
      3. Click Fields & Relationships, and then click the name of the picklist field **Type** to update.  
      4. In the Help Text enter the following: Select "Non-Skilled" for volunteer engagements that don't require qualifications and to hide these records on the J.P. record page.  
      5. In the Type Picklist Values section click **New.**  
      6. In the text box add the following values separated by line breaks  
         1. As Needed  
         2. Non-Skilled  
         3. Skilled  
         4. Other  
      7. Click **Save**.  
   2. Position: Schedule Type  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Position**.  
      3. Click Fields & Relationships, and then click the name of the picklist field **Schedule Type** to update.   
      4. In the Help Text enter the following: Select "As Needed" for volunteer engagements that don't require J.P. Shifts and to hide Shifts on the J.P. record page.  
      5. In the Values section click **New.**  
      6. In the text box add the following values separated by line breaks  
         1. Daily  
         2. Weekly  
         3. Monthly  
         4. As Needed  
      7. Click **Save**.  
   3. Position Qualification: Proficiency Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Position Qualification**   
      3. Click Fields & Relationships, and then click the name of the picklist field **Proficiency Level** to update.   
      4. At the top click **Edit.**  
      5. In the Description enter the following:

         An automation was created to translate the Proficiency Level picklist field on Job Position Qualification and Position Qualification to the numbers stored in the Qualification Level field.

         For a Job Position Qualification, Position Qualification, and Person Competency to show up in a Search for Volunteers interface both Proficiency Level and Qualification Level must be populated. Further having them as numbers allows you to identify volunteers that exceed your requirements (ie finding volunteers that are Advanced when you only need Intermediate).

         If you add a picklist value here, be sure to review this automation and add to the Proficiency Level Mapping custom metadata type. 

      6. Click **Save**.  
      7. In the Proficiency Level Values section click **New.**  
      8. In the text box add the following values separated by line breaks  
         1. Pass  
      9. Click **Save**.  
   4. Position Qualification: Qualification Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Position Qualification**  
      3. Click Fields & Relationships, and then click the name of the number field **Qualification Level** to update.   
      4. At the top click **Edit.**  
      5. In the Help Text enter the following: This field is automatically populated based on the Proficiency Level selected.  
      6. Click **Save**.  
   5. Job Position Qualification: Proficiency Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Job Position Qualification**   
      3. Click Fields & Relationships, and then click the name of the picklist field **Proficiency Level** to update.   
      4. At the top click **Edit.**  
      5. In the Description enter the following:

         An automation was created to translate the Proficiency Level picklist field on Job Position Qualification, Position Qualification, and Person Competency to the numbers stored in the Qualification Level field.

         For a Job Position Qualification and Position Qualification to show up in a Search for Volunteers interface both Proficiency Level and Qualification Level must be populated. Further having them as numbers allows you to identify volunteers that exceed your requirements (ie finding volunteers that are Advanced when you only need Intermediate).

         If you add a picklist value here, be sure to review this automation and add to the Proficiency Level Mapping custom metadata type. 

      6. Click **Save**.  
   6. Job Position Qualification: Qualification Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Job Position Qualification**  
      3. Click Fields & Relationships, and then click the name of the number field **Qualification Level** to update.   
      4. At the top click **Edit.**  
      5. In the Help Text enter the following: This field is automatically populated based on the Proficiency Level selected.  
      6. Click **Save**.  
   7. Person Competency: Proficiency Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Person Competency**.  
      3. Click Fields & Relationships, and then click the name of the picklist field **Proficiency Level** to update.   
      4. At the top click **Edit.**  
      5. In the Description enter the following:

         An automation was created to translate the Proficiency Level picklist field on Job Position Qualification, Position Qualification, and Person Competency to the numbers stored in the Qualification Level field.

         For a Job Position Qualification and Position Qualification to show up in a Search for Volunteers interface both Proficiency Level and Qualification Level must be populated. Further having them as numbers allows you to identify volunteers that exceed your requirements (ie finding volunteers that are Advanced when you only need Intermediate).

         If you add a picklist value here, be sure to review this automation and add to the Proficiency Level Mapping custom metadata type. 

      6. Click **Save**.  
   8. Person Competency: Qualification Level  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Person Competency**.  
      3. Click Fields & Relationships, and then click the name of the number field **Qualification Level** to update.   
      4. At the top click **Edit.**  
      5. In the Help Text enter the following: This field is automatically populated based on the Proficiency Level selected.  
      6. Click **Save**.  
   9. Person Competency: Verification Status  
      1. From Setup, click the Object Manager tab.  
      2. Click the object name **Person Competency**.  
      3. Click Fields & Relationships, and then click the name of the picklist field **Verification Status** to update.   
      4. In the Verification Status Values section click **New.**  
      5. In the text box add the following values separated by line breaks  
         1. Awaiting Approval  
         2. Pending  
         3. Approved  
         4. Not Approved  
      6. Click **Save**  
   10. Person Examination: Verification Status  
       1. From Setup, click the Object Manager tab.  
       2. Click the object name **Person Examination**  
       3. Click Fields & Relationships, and then click the name of the picklist field **Verification Status** to update.   
       4. In the Verification Status Values section click **New.**  
       5. In the text box add the following values separated by line breaks  
          1. Awaiting Approval  
          2. Pending  
          3. Approved  
          4. Not Approved  
       6. Click **Save**.

Supporting documentation:

* [https://help.salesforce.com/s/articleView?id=sales.account\_person\_enable.htm\&type=5](https://help.salesforce.com/s/articleView?id=sales.account_person_enable.htm&type=5)  
* [https://help.salesforce.com/s/articleView?id=platform.perm\_set\_groups\_assign.htm\&type=5](https://help.salesforce.com/s/articleView?id=platform.perm_set_groups_assign.htm&type=5)  
* [https://help.salesforce.com/s/articleView?language=en\_US\&id=ind.fsc\_admin\_enable\_interest\_tags.htm\&type=5](https://help.salesforce.com/s/articleView?language=en_US&id=ind.fsc_admin_enable_interest_tags.htm&type=5)  
* [https://help.salesforce.com/s/articleView?id=ind.group\_membership\_set\_up.htm\&type=5](https://help.salesforce.com/s/articleView?id=ind.group_membership_set_up.htm&type=5)

### Installation

1. Create either a sandbox or a scratch org. It is possible to install into production but that is only advised if you have no existing configuration and have already confirmed all elements of the Volunteer Management Quick Start are applicable.  
      
2. Review this file and other appropriate documentation linked in this document.

3. Install the unmanaged package  
   1. Login into your sandbox or scratch org.  
   2. Choose the appropriate URL:   
      1. For Sandboxes and Scratch Orgs: https://test.salesforce.com/packaging/installPackage.apexp?p0=04tfh000000ZNkv   
      2. For Production Environments:   
         https://login.salesforce.com/packaging/installPackage.apexp?p0=04tfh000000ZNkv  
   3. Paste the URL into your browser navigation bar and press Enter.  
   4. Select Installation Scope: Choose how to install the package:   
      1. Recommended: Install for Admins Only: The package components are only accessible by users with the Administrator profile.   
      2. Install for All Users: The components are available to all users in your organization.   
      3. Install for Specific Profiles: You can choose to install for particular profiles, giving you more granular control.  
   5. Click Install.  
   6. If the installation takes a while, you can click Done and the installation completes in the background. Check your email for confirmation that the installation was successful.

### Post-Install Setup & Configuration

1. Create Experience Cloud Site  
   1. From Setup, enter Digital Experiences in the Quick Find box, then select Digital Experiences | Settings.  
      1. Select Enable Digital Experiences.  
      2. Click Save.  
   2. From Setup, enter Digital Experiences in the Quick Find box, select ‘All Sites’, and then click **New**.  
      1. The creation wizard opens with several templates for you to choose from. Select **Build Your Own (Aura)** as your template.  
      2. Read the template description and key features, and click **Get Started.**  
      3. Enter  
         1. Name: ‘Volunteer Sign Up’  
         2. URL: ‘volunteersignup’  
      4. Click **Create**  
2. Modify Home Page  
   1. Change Content  
      1. Select text at the top of the page in the Rich Content Editor  
      2. Click ‘Edit Content’  
      3. Replace text with ‘Thank you for volunteering\!’  
   2. Grant Public Access  
      1. On the left side of the page click the gear icon for Settings.  
      2. In the General panel, select **Guest users can see and interact with the site without logging in**.  
   3. Modify Page Settings  
      1. Click “Home” and then click “...”  
      2. Under Page Access change the dropdown to ‘Public’  
   4. Add Volunteer Signup Screen   
      1. Select Components from the left side (its the lightning bolt symbol)  
      2. In the Search Box type ‘Flow’  
      3. Select ‘Flow’ and drag underneath the Rich Content Editor text box.  
      4. In the right side panel under “Flow” type ‘VMQS Sign Up Guest User’  
      5. Enter the following values:  
         1. email: {\!email}   
         2. fName: {\!fName}  
         3. inputId: {\!inputId}  
         4. lName: {\!lName}  
         5. volunteerId: {\!volunteerId}  
   5. Click Publish in the upper right corner.  
3. Publish Experience Cloud Site  
   1. From Setup, enter Digital Experiences in the Quick Find box, then select Digital Experiences | Settings.  
   2. For the Volunteer Signup site click select ‘Workspaces’  
   3. Then select ‘Administration’  
   4. On the Settings page click **Activate**  
4. Set up Sharing Rules  
   1. From Setup, in the Quick Find box, enter ‘Sharing Settings’, and then select Sharing Settings  
      1. Under Volunteer Initiative Sharing Rules click **New**  
         1. Step 1: Rule Name  
            1. Label: Guest Access for Volunteer Initiative  
            2. Rule Name: Guest\_Access\_for\_Volunteer\_Initiative  
            3. Description: This enables volunteer signups by providing access publicly based on Status and the Is Published checkbox.  
         2. Step 2: Select your rule type  
            1. Select ‘Guest user access, based on criteria’  
            2. Set the Criteria  
               1. Field: ‘Published’ In Progress  
               2. Operator: ‘equals’  
               3. Value: ‘True’  
            3. Set the Criteria  
               1. Field: ‘Status’  
               2. Operator: ‘equals’  
               3. Value: ‘In Progress’  
         3. Step 3: Select which records to be shared  
         4. Step 4: Select the users to share with  
            1. Share with: Volunteer Signup Site Guest User  
         5. Step 5: Select the level of access for the users  
            1. Access Level: Read Only  
         6. Click **Save**  
      2. Under Job Position Sharing Rules click **New**  
         1. Step 1: Rule Name  
            1. Label: Guest Access for Job Position  
            2. Rule Name: Guest\_Access\_for\_Job\_Position  
            3. Description: This enables volunteer signups by providing access publicly based on Status field.  
         2. Step 2: Select your rule type  
            1. Select ‘Guest user access, based on criteria’  
            2. Set the Criteria  
               1. Field: ‘Status’  
               2. Operator: ‘equals’  
               3. Value: ‘In Progress’  
         3. Step 3: Select which records to be shared  
         4. Step 4: Select the users to share with  
            1. Share with: Volunteer Signup Site Guest User  
         5. Step 5: Select the level of access for the users  
            1. Access Level: Read Only  
         6. Click **Save**  
      3. Under Job Position Shift Sharing Rules click **New**  
         1. Step 1: Rule Name  
            1. Label: Guest Access for Job Position Shift  
            2. Rule Name: Guest\_Access\_for\_for\_Job\_Position\_Shift  
            3. Description: This enables volunteer signups by providing access publicly based on Status field.  
         2. Step 2: Select your rule type  
            1. Select ‘Guest user access, based on criteria’  
            2. Set the Criteria  
               1. Field: ‘Status’  
               2. Operator: ‘equals’  
               3. Value: ‘In Progress’  
         3. Step 3: Select which records to be shared  
         4. Step 4: Select the users to share with  
            1. Share with: Volunteer Signup Site Guest User  
         5. Step 5: Select the level of access for the users  
            1. Access Level: Read Only  
         6. Click **Save**  
5. Set up Permission Set License for Guest User  
   1. From Setup, in the Quick Find box, enter ‘Permission Sets’, and then select Permission Sets  
   2. Find Volunteer Management in Experience Cloud Guest Access and click ‘**Clone**’   
   3. Enter the following:  
      1. Label: VMQS Volunteer Sign Up Access  
      2. API Name: VMQS\_Volunteer\_Sign\_Up\_Access  
      3. Description: Cloned from Volunteer Management in Experience Cloud Guest Access on \[DATE\]  
   4. Click **Save**   
   5. Provide access to Volunteer Signup Flow  
      1. Click ‘Flow Access’  
      2. Click Edit  
      3. Select ‘VMSQ Sign Up Guest’ from the Available Flows column and add them to the Enabled Flows column.   
      4. Click **Save**   
   6. Provide system permissions   
      1. Click ‘Systems Permissions’  
      2. Click Edit  
      3. Check the **Enabled** box next to Access Volunteer Management as Guest  
      4. Click **Save**  
   7. Provide object and field  access on the following objects  
      1. Volunteer Initiatives \-  
         1. Object Permissions: Read   
         2. Field Permissions: Read Access  
            1. Default Duration  
            2. Description  
            3. End Date  
            4. Parent Volunteer Initiative  
            5. Published  
            6. Start Date  
            7. Status  
            8. Volunteer Initiative Name  
            9. Volunteer Signup URL  
      2. Job Position  
         1. Object Permissions: Read  
         2. Field Permissions: Read Access  
            1. Default Duration  
            2. Description  
            3. End Date  
            4. External ID  
            5. Last Filled Date  
            6. Last Modified By  
            7. Last Modified Date  
            8. Location  
            9. Manager  
            10. Name  
            11. Owner Name  
            12. Position  
            13. Related Volunteer Initiative  
            14. Start Date  
            15. Status  
            16. Title  
            17. Volunteer Signup URL  
      3. Job Position Shift  
         1. Object Permissions: Read  
         2. Field Permissions: Read Access  
            1. Default\_Duration\_\_c  
            2. Description   
            3. EndDate  
            4. EndTime  
            5. JobPositionId  
            6. Start\_and\_End\_DateTime\_\_c  
            7. StartDate  
            8. StartTime  
            9. Status  
            10. Volunteer\_Signup\_URL\_\_c  
      4. Job Position Assignment   
         1. Object Permissions: Read and Create  
         2. Field Permissions: Read Access and Edit Access  
            1. All Fields  
6. Modify Guest User 

   Navigating to the Guest User profile is challenging the first time, the system hides this profile from this view. For this reason we have provided three methods to navigate to this record. 

   1. Find the profile:  
      1. Method 1: In Search Setup enter ‘Volunteer Signup Site Guest User’ and select ‘Volunteer Signup Site Guest User’  
      2. Method 2: Go to Setup Home and scroll down to ‘Recent Items’ and  select ‘Volunteer Signup Site Guest User’  
      3. Method 3:   
         1. From Setup, enter Digital Experiences in the Quick Find box, then select Digital Experiences | All Sites.  
         2. Click **Builder**  
         3. On the left side of the page click the gear icon for Settings.![][image1]  
         4. In the General Panel under ‘Guest User Profile’ click ‘Volunteer Sign Up Profile’  
   2. Under Permission Set Assignments click ‘Edit Assignments’  
   3. Select ‘VMQS Volunteer Sign Up Access’ under Available Permission Sets and move to Enabled Permission Set  
   4. Click **Save**    
7. Change Custom Metadata   
   1. Get URL  
      1. From Setup, in the Quick Find box, enter ‘Sites’, and then select ‘All Sites’  
      2. Copy the value under the URL, beginning with ‘https:...’  
   2. Modify Custom Metadata Record  
      1. From Setup, in the Quick Find box, enter ‘Custom Metadata’ and then select ‘Custom Metadata Types”  
      2. Find ‘Site URL’s Custom Metadata Types  
      3. Click **Manage Records**  
         1. Under Label click **Volunteer Signup**  
         2. Paste URL from step above ensure that it ends in ‘/s/’   
8. Change Access to Lightning Apps  
   1. From Setup, in the Quick Find box, enter ‘App Manager’, and then select ‘App Manager’  
   2. Click ![Action dropdown][image2] on a ‘Volunteer Management’ app’s row, and select **Edit**.  
   3. Under ‘App Settings’ click on ‘User Profiles’.  
   4. Select all Profiles in the ‘Selected Profiles’ column and move to ‘Available Profiles’.  
   5. Click **Save.**  
   6. Click ![Action dropdown][image2] on a ‘Volunteer Management Quick Start’ app’s row, and select **Edit**.  
   7. Under ‘App Settings’ click on ‘User Profiles’.  
   8. Select the appropriate Profiles in the ‘Available Profiles’ column and move to ‘Selected Profiles’.  
   9. Click **Save.**

## Known Issues

* None

### Post Install Considerations

1. Set up volunteer activities  
   * Event Based \- The accelerator is designed for event based activities. Create the following records 

     1. Volunteer Initiative \- Use Volunteer Initiatives to group your Job Position together by how you would like to report out on. Typically by program area and reporting period (calendar or fiscal year).   
        1. Name: Food and Nutrition  
     2. Position \- Use Positions to answer the question “what do you need volunteers to do?”. They can be   
        1. Name: General Volunteer  
        2. Type: Non-Skilled  
        3. Schedule Type: Weekly  
     3. Job Position \-  Use Job Positions to connect Positions to Volunteer Initiatives, in this case the Job Position represents a series of volunteer events at a particular location.   
        1. Name: Food Distribution \- General Volunteer  
        2. Title: Food Distribution

       
           From here you can add the Location, Job Position Qualifications, and Job Position Shifts as necessary.

   * As Needed \- An additional option is to create Job Position Assignments after Volunteer work is completed to record their efforts. In this situation the absolute minimum is Volunteer Initiative and Job Position Assignments. In addition to these two records it is also recommended to create Positions and Job Positions to help better track the actual type of volunteer work.   
     1. Volunteer Initiative \-   
        1. Name: Governance  
     2. Position  
        1. Name: Directors  
        2. Type: Skilled  
        3. Schedule Type: As Needed  
     3. Job Position  
        1. Name: Board of Directors

     For the Job Position Assignment you can use the Actual Start Date and the Actual Start Time to record the times of the individual meetings. Or you can set these to capture the beginning and end of the reporting period, the first of the month and the last of the month.

     

* Job Position Details   
* Location and Address \- On the Job Position record under the ‘Location’ tab you can create a new Location or update an existing Location. You can also use an existing Location record by populating the Location lookup field on the Job Position record.

    
  It is recommended to create at least one Location if you want to record when a volunteer is available. 


* Skills, Interests, Requirements  \- You can record these concepts as Competencies and Examination. Further it is best to use Competencies for things a volunteer has before you begin to onboard them and Examinations for the result of the onboarding process. The reason for this is as of the Winter ‘26 release Examinations aren’t supported by the Search Volunteers interface.

    
  Some examples of Competencies: Financial Background, Spanish Language Proficiency, Previous Nonprofit Board Service or Fundraising Background.

  Some examples of Examinations: Background Check or Food Safety Training.

  Qualifications \- You then link these Competency and Examination records to Positions with Position Qualifications or to Job Positions with Job Position Qualifications. These records can be linked to either Competency or Examinations.

  For those linked Competencies you must specify the Proficiency Level needed for the Position or Job Position as either Advanced, Intermediate, or Beginner. An automation maps these picklist values to a number value stored in Qualification Level. This mapping enables a user to use the Search Volunteers interface and to identify volunteers that exceed your requirements (i.e. finding volunteers that are Advanced when you only need Intermediate).


2. Set up Volunteers   
   * Person Accounts  
   * Preferences  
     1. Person Location Availability and Operating Hours  
     2. Time Slots   
   * Qualifications  
     1. Person Competencies   
     2. Person Examinations 

3. Review Lightning Pages   
     
   Review and modify the Lightning Pages to ensure they meet your needs and considerations.  
     
* [https://help.salesforce.com/s/articleView?id=platform.dynamic\_forms\_overview.htm\&language=en\_US\&type=5](https://help.salesforce.com/s/articleView?id=platform.dynamic_forms_overview.htm&language=en_US&type=5)  
* [https://trailhead.salesforce.com/content/learn/modules/lightning\_app\_builder](https://trailhead.salesforce.com/content/learn/modules/lightning_app_builder)  
    
  The following objects had limitations at the time of the latest release. The package provides workarounds to these limitations. These issues are likely to be fixed in upcoming releases and these elements will be unnecessary. If they are unnecessary then it is suggested that you use standard functionality over these items.  
    
* Location \- Dynamic form features are not supported.  
* Account and Person Account  
  * Cannot deploy a Quick Action based on Person Examination or Person Competency  
* Examination   
  * Cannot add Position Qualifications, Job Position Qualifications as related lists.  
  * It is impossible to deploy metadata elements related to the picklist field ‘Verification Status’ due to restricted picklist values.   
* Competency  
  * Cannot add Person Competencies, Position Qualifications, Job Position Qualifications as related lists.


4. Brand Experience Cloud site and add additional critical information

   Return to Post-Install Setup & Configuration’s second step and add additional graphics on content to match your organization’s needs.

5. Review flows \- 

   Review the following documentation and training resources to modify the ‘VMQS Sign Up Guest User’ screen flow to add information about the volunteer activities to end users.

   Additionally Volunteer Management provides a flow out of the box ‘Assign Volunteers to Job Position Shifts’ that can be used from the Person Account, Contact, and Volunteer Initiative records to add multiple volunteers to multiple shifts. This flow is only incorporated into the page layout for the Person Account as of the Winter ‘26 release of this Accelerator through a Quick Action created for this accelerator. 

   * [https://admin.salesforce.com/blog/2023/what-is-a-screen-flow](https://admin.salesforce.com/blog/2023/what-is-a-screen-flow)  
   * [https://help.salesforce.com/s/articleView?id=sf.extend\_click\_process.htm\&type=5](https://help.salesforce.com/s/articleView?id=sf.extend_click_process.htm&type=5)  
   * [https://help.salesforce.com/s/articleView?id=platform.platform\_automation.htm\&type=5](https://help.salesforce.com/s/articleView?id=platform.platform_automation.htm&type=5)  
   * [https://trailhead.salesforce.com/content/learn/trails/build-flows-with-flow-builder](https://trailhead.salesforce.com/content/learn/trails/build-flows-with-flow-builder)

   

6. Create ‘Email Templates’

   Review the following documentation to create Email Templates:

   [https://help.salesforce.com/s/articleView?id=sales.email\_templates\_lightning\_parent.htm\&type=5](https://help.salesforce.com/s/articleView?id=sales.email_templates_lightning_parent.htm&type=5)

   If you don’t have an integrated Marketing Solution with your salesforce you can additionally create Scheduled Flows off of Job Positions Assignments to send volunteer event reminders and follow up.

7. Set up Service Cloud to handle volunteer interest inquiries

   An Experience Cloud site can be built out to allow volunteers to discover and select available volunteer opportunities. If that is not realistic for your organization to set up and maintain, using Service Cloud to handle volunteer interest inquiries and communicate with volunteers is available. Review the training resource on Service Cloud and the documentation on ‘Email to Case’ specifically.

   * [https://trailhead.salesforce.com/content/learn/projects/set-up-case-escalation-entitlements](https://trailhead.salesforce.com/content/learn/projects/set-up-case-escalation-entitlements)  
   * [https://help.salesforce.com/s/articleView?id=service.setting\_up\_email-to-case.htm\&type=5](https://help.salesforce.com/s/articleView?id=service.setting_up_email-to-case.htm&type=5)

   

8. Review Nonprofit Cloud Setup steps   
     
   Volunteer Management is a component of Nonprofit Cloud and has lots of additional functionality and features. In “Before You Install” steps you have enabled Interest Tags and Group Membership features. Beyond these two, looking at the applicability of Interaction Summaries, Record Alerts and Timeline features may be relevant to your use of Volunteer Management. 

     
   * [https://trailhead.salesforce.com/content/learn/modules/stakeholder-management-in-nonprofit-cloud](https://trailhead.salesforce.com/content/learn/modules/stakeholder-management-in-nonprofit-cloud)  
   * [https://help.salesforce.com/s/articleView?id=sfdo.npc\_prerequisites.htm\&type=5](https://help.salesforce.com/s/articleView?id=sfdo.npc_prerequisites.htm&type=5)

   

9. Set up action plans to create reusable task lists 

   * [https://help.salesforce.com/s/articleView?id=ind.fsc\_action\_plans.htm\&type=5](https://help.salesforce.com/s/articleView?id=ind.fsc_action_plans.htm&type=5)

## Miscellaneous 

### Revision History

**2.0 Winter ‘26 release (14 Nov 2025)** - The following modifications were made.

* Accounts  
  * Replace flows to display Person Competencies and Person Examinations since these related lists are now supported natively.  
* Job Position Qualification and Position Qualification  
  * Added automation with flow and custom metadata type to map the Proficiency Level picklist to a number for the numerical Qualification level field.   
  * Removed automation to display the Qualification Record Related record in related record lists since that is now supported.   
* Added “Search Volunteers’ to Volunteer Management Quick Start custom application.  
* Addressed an known issue with the VMQS Sign Up Guest User flow by adding a decision element before the confirmation screen.  
* Addressed an known issue with VMQS Create Volunteer from J.P. Assignment where the ‘Is Volunteer Added’  a decision element was mapped to Last Name instead of VolunteerID.  
* The ‘Mark Absent’ quick action on Job Position Assignment was updated to also uncheck the Count Toward Shift Capacity field when used.

**1.0 Initial release (10 Sept 2025)** - First release. For detailed release notes and change logs, provide a link to another readme in the /docs/ folder of this repository.  

### Acknowledgements

Justin Gilmore  
Brian Richter \- For rollup flows and test data.   
Kevin Zeigler \- For his rebuilding of the guest user registration flow.  
Cassie Bartelme \- For through testing and validation.  
Toby Ward from Galvin for feedback and flagging known issues.

### Terms of Use

Thank you for using Global Public Sector (GPS) Accelerators. Accelerators are provided by Salesforce.com, Inc., located at 1 Market Street, San Francisco, CA 94105, United States.

By using this site and these accelerators, you are agreeing to these terms. Please read them carefully.

Accelerators are not supported by Salesforce, they are supplied as-is, and are meant to be a starting point for your organization. Salesforce is not liable for the use of accelerators.

For more about the Accelerator program, visit: https://gpsaccelerators.developer.salesforce.com/
