# API Design – Sorora.co

## Overview
Sorora.co primarily uses **Firebase services** (Firestore, Authentication) and **Expo APIs**.  
This document outlines expected operations, inputs, and outputs based on the current database schema.

---

## Authentication

### Create Account
- **Input:** `name`, `email`, `password`, `phone`, `birthday`, `gender`, `maritalStatus`, `address`, `postal`  
- **Action:** Creates a new user in Firebase Auth and stores additional profile fields in Firestore under `Users/{uid}`.  
- **Response:** User document created in Firestore with all fields, plus `uid`.  

### Login
- **Input:** `email`, `password`  
- **Action:** Firebase Auth login  
- **Response:** Firebase user object with `uid`  

### Forgot Password
- **Input:** `email`  
- **Action:** Firebase triggers password reset email  
- **Response:** Confirmation of email sent  

---

## Firestore Data Operations

### Get User Profile
- **Path:** `Users/{uid}`  
- **Action:** Retrieve all profile fields (`name`, `email`, `phone`, `birthday`, `gender`, `maritalStatus`, `address`, `postal`, `updatedAt`)  
- **Response:** JSON object of user data  

### Update User Profile
- **Path:** `Users/{uid}`  
- **Input:** Any combination of profile fields to update  
- **Action:** Validate inputs (e.g., email format, phone number format) → Update Firestore  
- **Response:** Confirmation + updated document  

---

## Emergency Contacts

### Get Contacts
- **Path:** `Users/{uid}/contacts`  
- **Action:** Retrieve all contact documents  
- **Response:** Array of contacts with `name` and `phoneNumber`  

### Add Contact
- **Path:** `Users/{uid}/contacts/{contactId}`  
- **Input:** `name`, `phoneNumber`  
- **Action:** Validate phone number → Add document to subcollection  
- **Response:** Confirmation + new contact document ID  

### Update Contact
- **Path:** `Users/{uid}/contacts/{contactId}`  
- **Input:** `name` and/or `phoneNumber`  
- **Action:** Validate inputs → Update contact document  
- **Response:** Updated document  

### Delete Contact
- **Path:** `Users/{uid}/contacts/{contactId}`  
- **Action:** Delete the document  
- **Response:** Confirmation of deletion  

---

## Device API Calls (via Expo)

### Send SOS SMS
- **Input:** List of contact `phoneNumber`s, custom alert message, live location (`latitude`, `longitude`)  
- **Action:** Open native SMS app with prefilled message to selected contacts  
- **Response:** User confirms sending via native app  

### Get Current Location
- **Input:** Location permission granted  
- **Action:** Fetch GPS coordinates  
- **Response:** `latitude`, `longitude`, timestamp  

---

## Notes
- All Firestore operations are **scoped to the authenticated user**.  
- Phone numbers and emails are **validated** before saving to Firestore.  
- Real-time updates ensure the app always has the latest profile and contact information.  
