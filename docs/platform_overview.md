### Overall Platform PRD for HR-AI Platform

**1\. Product Vision**

The HR-AI platform is a comprehensive solution designed to empower HR professionals by leveraging AI to streamline core HR functions. The platform acts as a centralized dashboard for HR teams, providing tools for data analysis, recruitment, employee administration, and policy management. A key component of the system is a WhatsApp chatbot, which serves as the primary interface for employees to interact with HR services and information, creating a seamless two-way communication channel. The goal is to reduce manual HR workload, provide actionable insights, and enhance the employee experience through accessible, AI-powered self-service.

**2\. Stakeholders**

*   **Primary Users:** HR Managers, Recruiters, HR Generalists.
    
*   **Secondary Users:** All employees (via the WhatsApp chatbot).
    
*   **Key Stakeholders:** HR Leadership, IT Department, Executive Management.
    

**3\. User Personas**

*   **HR Manager (Alex):** Needs a holistic view of the organization. Focuses on strategic insights from the dashboard, approving requests, and ensuring policy compliance.
    
*   **Recruiter (Sarah):** Needs an efficient way to manage the recruitment pipeline. Uses the platform to post jobs, track applications, and manage candidate communication.
    
*   **Employee (Maya):** Wants quick and easy access to information. Uses the WhatsApp chatbot to ask about policies, check leave balances, or submit administrative requests.
    

**4\. Core Features**

*   **Main Dashboard:**
    
    *   **Description:** A centralized hub for HR professionals. Provides a high-level overview of key HR metrics and a quick access point to all platform features.
        
    *   **Key Metrics:** Headcount, employee turnover rate, recruitment pipeline status, and leave requests pending approval.
        
*   **HR Insights:**
    
    *   **Description:** An AI-powered analytics module that provides predictive and prescriptive insights based on HR data.
        
    *   **AI Functionality:** \[Inference\]: Predicts employee turnover risk, analyzes sentiment from employee feedback, and identifies potential areas for policy improvement.
        
*   **Recruitment:**
    
    *   **Description:** A module to manage the entire recruitment lifecycle, from job posting to offer letter generation.
        
    *   **AI Functionality:** \[Inference\]: AI-driven resume screening and candidate matching based on job descriptions.
        
*   **Employee Administration:**
    
    *   **Description:** Tools for managing employee data, onboarding, offboarding, and handling administrative requests.
        
    *   **Core Functions:** Manages employee profiles, handles leave requests, and processes expense claims.
        
*   **Employee Management:**
    
    *   **Description:** A module focused on employee performance and development.
        
    *   **Core Functions:** Manages performance reviews, sets goals, and tracks training programs.
        
*   **HR Policy:**
    
    *   **Description:** A centralized repository for all company policies.
        
    *   **AI Functionality:** \[Inference\]: AI-powered search and summarization for employees via the WhatsApp chatbot, making it easy to find specific policy details.
        
*   **WhatsApp Chatbot (Employee Interface):**
    
    *   **Description:** The primary channel for employees to interact with HR services.
        
    *   **Functionality:**
        
        *   **Policy Queries:** Answers questions about company policies (e.g., "What is the WFH policy?").
            
        *   **Administrative Requests:** Allows employees to submit requests (e.g., "I need a letter of employment").
            
        *   **Status Updates:** Provides updates on submitted requests.
            
        *   **Escalation:** \[Unverified\] Routes complex queries to an HR professional via the dashboard.
            

**5\. User Stories**

*   **As an HR Manager, I want to see a dashboard with key metrics so I can quickly assess the health of the organization.**
    
*   **As an Employee, I want to ask about the company's leave policy through the WhatsApp chatbot so I don't have to search for the policy document.**
    
*   **As a Recruiter, I want the AI to suggest candidates based on a job description so I can quickly shortlist the most qualified applicants.**
    
*   **As an Employee, I want to request a letter of employment through the WhatsApp chatbot so I can get it approved by an HR manager.**
    
*   **As an HR Manager, I want to approve or deny an employee's request for a letter of employment from the dashboard so the process is documented and auditable.**
    

**6\. High-Level Requirements**

*   **System Architecture:** The platform will consist of a web-based dashboard for HR and a separate API for the WhatsApp chatbot integration.
    
*   **Security:** The platform must comply with data privacy regulations (e.g., GDPR, CCPA). All data must be encrypted in transit and at rest.
    
*   **Scalability:** The platform must be able to handle a growing number of employees and data.
    
*   **Integrations:** The platform must integrate with the WhatsApp Business API. Future integrations may include payroll systems and other HRIS.
    
*   **Usability:** The HR dashboard must have an intuitive and clean user interface. The WhatsApp chatbot must be responsive and easy to use for all employees.
    

**7\. \[Unverified\] High-Level ERD (Entity-Relationship Diagram) Concept**

\[Speculation\]: An ERD for this platform would likely include the following core entities and their relationships. This is a conceptual overview and not a finalized technical diagram.

*   **Employee**:
    
    *   Attributes: employee\_id, name, email, department, job\_title.
        
*   **HR\_User**:
    
    *   Attributes: hr\_user\_id, name, email, role (e.g., HR Manager, Recruiter).
        
*   **Policy**:
    
    *   Attributes: policy\_id, title, content, last\_updated.
        
*   **Request**:
    
    *   Attributes: request\_id, request\_type (e.g., leave, letter), status, submitted\_by\_employee\_id, reviewed\_by\_hr\_user\_id.
        
*   **Chatbot\_Interaction**:
    
    *   Attributes: interaction\_id, employee\_id, message\_text, timestamp, ai\_response\_text.
        
*   **Recruitment\_Job**:
    
    *   Attributes: job\_id, title, description, status.
        
*   **Recruitment\_Candidate**:
    
    *   Attributes: candidate\_id, name, email, resume, applied\_to\_job\_id.
        

**Relationships:**

*   Employee has many Request.
    
*   HR\_User reviews many Request.
    
*   Policy is queried via many Chatbot\_Interaction.
    
*   Employee has many Chatbot\_Interaction.
    
*   Recruitment\_Job has many Recruitment\_Candidate.
    
*   HR\_User (specifically Recruiters) manages Recruitment\_Job.