# Email Support Automation with n8n

This project automates customer support email replies using **n8n**, **Gmail**, **Google Sheets**, and **Google Gemini AI**.  
<img width="1319" height="580" alt="image" src="https://github.com/user-attachments/assets/319ab546-5600-4333-8c56-6ba61fa70b4a" />


📄 Full documentation:  
[Email_Support_Automation_Documentation.pdf](docs/Email_Support_Automation_Documentation.pdf)

---

## 🚀 Features
- Monitors Gmail inbox for new support requests.
- Extracts email fields (sender, subject, body).
- Searches historical Q&A stored in Google Sheets.
- Uses Google Gemini AI + memory for accurate replies.
- Sends automated responses back via Gmail.

---

## 📂 Repository Contents


---

## 🔧 Import Workflow into n8n
1. Open your **n8n Desktop** (or cloud instance).  
2. Click **Workflows → Import from File**.  
3. Upload `workflows/email_support_automation.json`.  
4. Reconnect credentials:
   - Gmail OAuth2  
   - Google Sheets OAuth2  
   - Google Gemini (PaLM) API  

---

## ⚙️ Workflow Overview
**Nodes used:**
1. **Gmail Trigger** → listens for new support emails.  
2. **Limit** → controls concurrency.  
3. **Edit Fields (Set node)** → extracts `From`, `Subject`, `threadId`, and body.  
4. **Wait** → optional 2s delay.  
5. **AI Agent** → main orchestrator node.  
   - Uses:
     - **Google Gemini Chat Model**
     - **Simple Memory**
     - **Google Sheets (Get Rows)**
     - **Send Gmail Message**  
6. **Google Sheets (Get Rows)** → retrieves historical Q&A.  
7. **Send a message in Gmail** → replies with AI-generated answer.  

---

## 🔒 Security
- All credentials are stripped from the workflow file.  
- Add your own **Gmail OAuth2**, **Google Sheets**, and **Gemini API keys** in n8n.  
- Do not commit secrets to GitHub.  

---

## 📌 Deployment
- **Local Testing**: n8n Desktop (used in this project).  


