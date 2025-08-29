# Database Schema – Sorora.co

## Firestore Structure

Sorora.co stores user and contact data in **Firestore**. Below is the current structure:

---

## Users Collection

**Collection:** `Users`  
**Document ID:** `uid` (unique ID from Firebase Auth)

**Fields under each `uid`:**

| Field          | Example Value                     | Type      | Description                        |
|----------------|----------------------------------|-----------|------------------------------------|
| `address`      | `"123 Main Street"`               | string    | User's home address                |
| `birthday`     | `"1990-01-01T00:00:00.000Z"`     | string    | User's birthday (ISO string)       |
| `email`        | `"user@example.com"`              | string    | User email (unique identifier)     |
| `gender`       | `"female"`                        | string    | User gender                        |
| `maritalStatus`| `"single"`                        | string    | Marital status                     |
| `name`         | `"Jane Doe"`                      | string    | User display name                  |
| `phone`        | `"5551234567"`                    | string    | User phone number                  |
| `postal`       | `"A1B2C3"`                        | string    | Postal/ZIP code                    |
| `updatedAt`    | `"2025-08-25T22:30:00.000Z"`     | timestamp | Last profile update                |

---

## Contacts Subcollection

**Collection path:** `Users/{uid}/contacts`  
**Document ID:** random generated ID per contact

**Fields under each contact document:**

| Field          | Example Value  | Type      | Description                        |
|----------------|----------------|-----------|------------------------------------|
| `name`         | `"John Smith"` | string    | Contact’s name                     |
| `phoneNumber`  | `"5559876543"` | string    | Contact’s phone number             |

---

## Notes
- Each user document is linked to their **contacts** via the `contacts` subcollection.  
- Phone numbers are **validated** before saving to Firestore.  
- Real-time updates ensure emergency contacts are immediately available for SOS alerts.  
- This structure allows flexibility for adding additional fields per user or per contact in the future (e.g., groups, custom labels, or alert preferences).  
