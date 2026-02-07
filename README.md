<!-- Improved compatibility of back to top link -->
<a id="readme-top"></a>

<div align="center">

  <img src="https://github.com/MJ-998201/cheap-attendace/blob/3d6a997d8550d23cf23d6de756f3fd7aea2e9c76/1757330910815_Nero_AI_Image_Upscaler_Photo_Face%20(1).png" alt="AttendAce Logo" width="200" height="200" />

  # AttendAce 🎯  
  ### Attendance. Without hardware. Without loopholes. Without creepiness.

  <p>
    AttendAce is a session-driven attendance system built for real classrooms — where devices fail, rooms change, and students try everything.
  </p>

  <p>
    <a href="#about-the-project"><strong>Explore the Project »</strong></a>
    <br />
    <br />
    <a href="#demo">View Demo</a>
    ·
    <a href="#roadmap">Roadmap</a>
    ·
    <a href="#reporting-issues">Report Bug</a>
  </p>

</div>

---

## 📌 Table of Contents

- [About The Project](#about-the-project)
- [Core Idea](#core-idea)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [How It Works](#how-it-works)
- [Security + Privacy](#security--privacy)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Usage](#usage)
- [API Flow](#api-flow)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🧠 About The Project

Most attendance systems start with a **device**:  
Fingerprint scanners. RFID machines. Hardware terminals stuck to a wall.

AttendAce starts with a different question:

> What if attendance isn’t a *place*…  
> What if attendance is a *moment*?

AttendAce is built around **time, identity, and verification** — not rooms, machines, or physical lock-in.

### ✨ What AttendAce Solves

✅ No dependency on a physical device  
✅ No “machine was down today” excuse  
✅ No location-locking  
✅ No screenshot QR cheating  
✅ No face images stored  
✅ No silent failures

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## ⏳ Core Idea

### **Time Over Place**

AttendAce does not care where you are.  
It cares about:

- **Who** you are  
- **When** the class is live  
- Whether verification happens **inside the active session window**
- Whether the context makes sense

> Attendance is not a location.  
> Attendance is a session.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🧰 Tech Stack

### Backend
- Node.js
- Express.js
- REST APIs
- MySQL (connection pooling + env configs)
- JWT Authentication
- Role-Based Access Control (RBAC)
- OTP Verification
- HTTPS (SSL)

### Frontend
- Plain HTML (role-specific pages)
- Tailwind CSS
- Vanilla JavaScript

### Face Recognition (Privacy First)
- face-api.js
- TensorFlow.js
- Tiny Face Detector
- Face descriptors (vectors only)

### Communication / Alerts
- Email (OTP + notices)
- Telegram Bot: **HEDWIG 🦉**
  - Dev alerts for feedback + bug reports

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🏗️ System Architecture

AttendAce is built with one rule:

> Backend and frontend are separate worlds.  
> They communicate.  
> They do not share state.  
> They do not trust each other.

### Backend Structure
### Frontend Structure
<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## ⚡ How It Works

### 1) Teacher Starts the Story
- Teacher activates a class
- A session becomes live
- QR becomes valid
- Clock starts ticking

### 2) Student Enters
- Student scans QR
- Face verification runs **locally in browser**
- Request hits backend
- Backend checks all conditions
- Attendance is recorded only if everything passes

### 3) Session Ends
- Teacher deactivates the class
- QR dies instantly
- Attendance stops immediately

> No grace periods.  
> No background jobs.  
> No ambiguity.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🧾 Attendance Engine (The Important Part)

Attendance is not a button.  
It is a checklist.

### ✅ Required Conditions

- Valid JWT token  
- Correct role  
- Active class session  
- Valid QR context  
- Successful face match  

### ❌ Fail Fast Rule

If any condition fails:

- No attendance is recorded
- No partial database writes
- No “almost”

Database writes happen last. Always.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🧑‍🤝‍🧑 Roles & Permissions

Roles are **not UI suggestions**.  
They are enforced in backend middleware.

### Students cannot:
- Activate classes
- Generate QR codes
- View teacher analytics

### Teachers cannot:
- Mark attendance for themselves
- Register student faces
- Enroll in classes

If role is wrong → request dies early.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🧿 Face Recognition (Without Being Creepy)

AttendAce uses face recognition as **verification**, not surveillance.

### 🔒 Privacy Guarantees

✅ No face images stored  
✅ No face images sent to server  
✅ Only numerical vectors (descriptors) are stored  
✅ Matching happens locally in browser  

> The server never sees your face.  
> Only math.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 📷 QR Sessions (Why Screenshots Fail)

QR codes do not identify students.

They identify:

- Class
- Session
- Time window

They:
- expire
- rotate
- die instantly when session ends

> QR provides context.  
> Face provides identity.  
> Both are required.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🔔 HEDWIG — Telegram Dev Alerts

HEDWIG is not a chatbot.

It is a **signal pipe**.

Whenever users submit feedback or report issues:

- backend sanitizes the message
- pushes it to Telegram Bot API
- Hedwig posts instantly in the dev group

> No inbox fatigue.  
> No silent failures.  
> Visibility is instant.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🛡️ Security & Posture

Security in AttendAce is quiet and unforgiving.

Common failure points:
- invalid token
- expired token
- wrong role
- invalid OTP
- inactive session
- dead QR

If something works, it already passed multiple gates.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 🚀 Getting Started

### Prerequisites
Make sure you have:

- Node.js (LTS recommended)
- MySQL Server
- npm
- A browser (Chrome recommended for face-api.js)

---

## 🧩 Installation

### 1) Clone the repo
```sh
git clone https://github.com/<your-username>/AttendAce.git
cd AttendAce
