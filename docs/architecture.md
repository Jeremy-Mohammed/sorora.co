# System Architecture – Sorora.co

## Overview
Sorora.co is a mobile application built with **React Native (Expo)** and powered by **Firebase** services.  
The architecture emphasizes **real-time communication, security, and accessibility**.

---

## Architecture Diagram
*(Insert diagram image here: e.g. ./architecture-diagram.png)*  

High-level flow:
1. **Mobile App (React Native)** – User interacts via authentication, SOS button, customization, and settings.
2. **Firebase Authentication** – Manages user login, account creation, and secure sessions.
3. **Firebase Firestore** – Stores emergency contacts, user settings, and alert messages.
4. **Firebase Cloud Functions (optional)** – For server-side logic such as notifications or advanced SOS handling.
5. **Device APIs (via Expo)** – Location services, SMS messaging, push notifications.

---

## Key Notes
- All data is scoped to the **authenticated user**.
- Real-time updates ensure contacts and settings are synced instantly.
- The design is modular for adding future integrations (e.g., smart devices, neighborhood watch).
