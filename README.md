![Public Sector Accelerators logo](/docs/Logo_GPSAccelerators_v01.png)

# Volunteer Management

Streamline volunteer initiatives and volunteer sign-up, attendance, and reporting in Nonprofit Cloud.

Accelerator Listing: [insert url to the public listing on the Accelerator site](https://gpsaccelerators.developer.salesforce.com/) (tbd once published)

## Description

The Volunteer Management Quick Start Accelerator helps nonprofits stand up a ready-to-use volunteer management solution on Salesforce Nonprofit Cloud. Designed to reduce setup complexity, it delivers a complete foundation for managing both event-based and skill-based volunteer opportunities on the new Volunteer Management (new as of the Summer '25 release).

With this Accelerator, organizations can create, publish, and track volunteer initiatives, job positions, and shifts -- all supported by streamlined Experience Cloud guest access for easy registration. Volunteers can sign up without logging in, while staff can efficiently track attendance, manage locations, and capture valuable engagement data for reporting.

## Included Assets

This Accelerator includes the following assets:
<ol>
  <li>An <strong>unmanaged package</strong> (link below; metadata is also found in the /force-app/main/default/ folder) that includes:
    <ul>
      <li>Apex classes (x2)</li>
      <li>Custom objects (x4)</li>
      <li>Lightning Web Components (LWCs) (x2)</li>
    </ul>
  </li>
  <li><strong>OmniScripts</strong> (x2) located in the /datapacks/ folder</li>
  <li><strong>Documentation</strong>, including:
    <ul>
      <li>This readme file</li>
      <li>White paper providing detailed setup instructions and a data dictionary (located in the /docs/ folder)</li>
    </ul>
  </li>
</ol>


## Before You Install

**License Requirements** [Required]
* Nonprofit Cloud with the Volunteer Management permission set (internal users)
* No license required for volunteer registration (external users) using guest user access. 


**Accelerator or Technology-Specific Assumptions** 
* This accelerator was built and designed primarily for the needs of an event based volunteering use case and the creation of volunteer activities focused on physical labor. The Experience Cloud page is set up to provide an easy registration experience collecting just the volunteers first name, last name, and email address. 
* The package doesn’t include a volunteer application, or a process to capture volunteer interest or inquiries.
* It does represent the manual tracking of examinations that could be used to track Background Checks but it doesn’t include any automation or integration with Background check providers. 
* It also assumes that the required information for each volunteer activity is a named individual, a date, and the number of hours they served. The Volunteer Management data model stores this information on the Job Position Assignment object and this Quick Start package determines this is stored using the fields Assigned Account, Actual Start Time, and Actual Start Duration. 
* The Volunteer Management product and data model includes fields for rollups but as of Winter ‘26 release doesn’t include any automation to calculate those rollup fields. This Quick Start package includes some sample flows to make those calculations, however these flows will only be appropriate for low data volumes. Organizations should consider alternative approaches, including using standard reports, custom data process engine (DPE), or Declarative Lookup Rollup Summaries (DLRS). 

## Installation

* Create either a sandbox or a scratch org. It is possible to install into production but that is only advised if you have no existing configuration and have already confirmed all elements of the Volunteer Management Quick Start are applicable.
* Review this file and other appropriate documentation referenced here
* Install the unmanaged package
* Login into your sandbox or scratch org.
* Choose the appropriate URL: For Sandboxes and Scratch Orgs: https://test.salesforce.com/packaging/installPackage.apexp?p0=04tfh000000ZNZd For Production Environments: https://login.salesforce.com/packaging/installPackage.apexp?p0=04tfh000000ZNZd
* Paste the URL into your browser navigation bar and press Enter.
* Select Installation Scope: Choose how to install the package: 
* Recommended: Install for Admins Only: The package components are only accessible by users with the Administrator profile. 
* Install for All Users: The components are available to all users in your organization. 
* Install for Specific Profiles: You can choose to install for particular profiles, giving you more granular control.
* Click Install.
If the installation takes a while, you can click Done and the installation completes in the background. Check your email for confirmation that the installation was successful.
Review the components included and select the ones that you wish to deploy to your production environment.



## Post-Install Setup & Configuration

## Create Experience Cloud Site

1. From Setup, enter **Digital Experiences** in the Quick Find box, then select **Digital Experiences | Settings**.
2. Select **Enable Digital Experiences**.
3. Click **Save**.
4. From Setup, enter **Digital Experiences** in the Quick Find box, select **All Sites**, and then click **New**.
5. The creation wizard opens with several templates for you to choose from. Select **Build Your Own (Aura)** as your template.
6. Read the template description and key features, and click **Get Started**.
7. Enter the following:
   - Name: `Volunteer Sign Up`
   - URL: `volunteersignup`
8. Click **Create**.

## Modify Home Page

### Change Content

1. Select text at the top of the page in the Rich Content Editor.
2. Click **Edit Content**.
3. Replace text with `Thank you for volunteering!`

### Modify Page Settings

1. Click **Home** and then click **...**.
2. Under Page Access change the dropdown to **Public**.

### Add Volunteer Signup Screen

1. Select **Components** from the left side (it's the lightning bolt symbol).
2. In the Search Box type `Flow`.
3. Select **Flow** and drag underneath the Rich Content Editor text box.
4. In the right side panel under "Flow" type `VMQS Sign Up Guest User`.
5. Enter the following values:
   - email: `{!email}`
   - fName: `{!fName}`
   - inputId: `{!inputId}`
   - lName: `{!lName}`
   - volunteerId: `{!volunteerId}`
6. Click **Publish** in the upper right corner.

## Publish Experience Cloud Site

1. From Setup, enter **Digital Experiences** in the Quick Find box, then select **Digital Experiences | Settings**.
2. For the Volunteer Signup site click select **Workspaces**.
3. Then select **Administration**.
4. On the Settings page click **Activate**.

## Set up Sharing Rules

### Volunteer Initiative Sharing Rule

1. From Setup, in the Quick Find box, enter **Sharing Settings**, and then select **Sharing Settings**.
2. Under Volunteer Initiative Sharing Rules click **New**.
3. **Step 1: Rule Name**
   - Label: `Guest Access for Volunteer Initiative`
   - Rule Name: `Guest_Access_for_Volunteer_Initiative`
   - Description: `This enables volunteer signups by providing access publicly based on Status and the Is Published checkbox.`
4. **Step 2: Select your rule type**
   - Select `Guest user access, based on criteria`
5. **Set the Criteria**
   - Field: `Published` In Progress
   - Operator: `equals`
   - Value: `True`
6. **Set the Criteria**
   - Field: `Status`
   - Operator: `equals`
   - Value: `In Progress`
7. **Step 3: Select which records to be shared**
8. **Step 4: Select the users to share with**
   - Share with: `Volunteer Signup Site Guest User`
9. **Step 5: Select the level of access for the users**
   - Access Level: `Read Only`
10. Click **Save**.

### Job Position Sharing Rule

1. Under Job Position Sharing Rules click **New**.
2. **Step 1: Rule Name**
   - Label: `Guest Access for Job Position`
   - Rule Name: `Guest_Access_for_Job_Position`
   - Description: `This enables volunteer signups by providing access publicly based on Status field.`
3. **Step 2: Select your rule type**
   - Select `Guest user access, based on criteria`
4. **Set the Criteria**
   - Field: `Status`
   - Operator: `equals`
   - Value: `In Progress`
5. **Step 3: Select which records to be shared**
6. **Step 4: Select the users to share with**
   - Share with: `Volunteer Signup Site Guest User`
7. **Step 5: Select the level of access for the users**
   - Access Level: `Read Only`
8. Click **Save**.

### Job Position Shift Sharing Rule

1. Under Job Position Shift Sharing Rules click **New**.
2. **Step 1: Rule Name**
   - Label: `Guest Access for Job Position Shift`
   - Rule Name: `Guest_Access_for_for_Job_Position_Shift`
   - Description: `This enables volunteer signups by providing access publicly based on Status field.`
3. **Step 2: Select your rule type**
   - Select `Guest user access, based on criteria`
4. **Set the Criteria**
   - Field: `Status`
   - Operator: `equals`
   - Value: `In Progress`
5. **Step 3: Select which records to be shared**
6. **Step 4: Select the users to share with**
   - Share with: `Volunteer Signup Site Guest User`
7. **Step 5: Select the level of access for the users**
   - Access Level: `Read Only`
8. Click **Save**.

## Set up Permission Set License for Guest User

1. From Setup, in the Quick Find box, enter **Permission Sets**, and then select **Permission Sets**.
2. Find **Volunteer Management in Experience Cloud Guest Access** and click **Clone**.
3. Enter the following:
   - Label: `VMQS Volunteer Sign Up Access`
   - API Name: `VMQS_Volunteer_Sign_Up_Access`
   - Description: `Cloned from Volunteer Management in Experience Cloud Guest Access on [DATE]`
4. Click **Save**.

### Provide access to Volunteer Signup Flow

1. Click **Flow Access**.
2. Click **Edit**.
3. Select `VMSQ Sign Up Guest` from the Available Flows column and add them to the Enabled Flows column.
4. Click **Save**.

### Provide system permissions

1. Click **Systems Permissions**.
2. Click **Edit**.
3. Check the Enabled box next to **Access Volunteer Management as Guest**.
4. Click **Save**.

### Modify Guest User

1. In Global Search enter `Volunteer Signup Site Guest User` and select **Volunteer Signup Site Guest User**.
2. Under Permission Set Assignments click **Edit Assignments**.
3. Select `VMQS Volunteer Sign Up Access` under Available Permission Sets and move to Enabled Permission Set.
4. Click **Save**.

## Change Custom Metadata

1. From Setup, in the Quick Find box, enter **Sites**, and then select **All Sites**.
2. Copy the value under the URL, beginning with `https:...`
3. From Setup, in the Quick Find box, enter **Custom Metadata** and then select **Custom Metadata Types**.
4. Find **Site URL's Custom Metadata Types**.
5. Click **Manage Records**.
6. Under Label click **Volunteer Signup**.
7. Paste URL from step 2 into **Base URL** and add `/s/` to the end.

## Add Picklist Values to Existing Fields

### Position: Type

1. From Setup, click the **Object Manager** tab.
2. Click the object name **Position**.
3. Click **Fields & Relationships**, and then click the name of the picklist field **Type** to update.
4. In the Values section click **New**.
5. In the text box add the following values separated by line breaks:
   - As Needed
   - Non-Skilled
   - Skilled
   - Other
6. Click **Save**.

### Position: Schedule Type

1. From Setup, click the **Object Manager** tab.
2. Click the object name **Position**.
3. Click **Fields & Relationships**, and then click the name of the picklist field **Schedule Type** to update.
4. In the Values section click **New**.
5. In the text box add the following values separated by line breaks:
   - Daily
   - Weekly
   - Monthly
   - As Needed
6. Click **Save**.

### Person Examination: Verification Status

1. From Setup, click the **Object Manager** tab.
2. Click the object name **Person Examination**.
3. Click **Fields & Relationships**, and then click the name of the picklist field to update.
4. In the Values section click **New**.
5. In the text box add the following values separated by line breaks:
   - Awaiting Approval
   - Pending
   - Approved
   - Not Approved
6. Click **Save**.

### Person Competency: Verification Status

1. From Setup, click the **Object Manager** tab.
2. Click the object name **Person Competency**.
3. Click **Fields & Relationships**, and then click the name of the picklist field to update.
4. In the Values section click **New**.
5. In the text box add the following values separated by line breaks:
   - Awaiting Approval
   - Pending
   - Approved
   - Not Approved
6. Click **Save**.



## FAQs

[Optional. Preemptive list of common questions or situations that need to be explained in how the Accelerator works (or doesn't).]

**_Q: Do I really need an FAQ for my Accelerator?_**

A: Great question! Perhaps not, but if you had common misunderstandings or confusion during beta testing with an aspect of setup or use, you may find it helpful to create some related FAQs. You might also wish to use FAQs to reiterate a critical point found in this readme or any other included documentation. An FAQ may also help point out a recommendation or tip about how to use your Accelerator.

## Additional Resources

[Optional. Summary list of additional links and references that you think are useful to. These links should be restricted to official Salesforce web resources and should not include third party references. Use an unordered list.]


## Revision History

[Required. High level description of the Accelerator's versions, with the date it was made publicly available. If more detailed release notes or change log are necessary, create a separate readme in the same folder and link to it from here.]
<strong>1.0 Initial release (30 Oct 2023)</strong> - Short description of the release. For detailed release notes and change logs, provide a link to another readme in the /docs/ folder of this repository.


## Acknowledgements

[Optional. Names of individuals involved in the creation, publication, and maintenance of this Accelerator and a link to their Github user profile.]


## Terms of Use

[Required. Cleared terms of use.  This must match the approved content used on the Accelerator listing.]

Thank you for using Global Public Sector (GPS) Accelerators.  Accelerators are provided by Salesforce.com, Inc., located at 1 Market Street, San Francisco, CA 94105, United States.

By using this site and these accelerators, you are agreeing to these terms. Please read them carefully.

Accelerators are not supported by Salesforce, they are supplied as-is, and are meant to be a starting point for your organization. Salesforce is not liable for the use of accelerators.

For more about the Accelerator program, visit: [https://gpsaccelerators.developer.salesforce.com/](https://gpsaccelerators.developer.salesforce.com/)
