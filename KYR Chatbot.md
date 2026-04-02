
---

# 🧾 **Hackathon Project Report: KYR Chatbot (Know Your Rights)**

---

## 👥 Team Details

- **Project Name:** KYR Chatbot – Know Your Rights
    
- **Domain:** Legal Awareness / AI for Social Good
    
- **Tech Stack:** React + TypeScript, FastAPI, Gemini 2.0 Flash, FAISS, Tailwind CSS
    
- **Team Type:** Solo (or fill in teammates)
    

---

## 📌 Problem Statement

Millions of Indian citizens are unaware of their **fundamental rights** under the Constitution. Legal information is often:

- Complex and full of jargon
    
- Scattered across hard-to-read government portals
    
- Inaccessible to non-lawyers and students
    

This lack of awareness leads to exploitation, injustice, and hesitation in seeking help — especially for youth, women, and underserved groups.

---

## 💡 Proposed Solution: KYR Chatbot

**KYR (Know Your Rights) Chatbot** is an AI-powered legal assistant that:

- Answers questions about the **Indian Constitution**
    
- Helps users understand their **legal rights**
    
- Responds to **real-life legal scenarios** like harassment, denial of services, or discrimination
    
- Cites relevant **constitutional articles**
    

---

## 🧠 Key Features

| Feature                     | Description                                                           |
| --------------------------- | --------------------------------------------------------------------- |
| ⚙️ RAG Architecture         | Combines FAISS (vector search) + Gemini 2.0 Flash (LLM)               |
| 📚 Legal Base: Constitution | Based on real, structured data from the Indian Constitution           |
| 💬 Chat UI                  | Beautiful React-based chat with avatars, scroll, and typing animation |
| ⚖️ Case Scenario Handling   | Understands real-world issues and suggests rights + actions           |
| 🔒 Scope Restricted         | Ignores non-legal/off-topic queries                                   |
| 🪙 Cost Efficient           | Uses minimal Gemini tokens — backend handles most logic               |

---

## 🧱 Architecture Overview

```plaintext
User ↔ React Chat UI ↔ FastAPI Backend
                      ↓
            FAISS + Sentence Embeddings
                      ↓
         Gemini 2.0 Flash (LLM) with legal context
                      ↓
       Constitution-grounded response + article citation
```

---

## 🛠️ Tech Stack

|Layer|Tools Used|
|---|---|
|Frontend|React, TypeScript, Tailwind CSS|
|Backend|FastAPI (Python)|
|Search|FAISS + Sentence Transformers|
|LLM|Gemini 2.0 Flash (Google AI)|
|Hosting|Localhost (demo)|

---

## 🚀 How It Works

1. User submits a query or legal problem
    
2. Backend retrieves the most relevant Constitution entries using **FAISS**
    
3. These are passed with the query into **Gemini 2.0 Flash**
    
4. Gemini generates a conversational legal answer, citing relevant **articles**
    
5. The styled chat UI displays it with avatars, source, and smooth UX
    

---

## 📊 Results & Impact

- ✅ Constitution made conversational
    
- 🧾 Cites real Articles like 14, 19, 21 in answers
    
- 🎓 Friendly for students and non-lawyers
    
- 🔒 Prevents misuse via off-topic blocking
    
- 🧠 Handles real issues like harassment, freedom, discrimination
    

---

## 🔮 Future Scope

- IPC & CrPC integration
    
- Multilingual support (Hindi, Marathi, Tamil...)
    
- Chat history + bookmarking
    
- Mobile app version
    
- Link to legal aid NGOs or real lawyers
    

---

## 📸 Demo Screenshots

Question:
![[Pasted image 20250419112034.png]]


Response:
![[Pasted image 20250419112129.png]]     

---

## 🙏 Acknowledgements

- Google Gemini API (Generative AI)
    
- Open-source NLP tools (FAISS, Sentence Transformers)
    
- Government of India for open legal data
    
- Hackathon mentors & organizers
    

---

## 🧾 Conclusion

**KYR Chatbot bridges the gap between people and their rights.**  
With AI and accessible design, we empower users to protect themselves, ask smart legal questions, and understand their place in the Constitution — one message at a time.

---

