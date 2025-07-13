# UiPath Dispatcher & Performer – Employee Data Uploader
This two‑phase UiPath solution (Dispatcher & Performer) automates the upload of employee records from an Excel file into UiPath Orchestrator queues, then processes each item with robust error‑handling logic.

## Solution Overview
| Phase | Key Actions |
|-------|-------------|
| **Dispatcher** | • Reads employee data from an Excel workbook<br>• Pushes each row as a queue item into **Orchestrator** (`EmployeeQueue`) using secure **Assets** for credentials / URLs |
| **Performer** | • Retrieves items from `EmployeeQueue`<br>• Uploads records to the target HR system/web form<br>• Applies business rules:<br>&nbsp;&nbsp;• If `CompanyName = "Timepath Inc."` → throw **Business Rule Exception**<br>&nbsp;&nbsp;• If `CompanyName = "MediCare"` → simulate **System Exception** to test retry logic |

## Tech Stack
- **UiPath Studio / Orchestrator**
- Queues & Assets (credential, config)
- Excel‑to‑DataTable conversion
- Exception handling & retry mechanism

<img width="1892" height="606" alt="image" src="https://github.com/user-attachments/assets/d0d267be-b453-411e-962b-4832e67c9cc1" />


## Project Organization Highlights
- `Dispatcher.xaml`, `Performer.xaml`,`InitAllSettings.xaml`,`ReadData.xaml` 
- Descriptive naming conventions & annotations
- Reusable components for Excel, Queue, and Logging

## Error‑Handling Logic
- **Business Rule Exception** → Marks item as *BusinessException* without retry  
- **System Exception** → Marks item as *SystemException*; Orchestrator retry enab
