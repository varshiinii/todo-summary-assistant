Todo Summary Assistant

A full-stack productivity tool that helps you manage to-do lists and summarize them with AI integration (via Cohere) and sends the summary to Slack.

->Features:
1. Add, edit, and delete todos.
2. Summarize all tasks using Cohere's LLM.
3. Automatically send summaries to a Slack channel.
4. Fully integrated with Supabase for backend data storage.

->Tech Stack:
Frontend: React, Backend: Node.js, Express.js, LLM Provider: Cohere, Database & Hosting: Supabase, Communication: Slack Webhook

->Setup Instructions
1. Clone the Repo:
git clone https://github.com/varshiinii/todo-summary-assistant.git
cd todo-summary-assistant
2. Install Dependencies
cd backend
npm install

cd ../frontend
npm install
3. Setup Supabase
Go to Supabase and create a project.
Create a table todos with the following schema:
-id: bigint (primary key)
-task: text
In the .env file in the backend/ directory, add:
SUPABASE_URL=https://<your-project-id>.supabase.co
SUPABASE_SERVICE_ROLE_KEY=<your-service-role-key>
To find the Service Role Key:
Go to your Supabase project > Settings > API
Copy the value under service_role.
4. Setup Slack Webhook
Create an incoming webhook at Slack API.
In your .env file, add:
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/your/webhook/url
5. Setup Cohere
Create an account at Cohere.
In .env:
COHERE_API_KEY=your-api-key
6. Run the app
# Backend
cd backend
node index.js
# Frontend (in another terminal)
cd frontend
npm start

->LLM & Slack Integration
The backend uses Cohere’s generate endpoint (model: command) to summarize todos.
The result is sent to Slack via the incoming webhook.
Summary triggered by a button on the frontend.

->Design/Architecture Decisions
Supabase over Local JSON: For persistence and scalability.
Cohere instead of OpenAI: Due to API quota exhaustion.
Separation of Concerns: Clean separation between routes, services, and frontend.
Slack Integration: For real-time team communication.
