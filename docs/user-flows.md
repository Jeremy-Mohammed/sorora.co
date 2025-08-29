# User Flows – Sorora.co

## Overview
The following diagrams and steps illustrate how a user navigates the Sorora.co app.  

---

## Authentication Flow
1. User opens app → Login screen.  
2. If new, they go to **Create Account**.  
3. If returning, they log in.  
4. If password forgotten → **Forgot Password** flow triggers email reset.  

---

## SOS Flow
1. User opens **Home Screen**.  
2. User taps **SOS button**.  
3. App retrieves current location.  
4. App opens native SMS app with **pre-filled alert message + location**.  
5. User taps send → emergency contacts notified.  

---

## Emergency Contacts Management
1. User navigates to **Customization → Emergency Contacts**.  
2. Options: **Add Contact**, **Edit Contact**, **Remove Contact**.  
3. Changes update **Firestore** in real time.  
4. Updated contacts immediately available for SOS.  

---

## Settings Flow
1. User opens **Settings screen**.  
2. Options: **About Us**, **Delete Account**, Notification preferences, etc.  
3. Delete Account requires confirmation ("type DELETE") → triggers Firebase Auth deletion.  
