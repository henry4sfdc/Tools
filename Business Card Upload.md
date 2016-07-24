h1. Business Card Upload (Salesforce)
This document is meant to highlight the different levers and processes involved in uploading business card leads into Salesforce.\\

# The following business card information needs to be entered very specifically into a .csv file before uploading.
* 
** Column 1 = First Name
** Column 2 = Last Name
** Column 3 = Title
** Column 4 = Company
** Column 5 = Mobile Phone
** Column 6 = Work Phone
** Column 7 = Email
** Column 8 = Attendee Salesforce ID
** Column 9 = Sales Rep First Name
** Column 10 = Event Date
** Column 11 = Event Salesforce ID
** Column 12 = Notes from Business Card
** Column 13 = Hot Lead Designation
** Column 14 = Event Name
** Column 15 = Dates for Task Formatting e.g. (June 6 - 7)
 

2. When saved, this file should overwrite "Transcribed.csv".

3. Once you have successfully filled out your .csv file and overwritten the "Transcribed.csv" file you need to locate the "Business Card Campaign.py" file and run it. This file will automatically evaluate whether or not the emails you have written to "Transcribed.csv" exist in Salesforce and write those who don't to "Lead Insert.csv". This file is meant to specify exactly which leads do not exist in Salesforce and need to be created.

4. Open Data Loader

5. Select *Insert *and sign in.

6. Click *Next *and select the *Lead* object from the list of options.

7. *Browse* for the "Lead Insert.csv" file.

8. Click *Create or Edit a Map*

9. Click *Auto-Match Fields to Columns* and click *OK.*

10. Click *Finish*.

{color:#FF0000}11. Wait 10 Minutes or until sf_replication db has refreshed.{color}

12. Locate the "Updates & Tasks.py" file and run it. This file will grab all leads and contacts from Salesforce with emails from original "Transcribed.csv" file, their corresponding owners, statuses, etc. This then writes various information to the following files:

** "Lead Update.csv"
** "Contact Update.csv"
** "Completed Task Insert.csv"
** "Open Task Insert.csv"
        13. Run the above listed files through their respective Data Loader objects. When uploading the "Lead Update.csv" and the "Contact Update.csv" through Data Loader, be sure to use the *Update* function at the very beginning as opposed to the *Insert *function. Also, use the respective objects for each file:

* 
** "Lead Insert.csv" = *Lead, Update*
** "Contact Update.csv" = *Contact, Update*
** "Completed Task Insert.csv" = *Task, Insert*
** "Open Task Insert.csv" = *Task, Insert*
