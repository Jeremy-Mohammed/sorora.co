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
4. App checks for any **custom alert message** set by the user.  
5. App opens native SMS app with **pre-filled alert message + location**.  
6. User taps send → emergency contacts notified.  

---

## Emergency Contacts Management
1. User navigates to **Customization → Emergency Contacts**.  
2. Options: **Add Contact**, **Edit Contact**, **Remove Contact**.  
3. Changes update **Firestore** in real time.  
4. Updated contacts immediately available for SOS.  

---

## Settings Flow
1. User opens **Settings screen**.  
2. Options: **About Us**, **Delete Account**, etc.  
3. Delete Account requires confirmation ("type DELETE") → triggers Firebase Auth deletion.  

---

## Profile Flow
1. User navigates to **Profile screen**.  
2. Options: **Change Name**, **Update Email**, **Update Phone Number**, etc.
3. App validates inputs (e.g., email format, phone number length).  
4. On success → data saved to **Firestore** and synced with account.  
5. Updated information is reflected across the app (e.g., messages, contacts).  
