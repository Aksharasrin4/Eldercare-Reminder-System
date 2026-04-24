# 🏥 Eldercare Reminder System

> An AI-powered prescription & diet reminder system for elderly patients — built with **Dify**, **Gemini API**, **Docker**, and **Google Calendar**.

---

## 📌 Overview

The **Eldercare Reminder System** is a GenAI application that helps elderly patients manage their daily medications and diet plans. The system reads doctor prescriptions and nutritionist plans, then generates personalized, friendly reminders delivered directly through **Google Calendar events**.

---

## ✨ Features

- 💊 **Medication Reminders** — Extracts medicine names, dosages, and timings from prescriptions
- 🥗 **Diet Plan Reminders** — Schedules meal and nutrition alerts from nutritionist plans
- 📅 **Google Calendar Integration** — Reminders appear as calendar events on the patient's device
- 🤖 **AI-Powered** — Uses **Gemini API** via Dify to generate warm, friendly reminder messages
- 🐳 **Dockerized** — Fully containerized for easy local or cloud deployment

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| AI Platform | [Dify](https://dify.ai) |
| LLM | Google Gemini (via Gemini API) |
| Reminder Delivery | Google Calendar API |
| Containerization | Docker & Docker Compose |
| Workflow Definition | YAML |

---

## 🏗️ Architecture

```
User Input (Name, Prescriptions, Diet Plan)
        ↓
    Dify Workflow
        ↓
  Gemini API (LLM)
  → Generates friendly reminder schedule
        ↓
  Google Calendar API
  → Creates calendar events with reminders
        ↓
Patient receives alerts on phone/desktop 📱
```

---

## 🚀 Getting Started

### Prerequisites

- Docker & Docker Compose installed
- A [Google Gemini API key](https://aistudio.google.com/app/apikey)
- A Google Cloud project with **Google Calendar API** enabled
- OAuth 2.0 credentials (`credentials.json`) from Google Cloud Console

---

### 1. Clone the Repository

```bash
git clone https://github.com/AksharaSrin4/Eldercare-Reminder-System.git
cd eldercare-reminder-system
```

### 2. Set Up Environment Variables

Copy the example env file and fill in your credentials:

```bash
cp .env.example .env
```

Edit `.env`:

```env
GEMINI_API_KEY=your_gemini_api_key_here
GOOGLE_CALENDAR_ID=your_calendar_id@gmail.com
```

### 3. Add Google Calendar Credentials

Place your `credentials.json` (OAuth 2.0) from Google Cloud Console in the root directory:

```
eldercare-reminder-system/
├── credentials.json   ← Place here
├── docker-compose.yml
└── ...
```

> **Note:** `credentials.json` is in `.gitignore` — never commit it to GitHub.

### 4. Run with Docker

```bash
docker-compose up -d
```

Dify will be available at: `http://localhost`

### 5. Import the Dify Workflow

1. Open Dify at `http://localhost`
2. Go to **Studio → Import DSL**
3. Upload `workflow/elderly_reminder.yml`
4. Set your **Gemini API key** in Dify's Model Provider settings
5. Run the workflow!

---

## 📂 Project Structure

```
eldercare-reminder-system/
│
├── workflow/
│   └── elderly_reminder.yml       # Dify workflow definition
│
├── docs/
│   └── Eldercare_Reminder_System.pptx  # Project presentation
│
├── docker-compose.yml             # Docker setup for Dify
├── .env.example                   # Environment variable template
├── .gitignore                     # Ignores secrets & build files
└── README.md                      # This file
```

---

## 🔄 Workflow Details

The Dify workflow (`elderly_reminder.yml`) does the following:

| Step | Node | Description |
|------|------|-------------|
| 1 | **Input** | Collects user info, prescriptions, and diet plan |
| 2 | **LLM (Gemini)** | Generates a warm, emoji-rich daily reminder message |
| 3 | **Scheduler** | Triggers daily at 7:00 AM |
| 4 | **Calendar Action** | Creates Google Calendar events for each reminder |

### Example Output

```
🌞 Good morning, Margaret!

⏰ 8:00 AM  - Take your Vitamin D with a glass of water 💊
🍎 9:00 AM  - Enjoy your oatmeal with fresh fruits 🥣
💊 1:00 PM  - Time for your Blood Pressure pill
🫖 3:00 PM  - Green tea and a light snack
🌙 9:00 PM  - Take your evening Calcium tablet
```

---

## 🔐 Security Notes

- **Never commit** `credentials.json`, `.env`, or any API keys to GitHub
- Use `.gitignore` (provided) to keep secrets safe
- For production, use a secrets manager (e.g., Google Secret Manager)

---

## 🔮 Future Enhancements

- [ ] WhatsApp / SMS reminder delivery
- [ ] Voice assistant integration (Google Assistant)
- [ ] Caregiver dashboard for monitoring
- [ ] Multi-language support
- [ ] Integration with pharmacy refill systems

---

## 📊 Project Presentation

See [`docs/Eldercare_Reminder_System.pptx`](docs/Eldercare_Reminder_System.pptx) for the full project walkthrough.

---

## 🙏 Acknowledgements

- [Dify](https://dify.ai) — Open-source LLM app development platform
- [Google Gemini](https://deepmind.google/technologies/gemini/) — Generative AI model
- [Google Calendar API](https://developers.google.com/calendar) — Reminder delivery

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
