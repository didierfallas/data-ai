# RL SOAR Proposal for Q4 

## Premium service to set the stage for 2025

With “primary” Q4 feature development targets in mind ([see notes](#bookmark=id.tqb7eajqaj9z)):

### **1\. Team Enhancements**

* **Front-end (Application Dev Team) Team Expansion**: Increase Front-end development resources to 3.75 FTEs.  
* **Seniority**: Incorporate more senior resource FTE time for improved quality and oversight.  
* **Dedicated resource**:  Clever Serrano, a senior team member, will be dedicated to SOAR for Q4 to ensure continuity and quality.  
* **Mix of Roles**: Currently, there are 10 Siftia team members that contribute to the 6.5 FTEs.  This mix of talent, allows greater flexibility on the assignment of FTEs as the platform needs arise.  The application dev team includes a mix of senior and mid-level developers. Data Team senior resources total 2.5 FTEs, and 0.25 FTE for senior Cloud Engineering.  
* **Project Management Support**: 0.5 FTE allocated to Project Management, ensuring seamless project execution.  To date, Siftia has been providing 7 FTEs as the PM role and time has not been billed as part of the FTEs.   

### **2\. Reporting Improvements**

* **Monthly Reports**: Provide detailed monthly reports on resource allocation (FTEs by areas of service such as Support, Maintenance, and Feature development).  
* **Role Reporting**: Break down resource usage by FTE specialty (Front-end, Data, Cloud Engineering).  
* **SLA Dashboard**: Continue enhancing SLA dashboard to monitor incident compliance, response times, and resolution times, ensuring transparency in service level agreements.  The SLA dashboard time and improvements are not billed to Recovery Link.

### **3\. Productivity and Quality Enhancements**

* **Collaborative Development (Pair Programming)**: Strengthen Application Dev Team teamwork by using techniques such as pair programming to prevent deadlocks, improve code quality, and bring diverse perspectives to problem-solving.  
* **Quality Assurance (QA) Processes**: Enhance QA by introducing QA tasks to ticket workflow, using checklists, and progressing towards automated testing. This ensures that quality control is maintained from the early stages of development.  
* **Improved Project Management**: Enhance communication and planning through better documentation (e.g., Jira updates and Slack follow-ups) and better handling of task dependencies to improve sequencing and prioritization.  
* **Maintenance routines**: As mentioned on the recent call, we have a list of maintenance routines that we perform and that we will begin to report on via the Jira platform.  To date these were documented in our internal ticketing system.  [See routines](#bookmark=id.c2j9a6rfd1q7)

### **4\. Product Owner Partnership**

* **CX and Product Owner and Data Quality Dashboards**: Continue to work closely with the Product Owner to improve Customer Experience (CX) insights and data quality tracking.  
* **Roadmap Ideation**: Collaborate on developing and refining the product roadmap, ensuring alignment with Recovery Link’s long-term goals.  [See ideas](https://docs.google.com/document/d/1lkZqpSV5YkxpcoiVGd_nk8tNt4SCmljyWlcP5GQ8kVM/edit#heading=h.1satpwi5ws2z)

## Discounts over 18 months (duration)

**Total Discount in PM cost** 

* PM 0.5 FTE  \= $3,900/month (Total $70,200) 5%

**Total Discount lower rate**

* Monthly rate 6.5 FTEs \= $14,300/month ($258,570)  20% discount past 18 mo

**Equivalent current cost (normal equivalent for ‘premium service’ we’re** 

* $68,800/month (this level of premium service today would be at this level).versus current $49,875 

# ANNEX

1. # Primary Q4 targets

* **Staff Profile [ERR-38](https://team-1607816385495.atlassian.net/browse/ERR-38)**  
  * Summary… Add Staff Context and UI similar to participant profile  
  * Correct issues in existing records from initial migration  
  * I believe that Alonso can most effectively deliver this full scope with Data Team support.  
* **Audit Log [ERR-67](https://team-1607816385495.atlassian.net/browse/ERR-67)**  
  * Still getting fully defined  
  * Initial requirement is part of Staff Profile but should translate to other needs.  
  * Data is being captured but requires corrective steps to meet requirements  
  * Caliche created the Audit Log app so will be involved here, but is really about 3 UI pages to expose audit log date to administrators. Santi might be able to do this in tandem with CV.  
* **Multi-factor Auth [ERR-928](https://team-1607816385495.atlassian.net/browse/ERR-928)**  
  * Blocked by my inability to focus time on the full requirements for UI integration and needs.  
  * Pravia has been indicated to me as a possibility to work on this in the wake of prototyping done by Julio Silva. But I believe there will be front-end requirements that I think Carlos V & Alonso are best suited for.

**Other targets for Q4**

* **Assessments integration release [ERR-583](https://team-1607816385495.atlassian.net/browse/ERR-583)**  
  * We’re pretty good here. Just waiting for final QA on Microservices side  
* **Finish dynamic navigation [ERR-597](https://team-1607816385495.atlassian.net/browse/ERR-597)**  
  * This was supposed to be part of original dynamic menu requirements, was skipped, and is now being spun as a large re-factoring (admittedly with some value adds)  
  * I have 80% of new requirements specified  
  * Known, untouched since April [ERR-797](https://team-1607816385495.atlassian.net/browse/ERR-797)  
* **Kiosk v2 [ERR-939](https://team-1607816385495.atlassian.net/browse/ERR-939)**  
  * Like Assessments, we’re in good shape here and awaiting release plan.  
* **Telerecovery integration [ERR-1093](https://team-1607816385495.atlassian.net/browse/ERR-1093)**  
  * Finish review and update of current integration points.  
  * In current assignments.  
* **Stored Procedures/Scheduled Queries [ERR-961](https://team-1607816385495.atlassian.net/browse/ERR-961)**  
  * Defined in July, Data Team was going to secure these important resources in code management and create an archiving system to save money on storage costs  
  * Julio Silva started in here. Understandable that his departure added delay.

**Issues to reintroduce into planning**  
Identified immediately upon my start in SOAR, these issues continue to bubble up and cause process issues and lost time in manual reviews.

* Code workflow, testing, and build management  
  * *Some* progress has been made over 18 months and I have had to continually de-prioritize in relation to customer facing needs  
  * This continues to be a key factor in delays to delivery. With an automated testing system we could eliminate hours of human effort by allowing machines to verify test steps. It would also eliminate a lot of the "kick back" on issues where I review and find no solution provided since dev team would have a way to check their own work.

2. ## Resource equivalents dedicated (historical)

[SR4 SOAR (Hours 2024\)](https://docs.google.com/spreadsheets/d/1jbG7R4FZDSIX3fjkKq9n5Y22eZownfSQhBCbv2R8dq8/edit?gid=1016514640#gid=1016514640)

3. ## **MAINTENANCE, SUPPORT** **& FEATURES** \- Service Descriptions**:**

**The Maintenance service (PROACTIVE Attention) consists of: 30%\***

* INFRA:   Infrastructure monitoring, assurance and maintenance  
  * Cloud infrastructure monitoring to ensure the stability of the service   
  * Promptly raise alerts for incidents to minimize impact and restore normal operations  
  * Manage updates for software and tools, and provide users with information on usage and maintenance to ensure optimal performance.  
  * Oversee the provisioning of application, data, and cloud architecture to ensure efficient and scalable infrastructure.  
  * Conduct cost analysis to optimize resource allocation and manage expenses effectively  
  * Oversee the monitoring of billing, subscriptions, licenses, SSL certificates, and hosting domains to ensure compliance, cost efficiency, and uninterrupted service.  
  * Manage notification channels for cloud services and external providers to ensure timely alerts and updates.  
  * Manage GCP services backups to ensure business continuity.  
  * Manage security notifications, security audits, and apply security patches to maintain a secure and resilient environment.  
  * Manage and monitor the GCP cloud services dashboard to maintain optimal performance and quickly address potential issues.  
  * Review, validate, and update the Disaster Recovery Plan to ensure it remains effective and aligned with current business needs.  
  * Organize, maintain, and update all critical documentation to ensure accurate and accessible records that support efficient operations and compliance.

* DATA:  Data monitoring, assurance and maintenance  
  * Data quality management to ensure the stability of the service.   
  * Promptly raise alerts for incidents to minimize impact and restore normal operations.  
  * Oversee and manage data transfer processes to ensure secure and efficient movement of data across systems.  
  * Implement and manage backup and restore strategies to safeguard data and ensure rapid recovery in case of loss.  
  * Monitor and optimize data performance to ensure fast and reliable access to critical information.  
  * Manage data archiving processes for both files and data tables, ensuring long-term storage and easy retrieval when needed.  
  * Organize, maintain, and update all critical documentation to ensure accurate and accessible records that support efficient operations and compliance.  
* APP:  Application monitoring, assurance, and maintenance  
  * Application monitoring to ensure the stability of the service   
  * CX evaluations and improvements recommendations  
  * CX A/B testing   
  * CX UI Refactoring  
  * UI Style guide maintenance  
  * Promptly raise alerts for incidents to minimize impact and restore normal operations  
  * Manage updates for software and tools, and provide users with information on usage and maintenance to ensure optimal performance.  
  * Address and resolve compatibility issues between software and tools to ensure integration and functionality.  
  * Oversee and manage deployment processes to ensure efficiency, smooth, and error-free software releases.  
  * Coordinate and manage testing activities to validate software functionality, performance, and quality.  
  * Continuously monitor and enhance application performance to improve speed, reliability, and user satisfaction.  
  * Implement refactoring initiatives to enhance security, reliability, and maintainability of the codebase.  
  * Lead efforts to enhance user experience through continuous evaluation and improvements.  
  * Manage and update the product owner dashboard to provide clear insights and data-driven decisions.  
  * Organize, maintain, and update all critical documentation to ensure accurate and accessible records that support efficient operations and compliance.

   
**The Support service (REACTIVE Attention) consists of: 20%\***

* Cloud services support   
* Data management support  
* Application support  
* Providing a customer assistance service and emergency assistance to guarantee the proper management of reactive requests that need to be attended to for the correct functioning of the client's platform.  These issues are commonly referred to as “Bugs”.

**Features (Implement new functionalities) 50%\***

* Data Optimization and Backup Enhancements:   
  * Implement automated data cleanup processes to improve performance and storage efficiency.   
  * Introduce advanced backup and recovery mechanisms to ensure data integrity and quick restoration in case of failures.  
* Cloud Infrastructure Security and Scalability Improvements:   
  * Upgrade security protocols and implement real-time monitoring to detect and prevent potential threats.   
  * Optimize cloud resource allocation and scaling policies to improve cost efficiency and accommodate growing user demands.  
* React Client Performance and UI/UX Upgrades:   
  * Enhance the front-end performance by optimizing component rendering and reducing load times.   
  * Update the user interface to be more intuitive and accessible, ensuring a seamless experience across all devices and platforms.

\*Reference for 6-8 FTE resource equivalents.

4. ## Ideas (Future SOAR)

[Future of SOAR \- 2024](https://docs.google.com/document/d/1lkZqpSV5YkxpcoiVGd_nk8tNt4SCmljyWlcP5GQ8kVM/edit#heading=h.1satpwi5ws2z)

# 

# ---

# ChatGPT ideas:

To craft a compelling argument for selling the upcoming three-month contract at better terms, while still addressing the client's concerns about improved productivity and quality, the following points could be emphasized:

### **1\. Enhanced Seniority and Expertise:**

* **Argument**: “We are allocating more senior and experienced resources to ensure the quality and productivity improvements requested. Senior developers, such as Carlos Valverde, will not only contribute directly to development but also guide the team, improving the overall quality of output.”  
* **Value to Client**: Emphasizing the value of seniority can help justify a higher rate, as experienced developers often deliver better results faster, minimizing rework and improving efficiency.

### **2\. Improved Transparency and Reporting:**

* **Argument**: “In addition to dedicated resources, we will implement advanced reporting and time usage transparency to ensure full visibility into how resources are allocated and how improvements are being made.”  
* **Value to Client**: Offer the client greater insight into where time is spent, allowing them to see the productivity gains directly. This can be a selling point for a premium service, especially when you tie it to measurable outcomes.

### **3\. Stronger Quality Processes:**

* **Argument**: “To address concerns about quality, we will enhance our quality assurance processes, including more rigorous code reviews, automated testing, and continuous integration workflows to ensure that the work meets your standards consistently.”  
* **Value to Client**: Assure the client that the increased focus on quality will prevent the issues experienced with the Frontend work, ultimately saving them time and frustration by reducing bugs or rework.

### **4\. More Efficient Project Management Support:**

* **Argument**: “Our improved project management will provide better alignment between your expectations and the work being delivered. By increasing our PM resource allocation, we will streamline communication and ensure quicker response times to any issues.”  
* **Value to Client**: You’ve been providing this PM resource at 0.5 FTE at no cost. You can now explain how the improved PM structure will ensure the project stays on track, and make the case that this resource is even more critical now, justifying a more formal inclusion.

### **5\. Long-Term Value:**

* **Argument**: “Although this contract is only for three months, the investment in higher-quality resources and processes will lead to longer-term cost savings by reducing the number of revisions and ensuring smoother project completion.”  
* **Value to Client**: Highlight that while the short-term costs may be higher, the client will benefit from fewer problems and faster turnaround times in the long term, making this a cost-effective solution.

### **Example of Pricing Positioning:**

1. **Previous Contract**:  
   * FTEs at $50/hour, including a PM at 0.5 time for free.  
2. **New Proposal**:  
   * Senior and mid-level resources at market rates ($62.50 or higher for seniority), with a focus on quality and transparency.  
   * Offer some flexibility with junior developers to balance the budget.  
   * Explain that the free PM was a goodwill gesture for the long contract but going forward, proper management is critical for the improved quality and productivity they are seeking.

---

### **Combating push-back Final Pitch:**

Your sales team can position this three-month contract as a **premium service**, offering the client:

* **Improved seniority and expertise** for better outcomes.  
* **Better resource allocation transparency** so they can track and understand how improvements are being made.  
* **Enhanced quality control** through refined processes.  
* A strong **PM resource** to keep the project on track and aligned with their goals.

To address the team's concern that the client may reject increasing costs or the 6.5 FTE proposal, you can create a **tiered proposal** that offers flexibility while still emphasizing the improvements in quality and productivity. This way, the client can see that they have options and can choose what aligns with their budget, while still addressing their request for better performance.

### **Tiered Proposal Options:**

#### **Option 1: Full Senior Commitment (Higher Cost)**

* **6.5 FTEs**, with a higher percentage of senior resources to ensure improved quality.  
* **Carlos Valverde (Full-time)**: Blended rate for architecture and development work.  
* **Marcelo (Full-time)**: Lower rate to balance cost, but full commitment and passion for front-end work.  
* **Partial PM (0.5 FTE)**: Included to ensure smooth project management.

**Key Selling Points**:

* Full-time senior and junior resource allocation for full focus.  
* The best option for achieving the client's goals of improved productivity and quality.  
* High accountability with a dedicated PM ensuring alignment.

#### **Option 2: Balanced Approach (Mid-tier Cost)**

* **4-5 FTEs**, with a mix of senior and mid-level resources, plus a more junior resource to balance costs.  
* **Carlos Valverde (Part-time)**: Used strategically for architecture and oversight.  
* **Marcelo (Full-time)**: Full-time front-end support at a competitive rate.  
* **Luis Alonso (Part-time)**: Retain some involvement without over-committing him.

**Key Selling Points**:

* A cost-conscious approach that still provides senior oversight and ensures quality improvements.  
* Focus on blending seniority and junior talent for productivity gains.  
* Reduces the cost while still aligning with the client’s request for consistency and quality.

#### **Option 3: Cost-Conscious Commitment (Lower Cost)**

* **3-4 FTEs**, focused on a leaner team but with targeted improvements.  
* **Carlos Valverde (Part-time)**: Only involved for key oversight and architecture work.  
* **Marcelo (Full-time)**: Focus on front-end work at a lower rate.  
* **Reduced PM (0.25 FTE)**: Minimal project management to keep costs low but still maintain oversight.

**Key Selling Points**:

* The most cost-effective approach.  
* Ensures some level of senior oversight while keeping the front-end focus with a junior developer.  
* Keeps the commitment to quality and transparency at a reduced cost.

---

### **Strategic Messaging to the Client:**

1. **Flexibility**: Emphasize that you are offering multiple options based on their priorities, whether it be quality, cost-efficiency, or a balance of both.  
2. **Improved Productivity**: All options address their request for better productivity and quality, even if they choose a more cost-effective option.  
3. **Long-term Partnership**: Frame the discussion around a partnership approach, showing that these improvements will provide long-term value and savings, especially in terms of reduced rework and faster delivery.

### **Final Approach:**

When presenting these options, you can highlight how each proposal aligns with their needs for better performance while offering them flexibility on cost and resource dedication. This gives the client control over their decision-making and may increase the likelihood of a positive outcome.

Conversation keypoints: (Carmen)

[https://docs.google.com/presentation/d/1IuXIW-MiWm8s85BqP6VYaXp2ZCXS66B3xiCuQryAe1E/edit\#slide=id.g30447bd3f51\_0\_50](https://docs.google.com/presentation/d/1IuXIW-MiWm8s85BqP6VYaXp2ZCXS66B3xiCuQryAe1E/edit#slide=id.g30447bd3f51_0_50)

* **Plan to improve the service**  
  * 4 points  
  * TEAM  
    * “Front-end” (i.e. Application Development)  
      * Increase Front-end to 3.75 FTEs  
      * Increase seniority of Front-end team (i.e. more time of Senior resources in FTEs)  
  * REPORTING  
    * Detailed reporting  
  * PRODUCTIVITY / QUALITY  
    * Process improvements  
  * PRODUCT OWNER PARTNERSHIP  
    * Improve/extend CX and Product / Data Quality Dashboards  
    * Product roadmap ideation  
* **Proposal as we continue the relationship**:  
  * Scenario 1:   
    * Hourly rate: $62.50  
    * PM time billed   
    * Minimum time contract: 3 months  
  * Scenario 2:  
    * Hourly rate: $59  
    * PM time billed   
    * Minimum time contract: 6 months  
  * Scenario 3:  
    * Hourly rate: $56  
    * PM time billed (10% discount)  
    * Minimum time contract: 12 months  
* Other ideas:   
  * New deal with new business model (p.e. Staff augmentation)  
  * What other business models?  
* Value Proposition: Benefits that Siftia has provided, costs of switching teams

