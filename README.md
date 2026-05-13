# technical-test-submission
1.Airtable base link or screenshots
https://airtable.com/invite/l?inviteId=invwXV3Rev405G2Ki&inviteToken=6e330cc665533cf1eb459c8403142ef9b423c122e85d3790daf8c8b0c5f57787&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts
2.n8n workflow export JSON
# Workflow Logic Explanation

This workflow automates the follow-up task process for students using Airtable and Gmail, while also handling error logging at each critical step.

1. The workflow starts manually using the **Execute Workflow** trigger.

2. It searches the **Students** table in Airtable to retrieve student records that require follow-up actions.

3. An **IF** node checks whether the student search was successful:
   - If the search fails, an error record is created in the log table.
   - If successful, the workflow continues.

4. Follow-up tasks are then created in Airtable for the retrieved students.

5. Another **IF** node validates whether the follow-up task creation succeeded:
   - If task creation fails, the workflow logs the error.
   - If successful, the workflow proceeds to update task-related checkboxes for the created students.

6. A second validation step checks whether the checkbox update operation succeeded:
   - If it fails, the workflow logs the failure.
   - If successful, the workflow continues to send notification emails.

7. Gmail is used to send follow-up notification messages.

8. A final **IF** node checks whether the email was sent successfully:
   - If successful, a success log record is created.
   - If the email fails, the workflow logs the notification error.

## Summary

The workflow ensures that:

- follow-up tasks are automatically generated,
- student records are updated,
- notifications are sent,
- and all failures are captured through centralized logging for easier debugging and monitoring.

# Screenshots 
## images for inital airtables
<img width="3840" height="2160" alt="image for student table" src="https://github.com/user-attachments/assets/fc0f690f-1903-4bc4-8c2a-45e123b41ffa" />
<img width="3840" height="2160" alt="image for follow up tasks table" src="https://github.com/user-attachments/assets/c1d6c43e-ff68-4f50-ae95-5835e5900e78" />
<img width="3840" height="2160" alt="image for Automation Logs table" src="https://github.com/user-attachments/assets/ef456a4c-2f65-4786-9eef-bffaabf40aaa" />

## images for the automation workflow
<img width="3446" height="1890" alt="image" src="https://github.com/user-attachments/assets/a7d38d77-6489-4c9b-ae87-ccc8a902f0d4" />

## images for airtables after workflow execution
<img width="3840" height="2160" alt="image of students table after automation" src="https://github.com/user-attachments/assets/bbe069e5-a8af-4ace-b1c3-2b6d0235ff0b" />
<img width="3840" height="2160" alt="image of follow up tasks table after automation" src="https://github.com/user-attachments/assets/ca6e28a2-5473-43d2-a067-2ba6054c596a" />
<img width="3840" height="2160" alt="image of Automation logs after automation" src="https://github.com/user-attachments/assets/29269d83-d7d2-4a56-b28f-d84318df7fd3" />

# Test case preventing duplicates
After triggered the automation once again, the workflow stops at the searching node since no output data is returned(The tasks have already been created and the checkboxs are checked thus no student will match the searching conditons)
<img width="3840" height="2160" alt="image showing workflow stops at searching node" src="https://github.com/user-attachments/assets/e7c42084-030d-4a78-8f48-b8df25ee431e" />
All the tables remain the same and this workflow is not logged since it stops halfway.

# Notification email
<img width="3840" height="2160" alt="image" src="https://github.com/user-attachments/assets/1328669a-a4fb-4180-8443-c918f56af4e2" />
<img width="3840" height="2160" alt="image" src="https://github.com/user-attachments/assets/ccb1ad3b-e111-4257-9c3e-85ac4bc4ba1e" />


# Error Log 
The log will show which node is wrong and show the error message.
If the creating node is not working due to some syntax error in the workflow.
<img width="3754" height="1794" alt="image" src="https://github.com/user-attachments/assets/04295cda-117a-42c3-9c9c-3f7cb436d9dc" />
Then the workflow will log the error into airtable
<img width="3426" height="1902" alt="image" src="https://github.com/user-attachments/assets/34048a97-cded-4020-a700-5dee0db42dde" />
<img width="3840" height="2160" alt="image" src="https://github.com/user-attachments/assets/2023bfd1-6b97-4ee1-8cf0-7bea359dc4ee" />
Similar logic applies to all the important nodes.





