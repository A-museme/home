# Custom CRM Modules for LLM-Based Summarization and Automated Follow-Up

**Technologies Used:**  
![Node.js](https://img.shields.io/badge/-Node.js-339933?logo=nodedotjs&logoColor=white) ![OpenAI API](https://img.shields.io/badge/-OpenAI_API-4299E1?logo=openai&logoColor=white) ![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?logo=javascript&logoColor=black) ![Google Apps Script](https://img.shields.io/badge/-Google_Apps_Script-E8F2FD?logo=google&logoColor=white) ![MongoDB](https://img.shields.io/badge/-MongoDB-47A248?logo=mongodb&logoColor=white) ![REST APIs](https://img.shields.io/badge/-REST_APIs-228B22?logo=api&logoColor=white) ![React](https://img.shields.io/badge/-React-61DAFB?logo=react&logoColor=black)

## Overview
Developed custom modules for an internal CRM system that leveraged large language models (LLMs) to pass contact properties (such as name, last name, follow-up date, email conversations, and notes) with proper context. The system provided actionable summarizations and an interactive interface, allowing users to engage with CRM data directly on contact pages. This integration enabled drafting of personalized, accurate follow-up emails and enhanced customer relationship management through AI-driven insights.

## Key Features
- **Property Contextualization for LLMs:** 
  - Passed CRM data (contact details, follow-up history, emails, and notes) to LLMs with specific context about what each property represents. This contextualization allowed the model to generate meaningful, action-oriented summaries that were directly relevant to the sales team.

- **LLM Summarization & Insights:** 
  - Automated the summarization of contact interactions, including previous conversations and follow-up actions. This feature allowed sales teams to gain quick insights and create next steps based on real-time data, improving decision-making efficiency.

- **Email Draft Generation:** 
  - Generated highly personalized follow-up emails based on CRM data. This feature made outreach more relevant to each contact’s history and context, enhancing the likelihood of successful communication.

- **Chat Interface for CRM Data:** 
  - Developed an interactive chat interface that allowed users to engage directly with CRM data. Users could ask for summaries, follow-up actions, or suggestions based on the history of a given contact, making the CRM more user-friendly and intuitive.

## Process

### Research & Planning
- Identified the need for more personalized and relevant follow-up actions based on CRM data and prior contact interactions. The team recognized that summarizing and generating insights manually was time-consuming and often led to inconsistencies in communication.

- Outlined a strategy to integrate LLMs to automatically summarize contact details, interactions, and draft follow-up emails that were accurate and tailored to individual contacts. This strategic move aimed to enhance efficiency and reduce manual workloads for the sales team.

- Created a roadmap for developing custom modules within the existing CRM, leveraging LLMs for actionable insights and automating workflows. This plan included defining the project scope, necessary resources, and potential challenges.

### Development
- **Contextualizing Contact Properties:** 
  - Developed custom logic to extract CRM properties such as first name, last name, follow-up date, and email threads. Each property was passed to the LLM with clear descriptions of its role, ensuring that the model could accurately interpret the data.

- **LLM API Integration:** 
  - Integrated the OpenAI API to process contact data and generate summaries or suggest follow-up actions. Ensured that API requests provided the LLM with clear context about the CRM data, including the importance of each contact property to enhance the relevance of the responses.

- **Data Formatting for Summarization:** 
  - Structured the CRM data in a format that allowed the LLM to parse it effectively. This included chronological lists of email exchanges, follow-up dates, and user notes, enabling the LLM to summarize the data into concise and actionable insights for the sales team.

- **Follow-Up Email Drafting:** 
  - Developed an automated email drafting feature that utilized the LLM to generate personalized follow-up emails based on previous conversations and the sales stage of each contact. Emails were automatically tailored to the contact’s history, addressing their specific needs or concerns to improve engagement.

### Interactive Chat Interface
- **Chatbot UI on Contact Pages:** 
  - Built a React-based chat interface integrated into the CRM’s contact pages, enabling users to interact with the CRM data through natural language queries (e.g., "What is the best follow-up message for this lead?" or "Summarize my last call with this contact"). This feature made data retrieval more intuitive for users.

- **LLM Interaction for Real-Time Summaries:** 
  - Allowed users to query the LLM for real-time summaries or suggestions on next steps, empowering sales teams to make decisions faster and with greater accuracy. The chatbot provided actionable recommendations on when and how to follow up, ultimately enhancing productivity.

---

This project significantly enhanced the internal CRM's capabilities by utilizing AI-driven insights, leading to improved efficiency in managing customer relationships and more effective follow-up strategies.
