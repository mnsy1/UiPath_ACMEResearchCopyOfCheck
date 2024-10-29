# ACME WI2 Research Copy Of Check

This UiPath project automates the workflow to research and validate check copies within the ACME System1 website and ACME System3 desktop application. The process captures client information and check details to facilitate accurate data handling across both systems.

## Libraries Used

The project utilizes these custom libraries:
1. [**Google Search Library**](https://github.com/mnsy1/UiPath_Google): Handles the Google Chrome search and navigation to the ACME System1 website.
2. [**ACME System1 Website Library**](https://github.com/mnsy1/UiPath_ACMESystem1): Manages operations on the ACME System1 website.
3. [**ACME System3 Desktop Application Library**](https://github.com/mnsy1/UiPath_ACMESystem3Application): Manages tasks within the ACME System3 desktop application.

## Process Workflow

### 1. Open ACME System1 Website
- Launches Google Chrome and opens the Google search page.
- Searches for "ACME System" and navigates to the ACME System1 website.

### 2. Login to ACME System1 Account
- Confirms logout status before logging in with the provided credentials.
- Accesses the dashboard for navigating work items.

### 3. Open ACME System3 Desktop Application
- Launches ACME System3 and logs in with the same credentials.
- Prepares the "Search by ID" window for handling check information.

### 4. Access Work Items
- Opens the Work Items list and retrieves items for processing.

### 5. Process WI2 Work Items
For each WI2 work item:
- Opens the item’s details on ACME System1 and downloads the associated PDF check request.
- Extracts the client and check information from the PDF.

### 6. Search and Validate Check in ACME Systems
- Returns to System1 and navigates to "Search Client Check."
- Enters check information and attempts to locate the check:
    - If found, saves the check image in System1 and updates the work item status to "Completed" with a comment indicating success.
    - If not found, proceeds to System3’s "Clients" section, searches by Client ID, and checks both active and inactive clients.
    - Reattempts check search in System3 by Check Number and Check Date:
        - If found, updates the status and comments in System1 as “Check found in System 3.”
        - If not found, sets the status to "Rejected" with the comment “Check not found in System 1 or System 3.”

### 7. Update Work Item and Repeat Process
- Updates each work item based on search results and moves to the next WI2 item in the queue.

## Conclusion

This project streamlines the ACME WI2 research process, handling check validation across multiple systems and minimizing manual input. By integrating custom libraries for both Google Search, System1, and System3 automation, the project reduces processing time and enhances accuracy in data handling.

## Prerequisites
- UiPath Studio (latest version)
- ACME System3 desktop application
- Google Chrome
- Valid credentials for ACME System1 and ACME System3 accounts
