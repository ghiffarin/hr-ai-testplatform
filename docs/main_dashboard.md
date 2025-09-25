### Product Requirements Document (PRD) for the Main Dashboard Feature

**1\. Feature Overview**

The Main Dashboard is the primary landing page for HR professionals upon logging into the platform. It is designed to provide a comprehensive, at-a-glance view of the most critical HR metrics and a quick navigation hub to all other platform modules. The goal is to enable HR users to quickly understand the current state of the organization and take immediate action on pending tasks.

**2\. Goals & Objectives**

*   **Primary Goal:** Provide a centralized, real-time overview of key HR data.
    
*   **Objective 1:** Reduce the time an HR user spends searching for critical information by consolidating it in one place.
    
*   **Objective 2:** Enable quick action on pending tasks, such as leave requests or approval of employee administration documents.
    
*   **Objective 3:** Provide actionable insights to help HR professionals make data-driven decisions.
    

**3\. User Stories**

*   **As an HR Manager,** I want to see a real-time headcount number so I can easily track the size of the organization.
    
*   **As an HR Manager,** I want to see a list of pending requests (e.g., leave, documents) so I can approve or deny them promptly.
    
*   **As an HR Generalist,** I want to view the current employee turnover rate so I can report on it to management.
    
*   **As a Recruiter,** I want to see a summary of the recruitment pipeline so I can quickly identify which roles need attention.
    
*   **As an HR Manager,** I want to see a quick summary of recent employee chatbot interactions so I can understand common employee queries and trends.
    

**4\. Functional Requirements**

*   **4.1. Key Metrics Widgets:** The dashboard must display real-time widgets for the following:
    
    *   **Headcount:** Total number of active employees.
        
    *   **Employee Turnover Rate:** A calculation of the percentage of employees who have left the company over a defined period (e.g., last 30 days, 90 days).
        
    *   **Recruitment Funnel Status:** Number of open roles and the number of candidates in each stage (e.g., Screening, Interview, Offer).
        
    *   **Upcoming Birthdays/Work Anniversaries:** A list of employees with upcoming special dates.
        
*   **4.2. Actionable Items Section:** A dedicated section that displays a summary of pending tasks requiring the user's attention.
    
    *   **Pending Requests:** List of requests submitted by employees via the WhatsApp chatbot that require HR approval (e.g., leave, document requests). Each item should be clickable to view full details.
        
    *   **AI-Suggested Actions:** \[Inference\]: Based on AI analysis from other modules, this section could recommend actions like "Review turnover risk for Department X" or "Update Policy Y based on high volume of related queries."
        
*   **4.3. Quick Access Navigation:** Prominently display links or icons to navigate to all other main platform modules:
    
    *   HR Insights
        
    *   Recruitment
        
    *   Employee Administration
        
    *   Employee Management
        
    *   HR Policy
        
*   **4.4. Recent Activity Log:** A feed that shows recent, high-level activities on the platform, such as new employee onboarding, offboarding of an employee, or a policy being updated.
    
*   **4.5. Search Bar:** A universal search bar that allows the HR user to search for employee profiles, policies, or specific documents from the dashboard.
    

**5\. Non-Functional Requirements**

*   **Performance:** The dashboard must load within 3 seconds, even with a large number of employees (e.g., up to 10,000). All metrics should be calculated and displayed in near real-time.
    
*   **Security:** Access to dashboard data must be restricted based on the HR user's role and permissions. For example, a Recruiter may not see turnover rates for a specific department unless they have permission.
    
*   **Usability:** The dashboard must be clean, intuitive, and visually appealing. All widgets should be self-explanatory.
    
*   **Responsiveness:** The dashboard should be accessible and fully functional on different screen sizes (desktops, tablets).
    

**6\. Assumptions**

*   Data from other modules (Recruitment, Employee Administration, etc.) is readily available via a centralized database or API.
    
*   User roles and permissions are already defined and can be used to control data visibility on the dashboard.
    
*   The system has a backend that can perform the necessary calculations for the dashboard metrics.
    

**7\. Success Criteria**

*   90% of HR users find the dashboard helpful in completing their daily tasks.
    
*   The average time to approve a request is reduced by 25% due to the "Actionable Items" section.
    
*   Users can navigate to other modules from the dashboard within 2 clicks.
    

### \[Speculation\] High-Level ERD for the Main Dashboard

This conceptual ERD focuses on the entities most directly related to the data displayed on the main dashboard. It's an abstraction and not a detailed technical diagram.

*   **HR\_User Entity:**
    
    *   hr\_user\_id (Primary Key)
        
    *   name
        
    *   role
        
*   **Employee Entity:**
    
    *   employee\_id (Primary Key)
        
    *   name
        
    *   status (Active, Inactive, etc.)
        
    *   hire\_date
        
    *   turnover\_risk\_score (from HR Insights module)
        
    *   department\_id (Foreign Key)
        
*   **Request Entity:**
    
    *   request\_id (Primary Key)
        
    *   request\_type (Leave, Document, etc.)
        
    *   status (Pending, Approved, Denied)
        
    *   submitted\_by\_employee\_id (Foreign Key)
        
    *   assigned\_to\_hr\_user\_id (Foreign Key)
        
*   **Recruitment\_Job Entity:**
    
    *   job\_id (Primary Key)
        
    *   title
        
    *   status (Open, Closed, etc.)
        
    *   candidates\_in\_stage (e.g., Interview: 5)
        
*   **Policy Entity:**
    
    *   policy\_id (Primary Key)
        
    *   title
        
    *   last\_updated
        
*   **Relationships:**
    
    *   HR\_User **has access to** Employee data.
        
    *   HR\_User **approves/denies** Request.
        
    *   Employee **submits** Request.
        
    *   HR\_User **manages** Recruitment\_Job.
        
    *   The Main Dashboard feature would **pull data from** all these entities to populate its various widgets and lists. It's a view, not a new entity itself.