**Automation Agents** are a core and powerful feature within the Gridlex App Builder designed to **automate business processes**. They act as **intelligent assistants that execute predefined sequences of steps automatically**, triggered by specific events or schedules. Their primary purpose is to **streamline business processes, reduce manual effort, and save time**.

### What are Automation Agents and Their Importance?
The App Builder uses "models" as fundamental building blocks to hold all the information a client application needs. While storing data in models is essential, it's not sufficient to create truly valuable applications. Automation Agents are the sophisticated solution provided by Gridlex App Builder to **bring critical business logic to these models**, transforming them into dynamic applications. This allows for the automation of intricate processes that would otherwise require manual intervention.

### Key Use Cases
Automation Agents are crucial for handling various business needs and workflows. Examples of their application include:
*   **Lead Assignment Automation**: Automatically assigning new leads to the appropriate sales representative based on predefined criteria like region or product interest, ensuring no lead is missed and sales teams can act quickly.
*   **Expense Approval Process**: Automatically sending approval requests to managers at the correct level based on the expense amount when a user submits a new expense, ensuring efficient and timely processing.
*   **Event Management**: Automatically creating an event member record and sending a confirmation email upon customer registration for an event, keeping attendees informed and organized.
*   **Auto-Close Cases**: Automatically closing customer support cases that have remained in a "Pending Customer Response" status for a set period (e.g., 14 days), which helps keep the support queue clean and current.
*   **Custom Workflows on Email Receipt**: When an email is received in a Shared Inbox, Automation Agents can be configured to:
    *   Feed the incoming email content to an LLM (Large Language Model) to categorize it (e.g., as a lead, support issue, or feedback) or extract structured output.
    *   Check for specific conditions within the email body or content to make further decisions.
    *   Create or update a record in a specific model and associate the email with it.
    *   Send notifications to internal team members for quick responses.

### Key Terms in Automation Agents
To understand how Automation Agents function, several key terms are important:
*   **Module Type**: Indicates the core area where the trigger for the automation belongs, such as Inbox, Models, or Webhooks.
*   **Modules**: Specific instances of a Module Type (e.g., "Support Inbox" under Inbox Module Type, or "Expenses Model" under Models Module Type).
*   **Steps**: The individual actions or units of work performed by an Automation Agent. A sequence of these steps forms the complete automation logic, such as sending an email or updating a record. A step can be executed immediately or scheduled.
*   **Edges**: Directional pathways that connect any two steps within an Automation Agent, dictating their precise execution sequence.
*   **Transactions**: Database operations that occur within the context of Automation Agents, such as creating, updating, or deleting a record.
*   **Transaction Atomicity**: A crucial property that ensures that a series of database transactions either all succeed and are saved, or if any part fails, none are saved, thus maintaining data integrity.
*   **Triggers**: The actions or events that initiate the execution of an automation, telling the system "when" to start. Examples include record creation or email receipt.

### Types of Automation Agents
Automation Agents in Gridlex App Builder are categorized based on their initiation method:
*   **Trigger-Based Automation Agents**: These are reactive and immediate, operating on predefined triggers based on user interaction or system events. Triggers can originate from:
    *   **Inbox**: Email Sent, Email Received, Email Received or Sent.
    *   **Models**: Record Created, Record Updated, Record Created or Updated, Record Deleted.
    *   **Webhook**: Webhook Received.
*   **Schedule-Based Automation Agents**: These run at specific times or intervals without any direct user interaction, making them ideal for routine tasks.
*   **No-Trigger Automation Agents**: These agents are not tied to a specific trigger or schedule. They can be manually called, often used for AI Form Agents or as callable functions within other automations. They function like **reusable functions**, providing reusable logic, enabling composable automations, and can be triggered from UI buttons. They use Input Variables (parameters passed when calling) and Output Variables (results returned).

### Automation Steps and Execution Flow
**Automation Steps** are the individual actions that an Automation Agent performs, forming the complete automation logic. These steps can include actions like Variable Assignment, Logic, getting/creating/updating/deleting records, sending emails, executing LLM (Large Language Model) interactions, For Loops, Triggering other Automations, and making HTTP/Webhook requests.

When a record is saved (created, updated, or deleted), a sophisticated flow of Automation Agents can be initiated based on their execution timing:
*   **Before Record Save**: Agents run before the record is committed to the database, primarily for real-time field updates and data validations (e.g., populating default values, validating data).
*   **After Record Save**: Agents run after the record is committed to the database, used for simple post-save actions (e.g., sending confirmation emails, updating related counters).
*   **In the Background**: These agents run as part of the App Builder's Background Jobs Runner, typically for complex or time-consuming operations that don't need immediate completion (e.g., syncing extensive customer data with a third-party CRM).

It's also important to note that multiple Automation Agents can be set up for a single trigger on a module, with their execution order dependent on their creation date.
