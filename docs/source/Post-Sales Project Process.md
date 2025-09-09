# Post-Sales Project Process

## Parties Involved

| Role | Responsibility |
| --- | --- |
| Project Manager | Initial Scheduling and communication |
| Engineer 1 | Executes the process |
| Engineer 2 | Assists as needed |
| Customer | Signs agreements and provides input |

---

## Process Overview

&lt;div style="display: flex; align-items: flex-start; gap: 20px;"&gt; &lt;img src="ReferenceImages/ProjectProcess_SwimlaneV2.png" alt="Project Process" style="width:auto; height:auto;"&gt; &lt;div&gt; ### 1. The order is placed, and assigned. - **Owner**: Project Manger - **Purpose**: Project manager filters by labor-6 and assigns project to Engineers ### 2. Schedule Kickoff Meeting > ⚠️\*\*Important\*\*⚠️ The project kickoff meeting must include `Engineer 1`. If the engineer cannot attend, the meeting must be rescheduled. - **Owner:** Project Manager - **Attendees:** Engineer 1, Engineer 2 (if applicable), Customer - **Purpose:** - Align expectations - Confirm scope and deliverables - Discuss timeline and next steps ### 3. Create Statement of Work (SoW) - **Owner:** Engineer 1 - **Tool:** PandaDoc - **Details:** Draft based on discussions during kickoff meeting - \[\*\*More Info\*\*\](#create-statement-of-work-sow) ### 4. Customer Signs the SoW - **Owner:** Customer - **Trigger:** After review and approval of SoW - **Action:** Sign the SoW in PandaDoc ### 5. Create Managed Service Ticket > ⚠️\*\*Important\*\*⚠️ > _Use the_ `Order Number` _in the_ `Invoice Number` _field &lt;br&gt; >_ Upload the `signed SoW PDF` to the ticket - **Owner:** Engineer 1 - **Tool:** Vector - \[\*\*More Info\*\*\](#create-managed-service-ticket) ### 6. Project Start - **Owner:** Engineer 1 - **Condition:** Project may begin only after the SoW is signed ### 7. Time Tracking - **Owner:** Engineer 1, Engineer 2 - **Tool:** Vizor (Manager Services ticket type) - Track all project time ### 8. Send Project Completion Agreement - **Owner:** Engineer 1 - **To:** Customer - **Purpose:** Confirm project completion - **Upload:** Add to the Vizor ticket if completed/signed - \[\*\*More Info\*\*\](#create-project-completion-agreement) ### 9. Auto-Close - **System Behavior:** Project ticket auto-closes two weeks after the Project Completion Agreement is sent &lt;!-- Div to close out site-by-side --&gt; &lt;/div&gt; &lt;/div&gt;

## Add a PandaDoc to an order

- Get the order number from the Project Manager / Labor-6 document &lt;br&gt;
- Go to `intcrm.bytepseed.com` and search for the order![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/CRM_OrderSearch.png)
- Select the order &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/CRM_SelectOrder.png)
- Change the view to `Order - ServerTeam` &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/CRM_OrderView.png)
- Scroll down to the PandaDoc pane and select `Create new document`
    - This is 3/4 of the way down the page
    - It will open a new window &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/CRM_CreatePandaDoc.png)
- In the new window, click `More Folders` under the `templates` section of the `My templates` tab
- Navigate to the `Misc.` folder

## Create Statement of Work (SoW)

- Follow steps outlined in [Add a PandaDoc to an order](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/AllItems.aspx?viewid=05e5b127%2D51e5%2D41fd%2Dacbb%2Da0dfc5d38af4&id=%2Fsites%2FLabor%2D6Projects%2FShared%20Documents%2FGeneral%2FProcesses%2FProjectProcess%2Emd&parent=%2Fsites%2FLabor%2D6Projects%2FShared%20Documents%2FGeneral%2FProcesses#add-a-pandadoc-to-an-order)
- SoW template documents:
    
    | Document title | Description |
    | --- | --- |
    | Basic Network Configuration SoW ... | Template for flat rate AP and Switch projects |
    | Installation/Configuration SoW ... | Template for non-flat rate projects (includes a section for project notes) |
    
- Select the SoW template based on type of project and click `Add 1 Item`
- Enter Recipient information for `Sender` _(Engineer)_ and `Client` _(Customer)_![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_Recipient.png)
- Review doc
    - Can add `Network Engineer` and `Project Manger` fields manually if you know who you are working with.
    - Add a detailed project summary for the `Installation/Configuration SoW` document.
    - Sign and date the document
- Save the send link to include in your existing email chain. &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_SaveLink.png)
- Generate Links &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_GenerateLink.png)
- Copy Sender link &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_CopyLink.png)
- Paste in an email to the customer
- Do not start work until this is signed.

## Create Managed Service Ticket

- Login to `vizor.bytespeed.com` using your network credentials
- Click `Submit New` &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Vizor_CreateNew.png)
- Enter the following information: | Tab | Field | Value | |-----------------|----------------|------------------------------| | Ticket | Ticket Type | `Managed Services` | | Ticket | Company | `<Customer's company>` | | Ticket | Contact | `<Main contact>` | | Ticket | Sales | `Anna Hanson` | | Ticket | Invoice Number | `Order Number` | | HelpDesk Ticket | Description | `Project Summary` | | Ticket Details | Attachments | `Signed SoW PDF` | | Activity | Activity | `Time Entries` &lt;br&gt; (as you work) |Example ticket: &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Vizor_CreateTicket.png)
- Click ok to create the ticket
- Track time against this ticket as you work on the project

## Create Project Completion Agreement

- Follow steps outlined in [Add a PandaDoc to an order](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/AllItems.aspx?viewid=05e5b127%2D51e5%2D41fd%2Dacbb%2Da0dfc5d38af4&id=%2Fsites%2FLabor%2D6Projects%2FShared%20Documents%2FGeneral%2FProcesses%2FProjectProcess%2Emd&parent=%2Fsites%2FLabor%2D6Projects%2FShared%20Documents%2FGeneral%2FProcesses#add-a-pandadoc-to-an-order)
- Select the `Project Completion Agreement` template and click `Add 1 item`
- Enter Recipient information for `Sender` _(Engineer)_ and `Client` _(Customer)_ &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_Recipient.png)
- Review doc
- Sign the document
- Save the send link to include in your existing email chain. &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_SaveLink.png)
- Generate Links &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_GenerateLink.png)
- Copy Sender link &lt;br&gt;![alt text](https://bytespeedllc.sharepoint.com/sites/Labor-6Projects/Shared%20Documents/Forms/ReferenceImages/Panda_CopyLink.png)
- Paste in an email to the customer
- Project will close automatically if the document is not signed within in 2 weeks.