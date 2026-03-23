# Kharcha — Budget Planner

A sleek, Light-themed personal finance dashboard with Firebase persistence.

## Features
- 📊 Dashboard with KPI cards + charts (Pie, Bar, Line)
- ➕ Add income / expense entries with categories
- 📋 Transactions list with category filters
- 🎯 Savings goals with progress bars
- 🔥 Firebase Auth (anonymous) + Firestore persistence
- 📱 Responsive design

## Setup (Firebase)

1. Go to https://console.firebase.google.com → create a new project
2. Enable **Anonymous Authentication** (Auth → Sign-in method → Anonymous)
3. Create a **Firestore Database** (start in test mode)
4. Project Settings → Your apps → Add web app → copy the config
5. Open `index.html`, find `firebaseConfig` (~line 15) and paste your keys

```js
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  ...
};
```

6. Firestore Security Rules:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{col}/{docId} {
      allow read, write: if request.auth != null
        && request.auth.uid == resource.data.userId;
      allow create: if request.auth != null
        && request.auth.uid == request.resource.data.userId;
    }
  }
}
```

> Without Firebase config, the app runs in **Demo Mode** with sample data  no setup needed to previe
> 
 # THE BRATS (Ashvini Goswami and  Jyotirmoy Mahapatra)
