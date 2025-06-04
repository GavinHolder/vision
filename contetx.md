
# ✅ Refined App Spec: `Vision`

Your personal **WISP/FNO task, job & ops brain**, with integrated AI, reminders, and mobile-friendly flow.

---

## 🚀 CORE SYSTEM MODULES (with your new additions)

---

### 1. 🔁 OPERATIONS DAILY COMMAND DASHBOARD

> Desktop + Mobile + Web optimized. Loads instantly with **daily brief**.

#### Shows:

* 🔔 **Smart Notifications** (grouped, colour-coded by urgency)
* 📋 **Today’s Tasks**
* 🧠 **AI Insights & Suggestions** (more below)
* 🛠️ **Open Jobs Snapshot** (FNO, WISP, civil support)
* 🧾 **Pending Approvals**
* 💬 **New Internal Messages**
* 📦 **Stock Warnings / Low Inventory**
* 📅 **Events Today / Tomorrow**
* 🎤 **Voice Note Inbox → Tasks**

#### AI-Powered Memory Aid:

* “Remind me again why we delayed Tower 7 repairs?”
* → Shows task history, linked messages, decisions.

---

### 2. 🎤 VOICE-TO-TASK/JOB INPUT SYSTEM

> You’re in the field or driving — speak and it captures the job.

#### How it works:

1. You press “Record Task” on mobile.
2. Speech-to-text converts your voice to a draft task/job.
3. AI parses and:

   * Tags it as Job, Task, Meeting Note, Reminder, etc.
   * Links it to existing project/job if relevant.
   * Suggests deadlines or team members.

#### Example:

> “Need to get trenching team to Kabelkop by Friday, 30 meters, fix burst pipe.”

→ Auto-created:

* Job: “Civil Repair – Kabelkop trench”
* Location: Kabelkop
* Deadline: Friday
* Assigned: Civil Team
* Notes: “Fix burst pipe, 30m”

---

### 3. 🤖 AI INSIGHTS ENGINE

Integrated assistant trained on:

* Your historical data (jobs, teams, times)
* Industry patterns
* Your voice/task style

#### Examples:

* **Suggests best team** for job based on past performance
* Warns: “This job sounds similar to last month’s issue at Tower 4”
* Detects repetitive tasks → proposes automation
* “Task open >7 days without reply – suggest escalation?”

✅ Future scope: add ChatGPT plugin access or internal fine-tuned assistant.

---

### 4. 📦 ADVANCED STOCK MANAGEMENT SYSTEM

Now upgraded for:

* 🧭 Two companies: **WISP** and **FNO**
* 💸 Tracks **stock value**, movement, and usage
* 🏷 Labels:

  * "Company Ownership" (WISP or FNO)
  * "Category" (Radio, Fibre, Tools, Civil Materials)
  * "Assigned To" (Team, Site, Job)
  * "Condition" (New, Used, Broken)
  * "Restock Threshold"
* 📥 Issue Logs: what was used, where, when, why
* 🧾 Purchase orders linked to supplier + invoice files
* 💰 Stock Valuation Dashboard:

  * Total value held per company
  * Monthly movement
  * Damaged/lost asset reports

---

### 5. 📧 NOTIFICATION & REMINDER SYSTEM (Non-Overbearing)

> Your **external brain**, but *not annoying*.

#### Core Logic:

* Daily summary email at 07:00: Open tasks, new jobs, unread messages
* Smart re-notifications:

  * Only reminds if no action logged in X hours
  * Escalation notifications based on priority + delays
* Channels:

  * Email
  * In-app
  * Telegram/WhatsApp (optional)
* Calendar-based:

  * Scheduled nudges on deadlines
  * Slack off? It bumps the reminder up based on importance

#### Example:

* “Tower Team has not uploaded job report for Job #112 – 2 days late. Want to nudge them now?”

---

### 6. 📝 ROBUST TODO SYSTEM

More than just a checklist.

#### Features:

* [ ] Checklist mode with subtasks
* ⬆️ Priority tags (High / Medium / Low)
* 🔗 Linked to: Jobs, Notes, Calendar, Civil Jobs, Meeting Notes
* 📎 Attach files/voice notes
* 💬 Add internal chat to each item
* 🗂️ Group by:

  * Today / This Week / Overdue
  * By project
  * By company (WISP/FNO)
* 📱 Works offline (PWA optional)

#### Example:

> “FNO Weekly Ops TODO”

* [x] Approve 400m fibre purchase
* [ ] Confirm trench route at Mamelodi
* [ ] Send update to municipal contact (Remind Tuesday)

---

### 7. 🧾 TASK/PROJECT/JOB CREATION — ULTRA MOBILE-FRIENDLY UI

### Mobile-first creation:

* Big buttons: “+ Task”, “+ Job”, “+ Note”, “+ Voice”
* One-hand input (easy on-site or in bakkie)
* Presets to speed up input:

  * “Assign to Civil”
  * “Urgent + due this week”
  * “Send daily reminder”

✅ All forms have:

* File upload
* Voice support
* Auto-linking to calendar & teams
* Smart suggestions from AI assistant

---

## 🔒 Optional Future Enhancements

| Feature                  | Value                                                         |
| ------------------------ | ------------------------------------------------------------- |
| ONT/OLT Device Sync      | Auto-ping gear, flag unreachable ones                         |
| ICASA Compliance Module  | Store license docs, alert on renewal                          |
| SLA Expiry Tracker       | Warn when 3rd-party SLAs expire                               |
| Budget Module            | Tie civil job expenses + materials to cost centres            |
| PDF Jobcards             | Generate printable job cards for paper-based sites            |
| WhatsApp API Integration | Send stock confirmations or civil check-in links via WhatsApp |

---

## 🛠 NEXT STEPS (You Pick)

Would you like me to:

1. **Design a UI wireframe** flow (HTML+Tailwind or Figma style)?
2. **Scaffold Django models** and admin panels for this spec?
3. **Build Docker starter** project with Celery, Redis, auth, job/task CRUD?

Just say the word, my bru. This is now a full personal **COO operations hub**, not a toy. Let's build it to take pressure off your plate daily.


****

Detailed breakdown:
Project Context 
________________________________________
1. Development Guidelines
1.	Technology Stack
o	Framework: Django (latest stable release)
o	Language: Python (latest stable release)
o	Frontend:
	Use HTMX for HTML templates.
	Separate all CSS and JavaScript files from templates.
	Create a common base template; extend it in each app.
o	Signalling:
	Celery to be used for where possible to off load subtasks and notifications to
o	Server:
	Use WSGI (wsgi.py) to initialize signals.
2.	File & Module Structure
o	File Naming: Always state which files need editing/amending when making changes.
o	App-by-App Workflow:
	Begin with the Dashboard app—complete its structure, templates, and logic.
	Only proceed to the next app (e.g., Job Management, Inventory) after confirming completion of the current app.
o	Modularity & Isolation:
	Each Django app must contain its own models, views, templates, static files, and business logic.
	Do not place inventory logic (models, views, templates) in an unrelated app.
	Enable/disable entire apps at runtime for maintenance without affecting other apps.
3.	Notifications & Email Processing
o	Always use Django signals for any notification or email task.
o	Signals must run in their own thread/subprocess to avoid blocking the main request thread.
o	Centralize all signal definitions and handlers under a designated folder (e.g., /signals/).
4.	ORM & Performance
o	Design models and queries for efficiency and scalability.
o	Avoid N+1 query patterns: use select_related and prefetch_related as needed.
o	Denormalize only when justified by performance metrics.
________________________________________
2. Core Application (“Vision”) Overview
A WISP/FNO Task & Operations Hub with AI integration, mobile-friendly UI, and non-obtrusive notifications.
2.1. Operattions Daily Command Dashboard
•	Purpose: Single screen to review everything daily (tasks, notifications, jobs, messages, stock alarms).
•	Sections:
1.	Smart Notifications (grouped, color-coded by urgency)
2.	Today’s Tasks (personal + team)
3.	AI Insights & Suggestions (contextual prompts, history lookups)
4.	Open Jobs Snapshot (FNO, WISP, civil support)
5.	Pending Approvals (job sign-offs, budget sign-offs)
6.	New Internal Messages (chat inbox, email inbox to send and receive emails as well )
7.	Stock Warehouse & Warnings (low inventory alerts and stock warehousing for both WISP and FNO)
8.	Events Calendar (today/tomorrow events, also to keep track where FNO civil jobs and projects are)
9.	WISP/FNO Project Management ( grouping of task, teams, jobs, communictaion and stock based on a project scope )
10.	Voice Note Inbox (uncategorized voice recordings → tasks)
•	Mobile & Web Optimized:
o	Instant loading (minimal requests).
o	Responsive layout (bootstrap/HTMX).
2.2. Voice-to-Task/Job Input System
•	Workflow:
1.	User taps “Record Task” on mobile.
2.	Frontend records audio, sends to backend.
3.	Backend uses Speech-to-Text → generates draft task.
4.	AI processor tags:
	Category: Job, Task, Meeting Note, Reminder.
	Metadata: Location, Deadline, Suggested Team.
5.	Task is stored; user can review/edit immediately.
•	Signal Use:
o	After transcription, send signal to tasks.signals.handle_new_voice_input for parsing & categorization.
o	Do not block HTTP response; spawn in separate thread.
2.3. AI Insights Engine
•	Data Sources:
o	Historical tasks/jobs database.
o	Industry-specific patterns (e.g., typical turnaround times).
o	User’s voice/task style (trained over time).
•	Functionalities:
o	Team Recommendation: “Based on past performance, assign to Civil Team.”
o	Issue Detection: “This resembles last month’s Tower-4 outage—flag for review.”
o	Automation Suggestions: “Task open >7 days without updates—suggest escalation.”
•	Integration Points:
o	On task creation or update, fire a signal to ai_engine.signals.generate_insights.
o	Insights are stored in a dedicated table and surfaced on the Dashboard.
2.4. Advanced Stock Management
•	Multi-Company Support:
o	Track stock separately for WISP and FNO under one system.
•	Data Model:
o	StockItem: id, name, category (Radio/Fibre/Tools/Civil), company (WISP/FNO), quantity, unit_cost, condition (New/Used/Broken), restock_threshold
o	StockLog: id, stock_item, change_qty, timestamp, reason, related_job (nullable), user
o	PurchaseOrder: id, supplier, total_cost, date_ordered, invoice_file
o	Serial Number tracking:  link serial number to supplier and item
•	Features:
1.	Inventory Dashboard:
	Total stock on hand value per company
	Monthly movements (in/out)
	Damaged/lost item reports
2.	Issue Logging: Automatic signal on stock decrement → stock.signals.log_stock_issue.
3.	Restock Alerts: If quantity ≤ restock_threshold, trigger email/in-app notification via signals.
2.5. Notification & Reminder System
•	Mechanics:
o	Daily Summary Email (07:00 local time):
	Open tasks, new jobs, unread messages.
o	Conditional Re-notifications:
	Only if no action in X hours (configurable).
	Priority-based escalation.
o	Channels:
	Email (Django’s send_mail)
	In-app (Notification model + UI overlay)
	Optional: Telegram/WhatsApp webhook integration.
•	Scheduling:
o	Use Django cron (or Celery beat) tasks to send scheduled reminders.
o	Each scheduled job fires a signal to notifications.signals.send_reminder.
•	Customization:
o	User preference toggles: frequency, channels, quiet hours.
o	For each task/job, store last_notified_at to prevent spam.
2.6. Robust To-Do System
•	Data Model:
o	ToDoItem: id, title, description, priority (High/Med/Low), status (Open/Done), due_date, created_by, assigned_to (nullable), related_job (nullable), related_stock_item (nullable), attachments
o	SubTask: id, parent_todo, title, status
•	Features:
1.	Checklist & Subtasks (nested ToDo).
2.	Priority Tags (High/Medium/Low).
3.	Linking:
	Jobs, Civil Jobs, Meeting Notes, Calendar events.
4.	Grouping & Filters:
	Today / This Week / Overdue
	By Project / By Company (WISP / FNO)
5.	Attachments: File and voice note uploads.
•	Offline Support:
o	Use PWA techniques or service worker to cache open To-Dos.
o	Sync changes when online.
2.7. Mobile-Friendly Task/Project Creation UI
•	Key Elements:
o	Big Buttons: “+ Task”, “+ Job”, “+ Note”, “+ Voice”
o	One-Hand Input: Forms optimized for thumb reach.
o	Presets & Smart Suggestions:
	“Assign to Civil Team”
	“Urgent + Due This Week”
	“Auto-send daily reminder”
o	Common Form Elements:
	File upload
	Voice memo attachment
	Auto-linking to calendar & teams
	AI-powered field suggestions
•	UX Details:
o	HTMX-driven, minimal page reloads.
o	Progressive form validation & inline error messages.
________________________________________
3. AI Context Instructions
Use the above guidelines as your source of truth. Whenever you (the AI assistant) suggest code changes, scaffolding, or architectural decisions, ensure that you:
1.	Adhere Strictly to the “Development Guidelines” (Section 1).
2.	Follow the Modular App Structure (Section 2) in the specified order: Dashboard → Voice-to-Task → AI Engine → Stock → Notifications → To-Do → Mobile UI.
3.	Always mention which files (e.g., models.py, views.py, signals.py, templates/<app>/…, static/<app>/css/…, static/<app>/js/…) need to be created or modified.
4.	Use Django signals for any background task (notifications, email, voice parsing, stock alert).
5.	Keep all CSS/JS separate from templates—never inline.
6.	Ensure ORM queries are performant—no N+1.
7.	Allow enabling/disabling of each app in INSTALLED_APPS (e.g., via a feature flag or config) without impacting other modules.
8.	Bootstrap 5.3.6 new features one app at a time only after confirming the prior app’s completion.
Whenever you produce code or architectural guidance, list the exact file paths and code snippets. If any suggestion deviates from these guidelines, be sure to justify why it’s necessary.

